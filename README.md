# Bitcoin Wallet

**DO NOT USE! ONLY FOR TESTING PURPOSES**

This project contains Python code to generate Bitcoin wallets, including both private/public keys and addresses, using hierarchical deterministic (HD) key derivation techniques. The project features a Python-based approach using Jupyter Notebook to interact with wallet management functionalities.

The solution consists of the following components:

- **Bitcoin-Wallet.ipynb**: Implements the core operations for wallet generation, key derivation, and address management.
- **english.txt**: Provides a word list for BIP-39 mnemonic generation.

The intended audience for this README is experienced developers who are familiar with cryptographic concepts and hierarchical key derivation (such as BIP-32, BIP-39). The code relies on Python libraries for cryptographic functions and mnemonic generation.

---

## Key Features
- **Mnemonic Phrase Generation**: Uses a BIP-39-compatible word list to convert entropy into a human-readable mnemonic phrase.
- **Master and Child Key Derivation**: Utilizes HMAC-SHA512 to derive a master key and chain code for hierarchical deterministic key generation.
- **Bitcoin Address Management**: Allows for the generation of Bitcoin addresses from derived keys.
- **Jupyter Notebook Integration**: Provides an interactive environment for generating and managing wallets.

---

## Code Walkthrough

### Bitcoin-Wallet.ipynb
This notebook is responsible for the cryptographic backend and wallet generation operations, which include entropy generation, checksum calculation, and key derivation.

### Steps of Wallet Generation
1. **Generate Entropy**: 
   - The function generates 128 bits of entropy.
2. **Calculate Checksum**:
   - Computes a checksum from the SHA-256 hash of the entropy.
3. **Append Checksum to Entropy**:
   - Combines the checksum with the original entropy to form 132 bits.
4. **Split Binary Data into 11-bit Parts**:
   - The binary data is divided into twelve 11-bit segments.
5. **Convert Parts to Mnemonic Words**:
   - Uses the BIP-39-compatible word list (`english.txt`) to map 11-bit segments to words.
6. **Derive Seed from Mnemonic**:
   - A seed is generated using PBKDF2-HMAC-SHA512 from the mnemonic phrase.
7. **Master Key and Chain Code Derivation**:
   - HMAC-SHA512 is used to derive the master private key and chain code from the seed.
8. **Generate Master Public Key**:
   - A public key is derived using elliptic curve cryptography (secp256k1).
9. **Child Key Derivation**:
   - Supports hierarchical key derivation for both hardened and non-hardened child keys.

---

## Requirements
- Python 3.7+
- Jupyter Notebook
- Required libraries listed in `requirements.txt`

---

## Dependencies
Install the following dependencies before running the project:
- **bit**: Bitcoin library for address generation and interaction (`pip install bit`)
- **ecdsa**: Library for elliptic curve operations (`pip install ecdsa`)
- **PyQt5**: For graphical user interface integration (if planning to add a GUI) (`pip install PyQt5`)

---

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/KyllianGenot/Bitcoin-Wallet.git
   cd Bitcoin-Wallet
   ```
2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Install Jupyter (if not already installed):
   ```bash
   pip install jupyter
   ```
4. Open the Jupyter Notebook:
   ```bash
   jupyter notebook Bitcoin-Wallet.ipynb
   ```

---

## Usage
1. **Generate a new mnemonic phrase**: 
   - Run the notebook cells to create a mnemonic using the word list in `english.txt`.
2. **Create a new wallet**:
   - Use the generated mnemonic to create and manage a new wallet.
3. **Manage transactions**:
   - Generate addresses and perform operations such as querying balance and signing transactions.

---

## Important Notes
- **Wordlist**: The word list used for mnemonic generation is provided in `english.txt` and should conform to BIP-39 (2048 words).
- **Test Environment Only**: This code is intended for educational purposes and testing. It is not suitable for use in a production environment.
- **Security**: Always store private keys and mnemonic phrases securely.

---

## License
This project is licensed under the MIT License.

---

## Acknowledgements
- BIP-32 and BIP-39 standards for hierarchical deterministic wallets.
- The Python `bit` library for Bitcoin address and key management.

---

By following this guide, you can explore the inner workings of Bitcoin wallet generation and hierarchical key derivation techniques.
