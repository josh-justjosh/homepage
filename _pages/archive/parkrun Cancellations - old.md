---
layout: page
title: parkrun Cancellations
permalink: /parkrun-cancellations-old/
date: 2019-08-20 10:39 +0100
last_modified_at: 2021-05-24 00:01 +0100
tag: parkrun
published: false
---

<iframe src="https://www.google.com/maps/d/embed?mid=1d3lRdUmVhjoWycGXhI0spTbu_IgY-1bv" width="100%" height="500"></iframe>

<div style="text-align: center;">
    <iframe src="https://free.timeanddate.com/countdown/i7q1ask7/n1325/cf100/cm0/cu4/ct0/cs0/ca0/cr0/ss0/cacfff/cpcfff/pc2b233d/tc66c/fs200/szw448/szh189/tatparkrun%20Returns%2a/tacfff/tptparkrun%20is%20Back!/tpcfff/mat(in%20England)/macfff/mpt%20(in%20England)/mpcfff/iso2021-06-26T09:00:00" allowtransparency="true" frameborder="0" width="448" height="189"></iframe>
</div>

<p style="text-align: center;">* Dependent on a substantial number of events returning. You can read more about that <a href="https://blog.josh.me.uk/2021/05/12/update-to-the-parkrun-cancellations-map/">here</a>.

<h2> The following events have been granted permission to return </h2>

<table style="margin-left:auto; margin-right:auto;">
  {% for row in site.data.PtRtable %}
    {% unless forloop.first %}
    {% tablerow pair in row %}
      {{ pair[1] }}
    {% endtablerow %}
    {% endunless %}
  {% endfor %}
</table>
