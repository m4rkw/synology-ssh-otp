# Synology SSH OTP

USE AT YOUR OWN RISK

## Installation

First install the script:

````
# mkdir /usr/local/bin
# cp otp /usr/local/bin/
# chmod 755 /usr/local/bin/otp
````

Enable it for specific users in /etc/ssh/sshd\_config:

````
Match User root
  ForceCommand /usr/local/bin/otp --login

Match User admin
  ForceCommand /usr/local/bin/otp --login
````

## Usage

If ~/.totp doesn't exist, login will simply proceed. To create your OTP seed
just execute:

````
$ otp
````

Scratch codes are stored in ~/.scratch and can only be used once.

If you want to exclude your local LAN from the OTP requirement:

````
$ echo '192.168.30.' > ~/.totp_home_network
````

Allow specific commands to negate the need for OTP:

````
$ echo 'ls -la' > ~/.totp_exclude_commands
