# Basic E-mail

Here is a full example:

```json
{
    "id": "fed5cadb",
    "utc": "2022-09-01T22:44:11.852662+00:00",
    "notify_error": [
        "Developers <dev-team@example.com>"
    ],
    "email": {
        "system": "My Automations System",
        "subsystem": "[ID:12345] Trigger: Server Disk Out-of-Space",
        "from": "Mail System <tech-support@example.com>",
        "to": [
            "Rick S. <rick_s@example.com>"
        ],
        "cc": [],
        "bcc": [],
        "reply_to": [
            "System Admin <admin@example.com>",
            "Project Lead <lead@example.com>"
        ],
        "subject": "Warning: Your server's disk is out-of-space",
        "template": "ops_department",
        "alternative_content": "Unable to render HTML. Please refer to the Ops department for details.",
        "attachments": [],
        "unique_by": ""
    },
    "context": {
        "message": {
            "heading": "Detected Problems in Your Server",
            "body": "We have detected a disk capacity problem with one or more of your servers. Please refer to the instructions below"
        }
    }
}
```

## Templates

The `templates` directory is meant to contain all templates in separated directories, with their (optional) _resources_ and _assets_ included, where each directory name represents the template's name.

The template index file is called `template.html`. In the example above, we use the `ops_department` template. 

Under the `templates` directory, create a directory called `ops_department` and then create a text file and name it  `template.html`  

Copy the following HTML content into `template.html` and save the file.


## Example  

> 📦osa_mailer  
> ┣ 📂templates      
> ┃ ┗ 📂ops_department  
> ┃  ┗ 🗎template.html  👈  
> ...


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
    <table width="100%" border="0" cellspacing="0" cellpadding="0" bgcolor="#f4f4f4">
        <tr>
            <td align="center" valign="top">
                <table width="600" border="0" cellspacing="0" cellpadding="20" bgcolor="#ffffff">
                    <tr>
                        <td align="center" valign="top">
                            <h1>{{message.heading}}</h1>
                        </td>
                    </tr>
                    <tr>
                        <td align="center" valign="top">
                            <p>{{message.body}}</p>
                        </td>
                    </tr>
                </table>
            </td>
        </tr>
    </table>
</body>
</html>
```

