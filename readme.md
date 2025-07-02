# Issue

When trying to retrieve the path to the `cropperjs` library with `require`, since the CropperJS `package.json` default CommonJS export contains a path to `./cropper.raw.js` rather than `./dist/cropper.raw.js`, this error occurs:

<!-- Display the PNG as an image -->
![CropperJS raw-JS error screenshot](./assets/cropper-raw-js.png)

Adjusting this to `./dist/cropper.raw.js` fixes the issue.

Also, adding `"./package.json": "./package.json"` to the exports ensures `require('cropperjs/package.json')` (or `import pkg from 'cropperjs/package.json'`) will resolve correctly, making CropperJS's metadata (version, author, license, etc.) available to consumers and tooling.

# Demo Video

<!-- Embed the MP4 as a video with controls -->
<video controls width="640" height="360">
  <source src="./assets/demo.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>

# Steps to reproduce
1. Clone this repository, and navigate to `cropper-js-package-path-issue` in your terminal.
2. Run `npm install`.
3. Run `node script.js`. The issue described above should occur.