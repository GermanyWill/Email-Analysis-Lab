# Email-Analysis-Lab

## Objective

Analyze email headers, links, attachments, and sender information to identify phishing indicators and assess potential security threats.

### Skills Learned

- Phishing email detection and analysis
- Email header and metadata investigation
- Threat identification through link and attachment analysis

### Tools Used

- Notepad++ to fully extract the metadata from the email.
- CyberChef to decode messages.
- HxD to reveal file types.

## Steps
•	First I started up my Windows 10 virtual machine. 
•	Inside of the VM I went to Blue Team Labs’ Challenges to find the challenge called “The Planets Prestige”

 <img width="975" height="444" alt="image" src="https://github.com/user-attachments/assets/5c83d633-b6b2-4d5c-8967-6fe42f5122cd" />

•	I read the prompt and then read the downloaded email. 
•	I used a tool called “Notepad++” to fully extract the email.

<img width="975" height="419" alt="image" src="https://github.com/user-attachments/assets/5f7a3958-0523-4867-b9a5-c413338f7594" />
 
•	I looked at the results and noticed that the SPF was set to fail and that mivroapple.com didn’t designate whoever 93.999.104.210 as a permitted sender. Just the fact that the spf was set to fail was already suspicious alone. 

<img width="736" height="232" alt="image" src="https://github.com/user-attachments/assets/7b292ab6-2206-46e5-8bed-5b41a5d46181" />

•	I also noticed that the “from” email and “reply to” emails are different which is a major red flag. 

  <img width="1125" height="114" alt="image" src="https://github.com/user-attachments/assets/86a2cd63-a89d-4276-b317-e769615c39b3" />
  
•	We were hit with a base 64 encoded message, so I decoded it using the tool “cyberchef.”

 <img width="1056" height="625" alt="image" src="https://github.com/user-attachments/assets/6b509e1b-ca58-4e17-b1d4-dd2cd9783d5f" />

•	The message mentioned that it had an attachment that would lead me to more clues, so I went and scrolled down a bit more and noticed an attachment that was again encrypted with Base64.
•	I copied it and pasted it into cyberchef once again, only this time I set the output to hex.

 <img width="1105" height="123" alt="image" src="https://github.com/user-attachments/assets/637290f6-b52a-461b-9390-98f0fa530fc3" />

•	I copied the first four bytes and pasted them into a tool called garykessnerfilesignatures.

 <img width="1125" height="467" alt="image" src="https://github.com/user-attachments/assets/73bca19a-4d07-47f5-a224-05cd3dcf1837" />

•	This information let me know that it was a zip extension file even though the attachment states pdf.
•	I removed the hex and then saved the decoded output to file.
•	I then extracted said file. 
•	I wanted to view all potentially hidden files, so I enabled that view and found a file named Money.

 <img width="1027" height="614" alt="image" src="https://github.com/user-attachments/assets/d1fff142-e00b-47af-9d36-47a5e15def1a" />


•	I used a tool called HxD and inserted the first file into it to find out that the real file type was .jpeg.
•	I renamed it to end with .jpeg and then opened it, and this image showed up.

 <img width="976" height="469" alt="image" src="https://github.com/user-attachments/assets/367747d7-6a3e-4080-97e0-210477d04a5f" />

•	I repeated the process with Goodjob Major and received this image.

 <img width="1045" height="537" alt="image" src="https://github.com/user-attachments/assets/40550912-fb52-410a-a5c2-113d957c0bad" />

•	I finally did the same thing for the last file and found out that it was an xlsx file. I used a tool called Square to view the file and received this.

 <img width="994" height="604" alt="image" src="https://github.com/user-attachments/assets/a448e956-1a30-46b3-9539-02157418e893" />

•	I went to Sheet 3 and clear formatted it to reveal any hidden information and found this. 
 <img width="943" height="645" alt="image" src="https://github.com/user-attachments/assets/d8840c8d-e501-4fd0-a4e3-1e1af8fdf84b" />

•	I copied the text and pasted it into cyberchef and received this message. 
<img width="984" height="779" alt="image" src="https://github.com/user-attachments/assets/112c9428-ce5a-43ba-8718-aa9365a424a6" />


The outcome of this project was very successful. I was able to successfully investigate and analyze the email. I was able to find the email service that was used by the malicious actor. I was able to continue investigations. I was also able to find out their true goals and how to find them. I learned how some important things that come with email analysis such as the from and reply to emails should match, and that the spf should usually be set to “pass” This project taught me a lot about email analysis and how important it is to go over every little detail. I can’t wait until I have the opportunity to perform this for a company.

