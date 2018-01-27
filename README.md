<!-- travis-ci -->
[travis-img]: https://img.shields.io/travis/okramlabs/aframe.svg?style=flat-square
[travis-link]: https://travis-ci.org/okramlabs/aframe

<!-- appveyor -->
[appveyor-img]: https://ci.appveyor.com/api/projects/status/8w0pjo5xs8n1wap8?svg=true&style=flat-square
[appveyor-link]: https://ci.appveyor.com/project/okramlabs/aframe

<!-- circleci -->
[circleci-img]: https://circleci.com/gh/okramlabs/aframe/tree/master.svg?style=svg&?style=flat-square
[circleci-link]: https://circleci.com/gh/okramlabs/aframe/tree/master

<!-- CHANGES
- avoid html in markdown when possible
- collect links together for easier tracking
- add some useful badges exposing information what users care
- add builds for platforms Windows and macOS
- remove awesome-aframe link
-->
[![aframe cover][aframe-cover]][aframe-site-link]

# A-Frame
**A web framework for building virtual reality experiences.**

[Site][aframe-site-link] &mdash;
[Docs][aframe-docs-link] &mdash;
[School][aframe-school-link] &mdash;
[Slack][aframe-slack-link] &mdash;
[Blog][aframe-blog-link] &mdash;
[Examples][aframe-examples-link]

*Find more examples on [the homepage][aframe-site-link], [A Week of A-Frame][aframe-blog-link][aframe-blog-link].*

[![A-Frame Latest Version][aframe-version-img]][aframe-version-link]
[![GitHub license badge][license-img]][license-link]
[![GitHub issues][github-issues-img]][github-issues-link]
[![GitHub forks][github-forks-img]][github-forks-link]
[![GitHub stars][github-stars-img]][github-stars-link]
[![A-Frame downloads][npm-downloads-img]][npm-downloads-link]

**Development**

| Linux | macOS | Windows | Code Coverage |
| --- | --- | --- | --- |
| [![TravisCI Build Status][travis-img]][travis-link] | [![CircleCI Build Status][circleci-img]][circleci-link] | [![AppveyorCI Build Status][appveyor-img]][appveyor-link] | [![Coverage Status][codecov-img]][codecov-link] |

## Features

:eyeglasses: **Virtual Reality Made Simple**: A-Frame handles the 3D and WebVR
boilerplate required to get running across platforms including mobile, desktop,
Vive, and Rift just by dropping in `<a-scene>`.

:heart: **Declarative HTML**: HTML is easy to read and copy-and-paste. Since
A-Frame can be used from HTML, A-Frame is accessible to everyone: web
developers, VR enthusiasts, educators, artists, makers, kids.

:globe_with_meridians: **Cross-Platform**: Build VR applications for Vive,
Rift, Daydream, GearVR, and Cardboard. Don't have a headset or controllers? No
problem! A-Frame still works on standard desktop and smartphones.

:electric_plug: **Entity-Component Architecture**: A-Frame is a powerful framework,
providing a declarative, composable, reusable entity-component structure for
three.js. While A-Frame can be used from HTML, developers have unlimited access
to JavaScript, DOM APIs, three.js, WebVR, and WebGL.

:zap: **Performance**: A-Frame is optimized from the ground up for WebVR. While
A-Frame uses HTML, Custom Elements don't touch the browser layout engine. All
3D object updates are all done in memory with little overhead under a single
global `requestAnimationFrame` call.

&#128296; **Tool Agnostic**: A-Frame works with normal JavaScript DOM APIs and
therefore with all libraries such as
[React](https://github.com/aframevr/aframe-react/), Vue.js, jQuery, or d3.js.
Web developers don't have to jump ship to yet another framework, feeling right
at home with A-Frame.

:mag: **Visual Inspector**: A-Frame provides a built-in visual 3D inspector
with a workflow similar to a browser's developer tools and interface similar to
Unity. Open up any A-Frame scene and hit `<ctrl> + <alt> + i`.

:package: **Registry**: Reuse powerful components that other A-Frame developers
have created and shared. The [A-Frame
Registry](https://aframe.io/aframe-registry) collects and curates components
similar to the Unity Asset Store. Stand on the shoulders of giants and plug in
components right from HTML.

:runner: **Features**: Hit the ground running with A-Frame's built-in
components such as geometries, materials, lights, animations, models,
raycasters, shadows, positional audio, Vive / Touch / Cardboard controls. Get
even further with community components such as particle systems, physics,
multiuser, oceans, mountains, speech recognition, or teleportation!

## Top-Level Goals

- **Community:** help people get involved with WebXR in a fun and welcoming environment
- **Performance:** maintain high framerate with low latency
- **Ecosystem:** enable discovery and distribution of reusable components

## Usage

### Example

Build VR scenes in the browser with just a few lines of HTML! To start playing
and publishing now, remix the starter example on Glitch:

[![Remix][remix-eg1-img]][remix-eg1-link]

```html
<html>
  <head>
    <script src="https://cdn.jsdelivr.net/npm/aframe/dist/aframe.min.js"></script>
  </head>
  <body>
    <a-scene>
      <a-box position="-1 0.5 -3" rotation="0 45 0" color="#4CC3D9"></a-box>
      <a-sphere position="0 1.25 -5" radius="1.25" color="#EF2D5E"></a-sphere>
      <a-cylinder position="1 0.75 -3" radius="0.5" height="1.5" color="#FFC65D"></a-cylinder>
      <a-plane position="0 0 -4" rotation="-90 0 0" width="4" height="4" color="#7BC8A4"></a-plane>
      <a-sky color="#ECECEC"></a-sky>
    </a-scene>
  </body>
</html>
```

With A-Frame's [entity-component
architecture][aframe-core-link], we can drop in community
components from the ecosystem (e.g., ocean, physics) and plug them into our
objects straight from HTML:

[![Remix](https://cloud.githubusercontent.com/assets/674727/24572421/688f7fc0-162d-11e7-8a35-b02bc050c043.jpg)](https://glitch.com/~aframe-registry)

```html
<html>
  <head>
    <script src="https://aframe.io/releases/0.7.1/aframe.min.js"></script>
    <script src="https://unpkg.com/aframe-animation-component@3.2.1/dist/aframe-animation-component.min.js"></script>
    <script src="https://unpkg.com/aframe-particle-system-component@1.0.x/dist/aframe-particle-system-component.min.js"></script>
    <script src="https://unpkg.com/aframe-extras.ocean@%5E3.5.x/dist/aframe-extras.ocean.min.js"></script>
    <script src="https://unpkg.com/aframe-gradient-sky@1.0.4/dist/gradientsky.min.js"></script>
  </head>
  <body>
    <a-scene>
      <a-entity id="rain" particle-system="preset: rain; color: #24CAFF; particleCount: 5000"></a-entity>

      <a-entity id="sphere" geometry="primitive: sphere"
                material="color: #EFEFEF; shader: flat"
                position="0 0.15 -5"
                light="type: point; intensity: 5"
                animation="property: position; easing: easeInOutQuad; dir: alternate; dur: 1000; to: 0 -0.10 -5; loop: true"></a-entity>

      <a-entity id="ocean" ocean="density: 20; width: 50; depth: 50; speed: 4"
                material="color: #9CE3F9; opacity: 0.75; metalness: 0; roughness: 1"
                rotation="-90 0 0"></a-entity>

      <a-entity id="sky" geometry="primitive: sphere; radius: 5000"
                material="shader: gradient; topColor: 235 235 245; bottomColor: 185 185 210"
                scale="-1 1 1"></a-entity>

      <a-entity id="light" light="type: ambient; color: #888"></a-entity>
    </a-scene>
  </body>
</html>
```

### Builds

To use the latest stable build of A-Frame, include [`aframe.min.js`][aframe-latest]:

```js
<head>
  <script src="https://cdn.jsdelivr.net/npm/aframe/dist/aframe.min.js"></script>
</head>
```

To check out the stable and master builds, see the [`dist/` folder](dist/).

### npm

```sh
npm install --save aframe
# Or
yarn add aframe
```

```js
require('aframe')  // e.g., with Browserify or Webpack.
// or
require('aframe/src') // to rebuild A-Frame
```

## Local Development

```sh
git clone --origin github/aframevr https://github.com/aframevr/aframe.git  # Clone the repository.
cd aframe && npm install  # Install dependencies.
npm start  # Start the local development server.
```

And open in your browser **[http://localhost:9000](http://localhost:9000)**.

### Generating Builds

```sh
npm run dist
```

## Questions

For questions and support, ask on [Slack][aframe-slack-link] or  [StackOverflow][aframe-stackoverflow-link].

## Stay in Touch

- To hang out with the community, [join the A-Frame Slack][aframe-slack-link].
- [Follow `A Week of A-Frame` on the A-Frame blog][aframe-blog-link].
- [Follow @aframevr on Twitter][aframe-twitter-link].


## Contributing

Get involved! Check out the [Contributing Guide](.github/contributing.md) for how to get started.

## License

This program is free software and is distributed under an [MIT License](LICENSE).

<!-- A-Frame  -->
[aframe-cover]: ./examples/assets/img/acover.jpg
[aframe-site-link]: https://aframe.io
[aframe-docs-link]: https://aframe.io/docs/
[aframe-school-link]: https://aframe.io/aframe-school/
[aframe-slack-link]: https://aframevr-slack.herokuapp.com
[aframe-blog-link]: https://aframe.io/blog/
[aframe-examples-link]: https://aframe.io/examples/
[aframe-core-link]: https://aframe.io/docs/master/core/
[aframe-latest]: https://cdn.jsdelivr.net/npm/aframe/dist/aframe.min.js
[aframe-twitter-link]: https://twitter.com/aframevr
[aframe-stackoverflow-link]: https://stackoverflow.com/questions/ask/?tags=aframe

[aframe-version-img]: https://img.shields.io/npm/v/aframe.svg?style=flat-square
[aframe-version-link]: https://npmjs.org/package/aframe

[github-issues-img]: https://img.shields.io/github/issues/aframevr/aframe.svg?style=flat-square
[github-issues-link]: https://github.com/aframevr/aframe/issues

[github-forks-img]: https://img.shields.io/github/forks/aframevr/aframe.svg?style=flat-square
[github-forks-link]: https://github.com/aframevr/aframe/network

[github-stars-img]: https://img.shields.io/github/stars/aframevr/aframe.svg?style=flat-square
[github-stars-link]: https://github.com/aframevr/aframe/stargazers

[npm-downloads-img]: https://img.shields.io/npm/dt/aframe.svg?style=flat-square
[npm-downloads-link]: https://npmjs.org/package/aframe

<!-- codecov -->
[codecov-img]: https://codecov.io/gh/aframevr/aframe/branch/master/graph/badge.svg?style=flat-square
[codecov-link]: https://codecov.io/gh/aframevr/aframe

<!-- License -->
[license-img]: https://img.shields.io/github/license/aframevr/aframe.svg?style=flat-square
[license-link]: https://github.com/aframevr/aframe/blob/master/LICENSE

<!-- Remix -->
[remix-eg1-link]:  https://glitch.com/~aframe
[remix-eg1-img]: https://cloud.githubusercontent.com/assets/674727/24572421/688f7fc0-162d-11e7-8a35-b02bc050c043.jpg
