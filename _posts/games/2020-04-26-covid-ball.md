---
layout: post
current: post
cover: assets/images/games/covid-ball/covid-ball-play.PNG
navigation: True
title: Covid Ball Block Breaker Game
date: 2020-04-26 15:13:00
tags: game
class: post-template
subclass: 'post'
author: thomas
---

Play as a little virus with the goal of infecting or destroying blocks. The world is yours

You can download the desktop version of the game [here](https://github.com/thomashzhang/covid-ball/releases) and view the source code with all assets [here](https://github.com/thomashzhang/covid-ball).

<script src="{{ site.baseurl }}assets/games/covid-ball/TemplateData/UnityProgress.js"></script>
<script src="{{ site.baseurl }}assets/games/covid-ball/Build/UnityLoader.js"></script>
<script>
  UnityLoader.Error.handler = function(e, t)
  {
    console.log(e);
  }
  UnityLoader.instantiate("unityContainer", "{{ site.baseurl }}assets/games/covid-ball/Build/webgl.json", {onProgress: UnityProgress});
</script>
<div class="webgl-content">
  <div id="unityContainer" style="width: 936px; height: 702px"></div>
</div>
