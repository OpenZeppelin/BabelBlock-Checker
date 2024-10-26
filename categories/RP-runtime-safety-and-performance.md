# Runtime Safety and Performance

## Description

The **Runtime Safety and Performance** category focuses on the operational aspects of smart contracts during execution. It ensures that the language and its compiler generate efficient and secure code that performs reliably on the blockchain platform. Key considerations include correct gas charging to prevent denial-of-service attacks and unnecessary costs, optimization of contract size to meet platform constraints, and efficient memory management to avoid resource exhaustion or leaks. Additionally, this category emphasizes the importance of safe compiler optimizations that do not introduce unexpected behaviors or vulnerabilities.

This section helps auditors assess the language's ability to produce performant and safe contracts, ensuring that they operate reliably and efficiently in the blockchain environment.

---

| Ref Number | Name                                       | Objective                                                                                                                                               | Potential Issues                                                                                                                                       |
|------------|--------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| RP-001     | Correct Gas Charging                       | Ensure gas is charged correctly to prevent denial-of-service scenarios and unnecessary costs, maintaining contract reliability and network stability. Verify that storage opcodes are not mispriced and validate that it is not free to store values under any circumstances.  | <ul><li>Denial-of-service attacks</li><li>Unnecessary user costs</li><li>Exploitation of gas accounting</li><li>Network instability</li></ul> |
| RP-002     | Contract Size Optimization                 | Ensure the build output is optimized for size to reduce deployment costs and meet platform size constraints.                                             | <ul><li>High deployment costs</li><li>Exceeding size limits</li><li>Deployment failures</li><li>Need for refactoring</li></ul> |
| RP-003     | Efficient Memory Allocation and Management | Ensure the language provides secure and efficient memory allocation mechanisms, managing memory usage effectively to optimize performance and prevent resource exhaustion or leaks. | <ul><li>Memory leaks leading to increased gas costs</li><li>Resource exhaustion causing contract failures</li><li>Vulnerabilities from improper memory handling</li><li>Inefficient memory usage impacting performance</li></ul> |
| RP-004     | Compiler Optimization Safety               | Ensure compiler optimizations do not introduce unexpected behavior or vulnerabilities, maintaining contract security while improving performance.        | <ul><li>Unexpected behavior from optimizations</li><li>Vulnerabilities introduced by optimizations</li><li>Compromised contract security</li></ul> |

---

## References

For more information, see also:

- **[Gas Gauge: A Security Analysis Tool for Smart Contract Out-of-Gas Vulnerabilities](https://ar5iv.labs.arxiv.org/html/2112.14771v1)**
- **[Improve the throughput of wasm contracts on parachains](https://github.com/paritytech/substrate/issues/9354)**
- **[FullInliner Non-Expression-Split Argument Evaluation Order Bug](https://soliditylang.org/blog/2023/07/19/full-inliner-non-expression-split-argument-evaluation-order-bug/)**
- **[There Ain’t No Such Thing as a Free Custom Memory Allocator](https://ar5iv.labs.arxiv.org/html/2206.11728)**
