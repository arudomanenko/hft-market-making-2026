set(SRC
    ../types.cpp
)

file(GLOB_RECURSE IMPL_SRC CONFIGURE_DEPENDS
    ../data_loader/*.cpp
    ../execution/*.cpp
    ../metrics/*.cpp
    ../portfolio/*.cpp
    ../strategy/*.cpp
)
list(APPEND SRC ${IMPL_SRC})

# static library
set(TARGET hft-market-making-lib)
add_library(${TARGET} STATIC ${SRC})
target_link_libraries(${TARGET} PUBLIC
    hft-market-making-common
)

# executable
set(TARGET hft-market-making)
add_executable(${TARGET} main.cpp)
target_link_libraries(${TARGET} PUBLIC hft-market-making-lib)
