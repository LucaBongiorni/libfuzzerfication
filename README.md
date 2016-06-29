
# libfuzzerfication

<img src="https://raw.githubusercontent.com/ouspg/libfuzzerfication/master/pictures/fuzzing.png" width="500" height="284" alt="Fuzzing in action">

# Synopsis
Purpose of fuzzing is to automatically generate lots of pseudo-random test input and to make code crash and increase code coverage.

This project uses [libFuzzer](http://llvm.org/docs/LibFuzzer.html) and purpose is to make it easy to find vulnerabilities from commonly used libraries. We have list of top 50 most used libraries from [Protecode SC](http://www.codenomicon.com/products/appcheck/). LibFuzzer itself can be built with any compiler without specific flags. Target code must be buit with Clang using [ASan](http://clang.llvm.org/docs/AddressSanitizer.html), [USan](http://clang.llvm.org/docs/UndefinedBehaviorSanitizer.html) or [MSan](http://clang.llvm.org/docs/MemorySanitizer.html) and -fsanitize-coverage=edge[,8bit-counters,trace-cmp,indirect-calls]

"LibFuzzer is a library for in-process, coverage-guided, evolutionary fuzzing of other libraries.
LibFuzzer is similar in concept to [American Fuzzy Lop (AFL)](http://lcamtuf.coredump.cx/afl/), but it performs all of its fuzzing inside a single process. This in-process fuzzing can be more restrictive and fragile, but is potentially much faster as there is no overhead for process start-up."
http://llvm.org/docs/LibFuzzer.html

# Motivation
There have been lots of vulnerabilities in popular libraries that should have been (theoretically) easy to test. We want to offer easy way to fuzz-test these libraries and increase awareness about the situation. We also want this to be available to everyone.

Google cloud is going to be used for scale.

You're welcome to collaborate!

This is part of [OUSPG-open](https://github.com/ouspg/ouspg-open)

# How does it work?
* Pull container from Dockerhub
* Write your own libfuzzer stub
* Share dockerfile with other users
* Use libFuzzer to collect corpus so that other people can continue where you left off

# Requirements
* [docker-machine version 0.7.0](https://docs.docker.com/machine/)
* [Docker version 1.11.2](https://www.docker.com/)
* [docker-compose version 1.7.1](https://docs.docker.com/compose/)

# About libfuzzer
* LibFuzzer is open-source library (part of LLVM)
* Relies on compiler instrumentation to get coverage feedback
* It is linked with the library under test
* Works fully in process -> Fast!
* Should be combined with [ASan](http://clang.llvm.org/docs/AddressSanitizer.html), [USan](http://clang.llvm.org/docs/UndefinedBehaviorSanitizer.html) or [MSan](http://clang.llvm.org/docs/MemorySanitizer.html)

# Material

* [libFuzzer](http://llvm.org/docs/LibFuzzer.html)
* [SanitizerCoverage](http://clang.llvm.org/docs/SanitizerCoverage.html)
* You can find some nice examples from: [libfuzzer-bot repo](https://github.com/google/libfuzzer-bot)
* [libFuzzer in Chrome](https://chromium.googlesource.com/chromium/src/+/master/testing/libfuzzer/README.md)
* [Efficient Fuzzer](https://chromium.googlesource.com/chromium/src/+/master/testing/libfuzzer/efficient_fuzzer.m

# Team
* Mikko Yliniemi (@mikessu)
* Atte Kettunen (@attekett)
* Pauli Huttunen (@WhiteEyeDoll)
