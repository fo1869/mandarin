# mandarin
npm i 360-image-viewer
const create360Viewer = require('360-image-viewer');
const canvasFit = require('canvas-fit');
 
// load your image
const image = new Image();
image.src = 'panosphere.jpg';
 
image.onload = () => {
  // when the image is loaded, setup the viewer
  const viewer = create360Viewer({
    image: image
  });
 
  // attach canvas to body
  document.body.appendChild(viewer.canvas);
 
  // setup fullscreen canvas sizing
  const fit = canvasFit(viewer.canvas, window, window.devicePixelRatio);
  window.addEventListener('resize', fit, false);
  fit();
 
  // start the render loop
  viewer.start();
};
