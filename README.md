Cell[][] grid;//sets it up?

int cols = 25;
int rows = 25;

void setup() {
  size(550, 550);
  grid = new Cell[cols][rows];
  for (int i = 0; i < cols; i++) {
    for (int j = 0; j < rows; j++) {
      // this initializes each object
      grid[i][j] = new Cell(i*20,j*20,20,20,i+j);
    }
  }
}

void draw() {
  background(127, 0, 0);
  // arguments to the constructor
  for (int i = 0; i < cols; i++) {
    for (int j = 0; j < rows; j++) {
      grid[i][j].oscillate();
      grid[i][j].display();
    }
  }
}


class Cell {
//defines the location
  float x,y;   // x,y location
  float w,h;   // width and height
  float angle; // angle for oscillating brightness
  
  Cell(float tempX, float tempY, float tempW, float tempH, float tempAngle) {
    x = tempX;
    y = tempY;
    w = tempW;
    h = tempH;
    angle = tempAngle;

  } 
  
  // this increases angle
  void oscillate() {
    angle += 0.02; 
  }

  void display() {
    noStroke ();
    fill(90+124*sin(angle));
    rect(x,y,w,h); 
  }
}
