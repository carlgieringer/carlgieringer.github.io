# Test scopes

The usual categorization is:

| Scope       | Definition       |
| ----------- | ---------------- |
| Unit        | Single module    |
| Integration | Multiple modules |
| End-to-end  | Entire system    |

But this categorization has some definitional and boundary problems:

* What is the definition of a module? Some possibilities:
  * Method
  * Class
* If a test includes a real dependency, does that make it an 
  integration tests?
* If a client-based test uses a SUT that includes fakes
  is it end-to-end?

# Test sizes

| Size        | Definition             |
| ----------- | ---------------------- |
| Small       | Single-threaded        |
| Medium      | Multi-threaded         |
| Large       | Multi-machine          |
| Extra large | Cross release boundary |
