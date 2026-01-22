# Vault
This project outlines the design and implementation of a cloud-based encrypted credit card vault
that securely stores and retrieves sensitive payment card information using advanced cryptographic techniques. The system employs AES-256-GCM encryption for data-at-rest protection,
TLS 1.3 for secure data transmission, and AWS Key Management Service (KMS) for reliable
key management via envelope encryption. To prevent exposure of sensitive cardholder information, the system implements a tokenization approach where credit card Primary Account
Numbers (PANs) are never stored in plaintext. Instead, randomly generated tokens serve as surrogate identifiers mapped to encrypted data in a secure database.

By putting in place several security layers, such as IAM-based access control, thorough audit
logging via AWS CloudTrail, and the least privilege principle, the architecture guarantees compliance with Payment Card Industry Data Security Standard (PCI DSS) regulations. The system
accepts credit card data through a secure REST API, encrypts it using envelope encryption where
Data Encryption Keys (DEKs) are themselves encrypted by Key Encryption Keys (KEKs) managed in AWS KMS, and stores only the token-to-encrypted-data mappings. Secure decryption is
carried out by authorized retrieval operations following appropriate authorization and authentication checks.

Performance testing demonstrates the system's ability to handle encryption and decryption operations efficiently while maintaining security guarantees. The threat model analysis validates the
system's resilience against common attack vectors including man-in-the-middle attacks, database
breaches, and unauthorized access attempts.
