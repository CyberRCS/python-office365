[![Code Climate](https://codeclimate.com/repos/580e1c8b429e9e61a3000001/badges/8526d07b056fbbdd672d/gpa.svg)](https://codeclimate.com/repos/580e1c8b429e9e61a3000001/feed)

# Python-office365 - Office365 for your server

The objective of office365api is to make it easy to make scripts and applications
that are to be run against an Office 365 account. 

If you wanted to script retrieving an email it could be as simple as:

```python
from office365api import Mail
auth = ('YourAccount@office365.com', 'YourPassword')
mail = Mail(auth=auth)
messages = mail.inbox.get_messages()
```

And sending an email like this.

```python
from office365api import Message, Mail
from office365api.model import Recipient, EmailAddress
auth = ('YourAccount@office365.com', 'YourPassword')
message = Message(Subject='Heads up', Body='First automated alarm.',
    From=Recipient(EmailAddress=EmailAddress(Name='Full Name', Address='you@gmail.com')),
    ToRecipients= [Recipient.from_email(email='somebody@gmail.com')]
    )
    
m = Mail(auth=auth)
m.send_message(message)
```

## Gotchas

Currently writen against v 1.0 of outlook rest api, in the future v 2.0 will be added.
May be even graph rest api. However probably as a separate project.

Currently uses basic authentication. In a very near future will be switching to OAuth2.

This commit have only Mail module.


## Mail

Main class for working with emails in Office 365. You can use it to perform access to different
folders and may features exposed by REST api.

### Inbox - Mail.inbox

A collection of emails in . This is used when ever you are requesting an email or emails. 
It can be set with filters so that you only download the emails which your script is interested in.
 
