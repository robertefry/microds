
add_executable(microds-tests "")
target_link_libraries(microds-tests PRIVATE microds)

file(GLOB_RECURSE GLOB_SOURCES CONFIGURE_DEPENDS
  "*.c" "*.cc" "*.cpp" "*.cxx")
target_sources(microds-tests PRIVATE ${GLOB_SOURCES})

CPMAddPackage("gh:catchorg/Catch2@3.10.0")
target_link_libraries(microds-tests PUBLIC Catch2::Catch2WithMain)

add_test(
  NAME microds-tests
  COMMAND $<TARGET_FILE:microds-tests>
)

add_custom_target(test-microds
  COMMAND $<TARGET_FILE:microds-tests>
  DEPENDS microds-tests
)
