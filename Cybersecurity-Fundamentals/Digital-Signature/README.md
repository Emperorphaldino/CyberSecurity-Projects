## Understanding and Implementing Digital Signatures and Public Key Distribution
### NAME: ISSA FUHAD 

#### BACKGROUND
### In cybersecurity, ensuring that a file or message has not been altered during transmission is critical. Digital signatures, created using private keys and verified using public keys, provide this assurance. GPG (GNU Privacy Guard) is an open-source encryption tool that implements the OpenPGP standard for securing data.

#### SCOPE
* Key Management: Importing the sender's public key into the local keyring.

* File Handling: Ensuring that the signed message and its corresponding signature file are correctly prepared.

* Signature Verification: Using GPG to check both the validity and integrity of the signed data.

* Error Handling: Diagnosing common errors (e.g., CRC errors, “no signature found”) and understanding their causes.

#### PROJECT OBJECTIVE
##### The goal of the project is to:

* Understand how digital signatures work.
* Learn how to generate key pairs using GPG.
* Sign and verify messages using public–private key cryptography.
* Share public keys securely.
* Test the integrity verification feature by detecting tampered messages.

### TOOLS TO BE USED 
* Operating System: Kali Linux
* Software: GPG (GNU Privacy Guard)
* Text Editor: nano
* Terminal: Bash Shell

### PROJECT STRUCTURE

Digital-Signature-and-PKI/
├── img/                          # All project screenshots
├── Temmy_Download/               # Files that Temmy received
├── message.txt                   # Original message file
├── public_key.asc                # Exported public key
├── README.md                     # This project report
└── signed_message.sig            # Signed message file


## PROJECT STEPS
### Step 1: Generate a GPG Key Pair
We start by generating a public–private key pair.
Command:
gpg --full-generate-key

![GPG Key Pair ](./img/1.%20Generate%20a%20GPG%20Key%20Pair.png)

### Step 2: Choose Key Length
For stronger encryption, 4096 bits should be chosen but we'll go with the default 3072 bits.

![Key Lenght](./img/2.%20Choose%20Key%20Length.png)

### Step 3: Set Key Validity Period
We set the key to be forever valid by choosing 0.

![Set key](./img/3.%20Set%20Key%20Validity%20Period.png)

### Step 4: Identity Construction
We provided:

* Name: Issa Fuhad
* Email: issafuhad135@gmail.com

![identify](./img/4.Identity%20Construction.png)

### Step 5: Final Options and Passphrase Choice
We confirmed the key type, length, validity, and then set a strong passphrase to protect the private key

![paraphase](./img/5.%20Final%20Options%20and%20Passphrase%20Choice.png)

### Step 6 Create a message
we created a text file with a confidential message:
'echo "This is confidential memo from Fuhad to peter

![Create](./img/6.%20Create%20a%20Message.png)

### Step 7: Sign the message

After signung the message using "gpp --amor --output signed_message.sig --sign message.txt

it produced the file containing signature 

![Sign](./img/7.%20List%20keys.png)

### Step 8: List Keys
To confirm our key exists in the local GPG keyring "gpg --list-keys

![List](./img/8.%20Exported%20Public%20key.png)

### Step 9: Export Public Key
We exported the public key linked to our email

gpg --armor --export issafuhad135@gmail.com > public_key.asc

![Export](./img/9.%20Verify%20the%20Key%20Export.png)

### Step 10: Verify the Key Export
We sent two files to Peter

![Export](./img/10.%20Send%20Files%20to%20Receiver.png)

### Step 11
Downoaded files

![download](./img/11.%20Download%20Files.png)

### Step 12: Open Downloads Folder in Terminal 

![Terminal](./img/12.%20Open%20Downloads%20Folder%20in%20Terminal.png)

### Step 13: Import Public Key

README.md
gpg --import public_key.asc

![Public](./img/13.%20Import%20Public%20Key.png)

### Step 14 Verify the Signature

"gpg --verify signed_message.sig

![Signature](./img/14.%20Verify%20the%20Signature.png)

### Step 15: Open Signed Message

![open](./img/15.%20Open%20Signed%20Message.png)

### Step 16 View Signed Message Content

![View](./img/16.%20View%20Signed%20Message%20Content.png)

### Step 17 Tamper with the file

![Tamper](./img/17.%20Tamper%20with%20the%20File.png)

### Step 18: Verify Again ==Failure
After tampering. GPG detects corruption:

"gpg --verify signed_message.sig"

gpg: CRC erroe...
gpg: the signature could not be verified.

![Verify](./img/18.%20Verify%20Again%20—%20Failure.png)