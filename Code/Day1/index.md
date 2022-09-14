
let t = 0; // time variable

function setup() {
  createCanvas(600, 600);
  noStroke();
  fill(100, 100, 100);
}

function draw() {
  background(10, 10); // translucent background (creates trails)

  // make a x and y grid of ellipses
  for (let x = 0; x <= width; x = x + 20) {
    for (let y = 0; y <= height; y = y + 20) {
      // starting point of each circle depends on mouse position
      const xAngle = map(mouseX, 0, width, -3 * PI, 1 * PI, true);
      const yAngle = map(mouseY, 0, height, -3 * PI, 1 * PI, true);
      // and also varies based on the particle's location
      const angle = xAngle * (x / width) + yAngle * (y / height);

      // each particle moves in a circle
      const myX = x + 20 * cos(2 * PI * t + angle);
      const myY = y + 20 * sin(2 * PI * t + angle);

      ellipse(myX, myY, 05); // draw particle
    }
  }

  t = t + 0.005; // update time
}
