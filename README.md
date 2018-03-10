# Steps
* Load the recipe into PiBakery
* Burn to SDCard and put card into Pi
* Wait for pi to boot and get setup
  * You can `ssh pi@raspberrypi.local` when its ready; it'll take a couple of minutes
* Change hostname `sudo vim /etc/hostname` and `sudo vim /etc/hosts`
* Change password `passwd`

! Add all features these to the recipe if possible...
* `sudo apt-get update` and `sudo apt-get upgrade`
* `sudo reboot`
* Then `ssh pi@<newhostname>.local`
* `sudo apt-get install git`
* Install node using https://github.com/audstanley/NodeJs-Raspberry-Pi if required
* Setup an 'application' user to run the node apps:
  * `sudo useradd application`
  * `sudo passwd application` - then set password
  * `sudo mkdir /home/application`
  * `sudo chown /home/application application`
  * `sudo cp .bashrc /home/application/.bashrc`
* Install and auto-run pi-monitor (As application user)
  * `git clone https://github.com/sdclibbery/pi-monitor.git`
  * `cd pi-monitor`
  * `npm install`
  * `chmod +x cron.sh`
  * Add `* * * * * /home/application/pi-monitor/cron.sh >> /home/application/cron-pi-monitor.log 2>&1` with `crontab -e`
