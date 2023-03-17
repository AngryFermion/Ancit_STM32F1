include(Utils)

add_executable(main)

target_sources(main
  PRIVATE
    #src/main.cpp
    src/main.c
    /home/vishnu/tools/STM32CubeF1/Drivers/STM32F1xx_HAL_Driver/Src/stm32f1xx_hal_gpio.c
    /home/vishnu/tools/STM32CubeF1/Drivers/STM32F1xx_HAL_Driver/Src/stm32f1xx_hal_rcc.c
    /home/vishnu/tools/STM32CubeF1/Drivers/STM32F1xx_HAL_Driver/Src/stm32f1xx_hal.c
/home/vishnu/tools/STM32CubeF1/Drivers/STM32F1xx_HAL_Driver/Src/stm32f1xx_hal_cortex.c
/home/vishnu/tools/STM32CubeF1/Drivers/STM32F1xx_HAL_Driver/Src/stm32f1xx_hal_pwr.c
/home/vishnu/tools/STM32CubeF1/Drivers/STM32F1xx_HAL_Driver/Src/stm32f1xx_hal_rtc.c
/home/vishnu/tools/STM32CubeF1/Drivers/CMSIS/Device/ST/STM32F1xx/Source/Templates/system_stm32f1xx.c
/home/vishnu/stm_cmake/stm32-cmake-blinking-led/cubemx/Src/stm32f1xx_hal_msp.c
#src/stm32f1xx_hal_msp.c
)

target_include_directories(main
  PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR}/inc
    ${CMAKE_CURRENT_SOURCE_DIR}/src
    /home/vishnu/tools/STM32CubeF1/Drivers/STM32F1xx_HAL_Driver/Inc
    /home/vishnu/tools/STM32CubeF1/Core/Inc
    /home/vishnu/tools/STM32CubeF1/Drivers/CMSIS/Device/ST/STM32F1xx/Include
    /home/vishnu/tools/STM32CubeF1/Drivers/CMSIS/Core/Include
)

target_link_libraries(main
  PRIVATE
    Crt
    #startup
    #hal
    #trace
)

set_property(TARGET main PROPERTY LINK_INTERFACE_MULTIPLICITY 3)
set_property(TARGET main PROPERTY SUFFIX .elf)

stm32_target_size(main)
stm32_target_listing(main)
stm32_target_install(main)

link_compile_commands_file(main)
