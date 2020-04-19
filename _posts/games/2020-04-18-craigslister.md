---
layout: post
current: post
cover: assets/images/mongodb/mongodb_cover.jpg
navigation: True
title: Craigslister - Unity Text Based Game
date: 2020-04-18 20:53:00
tags: game
class: post-template
subclass: 'post'
author: thomas
---

Play as a user trying to sell their items on Craigslist!

<head>
    <meta charset="utf-8">
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
    <title>Craigslister</title>
    <link rel="shortcut icon" href="{{ site.baseurl }}assets/craigslister/TemplateData/favicon.ico">
    <link rel="stylesheet" href="{{ site.baseurl }}assets/craigslister/TemplateData/style.css">
    <script src="{{ site.baseurl }}assets/craigslister/TemplateData/UnityProgress.js"></script>
    <script src="{{ site.baseurl }}assets/craigslister/Build/UnityLoader.js"></script>
    <script>
      var unityInstance = UnityLoader.instantiate("unityContainer", "{{ site.baseurl }}assets/craigslister/Build/Build.json", {onProgress: UnityProgress});
    </script>
  </head>
  <body>
    <div class="webgl-content">
      <div id="unityContainer" style="width: 960px; height: 600px"></div>
      <div class="footer">
        <div class="fullscreen" onclick="unityInstance.SetFullscreen(1)"></div>
        <div class="title">Craigslister</div>
      </div>
    </div>
  </body>
