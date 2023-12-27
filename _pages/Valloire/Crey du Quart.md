---
layout: blank
title: Valloire Crey du Quart
permalink: /valloire/crey-du-quart/
---
<style>
.Slopes {
    max-width: 127rem;
    margin: 0 auto
}

.Slopes-resume {
    display: none;
}

@media (max-width: 992px) {
    .Slopes-resume {
        flex-direction:column
    }
}

.Slopes-resumeInner {
    padding: 0.25rem 1rem 0;
    max-width: 90%
}

.Slopes-resumeList {
    width: 30rem;
    display: flex;
    flex-wrap: wrap
}

.Slopes-resumeList--Remontees {
    width: 50rem;
    max-width: 100%
}

.Slopes-resumePiste {
    display: flex;
    align-items: center;
    width: 10rem
}

.Slopes-resumeRemontee {
    width: 25rem;
}
p.Slopes-resumeRemontee {
    margin: 0.25rem 0;
}

.Slopes-secteur {
    margin-bottom: 0.25rem;
    flex-wrap: wrap;
    justify-content: space-between;
    display: flex
}

.Slopes-secteurList--pistes {
    columns: 2;
    max-width: 72rem
}

@media (max-width: 992px) {
    .Slopes-secteurList--pistes {
        columns:1
    }
}

.Slopes-secteurTitle {
    color: #000;
    position: relative;
    padding: 0;
    border-bottom: .1rem solid rgba(0,0,0,.2);
    display: flex;
    justify-content: space-between;
    align-items: center
}

.Slopes-item {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 35rem;
    margin-top: 0;
    margin-bottom: 1rem
}

.Slopes-item--pistes {
    padding-right: 2rem;
    display: inline-block
}

@media (max-width: 992px) {
    .Slopes-item {
        max-width:90%;
        padding-right: 0
    }
}

.Slopes-itemInner {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: space-between
}

.Slopes-pisteName {
    display: flex;
    align-items: center;
    font-weight: 400;
    font-size: 1.1rem;
    margin: 0;
    max-width: 24rem
}

@media (max-width: 992px) {
    .Slopes-pisteName {
        max-width:22rem
    }
}

.Slopes-pisteEtat {
    width: 9rem;
    height: 2.5rem;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 1.1rem;
    color: #fff;
    font-weight: 400;
    background-color: #c1c1c1
}

.Slopes-pisteEtat.F {
    background-color: #ce341a
}

.Slopes-pisteEtat.O {
    background-color: #7ab51d
}

.Slopes-typeName {
    font-size: 1.7rem;
    font-weight: 400;
    border-bottom: 1px solid #eef1f6;
}

.Slopes-pisteIndic {
    width: 1.2rem;
    height: 1.2rem;
    border-radius: 50%;
    margin-right: 1rem
}

.Slopes-pisteIndic.Verte {
    background-color: #5fb157
}

.Slopes-pisteIndic.Bleue {
    background-color: #00f
}

.Slopes-pisteIndic.Rouge {
    background-color: #da3832
}

.Slopes-pisteIndic.Noire {
    background-color: #131313
}

.SlopesInfo {
    display: flex;
    justify-content: space-between;
    align-content: center;
    flex-wrap: wrap;
    list-style-type: none;
    padding: 0;
    margin: 0 0 4rem 0
}

.SlopesInfo-content {
    width: 100%
}

.SlopesInfo-titre {
    font-size: 3.6rem;
    color: #C03733;
    font-weight: 600;
    margin: 0!important
}

@media (max-width: 768px) {
    .SlopesInfo-titre {
        font-size:3rem
    }
}

.SlopesInfo .SlopesToggle {
    padding: 1rem 0;
    margin: 0 0 2rem;
    position: relative;
    cursor: pointer;
    width: 100%;
    display: block;
    border-bottom: .1rem solid rgba(0,0,0,.5)
}

.SlopesInfo .SlopesToggle::before {
    content: "";
    position: absolute;
    top: 50%;
    right: 0;
    transform: translateX(-50%);
    width: 0;
    height: 0;
    border-style: solid;
    border-width: .8rem .8rem 0 .8rem;
    border-color: #C03733 transparent transparent transparent
}

.SlopesInfo .SlopesToggle.show::before {
    border-width: 0 .8rem .8rem .8rem;
    border-color: transparent transparent #C03733 transparent
}

.SlopesInfo-list {
    width: 100%;
    list-style-type: none;
    padding: 0;
    margin: 0;
    align-content: center;
    flex-wrap: wrap;
    overflow: hidden;
    display: none
}

.SlopesInfo-listing {
    width: calc((100% / 2) - (10rem / 2));
    margin: 0 10rem 5rem 0
}

.SlopesInfo-listing:nth-child(2),.SlopesInfo-listing:nth-child(4) {
    margin: 0 0 5rem 0
}

.SlopesInfo-details {
    margin: auto 0;
    display: flex;
    flex-direction: column
}

.SlopesInfo-title {
    color: rgba(0,0,0,.8);
    font-size: 2.4rem;
    font-weight: 600;
    margin: 0 0 4rem 0
}

.SlopesInfo-subTitle {
    color: #C03733;
    font-size: 1rem;
    font-weight: 600;
    letter-spacing: 2px;
    margin: 0 0 1.5rem 0
}

.SlopesInfo-bloc {
    display: flex;
    width: 100%
}

.SlopesInfo-time {
    display: flex;
    flex-direction: column
}

.SlopesInfo-time:first-child {
    margin: 0 7rem 0 0
}

.SlopesInfo-temp {
    display: flex
}

@media (max-width: 480px) {
    .SlopesInfo-temp {
        align-items:center
    }
}

.SlopesInfo-tempItem {
    font-size: 2.9rem;
    font-weight: 600;
    color: #392F2F;
    height: 100%;
    margin: 0 0 1rem 0
}

@media (max-width: 480px) {
    .SlopesInfo-tempItem {
        font-size:1.8rem
    }
}

.SlopesInfo-tempCelsius {
    font-size: 1.5rem;
    font-weight: 600;
    color: #392F2F;
    font-weight: 500;
    margin: auto 0 0 0
}

.SlopesInfo-icon {
    width: 8rem;
    height: 8rem;
    margin: 0 1.4rem 0 0
}

.SlopesInfo-icon>svg {
    fill: #392F2F
}

.SlopesInfo-indiceWarning .SlopesInfo-icon {
    width: 4.8rem;
    height: 4.8rem;
    margin: 0 2rem 0 0
}

.SlopesInfo-indice {
    margin: 1.6rem 0 1.6rem 0
}

.SlopesInfo-indiceItem {
    font-weight: 500;
    color: #392F2F;
    margin: auto 0 0 0
}

.SlopesInfo-indiceWarning .SlopesInfo-indiceItem {
    display: flex;
    flex-direction: column
}

.SlopesInfo-indiceBold {
    font-weight: 600
}

.SlopesInfo-indiceWarning .SlopesInfo-indiceBold {
    font-size: 2.9rem
}

.SlopesInfo-indiceWarning {
    display: flex;
    justify-content: flex-start;
    align-content: center;
    margin: 32px 0 0 0
}

.SlopesInfo-resumePiste {
    display: flex;
    justify-content: space-between;
    margin: 0;
    padding: 0;
    list-style-type: none;
    flex-direction: column
}

.SlopesInfo-resumeTotal,.SlopesInfo-resumePiste {
    color: #392F2F;
    margin: 0;
    padding: 0 0 4rem 0
}

@media (max-width: 768px) {
    .SlopesInfo-resumeTotal,.SlopesInfo-resumePiste {
        padding:0 0 2rem 0
    }
}

.SlopesInfo-resumeBold {
    font-weight: 600;
    font-size: 2.9rem
}

@media (max-width: 768px) {
    .SlopesInfo-resumeBold {
        font-size:2rem
    }
}

.SlopesInfo-resumePisteText {
    font-weight: 500;
    padding: 0 0 0 1.9rem
}

.SlopesInfo-resumePisteIndic {
    position: relative;
    font-size: 1.8rem;
    font-weight: 600;
    padding: 0 0 2rem 2.6rem;
    margin: 0;
    display: flex
}

@media (max-width: 768px) {
    .SlopesInfo-resumePisteIndic {
        font-size:1.5rem
    }
}

.SlopesInfo-resumePisteIndic.Verte::before {
    background: #7ab51d
}

.SlopesInfo-resumePisteIndic.Bleue::before {
    background: #0077B5
}

.SlopesInfo-resumePisteIndic.Rouge::before {
    background: #ce341a
}

.SlopesInfo-resumePisteIndic.Noire::before {
    background: #000
}

.SlopesInfo-resumePisteIndic::before {
    content: '';
    position: absolute;
    top: 8px;
    left: 0;
    width: 1rem;
    height: 1rem;
    border-radius: 50%
}

.Slopes-resumeTitle {
    color: rgba(0,0,0,.8);
    font-size: 2.4rem;
    font-weight: 600;
    display: block;
    margin: 0;
    padding: 0 0 0.5rem 0
}

@media (max-width: 768px) {
    .Slopes-resumeTitle {
        font-size:2rem;
        padding: 0 0 2rem 0
    }
}

.Slopes-resumeTitle::after {
    content: '';
    top: 0;
    right: 0;
    width: 15px;
    height: 15px;
    background-image: url(data:image/svg+xml;utf8,%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20viewBox%3D%220%200%2042%2042%22%3E%0A%20%20%3Cpath%20fill%3D%22%23FFF%22%20d%3D%22M42%2019H23V0h-4v19H0v4h19v19h4V23h19z%22%2F%3E%0A%3C%2Fsvg%3E);
    transition: transform 250ms ease
}

.Slopes-resumeList {
    display: flex;
    justify-content: space-between;
    margin: 0;
    padding: 0;
    list-style-type: none
}

@media (max-width: 768px) {
    .Slopes-resumeList {
        flex-direction:column;
        width: 100%
    }
}

@media (max-width: 992px) {
    .Slopes-resumeListing {
        width:100%
    }
}

.Slopes-resumePiste {
    margin: 0;
    padding: 0;
    list-style-type: none
}

.Slopes-resumeTotal,.Slopes-resumePiste {
    color: #392F2F;
    margin: 0;
    padding: 0 0 0.25rem 0
}

@media (max-width: 768px) {
    .Slopes-resumeTotal,.Slopes-resumePiste {
        padding:0 0 2rem 0
    }
}

.Slopes-resumeBold {
    font-weight: 600;
    font-size: 2.9rem
}

@media (max-width: 768px) {
    .Slopes-resumeBold {
        font-size:2rem
    }
}

.Slopes-resumePisteText {
    font-weight: 500;
    padding: 0 0 0 1.9rem
}

.Slopes-resumePisteIndic {
    position: relative;
    font-size: 1.8rem;
    font-weight: 600;
    padding: 0 0 2rem 2.6rem;
    margin: 0;
    display: flex
}

@media (max-width: 768px) {
    .Slopes-resumePisteIndic {
        font-size:1.5rem
    }
}

.Slopes-resumePisteIndic.Verte::before {
    background: #7ab51d
}

.Slopes-resumePisteIndic.Bleue::before {
    background: #0077B5
}

.Slopes-resumePisteIndic.Rouge::before {
    background: #ce341a
}

.Slopes-resumePisteIndic.Noire::before {
    background: #000
}

.Slopes-resumePisteIndic::before {
    content: '';
    position: absolute;
    top: 8px;
    left: 0;
    width: 1rem;
    height: 1rem;
    border-radius: 50%
}
.Slopes-secteurWrapper:nth-child(2),
.Slopes-secteurWrapper:nth-child(3),
.Slopes-secteurWrapper:nth-child(4),
.Slopes-secteurWrapper:nth-child(5),
.Slopes-secteurWrapper:nth-child(6),
.Slopes-secteurWrapper:nth-child(7) {
    display: none
}
</style>
<script type="text/javascript" src="https://www.valloire.net/cms/wp-includes/js/jquery/jquery.min.js?ver=3.7.1" id="jquery-core-js"></script>
<script type="text/javascript" src="https://www.valloire.net/cms/wp-includes/js/jquery/jquery-migrate.min.js?ver=3.4.1" id="jquery-migrate-js"></script>
<script type="text/javascript">

/* <![CDATA[ */

var themosis = {

ajaxurl: "https:\/\/www.valloire.net\/cms\/wp-admin\/admin-ajax.php",

};

/* ]]> */

</script>
<section id="__lumiplan_pistes" class="Slopes container">
    Chargement des pistes...
</section>
<script>
    jQuery(document).ready(function ($) {
        jQuery.ajax({
            type: 'POST',
            url: themosis.ajaxurl + '?action=lumiplan_pistes&lang=fr&wp_lang=fr',
            dataType: 'html',
            success: function (html) {
                $("#__lumiplan_pistes").empty().append(html);
            },
        });
    });
</script>