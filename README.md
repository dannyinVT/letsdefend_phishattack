# letsdefend_phishattack

Phishing Attack Write-up




From our alert, it appears that a phishing attack is being sent to lars@letsdefend.io
![img](https://github.com/dannyinVT/letsdefend_phishattack/blob/main/Picture1.png)


Let’s check the mailbox and see what the sender has to say.

![img](https://github.com/dannyinVT/letsdefend_phishattack/blob/main/Picture2.png)

  
We can see that the grammar is a little off while it appears to be as ambiguous as possible. An attachment is seen, as well. Let’s upload it to VirusTotal and see what the results are.

![img](https://github.com/dannyinVT/letsdefend_phishattack/blob/main/Picture3.png)

VirusTotal is able check the contents, revealing a Trojan. Let’s dig a little deeper.

![img](https://github.com/dannyinVT/letsdefend_phishattack/blob/main/Picture4.png)

The hash value offers quite a bit more information if we continue.

![img](https://github.com/dannyinVT/letsdefend_phishattack/blob/main/Picture5.png)

 
This area checks the hash value against other repositories. This is obviously malicious.
We’ll return to the SIEM and process this alert.
By following a playbook, we can go step-by-step to break it down further. From our research, it appears the e-mail is indeed malicious and unsolicited. Unfortunately, the e-mail made it pass the spam filter and was delivered to the recipient’s mailbox, increasing the likelihood of infection.
In the following screenshot, network logs were checked to see if outbound connections were made to a C2 server.

![img](https://github.com/dannyinVT/letsdefend_phishattack/blob/main/Picture6.png)

 
![img](https://github.com/dannyinVT/letsdefend_phishattack/blob/main/Picture7.png)

As we can see, contact was made to the IP 188.213.19.81 and was allowed.

The security alert can be closed and further reviewed by Level 2 if necessary, as this is a true positive.



