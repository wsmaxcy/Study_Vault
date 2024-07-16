[[SSH]] means Secure Shell and can also be enumerated

## Enumeration
Can go and try to find out what version that is running. That is basically it with SSH. The second that we attempt to make an login attempt is an exploitation part of the course.

## Ways to work
`ssh <ip-address>`

### Funky stuff
old boxes might need to include the key exchange. This does come up occasionally.

`Unable to negotiate with <ip-address> port 22: no matching key exchange method found. Their offer: diffie-helman-group-exchange-sha1,diffie-hellman-group1-sha1`

###### What does this mean?
the way to connect would be this way...
`ssh <ip-address> -oKexAlgorithms=+diffie-hellman-group1-sha1`

This will then give you the following note
`Unable to negootiate with <ip-address> port 22: no matching cipher found. Their offer: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc,rijndael128-cbc,rijndael192-cbc,rinjdael256-cbc,rijndael-cbc@lysator.liu.se`

then, type in this command
`ssh <ip-address> -oKexAlgorithms=+diffie-hellman-group1-sha1 -c aes128-cbc`

This will think allow for connection. It will then ask for a password. Why attempt? sometimes a banner is exposed and it will show more information to get. Can show company info, target info, etc.