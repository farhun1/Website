---
title: "Fifty Useful Linux Commands Part Two"
date: 2023-09-04
url: /Fifty-Useful-Linux-Commands-Part-Two/
description:
categories: [Commands]
draft: false
---
## Introduction

After part one we will look into more linux commands to enhance our use of commandline and troubleshoot any problems.

1. **ln** - Create hard or symbolic links to files.
   ```bash
   ln -s /path/to/source/file link_name
   ```

2. **uptime** - Display system uptime and load averages.
   ```bash
   uptime
   ```

3. **who** - Display information about logged-in users.
   ```bash
   who
   ```

4. **whatis** - Display one-line manual page descriptions.
   ```bash
   whatis command_name
   ```

5. **chroot** - Change the root directory for a command.
   ```bash
   chroot /new/root /bin/bash
   ```

6. **which** - Display the path of an executable.
   ```bash
   which command_name
   ```

7. **uptime** - Display system uptime and load averages.
   ```bash
   uptime
   ```

8. **nmcli** - Command-line client for NetworkManager.
   ```bash
   nmcli connection show
   ```

9. **rsync** - Sync files and directories between systems.
   ```bash
   rsync -avz source/ destination/
   ```

10. **cut** - Remove sections from lines of files.
   ```bash
   cut -d, -f2 file.csv
   ```

11. **sed** - Stream editor for text manipulation.
   ```bash
   sed 's/old_text/new_text/' file.txt
   ```

12. **awk** - Text processing tool for data extraction.
   ```bash
   awk '{print $1}' file.txt
   ```

13. **sort** - Sort lines of text files.
   ```bash
   sort file.txt
   ```

14. **uniq** - Remove duplicate lines from sorted files.
   ```bash
   sort file.txt | uniq
   ```

15. **diff** - Compare files line by line.
   ```bash
   diff file1.txt file2.txt
   ```

16. **tar** - Archive and compress files.
   ```bash
   tar -cvzf archive.tar.gz directory/
   ```

17. **crontab** - Schedule repetitive tasks using cron.
   ```bash
   crontab -l
   crontab -e
   ```

18. **wget** - Download files from the internet.
   ```bash
   wget https://example.com/file.zip
   ```

19. **curl** - Transfer data to/from servers.
   ```bash
   curl -O https://example.com/image.jpg
   ```

20. **zip** and **unzip** - Create and extract compressed zip archives.
   ```bash
   zip archive.zip file1.txt file2.txt
   ```

21. **ps** - Display information about running processes.
   ```bash
   ps aux
   ```

22. **kill** - Terminate processes.
   ```bash
   kill process_id
   ```

23. **killall** - Terminate processes by name.
   ```bash
   killall process_name
   ```

24. **nice** - Adjust process priority.
   ```bash
   nice -n 10 command
   ```

25. **renice** - Change the priority of a running process.
   ```bash
   renice -n 5 -p process_id
   ```

26. **whereis** - Locate the binary, source, and manual page files for a command.
   ```bash
   whereis command_name
   ```

27. **alias** - Create shortcut commands.
   ```bash
   alias ll='ls -al'
   ```

28. **file** - Determine file type.
   ```bash
   file file.txt
   ```

29. **df** - Display disk space usage.
   ```bash
   df -h
   ```

30. **du** - Display file and directory space usage.
   ```bash
   du -sh /var
   ```

31. **quota** - Manage disk quotas for users.
   ```bash
   quota -u user
   ```

32. **ssh-keygen** - Generate SSH key pairs.
   ```bash
   ssh-keygen -t rsa
   ```

33. **ssh-copy-id** - Copy SSH keys to a remote server.
   ```bash
   ssh-copy-id user@remote_server
   ```

34. **scp** - Securely copy files between systems.
   ```bash
   scp file.txt user@remote_server:/path/to/destination/
   ```

35. **ping** - Check network connectivity.
   ```bash
   ping google.com
   ```

36. **traceroute** - Trace the route packets take to a destination.
   ```bash
   traceroute google.com
   ```

37. **netstat** - Display network connections, routing tables, interface statistics, masquerade connections, and multicast memberships.
   ```bash
   netstat -tuln
   ```

38. **ss** - Display socket statistics.
   ```bash
   ss -tuln
   ```

39. **route** - Display and manipulate IP routing table.
   ```bash
   route -n
   ```

40. **hostname** - Display or set the system's host name.
   ```bash
   hostname
   ```

41. **history** - View command history.
   ```bash
   history
   ```

42. **shutdown** and **reboot** - Shutdown or restart the system.
   ```bash
   sudo shutdown -h now
   sudo reboot
   ```

43. **file** - Determine file type.
   ```bash
   file file.txt
   ```

44. **lsblk** - List block devices.
   ```bash
   lsblk
   ```

45. **parted** - Disk partitioning tool.
   ```bash
   parted /dev/sdX
   ```

46. **nmcli** - Command-line client for NetworkManager.
   ```bash
   nmcli connection show
   ```

47. **useradd** and **userdel** - Add and delete user accounts.
   ```bash
   sudo useradd newuser
   sudo userdel olduser
   ```

48. **groupadd** and **groupdel** - Manage user groups.
   ```bash
   sudo groupadd mygroup
   sudo groupdel mygroup
   ```

49. **w** - Show who is logged on and what they are doing.
   ```bash
   w
   ```

50. **chsh** - Change login shell.
    ```bash
    chsh -s /bin/bash username
    ```

## Conclusion

With these 50 additional Linux commands and examples, you can expand your knowledge and enhance your proficiency in managing and working with Linux systems. These commands cover a wide range of tasks, from text processing and file manipulation to network diagnostics and system administration. Continue to explore and experiment with these commands to become a more skilled Linux user.