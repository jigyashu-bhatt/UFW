    Linux (Ubuntu/Debian):

   
        
        Use ufw (Uncomplicated Firewall)


![Screenshot from 2025-06-27 09-59-49](https://github.com/user-attachments/assets/b3c85284-fff2-486f-93aa-6c71a9400815)


sudo ufw status


📋 2. List Current Firewall Rules

sudo ufw status numbered

This lists active rules with indices.
🚫 3. Block Inbound Traffic on Port 23 (Telnet)

sudo ufw deny 23/tcp
![Screenshot from 2025-06-27 10-07-22](https://github.com/user-attachments/assets/e21d7803-68a8-4138-aa33-c827281640dc)


This blocks all incoming traffic on TCP port 23.
🧪 4. Test the Block Rule

    Local test (Linux):

telnet localhost 23
![Screenshot from 2025-06-27 10-07-55](https://github.com/user-attachments/assets/1e2b012b-23ad-4772-a587-f15963a2fc3f)


    You should see “Connection refused” or timeout.

    Remote test:
    Try connecting from another machine using telnet <ip> 23

✅ 5. Allow SSH (Port 22) – Important for remote access

sudo ufw allow 22/tcp
![Screenshot from 2025-06-27 10-08-17](https://github.com/user-attachments/assets/a2db3954-013d-47e4-a1a6-d9e0a69e4773)


This ensures you don't get locked out when connected via SSH.
♻️ 6. Remove the Test Rule (Optional Cleanup)

sudo ufw delete deny 23/tcp
![Screenshot from 2025-06-27 10-08-28](https://github.com/user-attachments/assets/c3cc20c9-98b6-47c1-87a0-639610723527)


Or if using numbered rules:

sudo ufw status numbered
sudo ufw delete [rule_number]

📝 7. Documented Commands Summary
Action	Command
Check status	sudo ufw status numbered
Block Telnet	sudo ufw deny 23/tcp
Allow SSH	sudo ufw allow 22/tcp
Delete block	sudo ufw delete deny 23/tcp or by number
📚 8. How Firewalls Filter Traffic – Summary

Firewalls monitor and control incoming/outgoing network traffic based on predefined rules. They operate by:

    Allowing or blocking traffic on specific ports/IPs.

    Filtering packets based on protocol (TCP/UDP).

    Preventing unauthorized access to systems and services.

    Enforcing security policies to reduce attack surfaces.

    Example: Blocking port 23 protects against unencrypted Telnet attacks.
