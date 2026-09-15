cmake_minimum_required(VERSION 3.24)
project(rboot)



set(FILES_FOR_FORMATTING dummy.c )

if (NOT TARGET rlibhelper)
    include(FetchContent)
    FetchContent_Declare(
            rlibhelper
            GIT_REPOSITORY https://github.com/RoboticsHardwareSolutions/rlibhelper.git
            GIT_TAG main
    )
    FetchContent_MakeAvailable(rlibhelper)
endif ()


if(EXISTS "${rlibhelper_SOURCE_DIR}/format.cmake")
    include(${rlibhelper_SOURCE_DIR}/format.cmake)
else()
    message(WARNING "format.cmake file not found")
endif()
format_files(${PROJECT_NAME} SOURCES ${FILES_FOR_FORMATTING})