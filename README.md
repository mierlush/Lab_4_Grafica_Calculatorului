# Lab_4_Grafica_Calculatorului
Codul p5.js:

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>Index.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Model 3D</title>
    <link rel="stylesheet" type="text/css" href="style.css">
</head>
<body>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.4.0/p5.js"></script>
    <script src="sketch.js" type="text/javascript"></script>
</body>
</html>


  sketch.js
let masina, roti = [];
let angleX = 0;
let angleY = 0;

function preload() {
  masina = loadModel('lab_4_model.obj', true);
  roti[0] = loadModel('roata_1.obj', true);
  roti[1] = loadModel('roata_2.obj', true);
  roti[2] = loadModel('roata_3.obj', true);
  roti[3] = loadModel('roata_4.obj', true);
}

function setup() {
  createCanvas(800, 600, WEBGL);
}

function draw() {
  background(200);
  
  rotateX(angleX);
  rotateY(angleY);

  if (masina) {
    fill(184, 115, 51);
    scale(2);
    model(masina);
  }

  for (let i = 0; i < roti.length; i++) {
    push();
    fill(0);
    let scalaRoti = 0.2;
    scale(scalaRoti);
    let xOffset = (i < 2 ? -1 : 1) * 360;
    let zOffset = (i % 2 === 0 ? 1 : -1) * 160;
    let yOffset = -200;
    translate(xOffset, yOffset, zOffset);
    if (roti[i]) {
      model(roti[i]);
    }
    pop();
  }
}

function mouseDragged() {
  angleY += (pmouseX - mouseX) * 0.01;
  angleX -= (pmouseY - mouseY) * 0.01;
]

Style.css
canvas {
  display: block;
}

