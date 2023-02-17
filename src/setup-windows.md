# Windows Setup

## Preface

At this stage of the development, there is no installer.

Currently the way to use _OSA-Mailer_ is it have an external system to run its run script `osamailer.cmd`

## Download

**Steps:**
1. Get to the [releases](https://github.com/DK26/osa-mailer/releases) page
2. Pick the latest version of _OSA-Mailer_
3. Expand the `Assets` title by clicking on it
4. Pick the `.7z` 7-zip archive file for Windows and click on it to start downloading

## Extract

In order to extract a 7-zip archive, you need an extractor that supports it. Your best bet is probably to download the official 7-zip from its website [https://www.7-zip.org/](https://www.7-zip.org/)

**Steps:**  

1. Extract the archived file from the `Download` section anywhere you like, but make sure you will have controlled access to the extracted `outbox` directory as this directory serves clients as a gateway for sending E-mails

## Configure

1. Edit the script file `osamailer.cmd` with your favorite text editor
2. Look for the `:: Configurations` comment  
3. Notice the `SET` statements which set each environment variable for _OSA-Mailer_
4. Configure each environment variable accordingly:
   1. `SERVER` - SMTP server IP address or hostname (e.g. Gmail, Outlook, SMTP relay-proxy, etc.)
   2. `PORT` - The TCP port number for the `SERVER` variable
   3. `AUTH` - Authentication method: `TLS`, `STARTTLS` or `NOAUTH`
   4. `USERNAME` - Provides the username when using an authentication method other than `NOAUTH`. Uncomment by the removing the double-colons `::` from its `SET` statement (e.g. `::SET USERNAME=username` becomes `SET USERNAME=username`)
   5. `PASSWORD` - Provides the username when using an authentication method other than `NOAUTH`. Uncomment by the removing the double-colons `::` from its `SET` statement (e.g. `::SET PASSWORD=password` becomes `SET PASSWORD=password`)


```batch
:: Configurations
SET SERVER=localhost
SET PORT=25
SET AUTH=noauth
::SET USERNAME=username
::SET PASSWORD=password
```

## Setup a Task for Windows Task Scheduler