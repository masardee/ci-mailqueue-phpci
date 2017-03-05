CodeIgniter Mail Queue
=====================

Notice
------
This is a fork of https://github.com/izn/ci-mailqueue-phpci

General Information
-------------------

CI Mail Queue is a simple library (extended from CI_Mail) to queue emails in database and send them in background with CronJobs.

Installation
------------

1. Copy MY_email.php file into application/library folder
2. Import the schema
3. Add cronjobs.

E.g.:
- Send pending emails each 2 minutes.
 - */2 * * * * php /var/www/index.php queue_email/send_queue
- Send failed emails each 5 minutes.
 - */5 * * * * php /var/www/index.php queue_email/retry_queue

How to Use ?
------------

**Load the library**
```
$this->load->library('email');
```

**Send to Queue**

*This method will automatically clear the mail data (except attachment) for the next use*
```
$this->email-send();
```

**Send to Queue and clear the attachment **
```
$this->email->send(FALSE, TRUE, TRUE);
```

**Send to Queue without clearing the data **
```
$this->email->send(FALSE, FALSE);
```

**Send email directly (without queue)**
```
$this->email->send(TRUE);
```

Documentation
-------------
**Send**

Add email to Queue or send it directly
```
send($skip_job = FALSE, $auto_clear = TRUE, $clear_attachment = FALSE)
```

Parameter | Default | Description
--------- | ------- | -----------
$skip_job | FALSE | set to FALSE for add mail to Queue and TRUE for send mail directly 
$auto_clear | TRUE | Clear mail data (similar with clear() method in CI native email library)
$clear_attachment | FALSE | Clear attachment data (the first parameter of clear() method in CI native email library)

**Send Queue**

Send the mail queue
```
send_queue()
```

**Retry Queue**

Re adding failed email to the Queue
```
retry_queue()
```

Enjoy!
