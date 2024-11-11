let circle = {
  x: 0,
  y: 0,
  size: 50,
  color: 0,
  speedX: 0,
  speedY: 0
}

let rectangle = {
  x: 0,
  y: 0,
  size: 50,
  color: 0,
  speedX: 0,
  speedY: 0
}

function setup() {
  createCanvas(400, 400);


  circle.x = random(width);
  circle.y = random(height);
  circle.color = color(255, 0, 0); 
  circle.speedX = random(-2, 2);
  circle.speedY = random(-2, 2);

  // Initialize rectangle properties
  rectangle.x = random(width);
  rectangle.y = random(height);
  rectangle.color = color(0, 0, 255); 
  rectangle.speedX = random(-2, 2);
  rectangle.speedY = random(-2, 2);
}

function draw() {
  background(220);

  // Move shapes
  circle.x += circle.speedX;
  circle.y += circle.speedY;
  rectangle.x += rectangle.speedX;
  rectangle.y += rectangle.speedY;


  if (overlap(circle, rectangle)) {
    circle.speedX *= -1;
    circle.speedY *= -1;
    rectangle.speedX *= -1;
    rectangle.speedY *= -1;
    circle.color = color(0, 255, 0); 
    rectangle.color = color(255, 255, 0); 
  } else {
    circle.color = color(255, 0, 0); 
    rectangle.color = color(0, 0, 255)
  }


  fill(circle.color);
  ellipse(circle.x, circle.y, circle.size);
  fill(rectangle.color);
  rect(rectangle.x, rectangle.y, rectangle.size, rectangle.size);
}


function overlap(circle, rectangle) {
  return dist(circle.x, circle.y, rectangle.x + rectangle.size / 2, rectangle.y + rectangle.size / 2) < (circle.size + rectangle.size) / 2;
}


function keyPressed() {
  if (key === 'r') {
    circle.x = random(width);
    circle.y = random(height);
    rectangle.x = random(width);
    rectangle.y = random(height);
    circle.speedX = random(-2, 2);
    circle.speedY = random(-2, 2);
    rectangle.speedX = random(-2, 2);
    rectangle.speedY = random(-2, 2);
  }
}
