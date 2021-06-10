[![npm version](https://badge.fury.io/js/angular2-expandable-list.svg)](https://badge.fury.io/js/angular2-expandable-list)
[![code style: prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg?style=flat-square)](https://github.com/prettier/prettier)
# EcoCDN SDK

> Javascripts library for EcoCDN

---
## Installation

You can get from [nodejs](https://nodejs.org/en/) and package manager [npm](https://www.npmjs.com/get-npm) :


```sh
$ npm install ecocdn
```

Or simply using CDN
```javascript
<script source="https://cdn.jsdelivr.net/npm/ecocdn@1.0.0/vodjs.min.js"></script>
```

---

## Basic usage

General steps are:

1. Include EcoCDN scripts.
2. Create a player instance.
3. Call init function for the player.

---
## API

Use `window.Trscker` to init ... :
- `initHlsJsPlayer` - [hls.js](https://github.com/video-dev/hls.js) player integration
- `initClapprPlayer` - [Clappr](https://github.com/clappr/clappr) player integration
- `initJwPlayer` - [JW Player](https://www.jwplayer.com) integration
- `initVideoJsHlsJsPlugin` - another [Video.js](https://videojs.com) player integration

---

## Player Integrations

We support 4 popular players.

### `initHlsJsPlayer(player)`

[hls.js](https://github.com/video-dev/hls.js) player integration.

`player` should be valid hls.js instance.

Example
```javascript
var video_url = "https://example.com/path/to/your/playlist.m3u8";
var hls = new Hls({});

window.Tracker.initHls({player: hls, video_url: video_url});

hls.loadSource(video_url);

var video = document.getElementById("video");
hls.attachMedia(video);
```

### `initClapprPlayer(player)`

[Clappr](https://github.com/clappr/clappr) player integration.

`player` should be valid Clappr player instance.

Example
```javascript
var video_url = "https://example.com/path/to/your/playlist.m3u8";

var player = new Clappr.Player({
    parentId: "#video",
    source: video_url,
});

window.Tracker.initClappr({player: player, video_url: video_url});
```


### `initJwPlayer(player)`

[JW Player](https://www.jwplayer.com) integration.

`player` should be valid JW Player instance.

Example
```javascript
var video_url = "https://example.com/path/to/your/playlist.m3u8";

var player = jwplayer("video");
            
var callback = function(cb) {
    player.setup({
        file: video_url,
    });

    jwplayer_hls_provider.attach();

    if (typeof cb === "function") {
        cb();
    }
};

window.Tracker.init({
    player: player,
    video_url: video_url,
    cb: callback,
});
```

### `initVideoJsHlsJsPlugin()`

Another [Video.js](https://videojs.com) player integration.

Example
```javascript
var video_url = "https://example.com/path/to/your/playlist.m3u8";

var player = videojs("video");

var callback = function() {
    player.src({
        src: video_url,
        type: "application/x-mpegURL"
    });
}

window.Tracker.initVideojs({
    video_url: video_url,
    cb: callback,
})
```
## Contact
Support Teams - [support@ecocdn.net](support@ecocdn.net)

## License
[MIT](https://choosealicense.com/licenses/mit/)
