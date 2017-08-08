# wav-encoder
[![Build Status](https://img.shields.io/travis/mohayonao/wav-encoder.svg?style=flat-square)](https://travis-ci.org/mohayonao/wav-encoder)
[![NPM Version](https://img.shields.io/npm/v/wav-encoder.svg?style=flat-square)](https://www.npmjs.org/package/wav-encoder)
[![License](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](https://mohayonao.mit-license.org/)

> promise-based wav encoder

## Installation

```
$ npm install wav-encoder
```

## API

- `encode(audioData: AudioData, [format: object]): Promise<ArrayBuffer>`
  - `audioData` should contain two fields `sampleRate` and `channelData`.
  - `format` is an optional parameter which used to design the output wav format.
    - The default format is `{ float: false, bitDepth: 16 }`
- `encode.sync(audioData: AudioData, [format: object]): ArrayBuffer`
  - synchronous version

```js
interface AudioData {
  sampleRate: number;
  channelData: Float32Array[];
}
```

## Usage

```js
const fs = require("fs");
const WavEncoder = require("wav-encoder");

const whiteNoise1sec = {
  sampleRate: 44100,
  channelData: [
    new Float32Array(44100).map(() => Math.random() - 0.5),
    new Float32Array(44100).map(() => Math.random() - 0.5)
  ]
};

WavEncoder.encode(whiteNoise1sec).then((buffer) => {
  fs.writeFileSync("noise.wav", new Buffer(buffer));
});
```

## License
MIT
