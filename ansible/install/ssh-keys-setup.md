### create a user on all machines ( controller & all targets )

	useradd arjun -m -d /home/arjun -s /bin/bash

### add user to sudoers for root previliges  on all machines ( all targets )

	echo -e 'arjun  ALL=(ALL)  NOPASSWD:  ALL' > /etc/sudoers.d/arjun

### genereate ssh keys for above user on contrller machine 

```
	1) switch to user ( su - arjun )
	2) run "ssh-keygen" command as user ( this will genereate ssh keys for the user ) 
```

### copy user ssh keys from ansible contrller to all target hosts

```
	1) on ansible controller machine
		cd /home/arjun/.ssh 
		cat id_rsa.pub (copy the content)
```
```
	2) on all taget machines
		   swith to the user ( su - arjun )
		   mkdir -p /home/arjun/.ssh
		   touch /home/arjun/.ssh/authorized_keys
		   chmod -R 700 /home/arjun/.ssh
		   vi /home/arjun/.ssh/authorized_keys  (enter the copied contet of id_rsa.pub from controller & save the file)
```	
	

