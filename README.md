# Steps
* Load the recipe into PiBakery
* Burn to SDCard and put card into Pi
* :-| Have to use keyboard/monitor to set wifi country :-(
  nb this goes into /etc/wpa_supplicant/wpa_supplicant.conf as country=GB
* Wait for pi to boot and get setup
  * You can `ssh pi@raspberrypi.local` when its ready; it'll take a couple of minutes
* Change hostname `sudo vim /etc/hostname` and `sudo vim /etc/hosts`
* Change password `passwd`
* Update
 * `sudo apt-get update` and `sudo apt-get upgrade`
 * `sudo reboot`
* Then `ssh pi@<newhostname>.local`
* `sudo vim /etc/apt/apt.conf.d/50unattended-upgrades`
  * Add `"origin=Raspbian,codename=${distro_codename},label=Raspbian";` and setup auto reboot and log to syslog
   ? Maybe have a copy of the config file in this repo...
! Add all features to the recipe if possible...
* `sudo apt-get install git`
* Install node using https://github.com/audstanley/NodeJs-Raspberry-Pi if required
`sudo wget -O - https://raw.githubusercontent.com/audstanley/NodeJs-Raspberry-Pi/master/Install-Node.sh | sudo bash`
* Setup an 'application' user to run the node apps:
  * `sudo useradd application`
  * `sudo passwd application` - then set password
  * `sudo mkdir /home/application`
  * `sudo chown application /home/application`
  * `sudo cp .bashrc /home/application/.bashrc`
  * `sudo chsh -s /bin/bash application`
* Install and auto-run pi-monitor (As application user)
  * `git clone https://github.com/sdclibbery/tradr.git`
  * `git clone https://github.com/sdclibbery/pi-monitor.git`
  * `cd pi-monitor`
  * `npm install`
  * `chmod +x cron.sh`
  * Add `* * * * * /home/application/pi-monitor/cron.sh >> /home/application/cron-pi-monitor.log 2>&1` with `crontab -e`
