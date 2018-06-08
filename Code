int time = 30; 
currentColor cColor = new currentColor(255, 700, 10);
Timer   t = new Timer(time);
colorBox c = new colorBox();
int gSize = 10;
color clickColor = color(0);
final int gridSize = 500;
final int bigSize = (int)(gridSize + gridSize/2);
ArrayList<Square> grid = new ArrayList<Square>(); //declares the grid
int a = 0;
int b = a;


void settings() {
  size(bigSize, gridSize);
}
void setup() {  

  for (int i = 0; i < gridSize; i+=10) { //forms the grid
    for (int j = 0; j < gridSize; j+=10) {
      grid.add(new Square(i, j));
    }
  }

  //adds the color pickers (probably pretty ineffeciant) :/
}

void draw() {
  background(150);
  t.countDown();
  for (Square s : grid) {
    s.show(a,b);
  }
  t.display();
  c.show();
  cColor.show();
}

class Square {
  int x;
  int y;
  int size;
  color clr;
  color changeColor;
  boolean clicked;
  color tempColor;
  Square(int x_, int y_) {
    clicked = false;
    x=x_;
    y=y_;
    size=gSize;
    clr= color(255);
    tempColor= color(255);
  }
  void show(int x_, int y_) {
    stroke(160);
    fill(clr);
    rect(x+x_, y+y_, size, size);
  }
  void setColor(color newColor) { // sets a variable to whatever is inputed
    changeColor = newColor;
  }
  void clicked() { //sets the color to the variable mentioned above when the square is clicked
    if ((mouseX > x && mouseX < x+size) && (mouseY > y && mouseY < y+size)) {
      clr=changeColor;
      clicked = true;
    }
  }
  public boolean isClicked() {
    return clicked;
  }
  void wasClicked() {
    clicked = false;
  }
}

public class colorChanger {
  int x, y, size;
  color rgb;
  colorChanger(color myColor, int x_, int y_) {
    rgb = myColor;
    x = x_;
    y = y_;
    size = 40;
  }
  public void show() {
    stroke(160);
    fill(rgb);
    rect(x, y, size, size);
  }
  public color getColor() { //returns the current color
    return rgb;
  }
  void clicked() { //sets the variable that isn't used until clicked in all of the squares to the color of this instance of the color picker
    if ((mouseX > x && mouseX < x+size) && (mouseY > y && mouseY < y+size)) {
      for (Square s : grid) {
        s.setColor(rgb);
      }
      cColor.setColor(rgb);
    }
  }
}

public class currentColor {
  int x, y, size;
  color rgb;
  currentColor(color myColor, int x_, int y_) {
    rgb = myColor;
    x = x_;
    y = y_;
    size = 40;
  }
  public void show() {
    stroke(160);
    fill(rgb);
    rect(x, y, size, size);
  }
  public void setColor(color r) { //returns the current color
    rgb = r;
  }

}

public class Timer {
  double timeLeft;
  double currentTime;
  boolean done;

  Timer(double time) {
    done = false;
    timeLeft = time;
    currentTime = second();
  }
  public void display() {
    fill(0);
    textSize(32);
    if (!done) {
      text((int)timeLeft, mouseX, mouseY);
    }
  }
  public void setTime(double time) {
    timeLeft = time;
  }

  public void countDown() {
    if (currentTime < second() || (currentTime == 59 && second() == 0)) {
      currentTime = second();
      if (!done) {
        timeLeft--;
      }
      if (timeLeft <= 0) {
        done = true;
      } else {
        done = false;
      }
    }
  }

  public boolean isDone() {
    return done;
  }
}

class colorBox {
  ArrayList <colorChanger> CC; //declares the color pickers
  int size;
  int x;
  int y;
  colorBox() {
    size = 250;
    x = bigSize-size;
    y = 0;
    CC = new ArrayList<colorChanger>();
    CC.add(new colorChanger(color(255, 0, 0), x+10, y));
    CC.add(new colorChanger(color(255, 125, 0), x+10, y+40));
    CC.add(new colorChanger(color(255, 255, 0), x+10, y+80));
    CC.add(new colorChanger(color(125, 255, 0), x+10, y+120));
    CC.add(new colorChanger(color(0, 255, 0), x+10, y+160));
    CC.add(new colorChanger(color(0, 255, 125), x+10, y+200));
    CC.add(new colorChanger(color(0, 255, 255), x+10, y+240));
    CC.add(new colorChanger(color(0, 125, 255), x+10, y+280));
    CC.add(new colorChanger(color(0, 0, 255), x+10, y+320));
    CC.add(new colorChanger(color(125, 0, 255), x+10, y+360));
    CC.add(new colorChanger(color(255, 0, 255), x+10, y+400));
    CC.add(new colorChanger(color(0), x+200, y+410));
    CC.add(new colorChanger(color(255), x+200, y+450));
  }

  void show() {
    fill(255);
    rect(x, y, size, size*2);
    for (colorChanger c : CC) {
      c.show();
    }
  }

  void clicked() {
    for (colorChanger c : CC) { //tests to see if the color pickers are clicked
      c.clicked();
    }
  }
}

void mouseReleased() {
  System.out.println(mouseX + " " + mouseY);
  c.clicked();
  if (t.isDone()) { 
    for (Square s : grid) {//testzs to see if the grid is clicked
      s.clicked();
      if (s.isClicked()) {
        t.setTime(time);
        s.wasClicked();
      }
    }
  }
}
