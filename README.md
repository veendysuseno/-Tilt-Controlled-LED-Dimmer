# Tilt-Controlled LED Dimmer (RGB-LED-Tilt-Sensor)

This project demonstrates how to control the brightness of an LED using a tilt sensor. The LED brightness increases when the tilt sensor is tilted and decreases when it is in the upright position.

## Components Used

- Arduino Uno
- LED
- Tilt Sensor
- Resistors
- Jumper Wires
- Breadboard

## Pin Configuration

- **PIN_LED**: connected to the LED (Pin 3)
- **PIN_TILT**: connected to the tilt sensor (Pin 4)

## How It Works

- **Tilt Sensor**: When the sensor is tilted, the brightness of the LED increases. When the sensor is upright, the brightness decreases.
- **LED Control**: The LED brightness is adjusted using PWM (Pulse Width Modulation) based on the tilt sensor's state.

## Code

```cpp
const int PIN_LED = 3;
const int PIN_TILT = 4;

const int MAX_BRIGHTNESS = 255;
int brightness = 0;

void setup() {
    pinMode( PIN_LED, OUTPUT );
    pinMode( PIN_TILT, INPUT_PULLUP );
}

void loop() {

    if( digitalRead(PIN_TILT) == LOW ) {
        brightness += (brightness < 255) ? 1 : 0;
    } else {
        brightness -= (brightness > 0) ? 1 : 0;
    }

    analogWrite( PIN_LED, MAX_BRIGHTNESS - brightness );
    delay( 10 );
}
```

## How to Use

1. Connect the LED and tilt sensor to the Arduino as per the pin configuration.
2. Upload the code to your Arduino.
3. Tilt the sensor to increase the LED brightness and return it to the upright position to decrease the brightness.
4. Observe the LED brightness changing based on the tilt sensor's orientation.

## Features

- Smooth LED dimming based on tilt sensor position.
- Simple and effective way to control LED brightness with a tilt sensor.

## License

This project is open-source and can be modified or distributed freely.
