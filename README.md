# LangCheck: Smart Contract Language Audit Checklist

> **Pro Tip**: Bookmark this checklist and revisit it regularly to stay updated with best practices in smart contract language auditing.

## How to Use This Checklist

LangCheck is a comprehensive checklist designed for auditors evaluating the security, reliability, and maintainability of smart contract languages. It helps auditors systematically review aspects of a language that can impact the quality and security of the smart contracts developed with it.

This checklist is organized into distinct categories, each addressing a particular aspect of smart contract development. Each item includes explanations of the objectives, potential issues, and references to help auditors understand the importance of each check.

To use the checklist effectively:
1. Review the categories and choose those relevant to your audit focus.
2. Check each item to understand the rationale and context.
3. Proceed through each item systematically to ensure a comprehensive review.

Auditors are encouraged to take notes while progressing through the checklist, as these notes can be valuable for communicating findings to stakeholders and for creating detailed audit reports. LangCheck can also be used iteratively—returning to the checklist during different stages of the audit can help confirm that all issues are addressed.

## Table of Contents
1. [Language Syntax and Semantics](#1-language-syntax-and-semantics)
2. [Compiler and Tooling](#2-compiler-and-tooling)
3. [Security Features and Vulnerabilities](#3-security-features-and-vulnerabilities)
4. [Concurrency and Parallelism](#4-concurrency-and-parallelism)
5. [Storage and State Management](#5-storage-and-state-management)
6. [Performance and Gas Efficiency](#6-performance-and-gas-efficiency)
7. [Error Handling and Exception Safety](#7-error-handling-and-exception-safety)
8. [Documentation and Community Support](#8-documentation-and-community-support)
9. [Code Readability and Maintainability](#9-code-readability-and-maintainability)
10. [Dependency Management](#10-dependency-management)

---

## 1. Language Syntax and Semantics


| Ref Number | Name                         | Objective                                                                                                                                               | Potential Issues                                                                                                                                       | References        |
|------------|------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------|
| LS-001     | Function Selector Management | Ensure that selectors are uniquely and predictably generated, preventing collisions. Arbitrary selectors should not be allowed, and overloaded functions must produce distinct selectors. | <ul><li>Function selector collisions, leading to incorrect function execution</li><li>Proxy selector clashing in upgradeable contracts</li><li>Misrouting of calls due to poor handling of overloaded functions</li><li>Backdoor creation via custom selectors</li></ul> | <ul><li>[Example issue](https://blog.openzeppelin.com/stylus-rust-sdk-audit#custom-selectors-could-facilitate-proxy-selector-clashing-attack)</li></ul> |
| LS-002     | Strong, Static Type System   | Ensure the language has a strong, static type system to catch type-related issues at compile-time, reducing runtime errors and vulnerabilities.          | <ul><li>Runtime errors due to type mismatches</li><li>Type-related vulnerabilities</li><li>Unexpected behavior in deployed contracts</li></ul>          | None              |
| LS-003     | Type-Related Vulnerability Safeguards | Ensure the language provides safeguards against common type-related vulnerabilities, such as type confusion and unsafe type casting, to improve security and reliability. | <ul><li>Type confusion vulnerabilities</li><li>Exploitation via unsafe type casting</li><li>Reduced contract reliability due to type issues</li></ul> | None |
| LS-004     | Event Emissions and Logging  | Ensure the language provides efficient and standardized mechanisms for event emissions and logging to enhance transparency and facilitate off-chain monitoring. | <ul><li>Inefficient or non-standard event logging</li><li>Difficulties in off-chain monitoring and indexing</li><li>Reduced transparency of contract activities</li></ul> | None              |
| LS-005     | Misleading or Undefined Keywords | Ensure the language does not allow misleading or undefined keywords that can deceive reviewers and introduce hard-to-detect vulnerabilities.            | <ul><li>Deception of code reviewers</li><li>Hard-to-detect vulnerabilities</li><li>Misunderstandings of code intent</li><li>Difficulty spotting vulnerabilities during code review</li></ul> | None              |
| LS-006     | Explicit State Mutability Declarations | Ensure the language requires explicit declaration of state mutability to prevent unexpected behaviors and potential vulnerabilities due to implicit state changes. | <ul><li>Unexpected behaviors from implicit state mutability</li><li>Vulnerabilities due to unintended state changes</li><li>Challenges in maintaining contract integrity</li><li>Unauthorized state modifications</li></ul> | None |

---

## 2. Compiler and Tooling


| Ref Number | Name                         | Objective                                                                                                                                               | Potential Issues                                                                                                                                       | References        |
|------------|------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------|
| CT-001     | Compiler Error Clarity       | Ensure the compilation process is clear, and the compiler provides sufficient, meaningful error information to aid in quick identification and resolution of issues. | <ul><li>Delayed development due to cryptic errors</li><li>Undetected vulnerabilities</li><li>Difficulty in fixing issues</li></ul>                      | None              |
| CT-002     | Compiler Optimization Safety | Ensure compiler optimizations do not introduce unexpected behavior or vulnerabilities, maintaining contract security while improving performance.        | <ul><li>Unexpected behavior from optimizations</li><li>Vulnerabilities introduced by optimizations</li><li>Compromised contract security</li></ul>     | None              |
| CT-003     | Deterministic and Verifiable Builds | Ensure the build output is deterministic and verifiable, so the same code always produces the same bytecode, aiding in verification and preventing supply chain attacks. | <ul><li>Discrepancies between audited code and deployed contract</li><li>Supply chain attack vulnerabilities</li><li>Undermined trust in security</li></ul> | None |

---

## 3. Security Features and Vulnerabilities


| Ref Number | Name                               | Objective                                                                                                                                               | Potential Issues                                                                                                                                       | References        |
|------------|------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------|
| SV-001     | Built-in Reentrancy Protection     | Ensure the language provides built-in reentrancy protection mechanisms to prevent reentrancy attacks and enhance contract security.                      | <ul><li>Reentrancy attacks causing fund loss</li><li>Dependence on developer awareness</li><li>Common security pitfalls</li></ul>                       | None              |
| SV-002     | Integer Overflow/Underflow Protection | Ensure the language provides built-in mechanisms to prevent integer overflow and underflow vulnerabilities, maintaining contract integrity and security. | <ul><li>Financial exploits via integer overflow/underflow</li><li>Contract integrity compromise</li><li>Loss of funds</li></ul>                        | None              |
| SV-003     | Secure Random Number Generation    | Ensure the language offers secure random number generation primitives to prevent exploits due to predictable or manipulable randomness.                  | <ul><li>Exploits from predictable randomness</li><li>Manipulation of random-dependent logic</li><li>Unfair execution</li></ul>                          | None              |
| SV-004     | Array Bounds Checking Enforcement  | Ensure the language enforces proper array bounds checking to prevent buffer overflow vulnerabilities and unauthorized memory access.                    | <ul><li>Buffer overflow vulnerabilities</li><li>Unauthorized memory access</li><li>Security breaches</li></ul>                                         | None              |

---

## 4. Concurrency and Parallelism


| Ref Number | Name                               | Objective                                                                                                                                               | Potential Issues                                                                                                                                       | References        |
|------------|------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------|
| CP-001     | Concurrent State Update Management | Ensure the language provides primitives for managing concurrent state updates to prevent race conditions and maintain state consistency.                 | <ul><li>Race conditions causing inconsistent state</li><li>Unexpected behaviors</li><li>State manipulation by attackers</li></ul>                       | None              |
| CP-002     | Atomic Transactions and Error Handling | Ensure the language supports atomic transactions and rollback mechanisms to maintain state consistency in case of errors.                                | <ul><li>Inconsistent state from partial execution</li><li>Locked funds or incomplete operations</li><li>Vulnerability during errors</li></ul>          | None              |
| CP-003     | Explicit Native Asset Handling     | Ensure contracts cannot receive native assets without explicit handling to prevent unintended behaviors and vulnerabilities.                            | <ul><li>Unintended receipt of native assets</li><li>Vulnerabilities from unanticipated transfers</li><li>Unpredictable behavior</li></ul>              | None              |

---

## 5. Storage and State Management

| Ref Number | Name                               | Objective                                                                                                                                               | Potential Issues                                                                                                                                       | References        |
|------------|------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------|
| SM-001     | Storage Layout Management for Upgradability | Ensure the language manages storage layout consistently and predictably, especially for upgradable contracts, to prevent storage collisions and maintain state integrity. | <ul><li>Storage collisions corrupting state</li><li>Difficult-to-detect vulnerabilities</li><li>Compromised state integrity during upgrades</li></ul> | None              |
| SM-002     | Native Upgradeable Contract Support | Ensure the language provides native support for upgradeable contract patterns to standardize and secure the upgrade process.                             | <ul><li>Complex upgrade processes</li><li>Security vulnerabilities in upgrades</li><li>State inconsistencies during upgrades</li></ul>                 | <ul><li>[ink! Upgradeable Contracts](https://use.ink/basics/upgradeable-contracts#replacing-contract-code-with-set_code_hash)</li></ul> |
| SM-003     | Explicit Mutability of State Variables | Ensure state variables are explicitly marked as mutable or immutable to prevent unintended modifications and enhance code readability.                   | <ul><li>Accidental state changes</li><li>Vulnerabilities from unintended modifications</li><li>Inconsistent behavior</li></ul>                         | None              |
| SM-004     | Efficient State Pruning and Archiving | Ensure the language provides mechanisms for efficient state pruning or archiving to maintain contract performance and manage storage costs.              | <ul><li>Performance degradation from accumulated state</li><li>High storage costs</li><li>Inefficient state management</li></ul>                       | None              |

---

## 6. Performance and Gas Efficiency

| Ref Number | Name                         | Objective                                                                                                                                               | Potential Issues                                                                                                                                       | References        |
|------------|------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------|
| PE-001     | Correct Gas Charging         | Ensure gas is charged correctly to prevent denial-of-service scenarios and unnecessary costs, maintaining contract reliability and network stability.   | <ul><li>Denial-of-service attacks</li><li>Unnecessary user costs</li><li>Exploitation of gas accounting</li><li>Network instability</li></ul>          | None              |
| PE-002     | Contract Size Optimization   | Ensure the build output is optimized for size to reduce deployment costs and meet platform size constraints.                                             | <ul><li>High deployment costs</li><li>Exceeding size limits</li><li>Deployment failures</li><li>Need for refactoring</li></ul>                         | None              |

---

## 7. Error Handling and Exception Safety

| Ref Number | Name                         | Objective                                                                                                                                               | Potential Issues                                                                                                                                       | References        |
|------------|------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------|
| EH-001     | Error Propagation and Handling | Ensure errors are properly propagated and handled within contracts and during external calls to maintain predictable execution and prevent vulnerabilities. | <ul><li>Unpredictable execution</li><li>Locked funds</li><li>Vulnerabilities from unhandled errors</li><li>Failure recovery issues</li></ul>           | None              |
| EH-002     | Adequate Debugging Tools     | Ensure the language provides adequate debugging tools to assist developers in identifying and fixing issues during development and auditing.             | <ul><li>Difficulty fixing issues</li><li>Missed vulnerabilities</li><li>Increased development time</li><li>Reduced code quality</li></ul>              | None              |

---

## 8. Documentation and Community Support

| Ref Number | Name                         | Objective                                                                                                                                               | Potential Issues                                                                                                                                       | References        |
|------------|------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------|
| DC-001     | Up-to-date and Consistent Documentation | Ensure the language documentation is up to date and consistent with the current state of the language to provide accurate information to developers and auditors. | <ul><li>Misunderstandings due to outdated docs</li><li>Incorrect assumptions</li><li>Vulnerabilities introduced</li><li>Inefficient code</li></ul>     | None              |
| DC-002     | Active Community and Support Channels | Ensure the language has an active community and available support channels to assist developers and contribute to language improvements.                 | <ul><li>Lack of support</li><li>Unaddressed security issues</li><li>Slower evolution</li><li>Developers lacking resources</li></ul>                    | None              |

---

## 9. Code Readability and Maintainability


| Ref Number | Name                         | Objective                                                                                                                                               | Potential Issues                                                                                                                                       | References        |
|------------|------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------|
| CM-001     | Syntax Readability and Clarity | Ensure the language syntax is designed for readability and clarity to help developers write secure code and reduce mistakes.                            | <ul><li>Coding mistakes</li><li>Difficulty understanding code</li><li>Misunderstandings</li><li>Increased errors</li></ul>                             | None              |
| CM-002     | Encouragement of Proper Commenting Practices | Ensure the language encourages or enforces proper commenting practices to aid future maintainers and reduce bugs during updates.                         | <ul><li>Misunderstandings during maintenance</li><li>Introduction of bugs</li><li>Loss of code intent information</li><li>Difficulty updating code</li></ul> | None              |

---

## 10. Dependency Management


| Ref Number | Name                         | Objective                                                                                                                                               | Potential Issues                                                                                                                                       | References        |
|------------|------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------|
| DM-001     | Dependency Auditing and Verification | Ensure there are mechanisms to audit or verify dependencies to maintain overall contract security.                                                      | <ul><li>Vulnerabilities from dependencies</li><li>Risks from third-party code</li><li>Increased attack surface</li><li>Compromised security</li></ul>  | None              |
| DM-002     | Protection Against Dependency Hijacking | Ensure the language ecosystem provides protection against dependency hijacking to prevent malicious code inclusion.                                      | <ul><li>Malicious code introduction</li><li>Backdoors in contracts</li><li>Compromised security</li><li>Trust issues</li></ul>                         | None              |

---

## 🌟 Community Contributions Welcome! 🌟

We encourage the community to contribute to LangCheck by suggesting additional checklist items, best practices, or improvements. Your input can help make this checklist even more comprehensive and useful for smart contract language audits. Feel free to submit your suggestions or contribute to the ongoing discussion to help improve smart contract security for everyone.

**[Contribute to LangCheck](#)**
