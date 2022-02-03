# Metis

## What is Metis?

Metis is a messaging application based on blockchain technology. Each message is represented as an encrypted transaction on the Jupiter blockchain. Metis is a distributed service that runs on a decentralized blockchain network to provide a higher level of security, privacy, and independence from any authority. Anyone can run Metis on their own hardware, yet still talk to the entire global Metis network and distributed infrastructure.

## How are messages encrypted in Metis?

The messages are double-encrypted. First, by the blockchain protocol (Curve25519 – same as Monero, Polkadot or Solana, as well as others), which is decrypted with your passphrase (12-word private key to access your account in the Jupiter network) and second, a layer in the Metis application itself that communicates with the blockchain, with military grade encryption (AES256-cbc), decrypted with your encryption password in the application.

Logging into the Metis application takes both the passphrase and encryption password. You may set your login to use your mobile devices' built-in bio-metric feature to ease login and use.

Only people inside a channel can read the messages in that channel –and channels are only accessed by the invitation of another member.

## **Other apps also have different types of end-to-end encryption and sent messages have been accessed. What makes Metis different?**

Metis is different by design. Other services are centralized and rely on one company or one infrastructure system to work. Metis is not and does not. A government or a multinational like Facebook can dig into the servers, where your information is either stored unencrypted or transported by an unencrypted mechanism through their server stack and then decrypted. Services like Signal are 100% reliant on companies like Signal to fully work. You can't stand up your own Signal server and talk to **all** other Signal users. With Metis, you can!

What makes Metis different is how it encrypts the information first in the application, then sends it through an SSL-encrypted channel, and encrypts it again on the blockchain.

## How is Metis is decentralized?

That you don't depend on any central server. Anyone can run their own node (hardware where blockchain transactions are processed and a copy of the entire chain is stored, communicating with the rest of the nodes) and even set up a home instance so that you talk to your own node, and communicate through it with any Metis user through the blockchain, without your messages leaving your private network at any time, leaving only an encrypted trace on a public blockchain. In the same way, it ensures that no government or company can simply shut down the application's servers, as any computer (a Raspberry Pi, for example) is a functional node with a copy of the blockchain.

## So, my messages are stored on a public network?

Transactions on Jupiter's blockchain are transparent by default - if someone knows your alias or JUP address, they can see you send or receive messages. No one is able to access the content as they do not possess the passphrase of your wallet or the channels in which the messages are sent. Even if you left your passphrase exposed and someone could access your Jupiter account, when decrypting the message contained in the transaction recorded on the blockchain, they would only find another encrypted message. These messages could only be accessed through a Metis application with your alias, passphrase, and private encryption password. Therefore, you need both keys at the same time to be able to access your messages and no one can access them in any way without knowing these pieces of information.

## Can I delete my messages?

No. They are there forever, encrypted by the blockchain protocol and Metis’ AES256. You can't delete anything from a blockchain. Therein lies its nature. But, we are working towards message 'hiding' so at least you can remove unwanted comments from your channels.

## How does the app connect to my device, is it associated with my IMEI or phone number?

It does not connect in any way. Metis is only associated to your JUP account, that is basically the passphrase. And on top of that, you have the encryption password for second layer of protection. Your JUP account is something on its own that does not require any personal info to be created. No mail, no phone number, no anything.

## If you don't sell my data like other apps, how does Metis finance itself?

You pay with money, as it should be. As we have said, each message is attached to a transaction in the Jupiter blockchain, to which is associated a commission paid in your currency. The commission is called “tx fee” and its amount can be altered; being in any case a very low amount -practically negligible, currently 1 JUP for 10k messages- and being able to currently open an account with a small charge of JUP to be able to use it without prior payment. Metis is different by design. Other services are centralized and rely on one company or one infrastructure system to work. Metis is not and does not. A government or a company like Facebook can dig into the servers, where your information is either stored unencrypted or transported by an unencrypted mechanism through their server stack and then decrypted. Services like Signal, while open sourced, are 100% reliant on companies like Signal to fully work. You can't stand up your own Signal server and use their service.&#x20;
