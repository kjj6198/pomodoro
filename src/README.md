## Arduino Pomodoro
**WARNING: still in development, use at your own risk**

A simple pomodoro implementation using timer interrupt. By default, this app uses timer1 and timer2.

## Example

```c++
#include <pomodoro.h>

Pomodoro pomodoro = Pomodoro();
void callback() {
	int state = pomodoro.get_state(); // you can get pomodoro state
	int countdown = pomodoro.get_countdown(); // you can get pomodoro countdown

	Serial.println("A second is passed!");
}

void complete(pomodoro_state state) {
	// called when countdown finished
}


void setup() {
	pomodoro.set_per_second_callback(callback); // called every second
  pomodoro.set_timesup_callback(complete); // called when countdown finished
}

void loop() {

}

// register timer interrupt
ISR(TIMER1_COMPA_vect)
{
  pomodoro.handle_timer_interrupt();
}
```
