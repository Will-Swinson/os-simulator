include_directories(include)

add_library(scheduler_core STATIC src/scheduler.cpp)

target_compile_features(scheduler_core PUBLIC cxx_std_20)

target_include_directories(scheduler_core PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include)

pybind11_add_module(os_algorithms src/pybind_module.cpp)

target_link_libraries(os_algorithms PRIVATE scheduler_core)

install(TARGETS os_algorithms DESTINATION .)
