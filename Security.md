<p><a target="_blank" href="https://app.eraser.io/workspace/xMl8Mks1PaOOfsB9PM3A" id="edit-in-eraser-github-link"><img alt="Edit in Eraser" src="https://firebasestorage.googleapis.com/v0/b/second-petal-295822.appspot.com/o/images%2Fgithub%2FOpen%20in%20Eraser.svg?alt=media&amp;token=968381c8-a7e7-472a-8ed6-4a6626da5501"></a></p>

# 🔐 1. What is SunJCE Security?
👉 SunJCE is a **default security provider in Java**.

It is part of: 👉 Java Cryptography Extension.



👉 “SunJCE is a built-in Java security provider that implements cryptographic algorithms like AES, RSA, DES, and hashing.”



```
Application Code
      ↓
Cipher / KeyGenerator API
      ↓
Security Provider (SunJCE)
      ↓
Actual Algorithm Implementation (AES, RSA)
```
👉 SunJCE provides the **actual implementation** behind APIs like:

- `Cipher` 
- `KeyGenerator` 
- `KeyPairGenerator` 
```
Cipher cipher = Cipher.getInstance("AES");
```
```
Client Data
   ↓
AES Encryption (fast, symmetric)
   ↓
RSA Encryption (encrypt AES key)
   ↓
Secure Transmission
   ↓
Backend Decryption (RSA → AES)
```




# 🔐 . What is BouncyCastle?
👉 Bouncy Castle is an **external security provider**

BouncyCastle is a third-party cryptography provider that offers advanced and extended security features not available in default Java providers.



# 🚀 Why you used BouncyCastle
👉 Main reason in your case:

### 📄 Handling `.crt` files (Certificates)
SunJCE has **limited support** for:

-  Parsing certificates 
-  Advanced formats


### ✅ BouncyCastle helps in:
-  Reading `.crt`  / `.pem`  files 
-  Parsing X.509 certificates 
-  Extracting: 
    -  Public key

```
Security.addProvider(new BouncyCastleProvider());

CertificateFactory factory = CertificateFactory.getInstance("X.509");
InputStream in = new FileInputStream("certificate.crt");

X509Certificate cert = (X509Certificate) factory.generateCertificate(in);
PublicKey key = cert.getPublicKey();
```




👉
 “In our project, we used SunJCE as the default cryptographic provider for AES and RSA encryption. It works internally with Java Cipher APIs.

Additionally, we used BouncyCastle as an external provider to handle X.509 certificate (.crt) files, as it provides better support for parsing certificates and extracting public keys required for encryption.”

\





📊 AES Flow 

```
Plain Text
 ↓
SecretKey (generated)
 ↓
Cipher (AES)
 ↓
Encrypted Data 
```
🔐 AES Flow Diagram (with Class🔐)



```
Plain Text (String / byte[])
        ↓
🔑 Key Generation
   KeyGenerator (class)
        ↓
   SecretKey (interface)
        ↓
   SecretKeySpec (class)  ← (optional: if using custom key)
        ↓
🎲 IV Generation (for CBC/GCM)
   SecureRandom (class)
        ↓
   IvParameterSpec / GCMParameterSpec (class)
        ↓
⚙️ Encryption Engine
   Cipher (class)
   Cipher.getInstance("AES/CBC/PKCS5Padding")
        ↓
   cipher.init(ENCRYPT_MODE, SecretKey, IV)
        ↓
   cipher.doFinal()
        ↓
🔐 Encrypted Bytes
        ↓
📦 Encoding
   Base64 (utility class)
        ↓
Final Encrypted String 
```
# 🧠 AES One-line Flow (for quick revision)
👉
` “KeyGenerator → SecretKey → IV → Cipher → doFinal → Base64”` 



🔐 RSA Flow Diagram (with Classes)



```
Plain Text (byte[])
        ↓
🔑 Key Pair Generation
   KeyPairGenerator (class)
        ↓
   KeyPair (class)
     ↓           ↓
 PublicKey    PrivateKey   (interfaces)
        ↓
⚙️ Encryption
   Cipher (class)
   Cipher.getInstance("RSA")
        ↓
   cipher.init(ENCRYPT_MODE, PublicKey)
        ↓
   cipher.doFinal()
        ↓
🔐 Encrypted Data
        ↓
🔓 Decryption
   Cipher (class)
        ↓
   cipher.init(DECRYPT_MODE, PrivateKey)
        ↓
   cipher.doFinal()
        ↓
Original Data
```


**********************************************

🔐 **AES Flow Diagram (with Classes + Code)**

```
Plain Text (String / byte[])
        ↓
"Hello World".getBytes()

🔑 Key Generation
   KeyGenerator (class)
        ↓
   KeyGenerator keyGen = KeyGenerator.getInstance("AES");
   keyGen.init(256);
   SecretKey secretKey = keyGen.generateKey();

   SecretKey (interface)
        ↓

   SecretKeySpec (class)  ← (optional)
        ↓
   byte[] keyBytes = secretKey.getEncoded();
   SecretKey key = new SecretKeySpec(keyBytes, "AES");

🎲 IV Generation (for CBC/GCM)
   SecureRandom (class)
        ↓
   byte[] ivBytes = new byte[16];
   SecureRandom random = new SecureRandom();
   random.nextBytes(ivBytes);

   IvParameterSpec / GCMParameterSpec (class)
        ↓
   IvParameterSpec iv = new IvParameterSpec(ivBytes);
   // OR
   GCMParameterSpec gcmSpec = new GCMParameterSpec(128, ivBytes);

⚙️ Encryption Engine
   Cipher (class)
        ↓
   Cipher cipher = Cipher.getInstance("AES/CBC/PKCS5Padding");

   cipher.init(ENCRYPT_MODE, SecretKey, IV)
        ↓
   cipher.init(Cipher.ENCRYPT_MODE, key, iv);

   cipher.doFinal()
        ↓
   byte[] encryptedBytes = cipher.doFinal("Hello World".getBytes());

🔐 Encrypted Bytes
        ↓

📦 Encoding
   Base64 (utility class)
        ↓
   String encryptedString = Base64.getEncoder().encodeToString(encryptedBytes);

Final Encrypted String
```
****************************************************

🔐** RSA Flow Diagram (with Classes + Code)**

```
Plain Text (byte[])
 ↓
"Hello World".getBytes()
🔑 Key Pair Generation
 KeyPairGenerator (class)
 ↓
 KeyPairGenerator keyGen = KeyPairGenerator.getInstance("RSA");
 keyGen.initialize(2048);
 KeyPair (class)
 ↓
 KeyPair keyPair = keyGen.generateKeyPair();
```
```
↓                     ↓
```
```
PublicKey (interface) PrivateKey (interface)
 ↓ ↓
PublicKey publicKey = keyPair.getPublic();
PrivateKey privateKey = keyPair.getPrivate();
⚙️ Encryption (using Public Key)
 Cipher (class)
 ↓
 Cipher cipher = Cipher.getInstance("RSA");
 cipher.init(ENCRYPT_MODE, PublicKey)
 ↓
 cipher.init(Cipher.ENCRYPT_MODE, publicKey);
 cipher.doFinal()
 ↓
 byte[] encryptedBytes = cipher.doFinal("Hello World".getBytes());
🔐 Encrypted Bytes
 ↓
📦 Encoding
 Base64 (utility class)
 ↓
 String encryptedString = Base64.getEncoder().encodeToString(encryptedBytes);

🔓 Decryption (using Private Key)
 Cipher (class)
 ↓
 Cipher cipher = Cipher.getInstance("RSA");
 cipher.init(DECRYPT_MODE, PrivateKey)
 ↓
 cipher.init(Cipher.DECRYPT_MODE, privateKey);
 cipher.doFinal()
 ↓
 byte[] decryptedBytes = cipher.doFinal(Base64.getDecoder().decode(encryptedString));
Final Decrypted String
 ↓
 new String(decryptedBytes)
```


***************************************************************

🔐** RSA with **`**.crt**`** File (Your Project Flow 🔥)**

```
CRT File (.crt)
        ↓
📄 Certificate Parsing
   CertificateFactory (class)
        ↓
   CertificateFactory factory = CertificateFactory.getInstance("X.509");
   X509Certificate (class)
        ↓
   InputStream in = new FileInputStream("certificate.crt");
   X509Certificate cert = (X509Certificate) factory.generateCertificate(in);
   PublicKey (interface)
        ↓
   PublicKey publicKey = cert.getPublicKey();
⚙️ Encryption
   Cipher (RSA)
        ↓
   Cipher cipher = Cipher.getInstance("RSA");
   cipher.init(Cipher.ENCRYPT_MODE, publicKey);
   byte[] encryptedBytes = cipher.doFinal(data);
```




<!--- Eraser file: https://app.eraser.io/workspace/xMl8Mks1PaOOfsB9PM3A --->