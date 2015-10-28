# SMTPeter composer package

A library to abstract API calls to SMTPeter REST API. It exposes one class: Email.
This class can be used to easily created email message that can be sent via 
SMTPeter.

# Example

```php
/**
 *  REST API token that can be obtained from SMTPeter website.
 */
$apiToken = '';

// create new instance of email message
$email = new SMTPeter\Email($apiToken);

// set the email
$email->setFrom('Paweł Kuźnik <pawel.kuznik@copernica.com>');
$email->setSubject('SMTPeter test email');
$email->setText('text version');
$email->setHtml('<html><body><h1>HTML version</h1></body></html>');

// composer array of TO addresses and CC addresses
$to = array('someuser@example.com');
$cc = array('someotheruser@example.com');

// set to and cc
$email->setTo($to);
$email->setCC($cc);

// append recipients
$email->appendRecipients($to);
$email->appendRecipients($cc);

// send the email
$email->send();
```
