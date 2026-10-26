
This is project to monitor and protect a network perimeter using a generted firewall logs

**TASK 1:Examine the firewall logs. Which IP address is performing the port scan?**

I opened the file and look carefull into the logs, i found some ip of interest as they sent traffics to an ip address using different port number . This lead to a port scan suspicion as the attacker are looking for a open/weak port in the network shown  in the screenshot below:

<img width="382" height="314" alt="Image" src="https://github.com/user-attachments/assets/d51b1f7c-39b6-40bd-8b12-c8bb05aa83a2" />


As shown  ip address 203.0.113.10 try send traffic to with different port such 23 ,25 .

**TASK 2: In the WAF Logs, which single source IP is responsible for all the blocked web attacks?**

I opened the  file and ananlyse the log to look  for the IP responsible for block web attack as shown below in the screenshot below: THE IP IS 198.51.100.12.

<img width="458" height="292" alt="Image" src="https://github.com/user-attachments/assets/4b922ef9-8b65-44fb-a2d9-ea50b41d45fe" />

**TASK 3: In the VPN logs, how many brute-force attempts failed?**

I opeend the file and search for the Failed_AUTH to investigate the log and it display a total of 90 failed authenticatuon which suspect a brute force attack as shown below:

<img width="470" height="349" alt="Image" src="https://github.com/user-attachments/assets/e6494cb8-0913-459e-b685-f864154c4b4a" />

**TASK 4: Which suspicious IP address was found attempting the brute-force attack against the VPN gateway?**

I opened the same file and noticed that f ailed_auth came from a certain IP with no user; every instance goes to an internal IP with different usernames at different instances. this ip =45.137.22.13 as shown below:

<img width="433" height="281" alt="Image" src="https://github.com/user-attachments/assets/af2e6d38-ea5a-4885-96d3-af1429ab73ba" />

As seen above, the ip sent traffic with differnt username.

**TASK 5: As a new security analyst, you have been tasked with reviewing one month of perimeter logs to determine what techniques the adversary used, and whether they succeeded in breaching the perimeter.
Examine the firewall logs. What external IP performed the most reconnaissance?**

In this task, i  need to loog for the IP with the highest among of scan using the menual method (COMMAND LINE). I will analyze the firewall logs for any block requests using the command **_**_**cat firewall.log | grep “BLOCK” |**_ head**_** to read just the top of the log file and the blocked requests indicate that an external IP has been found probing against internal IPs using various ports (22,23,21,445,4444) this reveal the IP Addresss is **203.0.113.45**
<img width="418" height="180" alt="Image" src="https://github.com/user-attachments/assets/d19807c4-aa81-4263-86c8-6238683ac737" />

**TASK 6: In the firewall log, Which internal host was targeted by scans?**

In this task, i make use of the same command _**cat  firewall.log | grep "BLOCK"|  head**_  , and the analyses show the internal IP that is most targeted as shown in the screenshot below: _10.0.0.20_

<img width="412" height="181" alt="Image" src="https://github.com/user-attachments/assets/d3e1f72f-f1ad-4c16-9415-af6540f125e2" />

TASK 7: Which username was targeted in VPN logs?

In this task, i open the vpn_auth.log using the  _**cat  vpn_auth.log  | grep 203.0.113.45**_  Which reveal the  username  targeted in VPN logs as _**svc_backup**_
<img width="470" height="257" alt="Image" src="https://github.com/user-attachments/assets/eb13ebe4-ff86-45b0-acf2-6735568fbef2" />

**TASK 8: What internal IP was assigned after successful VPN login?**

From the same output above, i scroll down to  to find the internal IP  assigned after successful VPN login which is shown below as _**10.8.0.23**_ 
<img width="387" height="245" alt="Image" src="https://github.com/user-attachments/assets/5b821f18-cc4c-4c1f-8751-2341994d4350" />

**TASK 9: Which  port was used for lateral SMB attempts**

In this task, we used the same output as  abive to searcg for the IP with SMB port number 45 as shown in the screenshiot below:
<img width="481" height="307" alt="Image" src="https://github.com/user-attachments/assets/a8af8a3e-590e-4025-8d01-4c5a453891d9" />

**TASK 10: In the IDS logs, which host beaconed to the C2?**
In this task i cat the file "ids_file .log and grep the C2 to analyse the  log with the command ca_**t alert_file.log |grep c2 | head**_   this reveal the IP  to be 10.0.0.60
as shown in the screenshot below:

<img width="469" height="268" alt="Image" src="https://github.com/user-attachments/assets/164123ad-21cb-456a-bf79-64ddc45fd3c5" />

TASK 11: During the investigation, which IP was observed to be associated with C2?
In this task , in the output above  the C2 IP that  ip 10.0.0.60 was send the traffIc to which was  IP 198.51.100.77 as shown in the screenshot below:

_cat ids_alerts.log | grep -n “10.0.0.60” | cut -d’ ‘ -f6,7,8,9,10,19,22,23 | uniq -c | sort -nr | head_

<img width="482" height="290" alt="Image" src="https://github.com/user-attachments/assets/be30636d-f06c-419a-93d4-469c38d3ba38" />

TASK 12: Which host showed the exfiltration attempts?

Now that i  have identified the C2 communication and examined other alerts against suspicious IPs, i then investigate if there are any indicators of data being exfiltrated from our network. i  will apply a filter on the compromised hosts and examine the traffic originating from those to an external destination IP. making  use the _**command cat firewall.log | grep “198.51.100.77” | cut -d’ ‘ -f5,6,7 | uniq | sort.**_
As shown  below:

<img width="446" height="368" alt="Image" src="https://github.com/user-attachments/assets/a47590be-1d88-4304-adf9-a908fe1a9d54" />

Conclusion:

Monitoring the perimeter means using firewalls, intrusion detection/prevention systems (IDS/IPS), and access control to examine and limit exposure and enforce security rules. This  allows the security analysts to:
Spot early-stage attacks like port scans or brute-force attempts.
Detect misconfigurations that leave sensitive services exposed.
Identify outbound traffic anomalies that may indicate malware or data exfiltration.

