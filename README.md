# PUSHBUTTON
Push Button Counter Using Adriuno
Code:
const int buttonPin = 3;  // Pin for the push button
int counter = 0;  // Initialize counter to 0
int buttonState = 0;  // Variable for reading the push button status
int lastButtonState = 0;  // Variable for storing the last push button status

void setup() {
  pinMode(buttonPin, INPUT);  // Initialize the push button pin as an input
  Serial.begin(9600);  // Initialize serial communication at 9600 bits per second
}

void loop() {
  buttonState = digitalRead(buttonPin);  // Read the state of the push button

  if (buttonState != lastButtonState) {  // Check if the button state has changed
    if (buttonState == HIGH) {  // If the button is pressed
      counter++;  // Increment the counter
      Serial.println(counter);  // Print the current counter value

      if (counter >= 10) {  // If the counter reaches 10
        Serial.println("Maximum count reached!");  // Print a message
        counter = 0;  // Reset the counter
      }
    }
  }

  lastButtonState = buttonState;  // Store the current button state for the next iteration
  delay(50);  // Debounce the button press
}

