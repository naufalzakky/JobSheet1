
<h1 align="center">Laporan Praktikum Sistem Embedded</h1>
<p>Disusun Oleh:</p>

<ul>
  <li>Naufal Faterna Zakky 4.31.20.0.17</li>
</ul>

<h3>Daftar Jobsheet</h3>
<p></p>

<ul>
  <li><a href="https://github.com/naufalzakky/JobSheet1">JobSheet1</a></li>
  <li><a href="https://github.com/naufalzakky/JobSheet1.1">JobSheet1.1</a></li>
  <li><a href="https://github.com/naufalzakky/JobSheet2">JobSheet2</a></li>
  <li><a href="https://github.com/naufalzakky/JobSheet3">JobSheet3</a></li>
  <li><a href="https://github.com/naufalzakky/Nomor1">Nomor 1</a></li>
  <li><a href="https://github.com/naufalzakky/Nomor2">Nomor 2</a></li>
  <li><a href="https://github.com/naufalzakky/Nomor3">Nomor 3</a></li>
  <li><a href="https://github.com/naufalzakky/Nomor4">Nomor 4</a></li>
</ul>

<h2 align="center">Jobsheet 1</h2>
<h3>Coding</h3>
<p>Blink</p>

<pre>
<code>
// set pin numbers
const int buttonPin = 4; // the number of the pushbutton pin
const int ledPin = 5; // the number of the LED pin
const int buttonPin1 = 2;
const int ledPin1 = 19;
// variable for storing the pushbutton status
int buttonState = 0;
int buttonState1 = 0;
void setup() { 
 Serial.begin(115200);
 // initialize the pushbutton pin as an input
 pinMode(buttonPin, INPUT);
 pinMode(buttonPin1, INPUT);
 // initialize the LED pin as an output
 pinMode(ledPin, OUTPUT);
 pinMode(ledPin1, OUTPUT);
}
void loop() {
  
 // read the state of the pushbutton value
 buttonState = digitalRead(buttonPin);
 Serial.println(buttonState);
 // check if the pushbutton is pressed.
 // if it is, the buttonState is HIGH
 if (buttonState == HIGH) {
 // turn LED on
 digitalWrite(ledPin, HIGH);
 } else {
 // turn LED off
 digitalWrite(ledPin, LOW);
 }
 buttonState1 = digitalRead(buttonPin1);
 Serial.println(buttonState1);
 if (buttonState1 == HIGH) {
 // turn LED on
  digitalWrite(ledPin1, HIGH);   // turn the LED on (HIGH is the voltage level)
  delay(500);                       // wait for a second
  digitalWrite(ledPin1, LOW);    // turn the LED off by making the voltage LOW
  delay(500);                       // wait for a second
 } else {
 // turn LED off
 digitalWrite(ledPin1 , LOW);
 }
}
</code>
</pre>

<p>Push Button</p>
<pre>
<code>
// set pin numbers
const int buttonPin = 4;  // the number of the pushbutton pin
const int ledPin =  5;    // the number of the LED pin

// variable for storing the pushbutton status 
int buttonState = 0;

void setup() {
  Serial.begin(115200);  
  // initialize the pushbutton pin as an input
  pinMode(buttonPin, INPUT);
  // initialize the LED pin as an output
  pinMode(ledPin, OUTPUT);
}

void loop() {
  // read the state of the pushbutton value
  buttonState = digitalRead(buttonPin);
  Serial.println(buttonState);
  // check if the pushbutton is pressed.
  // if it is, the buttonState is HIGH
  if (buttonState == HIGH) {
    // turn LED on
    digitalWrite(ledPin, HIGH);
  } else {
    // turn LED off
    digitalWrite(ledPin, LOW);
  }
}

</code>
</pre>

<p>PWM</p>
<pre>
<code>
// the number of the LED pin
const int ledPin = 16;  // 16 corresponds to GPIO16
const int ledPin2 = 17; // 17 corresponds to GPIO17
const int ledPin3 = 5;  // 5 corresponds to GPIO5

// setting PWM properties
const int freq = 5000;
const int ledChannel = 0;
const int resolution = 8;
 
void setup(){
  // configure LED PWM functionalitites
  ledcSetup(ledChannel, freq, resolution);
  
  // attach the channel to the GPIO to be controlled
  ledcAttachPin(ledPin, ledChannel);
  ledcAttachPin(ledPin2, ledChannel);
  ledcAttachPin(ledPin3, ledChannel);
}
 
void loop(){
  // increase the LED brightness
  for(int dutyCycle = 0; dutyCycle <= 255; dutyCycle++){   
    // changing the LED brightness with PWM
    ledcWrite(ledChannel, dutyCycle);
    delay(15);
  }

  // decrease the LED brightness
  for(int dutyCycle = 255; dutyCycle >= 0; dutyCycle--){
    // changing the LED brightness with PWM
    ledcWrite(ledChannel, dutyCycle);   
    delay(15);
  }
}

</code>
</pre>
<p>ADC dan DAC</p>
<pre>
<code>
// These constants won't change. They're used to give names to the pins used:
const int analogInPin = 34;  // Analog input pin that the potentiometer is attached to
const int analogOutPin = 5; // Analog output pin that the LED is attached to

// setting PWM properties
const int freq = 5000;
const int ledChannel = 0;
const int resolution = 8;

int sensorValue = 0;        // value read from the pot
int outputValue = 0;        // value output to the PWM (analog out)

void setup() {
  Serial.begin(115200); // initialize serial communications at 115200 bps:

// configure LED PWM functionalitites
  ledcSetup(ledChannel, freq, resolution);
  
  // attach the channel to the GPIO to be controlled
  ledcAttachPin(analogOutPin, ledChannel);
}

void loop() {
  sensorValue = analogRead(analogInPin); // read the analog in value:
  outputValue = map(sensorValue, 0, 4095, 0, 255); // map it to the range of the analog out:
  analogWrite(analogOutPin, outputValue); // change the analog out value:

  // print the results to the Serial Monitor:
  Serial.print("sensor = ");
  Serial.print(sensorValue);
  Serial.print("\t output = ");
  Serial.println(outputValue);
  // wait 2 milliseconds before the next loop for the analog-to-digital
  // converter to settle after the last reading:
  delay(2);
}

</code>
</pre>

<h3>Hasil</h3>

https://github.com/naufalzakky/JobSheet1/blob/main/Pwm2.mp4

https://github.com/naufalzakky/JobSheet1/blob/main/2led_sCEXXukX.mp4

https://github.com/naufalzakky/JobSheet1/blob/main/20221117-115159_gTFsAO4o.mp4

https://github.com/naufalzakky/JobSheet1/blob/main/100ms.mp4
