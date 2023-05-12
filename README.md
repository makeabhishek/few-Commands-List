# few-Commands-List

https://stackoverflow.com/questions/61292460/how-do-i-make-sure-that-my-default-c-c-compiler-is-gcc
## Command list for c++ and c in macOs
which clang
which gcc

#### What is the name of the compiler used by make by default
On macOS Ventura, there are two aspects to the problem and some suggested solutions.
'''
$ mkdir junk
$ cd junk
$ > x.cpp
$ > y.c
$ make x y
c++     x.cpp     -o x
cc     y.c        -o y
$ cd ..
$ rm -fr junk
'''
This shows that the names used by make are cc and c++. Those are not obviously clang or clang++, but neither are they obviously gcc and g++

$ which cc c++
/usr/bin/cc
/usr/bin/c++
$

On macOS Catalina (and prior versions, and most likely subsequent versions too), there are two aspects to the problem and some suggested solutions.

What is the name of the compiler used by make by default?
$ mkdir junk
$ cd junk
$ > x.cpp
$ > y.c
$ make x y
c++     x.cpp   -o x
cc     y.c   -o y
$ cd ..
$ rm -fr junk
This shows that the names used by make are cc and c++. Those are not obviously clang or clang++, but neither are they obviously gcc and g++.

$ which cc c++
/usr/bin/cc
/usr/bin/c++
$

##### Which compiler is it really?
Which compiler really lives behind the names cc, c++, gcc, g++, clang, and clang++? We can check which compiler these really are by getting them to identify their version:

for compiler in cc c++ gcc g++ clang clang++
> do
>     which $compiler
>     $compiler --version
> done
/usr/bin/cc
Apple clang version 11.0.0 (clang-1100.0.33.17)
Target: x86_64-apple-darwin18.7.0
Thread model: posix
InstalledDir: /Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin
/usr/bin/c++
Apple clang version 11.0.0 (clang-1100.0.33.17)
Target: x86_64-apple-darwin18.7.0
Thread model: posix
InstalledDir: /Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin
/usr/bin/gcc
Configured with: --prefix=/Applications/Xcode.app/Contents/Developer/usr --with-gxx-include-dir=/usr/include/c++/4.2.1
Apple clang version 11.0.0 (clang-1100.0.33.17)
Target: x86_64-apple-darwin18.7.0
Thread model: posix
InstalledDir: /Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin
/usr/bin/g++
Configured with: --prefix=/Applications/Xcode.app/Contents/Developer/usr --with-gxx-include-dir=/usr/include/c++/4.2.1
Apple clang version 11.0.0 (clang-1100.0.33.17)
Target: x86_64-apple-darwin18.7.0
Thread model: posix
InstalledDir: /Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin
/usr/bin/clang
Apple clang version 11.0.0 (clang-1100.0.33.17)
Target: x86_64-apple-darwin18.7.0
Thread model: posix
InstalledDir: /Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin
/usr/bin/clang++
Apple clang version 11.0.0 (clang-1100.0.33.17)
Target: x86_64-apple-darwin18.7.0
Thread model: posix
InstalledDir: /Applications/Xcode.app/Contents/Developer/Toolchains/XcodeDefault.xctoolchain/usr/bin
$

As you can see, the versions installed in /usr/bin are all the same compiler, and that compiler is clang or clang++

## How do you change the default compiler?
