# Language Design and Implementation

## Description

The purpose of the category focuses on ensuring that the core features of the smart contract language promote secure, predictable, and maintainable code. By enforcing explicit declarations for mutability, visibility, and asset handling, and ensuring clear syntax and function management, this category helps prevent vulnerabilities caused by ambiguity or poor design choices. It also encourages the use of standardized mechanisms for logging and error handling, ensuring that contracts remain transparent and auditable throughout their lifecycle.

This section helps auditors evaluate the language's ability to facilitate secure development and provide a solid foundation for both developers and reviewers.

| Ref Number | Name                                       | Objective                                                                                                                                               | Potential Issues                                                                                                                                       |
|------------|--------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| LI-001    | Explicit State Mutability and Visibility Declarations     | Ensure the language requires explicit declaration of state mutability and visibility of functions and variables to prevent unexpected behaviors and potential vulnerabilities. | <ul><li>Unexpected behaviors from implicit state mutability</li><li>Vulnerabilities due to unintended state changes</li><li>Challenges in maintaining contract integrity</li><li>Unauthorized state modifications</li></ul> |
| LI-002    | Function Selector Management               | Ensure that selectors are uniquely and predictably generated, preventing collisions. Arbitrary selectors should not be allowed, and overloaded functions must produce distinct selectors. | <ul><li>Function selector collisions, leading to incorrect function execution</li><li>Proxy selector clashing in upgradeable contracts</li><li>Misrouting of calls due to poor handling of overloaded functions</li><li>Backdoor creation via custom selectors</li></ul> |
| LI-003    | Event Emissions and Logging                | Ensure the language provides efficient and standardized mechanisms for event emissions and logging to enhance transparency and facilitate off-chain monitoring. | <ul><li>Inefficient or non-standard event logging</li><li>Difficulties in off-chain monitoring and indexing</li><li>Reduced transparency of contract activities</li></ul> |
| LI-004    | Misleading or Undefined Keywords           | Ensure the language does not allow misleading or undefined keywords that can deceive reviewers and introduce hard-to-detect vulnerabilities.            | <ul><li>Deception of code reviewers</li><li>Hard-to-detect vulnerabilities</li><li>Misunderstandings of code intent</li><li>Difficulty spotting vulnerabilities during code review</li></ul> |
| LI-005    | Compiler Error Clarity                     | Ensure the compilation process is clear, and the compiler provides sufficient, meaningful error information to aid in quick identification and resolution of issues. | <ul><li>Delayed development due to cryptic errors</li><li>Undetected vulnerabilities</li><li>Difficulty in fixing issues</li></ul>                      |
| LI-006    | Deterministic and Verifiable Builds        | Ensure the build output is deterministic and verifiable, so the same code always produces the same bytecode, aiding in verification and preventing supply chain attacks. | <ul><li>Discrepancies between audited code and deployed contract</li><li>Supply chain attack vulnerabilities</li><li>Undermined trust in security</li></ul> |
| LI-007    | Error Propagation and Handling             | Ensure errors are properly propagated and handled within contracts and during external calls to maintain predictable execution and prevent vulnerabilities. | <ul><li>Unpredictable execution</li><li>Locked funds</li><li>Vulnerabilities from unhandled errors</li><li>Failure recovery issues</li></ul>           |
| LI-008    | Syntax Readability and Clarity             | Ensure the language syntax is designed for readability and clarity to help developers write secure code and reduce mistakes.                            | <ul><li>Coding mistakes</li><li>Difficulty understanding code</li><li>Misunderstandings</li><li>Increased errors</li></ul>                             |
| LI-009    | Explicit Native Asset Handling             | Ensure contracts cannot receive native assets without explicit handling to prevent unintended behaviors and vulnerabilities.                            | <ul><li>Unintended receipt of native assets</li><li>Vulnerabilities from unanticipated transfers</li><li>Unpredictable behavior</li></ul>              |

---

## References

For more information, see also:

- **[Ethereum Smart Contract Best Practices - Visibility](https://consensys.github.io/smart-contract-best-practices/development-recommendations/solidity-specific/visibility/)**
- **[Introduction of `view` and `pure` keywords in Solidity](https://github.com/ethereum/solidity/issues/992)**
- **[On the parity wallet multisig hack](https://blog.openzeppelin.com/on-the-parity-wallet-multisig-hack-405a8c12e8f7)**
- **[Lack of selector collision check - Stylus SDK audit](https://blog.openzeppelin.com/stylus-rust-sdk-audit#lack-of-selector-collision-check-in-external-macro)**
- **[Custom selector issue - Stylus SDK audit](https://blog.openzeppelin.com/stylus-rust-sdk-audit#custom-selectors-could-facilitate-proxy-selector-clashing-attack)**
- **[Custom selector issue - ink! audit](https://blog.openzeppelin.com/security-review-ink-cargo-contract#custom-selectors-could-facilitate-proxy-selector-clashing-attack)**
- **[Trojan Source: Invisible Vulnerabilities](https://trojansource.codes/)**
- **[CVE-2021-42574: Bidirectional Override Vulnerability](https://nvd.nist.gov/vuln/detail/CVE-2021-42574)**
- **[Hiding in Plain Sight](https://samczsun.com/hiding-in-plain-sight/)**
- **[Audit Finding: Non-determinism in ink! contract builds](https://blog.openzeppelin.com/security-review-ink-cargo-contract#non-determinism-in-ink-contract-builds)**
