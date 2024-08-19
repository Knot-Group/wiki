# Mediated Computation

Mediated computation is used when the input data originates with multiple parties and must be kept private from all other parties. A variety of technologies can be used to achieve private mediated computation, and these can also often be combined together or with ZKPs, depending on the requirements of the application.

![Mediated computation](../../images/mediated-computation.png)

## Homomorphic Encryption

Homomorphic encryption is a form of encryption that allows computations to be performed on encrypted data without first having to decrypt it.

## Secure Multi-Party Computation (MPC)

Secure MPC protocols typically use [secret sharing](https://en.wikipedia.org/wiki/Secret_sharing) at their core, sometimes combined with [oblivious transfer](https://en.wikipedia.org/wiki/Oblivious_transfer). At a high level, the input data is split up into secret shares which are distributed to all parties. Next, a circuit is evaluated in MPC using operation-specific techniques to compute each gate over the secret-shared values. When the circuit evaluation is complete, each party holds a secret share of the circuit’s output, and these can be used to get the output of the computation.

There are a number of generic protocols for MPC, as well as custom protocols for specific use-cases of MPC, such as Private Set Intersection and Threshold Signatures.

Fundamental protocols [[source](https://securecomputation.org/docs/ch3-fundamentalprotocols.pdf)]:

- Yao's Garbled Circuits Protocol
- Goldreich-Micali-Wigderson (GMW) Protocol
- BGW protocol
- MPC From Preprocessed Multiplication Triples
- Constant-Round Multi-Party Computation: BMR
- Information-Theoretic Garbled Circuits
- Oblivious Transfer

**Threshold signatures**

The idea in a threshold scheme is to divide a secret $S$ into $n$ pieces of data $S_1,...,S_n$ in such a way that:

1. Knowledge of any $k$ or more shares $S_i$ makes $S$ computable.
2. Knowledge of any $k - 1$ or fewer shares $S_i$ leaves $S$ completely undetermined.

[[source](https://en.wikipedia.org/wiki/Shamir%27s_secret_sharing)]

Threshold schemes are the foundation of threshold key cryptography. Threshold cryptosystems protect information by encrypting and distributing secrets amongst a cluster of independent computers that qualify as fault-tolerant. The fault-tolerance of a system simply means the system’s ability to continue operating despite failures or malfunctions.

[[source](https://blog.pantherprotocol.io/threshold-cryptography-an-overview/)]

Threshold schemes become threshold *cryptosystems* when combined with a decryption or signature protocol.

Consider a scenario in which $N$ parties each hold shards of a key. The key was used to encrypt some information (such as the location of a secret treasure). These $N$ parties agree to cooperate in decrypting this information only if a player can prove they are located near the secret treasure.

## Trusted Execution Environments

A trusted execution environment (TEE) is an area on the main processor of a device that is separated from the system's main operating system (OS). It ensures data is stored, processed and protected in a secure environment. TEEs provide protection for anything connected, such as a trusted application (TA), by enabling an isolated, cryptographic electronic structure and end-to-end security. This includes the execution of authenticated code, confidentiality, authenticity, privacy, system integrity and data access rights.

[[source](https://www.techtarget.com/searchitoperations/definition/trusted-execution-environment-TEE)]

![](https://github.com/Knot-Group/trust-infrastructure-wiki/blob/main/sgx_graphic.png?raw=true)

While there is a spectrum of functionality across TEEs, the most general case is something like the above. The trusted execution environment is physically isolated from the rest of the hardware. OS and all interfaces into shared RAM, disk etcetera ensure the information is first encrypted, either using hardware keys or some provisioned key that only the trusted environment can access.

This means, in practice, a TEE allows for fully confidential, tamper-proof compute by an untrusted server (e.g. cloud provider). This unlocks a different method for “shared private state” by allowing arbitrary functions to be computed over encrypted data, but in a much more centralised fashion than in MPC. 

Combining TEEs with MPC can be a powerful combination when stronger decentralisation guarantees are a requirement and may ameliorate some of the central party risks involved.

In theory, the provider will not be able to see the data or know what the code is computing. However, in practice, physical access to the device does offer unique attack vectors which are less present in the purely cryptographic schemes. Furthermore, the semiconductor industry is tightly controlled. Relying on a few chip manufacturers to securitise the world’s information (even under the presence of auditors) comes with unique risks. Furthermore (and for that reason), in the context of crypto TEEs may be “memetically suboptimal”, as [suggested](https://ethresear.ch/t/2fa-zk-rollups-using-sgx/14462) by Justin Drake. We also recommend this counterview from [Andrew Miller](https://www.youtube.com/watch?v=4qgPd5kcwBs).

Already TEEs are widely available in mobile phones, but generally limited to supporting biometric ID — for example Apple’s [SecureEnclave](https://developer.apple.com/documentation/cryptokit/secureenclave). Cloud computing platforms are beginning to offer secure, isolated compute environments to their customers.

Overall, trusted execution environments are an appealing option to faciliate shared private state. This is especially true when considering the high cost and caveats of alternative schemes.

## **References**

- [The Secret to Understanding MPC (Bain Capital Crypto Whiteboard Series with David Wong)](https://www.youtube.com/watch?v=L_ND1YPmI5E)
- [Pragmatic MPC](https://securecomputation.org/)