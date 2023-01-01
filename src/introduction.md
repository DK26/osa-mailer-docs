# Introduction

OSA-Mailer is a free and open-source feature-rich backend engine for sending automated E-mails.

It is meant to create a ready-to-use toolbox for sending E-mails which could contain some complex logical flows for dynamic inputs, outputting dynamic E-mails.

It is designed to completely separate front-end, back-end and data layers in a manner that enables to add and improve features behind the scenes by the backend community, while the frontend community can focus on designing E-mail templates, which are affected by the data the user is providing. 

It is designed to be fault-tolerant, and capable of accumulating a batch of E-mails into a single E-mail, merging the data from the entire E-mails batch, in order to prevent spam and maintain readability.

It is designed from the ground-up to be an open-source community project.

It supports multiple rendering engines: `tera`, `handlebars` and `liquid`.

It is written in the Rust programming language which packs all mentioned capabilities in a single, small, high-performing executable (Cloud friendly).

