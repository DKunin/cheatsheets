## Arduino 'reset'

Not actually resetting, but setting code in 0 position, so starting the code from beginning

```C
void(* resetFunc) (void) = 0; // Reset MC function
resetFunc(); //вызов
```
