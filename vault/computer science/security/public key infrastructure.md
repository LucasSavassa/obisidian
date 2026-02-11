# summary
public key infrastructure (PKI) is a system that enables sharing public keys securely
# how to generate
1. generate pair of keys
2. choose one to be you public key (pub.key)
3. choose one to be you private key (pri.key)
4. send a certificate request to a certificate authority (CA)
5. the CA produces a **certificate**
6. the CA hashes the certificate
7. the CA signs the hash using it's private key
8. the CA sends back the certificate with the signature
9. the peer install the certificate in a hardware
# problems
## fundamental problem
- when you type ``bank.com``, you want to encrypt your interaction
- so your browser and the server agree upon an **encryption key**
- this is how this happens:

1. your browser asks for the server pub.key
2. the server delivers the pub.key
3. you encrypt the encryption key using the server's pub.key
4. the server decrypts the encryption key using its pri.key
5. the server confirms that received and knows the encryption key

- finally you can both interact securely

- but what if there is a man-in-the-middle during step 2?

- you will receive its pub.key
- and you will stablish a session key with him
- and you will send sensitive data to him
- and he will discover your deepest secrets (:o)

![[public key infrastructure 2026-01-21 21.50.37.excalidraw]]
# concepts
## certificate
a certificate is a digital identity card + signature

![[public key infrastructure 2026-01-23 14.57.58.excalidraw]]

