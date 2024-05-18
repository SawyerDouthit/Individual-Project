PImage startScreenImage;
int screen = 0;
ArrayList<Ball> balls = new ArrayList<Ball>();

void setup() {
  size(800, 600);
  startScreenImage = loadImage("StartScreen.jpg");
  startScreenImage.resize(width, height);
}

void draw() {
  if (screen == 0) {
    drawStartScreen();
  } else if (screen == 1) {
    drawMainProgram();
  }
}

void drawStartScreen() {
  background(startScreenImage);
  fill(255);
  textSize(32);
  textAlign(CENTER, CENTER);
  text("Click to Start", width / 2, height / 2);
}

void drawMainProgram() {
  background(255);
  for (Ball ball : balls) {
    ball.update();
    ball.display();
  }
}

void mousePressed() {
  if (screen == 0) {
    screen = 1;
    for (int i = 0; i < 20; i++) {
      balls.add(new Ball(random(width), random(-500, -50)));
    }
  }
}

class Ball {
  float x, y;
  float speed;
  float diameter;

  Ball(float startX, float startY) {
    x = startX;
    y = startY;
    speed = random(2, 5);
    diameter = random(20, 40);
  }

  void update() {
    y += speed;
    if (y > height) {
      y = random(-500, -50);
      x = random(width);
    }
  }

  void display() {
    fill(255, 0, 0);
    noStroke();
    ellipse(x, y, diameter, diameter);
  }
}





