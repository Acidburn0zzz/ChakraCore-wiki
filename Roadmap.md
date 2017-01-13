_This is a living document. It describes the priorities as they exist today and will evolve over time._

All the changes done in the public repository flow into Chakra and Microsoft Edge on a regular basis as described in the [Contribution guidelines](https://github.com/Microsoft/ChakraCore/blob/master/CONTRIBUTING.md). The following is a summary of the ChakraCore team's backlog for the next 6 months. Last updated 1/12/17.

# Enhancing Host & Platform Support 
* **Node.js**
  * [x] Update [Node.js+ChakraCore](https://github.com/nodejs/node-chakracore) to include [ChakraCore 1.2](https://github.com/Microsoft/ChakraCore/tree/release/1.2)
  * [x] Implement V8 debug protocol in the Node.js [ChakraShim](https://github.com/nodejs/node-chakracore/tree/chakracore-master/deps/chakrashim) to enable debugging using VS Code.
  * [ ] Support Chrome Debug Protocol in Node-ChakraCore.

* **Cross-platform**: (See [#111: \[Discussion\] Linux / Cross-platform planning](https://github.com/Microsoft/ChakraCore/issues/111).) An implementation of ChakraCore interpreter and runtime on Linux, targeting x64 Ubuntu 16.04 LTS and Clang 3.8+
  * [x] Get GC host app to build and run (no concurrency and no partial collections)
  * [x] Get lib\runtime\base directory to compile
  * [x] Get lib\Parser to compile
  * [x] Get lib\runtime\bytecode directory to compile
  * [x] Get lib\runtime\library directory to compile
  * [x] Get lib\runtime\language directory to compile, rewrite assembly portions
  * [x] Make it link on Linux
  * [x] Make it run and pass unit tests on Linux
    * [x] Run hello world
    * [x] Run tests in the Basics directory
    * [x] Run Date-related unit tests
    * [x] Run Exception/Stack-walking related unit tests
    * [x] Run benchmarks
    * [x] Pass all unit tests
  * [x] Enable Jenkins CI support for Linux
  * [x] Build and pass unit tests on OS X
  * [x] Enable Jenkins CI support for OS X
  * [ ] Match node-chakracore on xplat
  * [ ] Enable Intl on xplat
  * [ ] Match Windows-ChakraCore on test262
  * [ ] Enable profiling interpreter on xplat
  * [x] Enable dynamic interpreter thunks on xplat
  * [x] Enable JIT on xplat
  * [x] Implement broader software-based write barrier support in the GC
  * [x] Enable concurrent GC on xplat
  * [x] Enable partial GC on xplat
  * [x] Ensure xplat perf is fully on par with Windows

# Language Innovation & Standards
* Begin decoding WebAssembly post-order binary format and converting to ASM.JS bytecode
    * [x] 0xB format
    * [x] 0xC format
    * [x] 0xD format
* [ ] Complete module implementation (ES6)
* [x] Eval support in default parameter list  (ES6)
- Well-known symbols: (ES6)
    * [x] [Symbol.hasInstance](https://github.com/Microsoft/ChakraCore/pull/1063)
    * [x] [Symbol.toPrimitive](https://github.com/Microsoft/ChakraCore/pull/1319) (under experimental features)
    * [x] [Symbol.toStringTag](https://github.com/Microsoft/ChakraCore/pull/1383)
    * [x] [Symbol.isConcatSpreadable](https://github.com/Microsoft/ChakraCore/pull/1198)
* [x] Prototype shared memory and atomics (ESNext)
- Regex Buffet (ESNext)
    * RegExp named capture groups
    * RegExp lookbehind
* [x] [Object.getOwnPropertyDescriptors (ESNext)](https://github.com/Microsoft/ChakraCore/pull/1202)

# Performance - Staying Fast and Lean
* Implement ability to "re-defer" functions and pitch byte code for already JITted functions.
    * [x] [Determine closure captures precisely in the presence of deferred functions.](https://github.com/Microsoft/ChakraCore/pull/1167)
    * [x] Identify legal re-deferral candidates.
    * [x] Put function in deferred state and change entry point.
    * [x] Design heuristics

# Diagnostics & Tooling Enhancements
* [x] [Merge JsRTDebugging branch to master.](https://github.com/Microsoft/ChakraCore/pull/926) This branch contains an implementation of flat C debugging APIs following the existing JSRT pattern that can easily be bridged to the V8 debug protocol.
* [x] [Integrate Time Travel Debugging implementation into master](https://github.com/Microsoft/ChakraCore/pull/1160)
  * Review and agree on JSRT API shape
* [x] Enhance the Node.js [ChakraShim](https://github.com/nodejs/node-chakracore/tree/chakracore-master/deps/chakrashim) to enable TTD recording of Node.js and playback using ch.exe.

# Engineering Improvements
* [x] [Introduce C++ unit testing mechanism](https://github.com/Microsoft/ChakraCore/pull/1224) using [Catch](https://github.com/philsquared/Catch)
* [x] [Move JSRT API unit tests from internal testing mechanism to new framework](https://github.com/Microsoft/ChakraCore/pull/1224)
* [ ] Enable easier authoring of JavaScript built-ins in JavaScript.

# Releases

See [[Release Notes]] for notes on published releases.