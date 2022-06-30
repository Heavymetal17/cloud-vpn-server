# cloud-vpn-server
bypassing network restrictions without drawbacks 

### Universities usually put in restrictions to block access the websites they feel for whatever causes lets bypass them for fun
_did this method in jan 2022 and my bad writing it after 6 months my main contribution was explaning for windows user(I have forgotten most part of that) and to save credits on vm._

 but with all restrictions they keep on adding amoung all the ports being blocked they do not block port 80 (http) and 443(https)
 while even port 22 is blocked you cannot ssh anywhere even  can’t push commits to a remote repo as GitHub authentication has shifted to ssh.
 
 use of vpn is costly(if you can do it for free why not) if using paid version for fast speed and // and I really dont remember weather we used to get ping n torrent 
 anyway here we are
 
 create a vm 
 Head over to the Azure portal to create a virtual machine. Follow these steps: Create a resource -> Compute -> Virtual Machine. Fill in the necessary details. A few things you need to be careful about are region, size, and image.

A standard B1s size is going to be good enough and last around 11 months using free credits. Now choose the closest region where the said size is available, which in my case was South-East Asia. A bigger (aka more costly) size would probably be available in Indian regions. Also, I choose to go with a Debian 11 image.

Make sure to generate the ssh key pair for authentication and put the details under the administrator account section. You can generate ssh key pair using the following command.

$ ssh-keygen -m PEM -t rsa -b 4096

This will generate a public-private key pair. Now choose the use existing public key option and fill in the username and contents of the generated public key (.pub file)

Keep the defaults in next sections and create the Virtual Machine.

Once the VM is ready, head to its overview and assign it a DNS name (Under essentials section). Also under settings->networking add a new inbound port rule to open either port 80 or 443.

Now you can ssh into the vm using $ ssh -i path/to/privatekey user@host_address.

the above steps need to be dne in putty if using on windows
now install openvpn server once sshes on remote machine

https://anjaygoel.github.io/posts/IIT-KGP-Bypass-Internet-Restrictions/

the important thing is to stop vm running when not requires that will save your credits.
