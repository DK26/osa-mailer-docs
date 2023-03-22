# Common E-mail Entry


The following example represents an E-mail entry. 

Currently, it is mandatory to be explicit about all possible fields. However it is not required to fill every possible field.

In the following examples, we will explain the roles of every key and JSON object.

## Entry Object Structure

Here is the base structure of every E-mail entry:  

### Example

```json
{
    "id": "<ENTRY ID>",
    "utc": "<SEND TIMESTAMP IN UTC ISO 8601 RFC3339 FORMAT>",
    "notify_error": [ "<OPTIONAL E-MAIL ADDRESS FOR ERROR NOTIFICATIONS>" ],
    "email": {
        "<KEY-VALUE>": "<KEY-VALUE INPUTS, DESCRIBING HOW TO SEND THE E-MAIL>"
    },
    "context": {
        "<KEY-VALUE>": "<KEY-VALUE INPUTS, DESCRIBING THE DATA FOR THE HTML TEMPLATE>"
    }
}
```

The structure above is common among all E-mail entries. What varies are the assigned values.

| Data Name      | Data Type            | Description                                                                                                                                   |
| -------------- | -------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| `id`           | `string`             | A unique ID provided by the entry generator. There is no mandatory standard. The only requirement is that each entry must have a unique value |
| `utc`          | `string`             | A UTC timestamp value in the ISO 8601 RFC3339 standard                                                                                        |
| `notify_error` | `array` of `string`s | A list of E-mail addresses to be notified about errors (not implemented yet)                                                                  |
| `email`        | `object`             | A dictionary or map of values that describes the E-mail to be sent. e.g. subject, recipients, attachments, HTML template, etc.                |
| `context`      | `object`             | Context variables for the HTML template                                                                                                       |


## E-mail Object Structure

The _`email` object_ within the _entry object_, is composed of the following structure:  

### Example

```json
{
    "email": {
        "system": "My Automations System",
        "subsystem": "[ID:12345] Trigger: Server Disk Out-of-Storage",
        "from": "Ops Auto-Mailing System <tech-support@example.com>",
        "reply_to": [
            "System Admin <admin@example.com>",
            "Project Lead <lead@example.com>"
        ],
        "to": [ "Rick S. <rick_s@example.com>" ],
        "cc": [],
        "bcc": [],
        "subject": "ATTENTION! Your server is out-of-storage",
        "template": "ops_department",
        "alternative_content": "Unable to render HTML. Please refer to the Ops department for details.",
        "attachments": [],
        "unique_by": ""
    }
}

```
| Data Name             | Data Type            | Description                                                                                                                                                     |
| --------------------- | -------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `system`              | `string`             | The name of the external system that uses OSA-Mailer                                                                                                            |
| `subsystem`           | `string`             | The name of the subsystem that uses OSA-Mailer. e.g. Name of the trigger or rule that fired or activated OSA-Mailer, within the external system                 |
| `from`                | `string`             | The E-mail address of the sender                                                                                                                                |
| `reply_to`            | `array` of `string`s | An optional array of E-mail addresses to re-direct replies to                                                                                                   |
| `to`                  | `array` of `string`s | An array of E-mail addresses representing the `To:` recipients                                                                                                  |
| `cc`                  | `array` of `string`s | An array of E-mail addresses representing the `Cc:` copy to recipients                                                                                          |
| `bcc`                 | `array` of `string`s | An array of E-mail addresses representing the `Bcc:` hidden recipients                                                                                          |
| `subject`             | `string`             | The E-mail subject                                                                                                                                              |
| `template`            | `string`             | The selected template for the message body, located under the `templates` directory                                                                             |
| `alternative_content` | `string`             | The message to be displayed for clients that cannot render the HTML body of the message. Some E-mail clients use this value for message preview                 |
| `attachments`         | `array` of `string`s | An array of file paths to attach                                                                                                                                |
| `unique_by`           | `string`             | An optional aid field to assist in generating a unique E-mail ID by providing custom values. This provides us the ability to affect how E-mails are accumulated |

> The entire _`email`_ object is hashed in order to identify it and provide a unique E-mail ID. Multiple E-mails with the same ID, can be optionally accumulated into a single E-mail.

## Context Object Structure

The _`context` object_ within the _entry object_, can be freely composed of any JSON value. Every _key_ within the _`context` object_, is passed down to the selected `template`


### Example

The following JSON context, can be accessed within its following HTML template example:

```json
{
    "context": {
        "message": "Hello, world!",
        "items": [ "apple", "orange", "watermelon" ]
    }
}

```

HTML template using the `handlebars` engine for rendering:

```html
<!--TEMPLATE handlebars-->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Email Template</title>
</head>
<body>
    <div>
        <h1>{{ message }}</h1>
        <p>Here's the list of items:</p>
        <ul>
            {{#each items}}
                <li>{{ this }}</li>
            {{/each}}
        </ul>
    </div>
</body>
</html>
```

> There are 3 supported template engines at the moment: [`Handlebars`](https://handlebarsjs.com/guide/), [`Liquid`](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers) and [`Tera`](https://tera.netlify.app/docs/#templates). You can tell _OSA-Mailer_ how to render the template with a special magic comment at the beginning of the HTML file `<--TEMPLATE [ENGINE NAME]-->` (case insensitive)

> 🚨 At the moment, there are still standards to be formulated. It is within my hopes that once the project attracts attention, a community consensus will be established. So far, I try to avoid creating limits and only formulate what seems to me absolutely necessary. Striving for a standard is somewhat necessary so different clients and different potential backends, could still interface with each other with minimal to no modifications or adaptions