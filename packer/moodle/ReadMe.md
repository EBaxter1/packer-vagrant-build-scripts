# Pre-steps to take
In order for the host system to send environment variables to the guest Vm being built you have to explicitly declare them on the command line before you issue a ```Packer build``` command.

This is how we are passing passwords in securely.

[https://www.packer.io/docs/templates/user-variables.html](https://www.packer.io/docs/templates/user-variables.html)

### What we need to set username and passwords securely in Packer
1) Issue the command inside of the moodle folder, ```cp variables-sample.json variables.json```
    1) The ```variables.json``` file contains key value pairs of variables and passwords to be passed into the provisioner shell script.
    1) This renames the file ```variables-sample.json``` to ```variables.json```  (there is an entry in the .gitignore so you cannot accidentially git push your passwords).
1) Edit the ```variables.json``` file replacing default values with your own    
1) Issue the command ```packer build --var-file=./variables.json ubuntu16043-moodle-32.json``` to begin the install with password and usernames properly seeded
    1) This way we can securely build the entire [Moodle](http://moodle.org "Moodle") system, deploy it and when building it pass in passwords via environment variables

### Future Features to add

+  Add Brotli compression for Nginx out of the box
+  Modify Gzip compression per different file types
+  Add SSL/TLS config out of box natively with Self-Signed Cert and 443 support using HTTP/2
+  Commented out for development: but add support for Letsencrypt fully automated install provided via .ini file for production
+  Import profiles, themes, and plugins automatically during install