# LangCheck: Smart Contract Language Audit Checklist

An organized and comprehensive checklist to assist auditors in evaluating the security, reliability, and quality of smart contract languages.

## How to Use This Checklist

1. **Familiarize Yourself with the Language**: Begin by understanding the fundamental concepts, syntax, and semantics of the smart contract language under review.

2. **Review Categories Systematically**: Go through each category in the checklist, examining the language features and tooling against each item.

3. **Document Findings**: For each item, note whether the language meets the criteria, partially meets it, or fails to meet it. Provide detailed explanations for any issues found.

4. **Prioritize Issues**: Identify critical vulnerabilities or shortcomings that could significantly impact security or functionality, and prioritize them for remediation.

5. **Provide Recommendations**: Suggest improvements or best practices to address any identified issues.

---

## Table of Contents

- [1. Language Syntax and Semantics](#1-language-syntax-and-semantics)
- [2. Compiler and Tooling](#2-compiler-and-tooling)
- [3. Security Features and Vulnerabilities](#3-security-features-and-vulnerabilities)
- [4. Concurrency and Parallelism](#4-concurrency-and-parallelism)
- [5. Storage and State Management](#5-storage-and-state-management)
- [6. Performance and Gas Efficiency](#6-performance-and-gas-efficiency)
- [7. Error Handling and Exception Safety](#7-error-handling-and-exception-safety)
- [8. Documentation and Community Support](#8-documentation-and-community-support)
- [9. Code Readability and Maintainability](#9-code-readability-and-maintainability)
- [10. Dependency Management](#10-dependency-management)

---

## 1. Language Syntax and Semantics

### 1.1 Misleading Notation and Syntax Ambiguities

- **L1**: Does the language allow the use of non-existent keywords or attributes without triggering an error?  
  *This can mislead developers and readers, potentially hiding malicious code.*

- **L2**: Are there any syntactic elements that could be confusing or easily misinterpreted?  
  *Ambiguities in syntax can lead to unintended code behavior.*

### 1.2 Arbitrary Custom Selectors

- **L3**: Does the language allow developers to define custom selectors for functions?  
  *Custom selectors can lead to selector collisions and security vulnerabilities.*

- **L4**: Are there mechanisms to prevent selector collisions, especially in proxy patterns and upgrades?

- **L5**: Can arbitrary custom selectors be exploited to introduce backdoors or obfuscate malicious code?

### 1.3 Implicit State Mutability

- **L6**: Does the language make state mutability explicit in functions and methods?  
  *Implicit mutability can lead to unintended state changes and side effects.*

- **L7**: Are there clear distinctions between pure, view, and mutating functions?

### 1.4 Inconsistent Type Inference

- **L8**: Is type inference consistent and predictable throughout the language?

- **L9**: Are there scenarios where type inference could lead to unexpected behavior or vulnerabilities?

---

## 2. Compiler and Tooling

### 2.1 Error Reporting and Debugging

- **C1**: Does the compiler provide clear and actionable error messages when code fails to compile?  
  *Opaque or unhelpful errors hinder development and debugging.*

- **C2**: Is there a robust debugger available for the language?  
  *A lack of debugging tools can make it difficult to trace and fix issues.*

### 2.2 Build Output

- **C3**: Is the compilation output excessively large?  
  *Large binaries can lead to increased deployment costs and may indicate inefficiencies.*

- **C4**: Is the build output deterministic?  
  *Deterministic builds are essential for verifying code and ensuring consistency across deployments.*

### 2.3 Toolchain Support

- **C5**: Are there reliable tools for testing, linting, and static analysis available?

- **C6**: Does the language integrate smoothly with existing development environments and CI/CD pipelines?

---

## 3. Security Features and Vulnerabilities

### 3.1 Reentrancy Protection

- **S1**: Is reentrancy enabled by default in the language?  
  *Reentrancy can lead to critical vulnerabilities if not properly managed.*

- **S2**: Does the language provide built-in primitives or abstractions to prevent reentrancy attacks?

- **S3**: Are there default protections or patterns recommended to developers to mitigate reentrancy?

### 3.2 Overflow and Underflow Protection

- **S4**: Does the language have built-in mechanisms to prevent integer overflow and underflow vulnerabilities?  
  *Arithmetic errors can lead to significant security issues.*

- **S5**: Are these checks enforced at compile-time or runtime?

### 3.3 Input Validation and Sanity Checks

- **S6**: Does the language encourage or enforce robust input validation mechanisms?  
  *Validating external data is critical for security.*

- **S7**: Are there standard libraries or functions to assist with input sanitization?

### 3.4 Error Propagation and Handling

- **S8**: How does the language handle errors and exceptions within contracts and across external calls?  
  *Proper error handling is essential for predictable and secure code execution.*

- **S9**: Are errors propagated correctly, and can they be handled gracefully by developers?

### 3.5 Native Asset Handling

- **S10**: Can contracts created with the language receive the native asset (e.g., Ether) without explicit indication?  
  *Implicit receipt of assets can lead to unintended vulnerabilities.*

- **S11**: Are there safeguards to prevent contracts from unintentionally accepting native assets?

### 3.6 Gas Management

- **S12**: Are there scenarios where gas is incorrectly charged, either overpriced or free?  
  *Improper gas charging can halt nodes or lead to denial-of-service attacks.*

- **S13**: Does the language provide accurate gas estimation and management tools?

### 3.7 Dependency Security

- **S14**: How does the language manage external dependencies and libraries?  
  *Dependency hijacking can introduce vulnerabilities.*

- **S15**: Are there mechanisms to verify the integrity and security of dependencies?

- **S16**: Are security audits required or facilitated for external dependencies?

---

## 4. Concurrency and Parallelism

### 4.1 Race Conditions and State Synchronization

- **P1**: Does the language support multi-threading or parallel execution?  
  *Concurrency introduces complexity in state management.*

- **P2**: Are there robust synchronization primitives (e.g., mutexes, semaphores) to ensure safe concurrent access to shared data?

- **P3**: Can race conditions emerge due to improper synchronization of state updates?

### 4.2 Reentrancy Concerns

- **P4**: How does the language handle reentrancy in concurrent contexts?

- **P5**: Are there built-in protections or best practices to prevent concurrent execution vulnerabilities?

---

## 5. Storage and State Management

### 5.1 Storage Layout and Upgradability

- **ST1**: How does the language manage the storage layout, particularly for complex data structures and upgradable contracts?  
  *Poor storage management can lead to storage collisions and data corruption.*

- **ST2**: Does it follow a consistent and predictable pattern for storage allocation?

- **ST3**: Are there tools or features to assist with safe contract upgrades without risking storage collisions?

### 5.2 Implicit State Changes

- **ST4**: Does the language have implicit state changes that are not obvious from the code?  
  *Hidden state changes can introduce bugs and vulnerabilities.*

- **ST5**: Are developers required to explicitly declare state modifications?

### 5.3 Native Asset Receipt

- **ST6**: Are there scenarios where contracts might implicitly receive the native asset without the developer's intention?  
  *This can lead to unintended asset holding and potential security issues.*

- **ST7**: Does the language provide mechanisms to prevent or alert developers about such scenarios?

---

## 6. Performance and Gas Efficiency

### 6.1 Gas Cost Accuracy

- **G1**: Does the language provide accurate gas cost estimations for operations?  
  *Incorrect gas costs can lead to failed transactions and inefficiencies.*

- **G2**: Are there tools to help optimize code for gas efficiency?

### 6.2 Performance Issues

- **G3**: Are there known performance bottlenecks within the language's execution model?

- **G4**: Does the language produce optimized bytecode or machine code?

### 6.3 Build Output Size

- **G5**: Is the compiled contract size excessively large?  
  *Large contract sizes can exceed platform limits and increase costs.*

- **G6**: Are there optimization techniques to reduce the build output size?

---

## 7. Error Handling and Exception Safety

### 7.1 Exception Management

- **E1**: How does the language handle exceptions and runtime errors?  
  *Consistent error handling is crucial for reliable contract execution.*

- **E2**: Are there constructs for try-catch mechanisms or equivalent?

### 7.2 Error Propagation

- **E3**: Are errors and exceptions properly propagated across contract calls?

- **E4**: Can contracts catch and handle exceptions from external calls safely?

### 7.3 Fail-Safe Defaults

- **E5**: Does the language encourage fail-safe defaults, ensuring that contracts default to secure states in case of errors?

- **E6**: Are there guidelines or patterns for implementing safe error handling?

---

## 8. Documentation and Community Support

### 8.1 Documentation Accuracy

- **D1**: Is there a mismatch between the language documentation and its current state?  
  *Outdated or incorrect documentation can lead to misuse and vulnerabilities.*

- **D2**: Is the documentation comprehensive, covering all language features and edge cases?

### 8.2 Learning Resources

- **D3**: Are there sufficient tutorials, guides, and examples to help developers learn the language effectively?

- **D4**: Does the language have an active community or support channels for developers?

### 8.3 Best Practices and Standards

- **D5**: Are there established best practices, style guides, or standards for writing secure and efficient code in the language?

- **D6**: Does the language documentation highlight common pitfalls and how to avoid them?

---

## 9. Code Readability and Maintainability

### 9.1 Syntax Clarity

- **R1**: Does the language syntax promote clarity and readability?  
  *A language that's hard to read is hard to write securely.*

- **R2**: Are there constructs or features that could lead to obfuscated or confusing code?

### 9.2 Consistency

- **R3**: Does the language enforce or encourage consistent coding styles?

- **R4**: Are there linters or formatters available to maintain code consistency?

### 9.3 Commenting and Documentation

- **R5**: Does the language support inline documentation or annotations?

- **R6**: Are developers encouraged to document code thoroughly, explaining complex logic and decisions?

---

## 10. Dependency Management

### 10.1 Package Management

- **DM1**: Does the language have a standard package manager for handling dependencies?  
  *Proper dependency management is essential for security and maintainability.*

- **DM2**: Are dependency versions locked to prevent unintentional upgrades?

### 10.2 Dependency Verification

- **DM3**: Are there tools to verify the integrity and authenticity of dependencies?  
  *Dependency hijacking is a significant security risk.*

- **DM4**: Can dependencies be audited for security vulnerabilities before inclusion?

### 10.3 Supply Chain Security

- **DM5**: Does the language ecosystem provide mechanisms to protect against supply chain attacks?

- **DM6**: Are there guidelines for securely managing and updating dependencies?

---

# Conclusion

This checklist serves as a comprehensive guide for auditors to evaluate the robustness, security, and developer-friendliness of smart contract languages. By systematically addressing each point, auditors can identify potential vulnerabilities, inefficiencies, and areas for improvement, ultimately contributing to the development of more secure and reliable smart contract platforms.
