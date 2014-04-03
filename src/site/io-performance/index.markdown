---
title: Dart I/O Performance
layout: default
description: Tracking Dart I/O performance on the server.
js:
- url: /js/performance-charts.js
  defer: true
---

<style>
/* https://code.google.com/p/dart/issues/detail?id=10602 */

#performance-charts > .tab-pane {
  display: block !important;
  height: 0;
  overflow: hidden;
}
#performance-charts > .tab-pane.active {
    height: 440px;
}

</style>

# {{ page.title }}

Tracking server-side performance, using the [Dart VM](/tools/dart-vm/) and the
[dart:io](https://api.dartlang.org/apidocs/channels/stable/dartdoc-viewer/dart-io)
library.

The [Dart Performance](/performance/) page tracks raw VM performance.

<ul class="nav nav-tabs" id="performance-charts-nav-io">
</ul>

<div class="tab-content" id="performance-charts-io" style='height: 445px'>
</div>

(*To navigate the chart, drag to pan and shift-drag to zoom.*)

<section id="performance-faq" markdown="1">

<div markdown="1">
Benchmark descriptions
: We are currently showing charts for the three HTTP server benchmarks
  *Hello*, *File* and *JSON*. These benchmarks are tracked as part of the
  [ton80](https://github.com/dart-lang/ton80)
  benchmarking suite. For all benchmarks, we track requests-per-second,
  average latency and max latency.

  * [Hello](https://github.com/dart-lang/ton80/tree/master/lib/src/Serve/dart/server.dart)
  is a simply HTTP server, responding the string "world" to all requests. This
  benchmark is showing the peek requests-per-second, for HTTP server running
  a single isolate.

  * [File](https://github.com/dart-lang/ton80/tree/master/lib/src/Serve/dart/server.dart)
  is a HTTP server that responds with the content of a 100kb file. This
  benchmark is mostly bound by file I/O.

  * [JSON](https://github.com/dart-lang/ton80/tree/master/lib/src/Serve/dart/server.dart)
  is a HTTP server that responds with the a dynamically generated JSON string,
  for each request. This benchmark reflects some REST-like APIs, where it's
  common to JSON-encode the response.
</div>

<div markdown="1">
About latency
: * *Avg latency* is the average latency recorded for all requests sent. For a
  single request, latency is the time passed from initiating the request to the
  full response has been received.

  * *Max latency* is the worst latency recorded, for all requests sent. While
  the average latency is closely bound to the requests-per-second, max latency
  indicate the HTTP servers ability to schedule fairly under heavy load.
</div>

<div markdown="1">
System setup
: The benchmarks are run on an Intel(R) Core(TM) i5-2400 CPU @ 3.10GHz
  processor running the Ubuntu 12.04 LTS x64 operating system.
  While the code runs on a 64-bit operating system, we’re
  running the 32-bit version the Dart VM.
</div>

<div markdown="1">
Will there be more benchmarks?
: Yes. As more benchmarks become ready, we will publish more charts.
</div>

</section>

