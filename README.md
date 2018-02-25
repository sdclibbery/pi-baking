# Steps
* Load the recipe into PiBakery
  ! to add to bakery recipe: vim package, do the apt get update/upgrade
* Burn to SDCard and put card into Pi
* Wait for pi to boot and get setup
  * You can `ssh pi@raspberrypi.local` when its ready; it'll take a couple of minutes
* Change hostname `sudo vim /etc/hostname` and `sudo vim /etc/hosts`
* Change password `passwd`
* `sudo apt-get update` and `sudo apt-get upgrade`
* `sudo reboot`
* Then `ssh pi@<newhostname>.local`
* `sudo apt-get install git` if required (note cloning my repo down was easier using https than ssh from github)
* Install node using https://github.com/audstanley/NodeJs-Raspberry-Pi if required
