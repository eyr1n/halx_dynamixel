# halx_dynamixel

## 使い方

### CMakeLists.txt

```cmake
# ~略~

# ファイル末尾に以下を追記

include(FetchContent)
FetchContent_Declare(halx
  GIT_REPOSITORY https://github.com/eyr1n/halx.git
)
FetchContent_Declare(halx_dynamixel
  GIT_REPOSITORY https://github.com/eyr1n/halx_dynamixel.git
)
FetchContent_MakeAvailable(halx halx_dynamixel)

target_link_libraries(${PROJECT_NAME}
  halx
  halx_dynamixel
)
```

### C++

```cpp
#include <dynamixel_sdk.h>

#include <halx/peripheral.hpp>
#include <halx/dynamixel/port_handler.hpp>

// ~略~

// Dynamixelを制御するルーチンにてPortHandlerを初期化

halx::peripheral::Uart<&huart1> uart1;  // 使用するペリフェラルに応じて変更する
halx::dynamixel::PortHandler halx_dynamixel_port_handler(uart1);
dynamixel::PortHandler *portHandler = &halx_dynamixel_port_handler;

// 以降、portHandlerを公式サンプルどおりに操作できる
```
