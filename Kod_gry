let points = 0;
let maxPoints = 5;
let erasmusText = "Erasmus+ to wspaniały program";

let player;
let gems = [];

function setup() {
  createCanvas(400, 400);
  player = new Player(width / 2, height / 2);
  
  // Generuj klejnoty
  for (let i = 0; i < 10; i++) {
    gems.push(new Gem(random(width), random(height)));
  }
}

function draw() {
  background(220);

  // Ruch gracza
  player.update();
  player.display();

  // Sprawdź kolizję gracza z klejnotami
  for (let i = gems.length - 1; i >= 0; i--) {
    let gem = gems[i];
    if (player.hits(gem)) {
      gems.splice(i, 1);
      points++;
    } else {
      gem.display();
    }
  }

  // Wyświetl aktualną liczbę punktów
  textSize(16);
  fill(0);
  text('Punkty: ' + points, 10, 20);

  // Wyświetl napis po zdobyciu wymaganej liczby punktów
  if (points >= maxPoints) {
    textAlign(CENTER);
    textSize(24);
    fill(255, 0, 0);
    text(erasmusText, width / 2, height / 2);
  }
}

class Player {
  constructor(x, y) {
    this.x = x;
    this.y = y;
    this.size = 20;
    this.speed = 2;
    this.color = color(0, 0, 255);
  }

  update() {
    if (keyIsDown(LEFT_ARROW)) {
      this.x -= this.speed;
    } else if (keyIsDown(RIGHT_ARROW)) {
      this.x += this.speed;
    }

    if (keyIsDown(UP_ARROW)) {
      this.y -= this.speed;
    } else if (keyIsDown(DOWN_ARROW)) {
      this.y += this.speed;
    }

    this.x = constrain(this.x, 0, width);
    this.y = constrain(this.y, 0, height);
  }

  display() {
    fill(this.color);
    ellipse(this.x, this.y, this.size, this.size);
  }

  hits(gem) {
    let d = dist(this.x, this.y, gem.x, gem.y);
    return d < this.size / 2 + gem.size / 2;
  }
}

class Gem {
  constructor(x, y) {
    this.x = x;
    this.y = y;
    this.size = 15;
    this.color = color(random(255), random(255), random(255));
    this.angle = 0;
    this.rotationSpeed = random(-0.05, 0.05);
  }

  display() {
    push();
    translate(this.x, this.y);
    rotate(this.angle);
    fill(this.color);
    rectMode(CENTER);
    rect(0, 0, this.size, this.size);
    pop();

    this.angle += this.rotationSpeed;
  }
}

function keyPressed() {
  if (keyCode === 32) {
    player.color = color(random(255), random(255), random(255));
  }
}
