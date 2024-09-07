# cpp-interrupt-example
This show how to encapsulate late interrupt in a class

https://www.reddit.com/r/embedded/comments/10y3u3w/how_to_handle_interrupt_with_cpp/
```cpp
class Uart {

  static constexpr size_t MAX_UARTS = 8;

  Uart(uint8_t index) {
    assert(index < MAX_UARTS);
    assert(registeredUarts[index] = nullptr);
    registeredUarts[index] = this;
  };
    
  static std::array<Uart*, MAX_UARTS> registeredUarts;
  static uint8_t getActiveUart() {
    // return which UART index the interrupt was for
  }
  static void onUartInterrupt() {
    Uart* u = registeredUarts[getActiveUart()];
    if (u) {
      u->doInterruptStuff();
    }
  }
}
```
