# C

## Lib

```c++

```

## Cortex-M

### IO

```c
#ifdef  __GNUC__
int __io_putchar(int ch)
{
        HAL_UART_Transmit(&huart1, (uint8_t *)&ch, 1, 100);
        return ch;
}
#else
int fputc(int ch, FILE *f)
{
        HAL_UART_Transmit(&huart1, (uint8_t *)&ch, 1, 100);
        return ch;
}
#endif
```

# C++

## Lib

```c++
// 查看是否为引用类型
#include <boost/type_index.hpp>
boost::typeindex::type_id_with_cvr<decltype(变量)>().pretty_name().c_str()
```

