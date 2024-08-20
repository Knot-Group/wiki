# Platforms and Products

Platforms or products offer out of the box solutions and typically come with various built-in constraints about how and where they are used.

## Programming languages, compilers, and VMs

### FHE
| Name | Summary | Limitations | Links |
| ---- | ------- | ----------- | ----- |
| Concrete  | TFHE Python compiler to convert Python programs into equivalent FHE programs | | [Concrete by Zama](https://docs.zama.ai/concrete) |
| Concrete ML  | Privacy-preserving machine learning | | [Concrete ML by Zama](https://docs.zama.ai/concrete-ml) |
| fhEVM  | develop confidential smart contracts in Solidity | | [fhEVM by Zama](https://docs.zama.ai/fhevm) |
| Sunscreen  | Compiler for FHE | | [Sunscreen](https://github.com/Sunscreen-tech/Sunscreen) |
| TFHE-rs  | Rust implementation of FHE over the Torus | for cryptographers & researchers | [TFHE-rs by Zama](https://docs.zama.ai/tfhe-rs) |

### MPC

| Name | Summary | Limitations | Links |
| ---- | ------- | ----------- | ----- |
| circom to arithmetic circuit compilers  | Libraries for compiling circom circuits to arithmetic circuits | | [circom-2-arithc](https://github.com/namnc/circom-2-arithc), [circom-2-arithc-ts](https://github.com/voltrevo/circom-2-arithc-ts) |
| mpz  | Multi-party computation libraries written in Rust | | [mpz by PSE](https://github.com/privacy-scaling-explorations/mpz) |

### ZK
| Name | Summary | Limitations | Links |
| ---- | ------- | ----------- | ----- |
| General-purpose zkVM based on RISC-V | generate ZK proofs from Rust code | performance cost for complex computations | [RISC Zero zkVM](https://dev.risczero.com/api), [Succinct SP1](https://docs.succinct.xyz/) |
| Circom | circuit compiler | | [Circom](https://docs.circom.io/) |
| Noir | domain-specific language for SNARK proving systems | | [Noir](https://noir-lang.org/) |



## Data Provenance

### Web Data Provenance
| Name | Summary | Limitations | Links |
| ---- | ------- | ----------- | ----- |
| Web Proof Services | generate proofs over TLS connections | | [Pluto](https://pluto.xyz/), [Reclaim Protocol](https://www.reclaimprotocol.org/), [zkPass](https://www.zkpass.org/) |

### Blockchain Data Provenance
| Name | Summary | Limitations | Links |
| ---- | ------- | ----------- | ----- |
| Herodotus | Prove storage of data at block hash | The verifier (on-chain or off-chain) must have access to an archive of block header hashes from the source chain. | [Link](https://herodotus.dev/) |


## Identity
| Name | Summary | Limitations | Links |
| ---- | ------- | ----------- | ----- |
| OpenPassport | an identity wallet based on a government-issued ID such as your passport | | [Link](https://github.com/zk-passport/proof-of-passport) |
| zuPass | software for storing and managing your cryptographic data | | [Link](https://github.com/proofcarryingdata/zupass) |
| Rarime | a MetaMask Snap that safely holds any of your credentials and allows you to prove your identity without revealing any personal data. | | [Link](https://github.com/rarimo/rarime) |