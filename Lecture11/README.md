# Cloud and Application in Security
### Basic Terms and Concepts
- **Confidentiality：** Only authorized party can get access to data.
- **Integrity**: Guarantee the user that the data is transmitted matches the data received by the cloud service.
- **Authenticity**: Is the data coming from an authorized source?
- **Availability**: Service should be accessible and usable during a specified time period. For a cloud service, the time period is 24/7/365.
- **Threat**: In computer security a threat is a possible danger that might exploit a vulnerability to breach security and therefore cause possible harm.
- **Vulnerability**: A weakness that can be exploited.
- **Attack Vectors**: A path or means by which a hacker can gain access to a computer or network server in order to deliver a payload or malicious outcome. Attack vectors enable hackers to exploit system vulnerabilities, including the human element.
- **Risk**: The possibility of loss or harm arising from performing an activity.
- **Security Controls**: Countermeasures used to prevent or respond to security theats and to reduce
- **Threat Agent**: An entity that poses a threat because it is capable of carrying out an attack.

## Cloud Security Threats
### Traffic Eavesdropping
Occurs when data being trasferred to or within a cloud service is passively intercepted for illegitimate information gethering purposes.
becuase of the passive nature of the attack, it can more easily go undetected for extended periods of time.
### Malicious Intermediary
messages are intercepted and altered by a malicious service agent, potentially compromising the message's confidentiality and/or integrity.
### Insufficient Authorization
access is granted to an attacker erroneously or too broadly.
### Denial of Service (DoS)
overload resources to the point wehre they cannot function properly. 
The workload is artificially increased with imitation messages or repeated communication requests.
The network is overloaded with traffic to reduce its responsiveness and cripple its performance.
Multiple requests are sent, each of which is designed to consume excessive memory and processing resources. 

### Flawed Implementations


## Cloud Security
- Cloud Security is a Shared Responsibility

### Cloud Provider Responsibility
protecting the infrastructure that runs all of hte services offered in their cloud.
This infrastructure is composed of the hardware, software, networking, and facilities that run the Cloud services.
### Cloud User Responsibility
determined by the Cloud Services that a customer selects.
IaaS, requres the customer to perform all of the necessary security configuration and management tasks.

## Security Mechanisms
### Encryption
Data is coded ina  readable format known as plaintext. When transmitted over a network, plaintext is vulnerable to unauthorized and potentially malicious access.
Encryption Mechanism is a digital coding system dedicated to preserving the confidentiality and integrity of data. Encoding palintext data into a protected and unreadable format.
Can help counter the traffic eavesdropping, malicious intermediary, insufficient authorization, and overlapping trust boundaries security threats.

#### Symmetric Encryption 对称加密
- Uses the same key for both encryption and decryption, both of which are performed by authorized parties that use the one shared key.
- AKA **Secret Key cryptography**, messages taht are encrypted with a specific key can be decrypted by only that same key.
- Parties that rightfully decrypt the data are provided with evidence that the original encryption was performed by parties that rightfully possess the key.
- A basic authentication check is alwys performed, because only authorized parties that own the key can create messages. This maintains and verifies data confidentiality.
- Symmetrical encryption does not have the characteristic of non-repudiation, since determining exactly which party performed the message encryptionor decryption is not possible if more than one party is in possession of the key.
对称加密没有 non-repudiation 的特性，non-repudiation - 授权者不能否认自己曾经对这个合同进行过授权。

#### Asymmetric Encryption 不对称加密
- Relies on the use of two different keys, namely a private key and a public key.
- aka public key cryptography, the private key is known only to its owner while the public key is commonly available.
- A document that was encrypted with a private key can only be correctly decrypted with the corresponding public key.
- Conversely, a document that was encrypted with a public key can be decrypted only using its private key counterpart.
- Almost always computationally slower than symmetric encryption.

### Securing Web-based Data Transmission
Most commonly applied via HTTPS, which refers to the user of SSL/TLS as an underlying encryption protocol for HTTP. TLS is the successor to the SSL technology.
#### SSL Secure Sockets Layer

#### TLS Transport Layer Security
TLS only use asymmetric encryption for its key exchange method.
TLS systems then switch to symmetric encryption once the keys have been exchanged.
Most TLS implementations primarily support RSA as the chief asymmetrical encryption cipher, while ciphers such as Triple-DES, and AES are supported for symmetrical encryption.

### Hashing
The hashing mechanism is used when a one-way, non-reversible form of data protection is required.
Can be used to derive a message digest from a message, sender attach the message digest to the message.

### Digital Signature

### Public Key Infrastructure (PKI)
A set of roles, policies, and procedures needed to create, manage, distribute, use, store, and revoke digital certificates and manage public-key encryption.
The purpose of a PKI is to facilitate the secure electronic transfer of information for a range of network activities such as e-commerce, internet banking and confidential email.
It is required for activites where simple passwords are an inadequate authentication method and mroe rigorous proof is required to confirm the idnetity of the parites involved in the communication and to validate the information being transferred.

In cryptography, a PKI is an arrangement that binds public keys with respective identities of entities (like persons and organizations)

## Application Security
### Core Security Problem: Users can Submit Arbitrary Input
Assume that all input is potentially malicious

## Core Defense Mechanisms
### Authentication
### Session Management
### Access Control
### Handling User Input

## Handling Hackers
### Mapping the Application
### Bypassing Client Side Controls
### Attacking Authentication
### Code Injection into Interpreted Languages
### Cross-site scripting (XSS)
### Cross-site request forgery (CSRF)

