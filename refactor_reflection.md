let circleX, circleY;
let rectX, rectY;
let circleSize = 50;
let rectSize = 50;
let circleColor, rectColor;
let circleSpeedX, circleSpeedY, rectSpeedX, rectSpeedY;


function setup() {
  createCanvas(400, 400);


  circleX = random(width);
  circleY = random(height);
  rectX = random(width);
  rectY = random(height);
 


  circleColor = color(255, 0, 0); // Red
  rectColor = color(0, 0, 255);   // Blue
 


  circleSpeedX = random(-2, 2);
  circleSpeedY = random(-2, 2);
  rectSpeedX = random(-2, 2);
  rectSpeedY = random(-2, 2);
}


function draw() {
  background(220);


  circleX += circleSpeedX;
  circleY += circleSpeedY;


  rectX += rectSpeedX;
  rectY += rectSpeedY;


  if (dist(circleX, circleY, rectX + rectSize / 2, rectY + rectSize / 2) < (circleSize + rectSize) / 2) {
 
    circleSpeedX *= -1;
    circleSpeedY *= -1;
    rectSpeedX *= -1;
    rectSpeedY *= -1;
    circleColor = color(0, 255, 0);
    rectColor = color(255, 255, 0);
  } else {


    circleColor = color(255, 0, 0);
    rectColor = color(0, 0, 255);  
  }


  fill(circleColor);
  ellipse(circleX, circleY, circleSize);
  fill(rectColor);
  rect(rectX, rectY, rectSize, rectSize);
}


function keyPressed() {
  if (key === 'r') {
    circleX = random(width);
    circleY = random(height);
    rectX = random(width);
    rectY = random(height);
    circleSpeedX = random(-2, 2);
    circleSpeedY = random(-2, 2);
    rectSpeedX = random(-2, 2);
    rectSpeedY = random(-2, 2);
  }
}
