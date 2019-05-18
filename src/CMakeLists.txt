add_executable(cpp-src-compression
        main.cpp
        )

find_library(CLANG_LIBRARY clang-6.0)

execute_process(COMMAND llvm-config --cppflags OUTPUT_VARIABLE CLANG_CPP_FLAGS)

get_target_property(CPP_SRC_COMPRESSION_COMPILE_FLAGS cpp-src-compression COMPILE_FLAGS)
if (NOT CPP_SRC_COMPRESSION_COMPILE_FLAGS)
    unset(CPP_SRC_COMPRESSION_COMPILE_FLAGS)
endif()
set(CPP_SRC_COMPRESSION_COMPILE_FLAGS "${CPP_SRC_COMPRESSION_COMPILE_FLAGS} ${CLANG_CPP_FLAGS}")
set_target_properties(cpp-src-compression PROPERTIES COMPILE_FLAGS ${CPP_SRC_COMPRESSION_COMPILE_FLAGS})

target_link_libraries(cpp-src-compression
        ${CLANG_LIBRARY}
        )