# Introduction

**OSA-Mailer** engine allows you to send dynamic and sophisticated E-mails, using your preferred template engine 

**O.S.A** stands for **_Open Smart Alert_**

### Open

It is a free and open-source feature-rich backend engine for sending automated E-mails

### Smart

It is using sophisticated, programable HTML templates ("Smart Templates") that can provide advanced capabilities when producing E-mails

### Alert

It is designed in the context of alerting or notifying about events and elegantly providing relevant context about them. 
(It can also be used to send newsletters, but for now you'll have to handle your own subscriptions backend services)

## Main Features

- Manages different smart templates for different categories of your choice
- Identifies a common denominator for multiple E-mails and merges them into a single E-mail with accumulated context as an optional feature to reduce spam
- Supports multiple template engines with large communities and great support: `Tera`, `Liquid` and `Handlebars`
- (To be implemented) Allowing custom functionalities such as embedding dynamic QRCodes or defanging untrusted URLs, IP Addresses and E-mail addresses
- More community ideas to follow...

### Smart Templates & Marketplace  

Logically separates the front-end, back-end and data layers which should allow for easier community adaption (one does not required to understand all layers when using, maintaining or configuring the tool) 

- Develop or use ready Smart Templates that are programmed to act differently upon varying data inputs

- (WIP) Download or share Smart Templates from the community marketplace

### Minimalist & Reliable 

It is written in the Rust programming language which is both highly reliable and packs all mentioned capabilities in a single, small, high-performing executable (Cloud friendly)

### MVP Status

The project is still in Minimum Viable Product state and is subject to constant change

