This is a collection of apps:
*Generate SSH Key pair for DigitalOcean* - this will dynamically generate private and public key pairs of your specified strength within the app.
*Digital Ocean SSH Keys Actions* - This app will add/remove keys within DigitalOcean.
*DigitalOcean Droplet Actions* - This app will create or destroy the specified droplet on DigitalOcean.

The provided example playbook, DigitalOcean Example, goes through an example flow of:

Hitting the HTTPLink Trigger -> Generate SSH Key pair for DigitalOcean

`This will output a dynamically generate Private/Public Key Pair`

Generate SSH Key pair for DigitalOcean -> Digital Ocean SSH Keys Actions

`This is done to add the generated SSH Key to DigitalOcean`

Digital Ocean SSH Keys Actions > DigitalOcean Droplet Actions

`The Action app creates a droplet of your size and choosing on Digital Ocean and returns the IP address.`

DigitalOcean Droplet Actions > SSH Client

`The IP address from the DigitalOcean Droplet Actions is passed over to the SSH Client`
`The private key generated by Generate SSH Key pair for DigitalOcean is also passed into the SSH Client app`
`Within SSH Client, the command cat /etc/password is ran`

SSH Client > DigitalOcean Droplet Actions

`The DigitalOcean Droplet Actions app then destroys the created droplet.`

DigitalOcean Droplet Actions > DigitalOcean SSH Keys Actions

`The DigitalOcean SSH Keys Actions removes the Public SSH Key that was added to DigitalOcean.`

This flow can be enhanced to be used for, malware detetonation, or remote reconnaissance of an adversary or infrastructure. 