# JavaScript engine

**JavaScript engines** are interpreters that parse and execute JavaScript code. Modern JavaScript engines use just-in-time (JIT) compilation to convert JavaScript code into machine code that can be executed by a computer's processor. A JavaScript engine is typically developed and used in web browsers to run client-side code but can also be used in server-side environments like Node.js.

In a browser, the JavaScript engine operates together with the rendering engine via the Document Object Model [DOM](https://developer.mozilla.org/en-US/docs/Glossary/DOM) and [Web IDL bindings](https://developer.mozilla.org/en-US/docs/Glossary/WebIDL). Some JavaScript engines also execute WebAssembly code in the same sandbox as regular JavaScript code.

Do not confuse JavaScript engines with [rendering engines](https://developer.mozilla.org/en-US/docs/Glossary/Engine/Rendering), which are also crucial parts of browsers.

## What is doing?

1. Work with heap and stack
2. memory allocation, garbage collector
3. Compile JS to machine code
4. Optimization (caches, hidden classes and etc.)

## Resources

1. https://developer.mozilla.org/en-US/docs/Glossary/Engine/JavaScript
