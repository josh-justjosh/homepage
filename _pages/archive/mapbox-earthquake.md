---
title: Mapbox Earthquake example
layout: page
published: false
---

<html>
<head>
<meta charset="utf-8">
<meta name="viewport" content="initial-scale=1,maximum-scale=1,user-scalable=no">
<link href="https://api.mapbox.com/mapbox-gl-js/v2.2.0/mapbox-gl.css" rel="stylesheet">
<script src="https://api.mapbox.com/mapbox-gl-js/v2.2.0/mapbox-gl.js"></script>
<style>
#map { width: 100%; height: 400pt }
</style>
</head>
<body>
<div id="map"></div>

<script>
	mapboxgl.accessToken = 'pk.eyJ1Ijoiam9zaC1qdXN0am9zaCIsImEiOiJja3A2eHdmajIwNGFvMndtcmNsbnZycm44In0.SvsoxpdU7NRLYLVRFIu2kw';
    var map = new mapboxgl.Map({
        container: 'map',
        zoom: 0.3,
        center: [0, 20],
        style: 'mapbox://styles/mapbox/light-v10'
    });

    map.addControl(new mapboxgl.NavigationControl());

    // filters for classifying earthquakes into five categories based on magnitude
    var mag1 = ['<', ['get', 'mag'], 2];
    var mag2 = ['all', ['>=', ['get', 'mag'], 2], ['<', ['get', 'mag'], 3]];
    var mag3 = ['all', ['>=', ['get', 'mag'], 3], ['<', ['get', 'mag'], 4]];
    var mag4 = ['all', ['>=', ['get', 'mag'], 4], ['<', ['get', 'mag'], 5]];
    var mag5 = ['>=', ['get', 'mag'], 5];

    // colors to use for the categories
    var colors = ['#fed976', '#feb24c', '#fd8d3c', '#fc4e2a', '#e31a1c'];

    map.on('load', function () {
        // add a clustered GeoJSON source for a sample set of earthquakes
        map.addSource('earthquakes', {
            'type': 'geojson',
            'data': 'https://docs.mapbox.com/mapbox-gl-js/assets/earthquakes.geojson',
            'cluster': true,
            'clusterRadius': 80,
            'clusterProperties': {
                // keep separate counts for each magnitude category in a cluster
                'mag1': ['+', ['case', mag1, 1, 0]],
                'mag2': ['+', ['case', mag2, 1, 0]],
                'mag3': ['+', ['case', mag3, 1, 0]],
                'mag4': ['+', ['case', mag4, 1, 0]],
                'mag5': ['+', ['case', mag5, 1, 0]]
            }
        });
        // circle and symbol layers for rendering individual earthquakes (unclustered points)
        map.addLayer({
            'id': 'earthquake_circle',
            'type': 'circle',
            'source': 'earthquakes',
            'filter': ['!=', 'cluster', true],
            'paint': {
                'circle-color': [
                    'case',
                    mag1,
                    colors[0],
                    mag2,
                    colors[1],
                    mag3,
                    colors[2],
                    mag4,
                    colors[3],
                    colors[4]
                ],
                'circle-opacity': 0.6,
                'circle-radius': 12
            }
        });
        map.addLayer({
            'id': 'earthquake_label',
            'type': 'symbol',
            'source': 'earthquakes',
            'filter': ['!=', 'cluster', true],
            'layout': {
                'text-field': [
                    'number-format',
                    ['get', 'mag'],
                    { 'min-fraction-digits': 1, 'max-fraction-digits': 1 }
                ],
                'text-font': ['Open Sans Semibold', 'Arial Unicode MS Bold'],
                'text-size': 10
            },
            'paint': {
                'text-color': [
                    'case',
                    ['<', ['get', 'mag'], 3],
                    'black',
                    'white'
                ]
            }
        });

        // objects for caching and keeping track of HTML marker objects (for performance)
        var markers = {};
        var markersOnScreen = {};

        function updateMarkers() {
            var newMarkers = {};
            var features = map.querySourceFeatures('earthquakes');

            // for every cluster on the screen, create an HTML marker for it (if we didn't yet),
            // and add it to the map if it's not there already
            for (var i = 0; i < features.length; i++) {
                var coords = features[i].geometry.coordinates;
                var props = features[i].properties;
                if (!props.cluster) continue;
                var id = props.cluster_id;

                var marker = markers[id];
                if (!marker) {
                    var el = createDonutChart(props);
                    marker = markers[id] = new mapboxgl.Marker({
                        element: el
                    }).setLngLat(coords);
                }
                newMarkers[id] = marker;

                if (!markersOnScreen[id]) marker.addTo(map);
            }
            // for every marker we've added previously, remove those that are no longer visible
            for (id in markersOnScreen) {
                if (!newMarkers[id]) markersOnScreen[id].remove();
            }
            markersOnScreen = newMarkers;
        }

        // after the GeoJSON data is loaded, update markers on the screen on every frame
        map.on('render', function () {
            if (!map.isSourceLoaded('earthquakes')) return;
            updateMarkers();
        });
    });

    // code for creating an SVG donut chart from feature properties
    function createDonutChart(props) {
        var offsets = [];
        var counts = [
            props.mag1,
            props.mag2,
            props.mag3,
            props.mag4,
            props.mag5
        ];
        var total = 0;
        for (var i = 0; i < counts.length; i++) {
            offsets.push(total);
            total += counts[i];
        }
        var fontSize =
            total >= 1000 ? 22 : total >= 100 ? 20 : total >= 10 ? 18 : 16;
        var r = total >= 1000 ? 50 : total >= 100 ? 32 : total >= 10 ? 24 : 18;
        var r0 = Math.round(r * 0.6);
        var w = r * 2;

        var html =
            '<div><svg width="' +
            w +
            '" height="' +
            w +
            '" viewbox="0 0 ' +
            w +
            ' ' +
            w +
            '" text-anchor="middle" style="font: ' +
            fontSize +
            'px sans-serif; display: block">';

        for (i = 0; i < counts.length; i++) {
            html += donutSegment(
                offsets[i] / total,
                (offsets[i] + counts[i]) / total,
                r,
                r0,
                colors[i]
            );
        }
        html +=
            '<circle cx="' +
            r +
            '" cy="' +
            r +
            '" r="' +
            r0 +
            '" fill="white" /><text dominant-baseline="central" transform="translate(' +
            r +
            ', ' +
            r +
            ')">' +
            total.toLocaleString() +
            '</text></svg></div>';

        var el = document.createElement('div');
        el.innerHTML = html;
        return el.firstChild;
    }

    function donutSegment(start, end, r, r0, color) {
        if (end - start === 1) end -= 0.00001;
        var a0 = 2 * Math.PI * (start - 0.25);
        var a1 = 2 * Math.PI * (end - 0.25);
        var x0 = Math.cos(a0),
            y0 = Math.sin(a0);
        var x1 = Math.cos(a1),
            y1 = Math.sin(a1);
        var largeArc = end - start > 0.5 ? 1 : 0;

        return [
            '<path d="M',
            r + r0 * x0,
            r + r0 * y0,
            'L',
            r + r * x0,
            r + r * y0,
            'A',
            r,
            r,
            0,
            largeArc,
            1,
            r + r * x1,
            r + r * y1,
            'L',
            r + r0 * x1,
            r + r0 * y1,
            'A',
            r0,
            r0,
            0,
            largeArc,
            0,
            r + r0 * x0,
            r + r0 * y0,
            '" fill="' + color + '" />'
        ].join(' ');
    }
</script>

</body>
</html>