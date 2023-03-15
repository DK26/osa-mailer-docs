# Sending an E-mail

On every run, _OSA-Mailer_ is scanning its `outbox` directory for new E-mail entries.

Each E-mail entry is represented as a JSON document file. 

An E-mail entry can be though of as just a single _"send E-mail"_ request that contains all details required to send it.  

When attempting to send multiple E-mails to the same recipients, on the same subject, having a common denominator, they are all considered to be E-mail _entries_ that compose the same, single E-mail ("Composed E-mail"), that represents the final product to be sent to your recipients.

You can have a relation of multiple E-mail entries per one composed E-mail
or one E-mail entry per one composed E-mail. It depends on your personal configurations.

Once the E-mail entry is processed and sent _**successfully**_, it is deleted from the `outbox` directory.

> 🚨 **If the `.json` entry file is not _deleted_ from the `outbox` directory, then an _error_ might have occurred. You can check the `logs` directory to get more details about the errors.**

## Outbox Directory  

In order to send an E-mail, we have to produce an E-mail entry which is a JSON document that contains all details required to send it, and place it in the `outbox` directory.

Using the `outbox` directory, enables us advanced features such as accumulating multiple E-mails into a single one that is containing accumulate context within its contents. This reduces spam in our recipients' inbox and provides them with more concise E-mails.

Other future features are in-bound such as delayed E-mails, etc. All of these features and more, are only possible to achieve when using an `outbox` directory to accumulate E-mails.

> Notice: In the future, we may use a database or provide an option for a database. For our MVP, we just put JSON files in the `outbox` directory

## Example  

> 📦osa_mailer  
> ┣ 📂outbox  👈  
> ┃ ┣ 🗎my_non_standard_email_entry.json  
> ┃ ┣ 🗎a40a6508.3b0c7586049dd2.c8e7d381.3e5f6e98.json   
> ┃ ┗ 🗎a40a6508.3b119a8fafdc3a.72e3d49e.fc982089.json  
> ...

## E-mail Entry Name Convention



The following describes the current, non-binding standard for E-mail entry file name convention:

 > **{`E-mail ID`}.{`Timestamp`}.{`Entry ID`}.{`CRC32 Checksum`}.json**
 
| Field            | Description                                                                                                   |
| ---------------- | ------------------------------------------------------------------------------------------------------------- |
| `E-mail ID`      | A unique ID to identify the E-mail, produced by hashing the `email` part of the entry, encoded in hexadecimal |
| `Timestamp`      | Creation time in nanoseconds, encoded in hexadecimal                                                          |
| `Entry ID`       | A unique ID to identify the entry, extracted from the entry itself                                            |
| `CRC32 Checksum` | A unique CRC32 checksum of the entire entry file, encoded in hexadecimal                                      |

> 🚨 **The file name convention isn't mandatory but it helps in debugging and avoiding coalitions when auto-generating E-mail entries. The standard is embedded in the `new_entry.py` script file which is located in the `mail_producer` directory**

The following chapters will demonstrate how to compose an E-mail entry JSON document.