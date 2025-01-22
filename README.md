# logrotate
Automating Log Management with Logrotate
<p align="center">
    <img width="1010px" src="https://miro.medium.com/v2/resize:fit:1400/format:webp/1*if-g3urBDTdnvuspquZnoA.png"/>
</p>

# Steps to Configure [Logrotate](https://medium.com/@ajm_joha/automating-log-management-with-logrotate-eb76c99a4e3f):
* Install Logrotate: Most Linux distributions include Logrotate by default. If not installed, you can add it using:
```
sudo apt install logrotate      # For Debian/Ubuntu
sudo yum install logrotate      # For CentOS/RHEL
```
* Check Logrotate Configuration: Logrotate’s main configuration file is located at:
```
/etc/logrotate.conf
```
* Additionally, individual service-specific configurations are often found in:
```
/etc/logrotate.d/
```
* **Create or Edit a Logrotate Configuration File:** To manage a specific log, create a configuration file in `/etc/logrotate.d/`. For example, to manage `/var/log/boot` , create:
```
sudo nano /etc/logrotate.d/bootlog
```
* Add the following content:
```
/var/log/boot {
    weekly
    rotate 4
    compress
    delaycompress
    missingok
    notifempty
    create 0640 root utmp
}
```

* **weekly:** Rotate logs weekly.
* **rotate 4:** Keep the last 4 log files.
* **compress:** Compress old logs.
* **delaycompress:** Delay compression by one cycle.
* **missingok:** Ignore errors if the log file is missing.
* **notifempty:** Skip rotation if the log file is empty.

# Test Logrotate Configuration:
* Run the following command to test your configuration:
```
  sudo logrotate -d /etc/logrotate.conf
```
# Apply Logrotate Manually
* You can force Logrotate to run using:
  ```
  sudo logrotate -f /etc/logrotate.conf
  ```

  **Happy troubleshooting and enjoy your Linux experience! 🎉**
