# Investigating Windows
## TryHackMe Rooms

This is a challenge that is exactly what is says on the tin, there are a few challenges around investigating a windows machine that has been previously compromised.

Connect to the machine using RDP. The credentials the machine are as follows:

Username: Administrator
Password: letmein123!

## Questions

1. What is the version and year of the windows machine?
- Windows Server 2016.
> run > winver to find this.

2. Which user logged in last?
- Administrator
> Run PowerShell, Get-LocalUser | Select Name, Lastlogon
https://imgur.com/8BTJmOu

3. When did John Last log onto the system?
- 03/02/2019 5:48:32 PM

4. What IP does the system connecto to when it first starts?
- 10.34.2.3
>  --> You see this show up at the beginning, otherwise, you can first check the hosts file. This is found is C:\ > Windows > System32 > drivers > etc > hosts
> --> The hosts file shows some suspicion of DNS tampering, as google is found here, and many sites point toward the local host.
> --> From here, we can check the regedit (registry editor), and under HKEY_LOCAL_MACHINE > Software > Microsoft > Windows > Run, we should see a data value set to 10.34.2.3. 
https://imgur.com/a/sN3HrSb  - Hosts File
https://imgur.com/a/ARGulzg - Regedit evidence of initial IP connection

5. What two accounts had administrative privileges (other than the Administrator user)?
- Jenny, Guest.
> PowerShell command Get-LocalGroupMember -Group "Administrators"
https://imgur.com/a/GlXzk0z

6. What is the name of the scheduled task that is malicious?
- Clean File System
> Powershell > Get-ScheduledTask
https://imgur.com/a/l9HmLZ5

7. What file was the task trying to run daily?
- nc.ps1
> Assign clean file system to $task > $task = Get-ScheduledTask | Where TaskName -EQ "Clean File System"
>https://imgur.com/a/0o5hE9o

8. What port did this file listen locally for?
- 1348
https://imgur.com/a/0o5hE9o
> Can also be done through task scheduler

9. When did Jenny last logon?
- Never
> net User Jenny | findstr "logon"
https://imgur.com/a/UhdGBna

10. At what date did the compromise take place?
- 03/02/2019
> Check the date that the inetpub, TMP folders were added to C:\

11. During the compromise, at what time did Windows first assign special privileges to a new logon?
- 03/02/2019 4:04:49 PM
> Event viewer, custom view> custom range> events on> March 02, 2019, 4:00:00 PM to 4:30:00 PM.
> Filter it by Security logs, name the filter > pressing Ok will reveal the number of events that meet the criteria.
> Start from the bottom, scrolling up until we find a category "Security Group Management".

12. What tool was used to get Windows passwords?
- Mimikatz
> Head to the TMP directory, found in C:\ 
> Inside TMP, there will be several files - one of them called mim.exe and mim-out.
> Opening mim-out as a text file reveals the tool name "mimkatz".

13. What was the attackers external control and command servers IP?
- 76.32.97.132
> Head to the hosts file, C: > Windows > System32 > drivers > etc > hosts; open this with a text utility program (notepad, notepad++)
> Within this file, we can see google.com and www.google.com - this is suspicious as it is not necessary to put into the hosts file, as it can be accessed normally.
> ping google.com in cmd - if it matches the host file, then it will be a legitimate file. After pinging google.com, we can see that the addresses do not match.

14. What was the extension name of the shell uploaded via the servers website?
- .jsp
> Go to C:\ > inetpub > wwwroot > we can see that the shell extension is .jsp



15. What was the last port the attacker opened?
- 1337
> Firewall settings > inbounds rules > first rule (allow outside connections for development) > protocols and ports > 1337 can be found here.

16. Check for  DNS poisoning, what site was targeted?
- google.com
> We found the targeted site in the hosts file earlier - google.com
