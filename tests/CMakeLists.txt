cmake_minimum_required(VERSION 3.14)
project(scp-tests VERSION 1.0 LANGUAGES CXX C)

macro(run_test test)
    add_executable(${test} ${test}.cc)
    target_link_libraries(${test} PathTraceExtension MasterIDExtension SystemC::systemc)
    add_test(NAME ${test} COMMAND ${test})
    set_tests_properties(${test} PROPERTIES TIMEOUT 10)
endmacro()

run_test(smoke)
