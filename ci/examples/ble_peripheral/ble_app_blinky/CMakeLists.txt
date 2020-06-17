cmake_minimum_required(VERSION 3.14)
project(ble_app_blinky LANGUAGES C ASM)

list(APPEND CMAKE_MODULE_PATH "../cmake")
include("nrf5")

add_executable(${CMAKE_PROJECT_NAME}
  "${NRF5_SDK_PATH}/examples/ble_peripheral/ble_app_blinky/main.c"
)
nrf5_target(${CMAKE_PROJECT_NAME})
nrf5_target_link_groups(${CMAKE_PROJECT_NAME} PRIVATE common log ble)
nrf5_target_link_libraries(${CMAKE_PROJECT_NAME} PRIVATE
  nrf5_nrfx_prs  
  nrf5_drv_uart
  nrf5_app_button
  nrf5_bsp
  nrf5_ble_srv_lbs
)
