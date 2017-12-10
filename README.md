# Microcontroller

#include <NewPing.h>

#define TRIGGER_PIN  35
#define ECHO_PIN     34
#define MAX_DISTANCE 200
NewPing sonar(TRIGGER_PIN, ECHO_PIN, MAX_DISTANCE);

int prevSonar=0;
int curSonar=0;

void sonarSensor() {
  Serial.print("Ping: ");
  Serial.print(sonar.ping_cm());
  Serial.println("cm");
  //delay(300);
}


// rows are the anodes
// cols are the cathodes

// 1-dimensional array of row pin numbers:
const int row[16] = {
  38, 39, 40, 41, 
  42, 43, 44, 45, 
  46, 47, 48, 49, 
  50, 51, 52, 53
};



// 1-dimensional array of column pin numbers:
const int col[4] = {
  22, 23, 24, 25
};

const int en0 = 26;
const int en1 = 27;


// 1-dimensional array of column pin numbers:
const int col2[4] = {
  28, 29, 30, 31
};

const int en20 = 32;
const int en21 = 33;


const int LEFT = 100;
const int RIGHT = 200;


int LED1[8][8] = 
{ {0, 1, 1, 1, 0, 1, 0, 1},
  {0, 1, 0, 1, 0, 1, 0, 1},
  {0, 1, 0, 1, 0, 1, 0, 1},
  {0, 1, 0, 1, 0, 1, 0, 1},
  {0, 1, 0, 1, 0, 1, 0, 1},
  {0, 1, 0, 1, 0, 1, 0, 1},
  {0, 1, 0, 1, 0, 1, 0, 1},
  {0, 1, 0, 1, 0, 1, 0, 1},
};

//
//
int LED2[16][16] = 
{ {0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1},
  {0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1},
  {0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1},
  {0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1},
  {0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1},
  {0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1},
  {0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1},
  {0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1},
  {0, 1, 1, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1},
  {0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1},
  {0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1},
  {0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1},
  {0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1},
  {0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1},
  {0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1},
  {0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1, 0, 1},
};

int player[16][16] = 
{ {0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0},
  {0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0},
  {0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0},
  {0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0},

  {0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0},
  {0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0},
  {0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0},
  {0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0},

  {0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0},
  {0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0},
  {0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0},
  {0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0},

  {0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0},
  {0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0},
  {0, 0, 0, 0, 0, 0, 0, 0, 1, 0, 0, 0, 0, 0, 0, 0},
  {0, 0, 0, 0, 0, 0, 0, 1, 1, 1, 0, 0, 0, 0, 0, 0}
};
int gameState[16][16] = 
{ {0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0},
  {0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0},
  {0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0},
  {0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0},

  {0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0},
  {0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0},
  {0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0},
  {0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0},

  {0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0},
  {0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0},
  {0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0},
  {0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0},

  {0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0},
  {0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0},
  {0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0},
  {0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0}
};


void drawPlayer(int gameState[][16],int x,int y)
{
   gameState[x][y+1]=gameState[x+1][y]=gameState[x+1][y+1]=gameState[x+1][y+2]=1;
   
}


// cursor position:
int x = 5;
int y = 5;
int playerPositionX = 7;





void setup() {

  Serial.begin(9600);
  
  // put your setup code here, to run once:
  // initialize the I/O pins as outputs iterate over the pins:

  /*
   * Configure row pins as digital output pins
   */
  for(int rowPin = 0; rowPin <16; rowPin++) {
    pinMode(row[rowPin], OUTPUT);
  }

  for(int rowPin = 0; rowPin <16; rowPin++) {
    digitalWrite(row[rowPin], LOW);
  }

  /*
   * Configure col pins as digital output pins
   */
  for(int colPin=0; colPin<4; colPin++) {
    pinMode(col[colPin], OUTPUT);
    pinMode(col2[colPin], OUTPUT);
  }

  for(int colPin=0; colPin<4; colPin++) {
    digitalWrite(col[colPin], LOW);
    digitalWrite(col2[colPin], LOW);
  }

  
  pinMode(en0, OUTPUT);
  pinMode(en1, OUTPUT);
  digitalWrite(en0, HIGH);
  digitalWrite(en1, HIGH);

  pinMode(en20, OUTPUT);
  pinMode(en21, OUTPUT);
  digitalWrite(en20, HIGH);
  digitalWrite(en21, HIGH);

  //displayAllPin();
  prevSonar = sonar.ping_cm();

}



void displayAllPin() {

  digitalWrite(en0, LOW);
  digitalWrite(en1, LOW);

  
  for(int rowPin = 0; rowPin <16; rowPin++) {
    digitalWrite(row[rowPin], HIGH);
  }

  int var1 = 0;

  for(int i=0; i<16; i++) {
    for(int j=0; j<4; j++) {
      var1 = (i>>j) & 1;
      digitalWrite(col[j], var1);
      
    }
    delay(1);
  }

}

void test() {
  digitalWrite(en0, LOW);
  digitalWrite(en1, LOW);

  
  for(int rowPin = 0; rowPin <16; rowPin++) {
    digitalWrite(row[rowPin], HIGH);
  }

  digitalWrite(col[0], HIGH);
}


void pattern1() {
  int var1;
  int var2;
  //digitalWrite(en0, LOW);
  //digitalWrite(en1, LOW);
  digitalWrite(en20, LOW);
  digitalWrite(en21, LOW);

  
  for(int j=0; j<16; j++) {
    
    for(int b=0; b<4; b++) {
      var1 = (j>>b) & 1;
      digitalWrite(col2[b], var1);
      digitalWrite(col[b], var1);
    }

    for(int i=0; i<16; i++) {
      digitalWrite(row[i], player[i][j]);
      //delay(1);
      digitalWrite(row[i], LOW);
    }
  }
}


void pattern2() {
  int var1;
  int var2;
  //digitalWrite(en0, LOW);
  //digitalWrite(en1, LOW);
  digitalWrite(en20, LOW);
  digitalWrite(en21, LOW);

  
  for(int j=0; j<16; j++) {
    
    for(int b=0; b<4; b++) {
      var1 = (j>>b) & 1;
      digitalWrite(col2[b], var1);
      digitalWrite(col[b], var1);
    }

    for(int i=0; i<16; i++) {
      if(i == j) var2 = 1;
      else var2 = 0;
      digitalWrite(row[i], var2);
      delay(0);
      digitalWrite(row[i], LOW);
    }
  }
}


void drawPlayer() {

  
  for(int i=0; i<16; i++) {
     digitalWrite(row[i], LOW);
  }
    
  int var1;
  int var2;
  //digitalWrite(en0, LOW);
  //digitalWrite(en1, LOW);
  digitalWrite(en20, LOW);
  digitalWrite(en21, LOW);

  for(int b=0; b<4; b++) {
    var1 = (playerPositionX>>b) & 1;
    digitalWrite(col2[b], var1);
    digitalWrite(col[b], var1);
  }

  digitalWrite(row[15], HIGH);
  digitalWrite(row[15], LOW);



  for(int b=0; b<4; b++) {
    var1 = ( (playerPositionX+1) >>b) & 1;
    digitalWrite(col2[b], var1);
    digitalWrite(col[b], var1);
  }

  digitalWrite(row[15], HIGH);
  digitalWrite(row[15], LOW);
  digitalWrite(row[14], HIGH);
  digitalWrite(row[14], LOW);


  for(int b=0; b<4; b++) {
    var1 = ( (playerPositionX+2) >>b) & 1;
    digitalWrite(col2[b], var1);
    digitalWrite(col[b], var1);
  }

  digitalWrite(row[15], HIGH);
  digitalWrite(row[15], LOW);

  

}



void drawPlayerLong(int limit = 10000) {

  for(int t=0; t<limit; t++) {
    
    for(int i=0; i<16; i++) {
     digitalWrite(row[i], LOW);
    }
      
    int var1;
    int var2;
    //digitalWrite(en0, LOW);
    //digitalWrite(en1, LOW);
    digitalWrite(en20, LOW);
    digitalWrite(en21, LOW);
  
    for(int b=0; b<4; b++) {
      var1 = (playerPositionX>>b) & 1;
      digitalWrite(col2[b], var1);
      //digitalWrite(col[b], var1);
    }
  
    digitalWrite(row[15], HIGH);
    delay(2);
    digitalWrite(row[15], LOW);
  
  
  
    for(int b=0; b<4; b++) {
      var1 = ( (playerPositionX+1) >>b) & 1;
      digitalWrite(col2[b], var1);
      //digitalWrite(col[b], var1);
    }
  
    digitalWrite(row[15], HIGH);
    delay(2);
    digitalWrite(row[15], LOW);
    digitalWrite(row[14], HIGH);
    delay(2);
    digitalWrite(row[14], LOW);
  
  
    for(int b=0; b<4; b++) {
      var1 = ( (playerPositionX+2) >> b) & 1;
      digitalWrite(col2[b], var1);
      //digitalWrite(col[b], var1);
    }
  
    digitalWrite(row[15], HIGH);
    delay(2);
    digitalWrite(row[15], LOW);
  }

}


void movePlayer(int dir) {
  
  if( dir == LEFT) {
    if(playerPositionX == 0) return;
    else playerPositionX--;
  }
  else {
    if(playerPositionX == 15) return;
    else playerPositionX++;
  }
}



void setPlayer(int x) {
  if(x>=0 && x<=13)
    playerPositionX = x;
}

int counter = 0;


void testAnimate() {
     playerPositionX = 0;
   for(int i=0; i<10000; i++){
    drawPlayer();
   }

   playerPositionX = 1;
   for(int i=0; i<10000; i++){
    drawPlayer();
   }
   playerPositionX = 2;
   for(int i=0; i<10000; i++){
    drawPlayer();
   }
   playerPositionX = 3;
   for(int i=0; i<10000; i++){
    drawPlayer();
   }
   playerPositionX = 4;
   for(int i=0; i<10000; i++){
    drawPlayer();
   }
}

void testAnimate2() {
  for(int x=0; x<15; x++) {
    setPlayer(x);
    drawPlayerLong(800);
  }
}



void syncSonar(int x) {
  int pos = 0;
    if(0<=x && x<=1) pos = 0;
    else if(0<=x && x<=1) pos = 0;
    else if(2<=x && x<=3) pos = 1;
    else if(4<=x && x<=5) pos = 2;
    else if(6<=x && x<=7) pos = 3;
    else if(8<=x && x<=9) pos = 4;
    else if(10<=x && x<=11) pos = 5;
    setPlayer(pos);
    drawPlayerLong(400);
}

void syncSonar2() {
  int pos = playerPositionX;
  if(pos - sonar.ping_cm() >= 5 ) {
    setPlayer(pos-1);
    drawPlayerLong(400);
  }
  else if (sonar.ping_cm() - pos >= 5) {
    setPlayer(pos+1);
    drawPlayerLong(400);
  }
}


void syncSonar3() {
  curSonar = sonar.ping_cm();
  
  int pos = playerPositionX;
  if(prevSonar - curSonar >= 3 ) {
    setPlayer(pos-1);
    drawPlayerLong(200);
  }
  if(curSonar - prevSonar >= 3) {
    setPlayer(pos+1);
    drawPlayerLong(200);
  }
  else{
    drawPlayerLong(200);
  }
  prevSonar = curSonar;
}

void syncSonar4() {

  int x;
  int s = sonar.ping_cm();
  int scounter=0;

  while(scounter++ <= 3) {
    if( s != sonar.ping_cm() ) return ;
    drawPlayerLong(1);
  }

  
  if( s == 0) {
    x = playerPositionX;
    setPlayer(x);
  }
    
  else {
     x = s - 3;
     setPlayer(x/2);
  }
   
  
  drawPlayerLong(2);
}

void syncSonar5() {

  int x;
  int s = sonar.ping_cm();
  int scounter=0;

  while(scounter++ <= 5) {
    if( s != sonar.ping_cm() ) return ;
    drawPlayerLong(20);
  }

  if(s<8) setPlayer(0);
  else
    setPlayer(s-7);
  drawPlayerLong(400);

}


void shoot() {
  int attackPos = playerPositionX + 1;
  int var1;
  digitalWrite(en20, HIGH);
  digitalWrite(en21, HIGH);
  
  digitalWrite(en0, LOW);
  digitalWrite(en1, LOW);
  
  for(int b=0; b<4; b++) {
    var1 = ( (playerPositionX+1) >>b) & 1;
    //digitalWrite(col2[b], var1);
    digitalWrite(col[b], var1);
  }

  for(int r=13; r>=0; r--) {
    digitalWrite(row[r], HIGH);
    //drawPlayerLong(1);
    delay(10);
    digitalWrite(row[r], LOW);
  }
  digitalWrite(en0, HIGH);
  digitalWrite(en1, HIGH);

  digitalWrite(en20, LOW);
  digitalWrite(en21, LOW);
}


void flexSensor() {
  float flex;
  flex = analogRead(A0)*5/1023.0;
  Serial.println(flex);
  if(flex<=1.0) {
    Serial.println("Shoot");
    shoot();
  }
  flex = 2;
  
}
 


void loop() {

  //sonarSensor();
  syncSonar4();
  flexSensor();

}

















