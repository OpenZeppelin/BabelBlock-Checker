# LangCheck: Smart Contract Language Audit Checklist

## How to Use This Checklist

LangCheck is a comprehensive checklist designed for auditors evaluating the security, reliability, and maintainability of smart contract languages. It helps auditors systematically review aspects of a language that can impact the quality and security of the smart contracts developed with it.

This checklist is organized into distinct categories, each addressing a particular aspect of smart contract development. Each item includes an explanation, hidden behind a toggle for ease of reading, explaining why the check is important and the risks or security concerns it addresses. By following the checklist, auditors can ensure that they don't overlook any critical areas and can gain a thorough understanding of the strengths and weaknesses of the language under review.

To use the checklist effectively:
1. Review the categories and choose those relevant to your audit focus. Multiple aspects may need to be considered simultaneously, as some language features can impact different areas of security, performance, and reliability.
2. Check each item to understand the rationale and context. The explanations provide deeper insights into why a particular aspect is important, helping assess the risks associated with the language.
3. Proceed through each item systematically to ensure a comprehensive review. A systematic approach helps ensure that no critical aspects are missed and that all potential vulnerabilities are identified.

Auditors are encouraged to take notes while progressing through the checklist, as these notes can be valuable for communicating findings to stakeholders and for creating detailed audit reports. LangCheck can also be used iteratively—returning to the checklist during different stages of the audit can help confirm that all issues are addressed.

>[!NOTE] 
> Click the toggle of each item to see the explanation behind.

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

## 1. Language Syntax and Semantics

<details>
<summary><strong>Does the language allow developers to define arbitrary custom selectors for functions?</strong></summary>
<i>Custom selectors can lead to collisions, especially in proxy patterns. Ensuring proper checks helps avoid introducing backdoors or making malicious code harder to detect. This is especially important in the context of contract upgrades and dispatchers that rely on unique selectors to route function calls correctly.</i>
</details>

<details>
<summary><strong>Does the language allow misleading or undefined keywords?</strong></summary>
<i>Allowing undefined keywords or misleading notation can be exploited to deceive reviewers and introduce vulnerabilities that are difficult to detect. Such features can lead to misunderstandings of the code's intent and make it harder to spot potential vulnerabilities during code review.</i>
</details>

<details>
<summary><strong>Does the language default to state mutability when not explicitly declared?</strong></summary>
<i>Implicit state mutability can lead to unexpected behaviors and potential vulnerabilities, especially in environments where state consistency is crucial. Explicitly declaring state mutability makes it clear when state changes are occurring, which is essential for maintaining contract integrity and preventing unauthorized modifications.</i>
</details>

## 2. Compiler and Tooling

<details>
<summary><strong>Is the compilation process clear, and do errors provide sufficient information?</strong></summary>
<i>Clear compiler errors are crucial for identifying issues quickly. Cryptic error messages can delay development and increase the risk of undetected vulnerabilities. A good compiler should provide meaningful feedback that helps developers understand what went wrong and how to fix it.</i>
</details>

<details>
<summary><strong>Is the build output deterministic and verifiable?</strong></summary>
<i>Deterministic builds ensure that the same code produces the same bytecode every time, which is critical for verifying contract deployments and preventing supply chain attacks. Non-deterministic builds can lead to discrepancies between the audited code and the deployed contract, undermining trust in the contract's security.</i>
</details>

## 3. Security Features and Vulnerabilities

<details>
<summary><strong>Does the language provide built-in reentrancy protection?</strong></summary>
<i>Reentrancy attacks can drain contracts of funds. Built-in reentrancy protection helps prevent these attacks, reducing reliance on developer awareness alone. Languages that provide primitives for managing reentrancy can help developers avoid common pitfalls and write more secure code by default.</i>
</details>

<details>
<summary><strong>Are there built-in mechanisms to prevent overflow and underflow vulnerabilities?</strong></summary>
<i>Ensuring integer safety at runtime or compile-time is critical to prevent financial exploits and maintain contract integrity. Overflow and underflow vulnerabilities have led to major exploits in the past, and having built-in safeguards is essential for protecting smart contract funds.</i>
</details>

## 4. Concurrency and Parallelism

<details>
<summary><strong>Does the language provide primitives for managing concurrent state updates?</strong></summary>
<i>In parallel execution environments, race conditions can lead to inconsistent state. Proper synchronization primitives are necessary to maintain consistency. Race conditions can lead to unexpected behaviors, allowing attackers to manipulate the contract state to their advantage.</i>
</details>

<details>
<summary><strong>Can contracts receive native assets without explicit handling?</strong></summary>
<i>Implicitly accepting native assets can lead to unintended behavior or vulnerabilities, especially if the developer does not anticipate such transfers. Explicit handling of native assets ensures that the contract behaves predictably when receiving funds and that appropriate security checks are in place.</i>
</details>

## 5. Storage and State Management

<details>
<summary><strong>How does the language manage storage layout, particularly for upgradable contracts?</strong></summary>
<i>Consistent and predictable storage layouts help prevent collisions and ensure state integrity, especially for contracts that are upgraded over time. Storage collisions can corrupt the contract state, leading to vulnerabilities that are difficult to detect and exploit.</i>
</details>

<details>
<summary><strong>Are state variables explicitly marked as mutable or immutable?</strong></summary>
<i>Explicitly marking state variables improves code readability and reduces the likelihood of accidental state changes. Immutable state variables help prevent unintended modifications, which can lead to vulnerabilities or inconsistent contract behavior.</i>
</details>

## 6. Performance and Gas Efficiency

<details>
<summary><strong>Are there scenarios where gas is charged incorrectly (overpriced or underpriced)?</strong></summary>
<i>Inefficient gas handling can lead to denial-of-service scenarios or unnecessary costs for users. Auditing gas efficiency is critical for contract reliability. Ensuring gas is charged correctly helps maintain network stability and prevents abusive behaviors that could exploit inefficient gas accounting.</i>
</details>

<details>
<summary><strong>Does the build output result in a large contract size?</strong></summary>
<i>Large contract sizes may lead to higher deployment costs and exceed size limits imposed by blockchain platforms, necessitating optimizations. Optimizing contract size is crucial for reducing deployment costs and ensuring that the contract can be deployed within the constraints of the target platform.</i>
</details>

## 7. Error Handling and Exception Safety

<details>
<summary><strong>Are errors properly propagated and handled, both within contracts and during external calls?</strong></summary>
<i>Proper error handling ensures that contract execution remains predictable and that unexpected conditions do not lead to vulnerabilities or locked funds. Ensuring errors are properly propagated allows developers to write contracts that handle failures gracefully, reducing the risk of funds being permanently locked due to unforeseen issues.</i>
</details>

<details>
<summary><strong>Does the language provide adequate debugging tools?</strong></summary>
<i>Debugging tools are essential for identifying and fixing issues, especially during the development and auditing phases. A lack of proper debugging tools can make it difficult for developers to understand how their contracts behave, leading to missed vulnerabilities and errors.</i>
</details>

## 8. Documentation and Community Support

<details>
<summary><strong>Is the language documentation up to date and consistent with the current state of the language?</strong></summary>
<i>Up-to-date documentation ensures developers and auditors have the correct information, reducing misunderstandings and mistakes. Inconsistent or outdated documentation can lead to incorrect assumptions about the language's behavior, resulting in vulnerabilities or inefficient code.</i>
</details>

<details>
<summary><strong>Does the language have an active community and available support channels?</strong></summary>
<i>A strong community can provide timely support, identify potential issues, and contribute to language improvements. Active community engagement helps ensure that the language evolves to address security concerns and that developers have access to the resources they need.</i>
</details>

## 9. Code Readability and Maintainability

<details>
<summary><strong>Is the language syntax designed for readability and clarity?</strong></summary>
<i>A language that promotes readability helps developers write secure code and reduces the likelihood of mistakes that lead to vulnerabilities. Readable syntax makes it easier for both developers and auditors to understand the code's intent, leading to fewer misunderstandings and a lower risk of errors.</i>
</details>

<details>
<summary><strong>Does the language encourage or enforce proper commenting practices?</strong></summary>
<i>Proper comments and documentation help future maintainers understand the code, reducing the risk of introducing bugs during updates. Enforcing good commenting practices ensures that important information about the code's behavior, limitations, and intent is preserved for future developers.</i>
</details>

## 10. Dependency Management

<details>
<summary><strong>Are there mechanisms to audit or verify dependencies?</strong></summary>
<i>Dependencies can introduce vulnerabilities if not properly audited. Ensuring all dependencies are secure is crucial for overall contract security. Proper auditing mechanisms help identify and mitigate risks associated with third-party code, reducing the attack surface of the contract.</i>
</details>

<details>
<summary><strong>Does the language ecosystem provide protection against dependency hijacking?</strong></summary>
<i>Dependency hijacking can lead to malicious code being introduced into contracts. Proper verification mechanisms help mitigate this risk. Protecting against dependency hijacking ensures that only trusted code is included in the contract, preventing potential backdoors and malicious behaviors.</i>
</details>

---

>[!tip]
>**Pro Tip**: Bookmark this checklist and revisit it regularly to stay updated with best practices in smart contract language auditing.

## 🌟 Community Contributions Welcome! 🌟

We encourage the community to contribute to LangCheck by suggesting additional checklist items, best practices, or improvements. Your input can help make this checklist even more comprehensive and useful for smart contract language audits. Feel free to submit your suggestions or contribute to the ongoing discussion to help improve smart contract security for everyone.

**[Contribute to LangCheck](#)**
