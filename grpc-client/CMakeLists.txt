# Copyright 2019 GSI, Inc. All rights reserved.
#
#

# odc-grpc-client executable
add_executable(odc-grpc-client
    "src/main.cpp"
    "src/GrpcControlClient.h"
    "src/GrpcControlClient.cpp"
)
target_link_libraries(odc-grpc-client
    Boost::boost
    Boost::program_options
    odc_grpc_proto_lib
    odc_core_lib
)
target_include_directories(odc-grpc-client PUBLIC
    "$<BUILD_INTERFACE:${CMAKE_CURRENT_BINARY_DIR}/src>"
    "$<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/src>"
    "${GRPC_INCLUDE_DIR}"
)
install(TARGETS odc-grpc-client EXPORT ${PROJECT_NAME}Targets RUNTIME DESTINATION ${PROJECT_INSTALL_BINDIR})
