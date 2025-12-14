# Generated Cmake Pico project file

cmake_minimum_required(VERSION 3.13)

set(CMAKE_C_STANDARD 11)

set(FREERTOS_KERNEL_PATH ../FreeRTOS-Kernel)
set(FREERTOS_KERNEL_RP2040_RELATIVE_PATH portable/ThirdParty/GCC  )

include(pico_sdk_import.cmake)
project(FreeRTOS_TEST C CXX ASM)

pico_sdk_init()

# Pull in FreeRTOS
#include($ENV{FREERTOS_KERNEL_PATH}/portable/ThirdParty/GCC/RP2040/FreeRTOS_Kernel_import.cmake)
#include(FreeRTOS_Kernel_import.cmake)

include(../FreeRTOS-Kernel/portable/ThirdParty/GCC/RP2040/FreeRTOS_Kernel_import.cmake)


# Add executable. Default name is the project name, version 0.1
add_executable(FreeRTOS_TEST main.c )



pico_set_program_name(FreeRTOS_TEST "FreeRTOS_TEST")
pico_set_program_version(FreeRTOS_TEST "0.2")

pico_enable_stdio_uart(FreeRTOS_TEST 1)
pico_enable_stdio_usb(FreeRTOS_TEST 1)


target_include_directories(FreeRTOS_TEST PRIVATE ${CMAKE_CURRENT_LIST_DIR})



target_sources(FreeRTOS_TEST PRIVATE
        ${CMAKE_CURRENT_LIST_DIR}/main.c
        )




target_link_libraries(FreeRTOS_TEST
        hardware_timer
        hardware_watchdog
        hardware_clocks
        hardware_exception
	pico_stdlib
	hardware_spi
	FreeRTOS-Kernel 
	FreeRTOS-Kernel-Heap4        
)



