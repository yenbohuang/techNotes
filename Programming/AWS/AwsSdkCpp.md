# Install cmake 3.x

    sudo apt-get install software-properties-common
    sudo add-apt-repository ppa:george-edison55/cmake-3.x
    sudo apt-get update
    sudo apt-get install cmake

See details on <http://askubuntu.com/questions/610291/how-to-install-cmake-3-2-on-ubuntu-14-04>

# CMake Error: Could not find CMAKE_ROOT !!!

    CMake Error: Could not find CMAKE_ROOT !!!
    CMake has most likely not been installed correctly.
    Modules directory not found in
    /usr/local/bin

Solution:

    export CMAKE_ROOT=/usr/share/cmake-3.2

See details on <http://www.linuxquestions.org/questions/slackware-14/cmake-build-crashes-when-running-as-user-800222/>

# No CMAKE_CXX_COMPILER could be found.

    No CMAKE_CXX_COMPILER could be found.
    
    Tell CMake where to find the compiler by setting either the environment
    variable "CXX" or the CMake cache entry CMAKE_CXX_COMPILER to the full path
    to the compiler, or to the compiler name if it is in the PATH.

Solution:

    sudo apt-get install g++

See details on <http://stackoverflow.com/questions/32801638/cmake-error-at-cmakelists-txt30-project-no-cmake-c-compiler-could-be-found>

# fatal error: curl/curl.h: No such file or directory

    /aws-sdk-cpp-master/aws-cpp-sdk-core/include/aws/core/http/curl/CurlHandleContainer.h:23:23: fatal error: curl/curl.h: No such file or directory

Solution:

    sudo apt-get install libcurl4-openssl-dev

See details on <http://stackoverflow.com/questions/11471690/curl-h-no-such-file-or-directory>

# Compile AWS SDK for C++

    cmake -DCMAKE_BUILD_TYPE=Release  <path-to-root-of-this-source-code>
    make
    sudo make install

See details on <https://github.com/awslabs/aws-sdk-cpp>