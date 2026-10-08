Linux Troubleshooting – Incident Report

Issue Description

The production server experienced performance and service-related issues. The application was slow, and system resources such as CPU, memory, and disk usage were investigated. Failed services and system error logs were also checked.

The objective was to identify the root cause, resolve the issue, and verify that the system was working correctly.

Investigation Steps

The following troubleshooting steps were performed:

Checked the current logged-in user.
Checked the hostname of the server.
Checked system uptime and load average.
Checked disk usage.
Checked memory usage.
Identified CPU-consuming processes.
Identified memory-consuming processes.
Checked failed services.
Checked recent error logs.
Investigated large directories in the home folder.
Checked Nginx service status and configuration.
Verified the system after corrective actions.

Commands Used---------------

Check Current User
whoami

Check Hostname
hostname

Check System Uptime
uptime

Check Disk Usage
df -h

Check Memory Usage
free -h

Monitor Processes and CPU Usage
top

Find Top CPU-Consuming Processes
ps aux --sort=-%cpu | head

Find Top Memory-Consuming Processes
ps aux --sort=-%mem | head

List Failed Services
systemctl --failed

View Latest Error Logs
journalctl -p err -n 20

Find Largest Directories in Home Folder
du -sh ~/* | sort -hr | head

Check Nginx Status
sudo systemctl status nginx

Test Nginx Configuration
sudo nginx -t

Restart Nginx
sudo systemctl restart nginx

Check Nginx Logs
sudo journalctl -u nginx -n 50

Findings-----------------

During the investigation:

CPU usage was checked and the processes consuming the most CPU were identified.
Memory usage and memory-consuming processes were checked.
Disk usage was checked using df -h.
Failed services were identified using systemctl --failed.
Recent system errors were checked using journalctl.
Large directories in the home folder were identified.
Nginx service status and configuration were verified.

The investigation helped identify the system resources and services that required attention.

Root Cause

The root cause was identified by analyzing system resource usage, service status, and error logs.

The main contributing factors identified during troubleshooting were:

High resource consumption by processes.
Insufficient available disk space or unnecessary files.
Service or application errors.
Configuration or permission issues where applicable.
Resolution

The following corrective actions were performed as required:

Identified and investigated high CPU-consuming processes.
Identified memory-consuming processes.
Removed unnecessary files after verification.
Checked and corrected service issues.
Validated Nginx configuration before restarting.
Restarted affected services when required.
Reviewed system and application logs.
Verified system resources after corrective actions.
Verification

After applying the corrective actions, the system was verified using:

uptime
free -h
df -h
systemctl --failed

Nginx was also verified using:

sudo systemctl status nginx
sudo nginx -t

The relevant services and system resources were checked again to confirm that the issue was resolved.

Lessons Learned
Always collect evidence before making changes in a production environment.
Check CPU, memory, and disk usage during performance troubleshooting.
Use system logs to identify the root cause of service and application failures.
Test configuration files before restarting services.
Avoid unnecessary or unsafe commands in production.
Do not use excessive permissions such as chmod 777 unless there is a specific and justified requirement.
Monitor disk, CPU, memory, and service health regularly.
Document the issue, root cause, resolution, and verification steps for future incidents.
Repository Structure
linux-troubleshooting-machine-test/
│
├── README.md
│
├── answers/
│   ├── part1.md
│   ├── part2.md
│   └── part3.md
│
└── screenshots/
    ├── cpu.png
    ├── memory.png
    ├── disk.png
    ├── services.png
    └── logs.png
Conclusion

The troubleshooting process followed a structured approach:

Identify → Investigate → Collect Evidence → Find Root Cause → Resolve → Verify → Document

This approach helps DevOps engineers troubleshoot Linux production issues safely and systematically.