### KParser

Arithmetic Expression Parser Koltin Multi-Platform Library

[![Build Status](https://travis-ci.com/theLimitBreaker/KParser.svg?branch=master)](https://travis-ci.com/theLimitBreaker/KParser)
[ ![Download](https://api.bintray.com/packages/thelimitbreaker/KParser/KParser/images/download.svg) ](https://bintray.com/thelimitbreaker/KParser/KParser/_latestVersion)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

### Features

- Handle Multiple Operators
    - Minus (-)
    - Plus (+)
    - Multiply (*)
    - Division (/)
    - Power (^)
    - Exponential (E)
- Mathematical Functions
    - Trigonometric (Sin, Cos, Tan, asin,acos,atan)
    - Hyperbolic (Sinh, Cosh, Tanh)
    - Log10, 
    - ln (Natural log)
    - sqrt(Square root)
- Mathematical Constants
    - PI
    - e
    
#### Sample 

**JVM/Android**
```
val parser = ExpressionParser()
val result = parser.evaluateExpression("sin(PI)+1+cos(PI)")
println(result)
        
// result 0.0
```

**C/C++**

build the project with `./gradlew build`

Navigate to `KParser/build/bin/linux/releaseShared/`

Use the generated `libkparser_api.h` (header file) and `libkparser.so` (shared object file)

```
#include <iostream>
#include "libkparser_api.h"

int main() {
    
    libkparser_ExportedSymbols* lib = libkparser_symbols();
    libkparser_kref_io_thelimitbreaker_ExpressionParser kparser = libkparser_kref_io_thelimitbreaker_ExpressionParser();

    double  result = lib->kotlin.root.io.thelimitbreaker.ExpressionParser.evaluateExpression(kparser,"1+sin(PI)+cos(PI)",3);
    std::cout<<result << std::endl;
    return 0;
}
```
**Compiling C/C++ (Command Line)**
```
g++ main.cpp libkparser.so
```

**Compiling C/C++ (CMake config)**

Provided `libkparser_api.h` and `libkparser.so` are under folder `kparser`
```
add_library(kparser SHARED IMPORTED)
set_property(TARGET kparser PROPERTY IMPORTED_LOCATION "${PROJECT_SOURCE_DIR}/kparser/libkparser.so")
add_executable(PROJECT_NAME main.cpp kparser/libkparser_api.h)
target_link_libraries(${PROJECT_NAME} kparser)
```

### Usage with Gradle(JVM/Android)
```
 // In root build.gradle
 repositories {
        maven {
            url  "https://dl.bintray.com/thelimitbreaker/KParser"
        }
  }
  
  //Add in the dependencies
  dependencies{
         implementation 'io.thelimitbreaker:KParser-jvm:0.0.1'
  }
    
```

**Work Left**
- Add usage with JS
- Add support Windows and iOS