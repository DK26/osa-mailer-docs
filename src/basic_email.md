# Basic E-mail

Here is a full example:

```json
{
    "id": "fed5cadb",
    "utc": "2022-09-01T22:44:11.852662+00:00",
    "notify_error": [
        "Developers <dev-team@somemail.com>"
    ],
    "email": {
        "system": "MyExternalSystem",
        "subsystem": "[ID:12345] Trigger: Server Disk Out-of-Space",
        "from": "Mail System <tech-support@somemail.com>",
        "to": [
            "Rick S. <someone@somemail.com>"
        ],
        "cc": [],
        "bcc": [],
        "reply_to": [
            "System Admin <admin@somemail.com>",
            "Project Lead <lead@somemail.com>"
        ],
        "subject": "Warning: Your server's disk is out-of-space",
        "template": "ops_department",
        "alternative_content": "Unable to render HTML. Please refer to the Ops department for details.",
        "attachments": [],
        "key": ""
    },
    "context": {
        "message": {
            "head": "Detected Problems in Your Server",
            "body": "We have detected a disk capacity problem with one or more of your servers. Please refer to the instructions below"
        }
    }
}
```