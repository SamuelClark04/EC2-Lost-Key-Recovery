## EC2 Lost SSH Key Recovery – AWS Troubleshooting Lab

This project simulates a real world AWS scenario where the SSH key to an EC2 instance is lost. Instead of terminating the instance or rebuilding it, I recovered access by working directly with the attached EBS volume.

# What This Covers
	•	Mounting and working with EBS volumes from a Helper EC2
	•	Manually updating the authorized_keys file to restore SSH access
	•	Real troubleshooting steps you’d take in a Cloud Support role

# Steps I Took
	1.	Created an EC2 instance with a new key pair and confirmed SSH access.
	2.	Simulated a lost key by deleting the private key from my system.
	3.	Stopped the instance and detached its root EBS volume.
	4.	Launched a temporary “Helper2” EC2 instance and attached the detached volume to it.
	5.	Mounted the broken volume: sudo mount -t xfs -o nouuid /dev/xvdf1 /mnt/tempfix
 	6.  	Copied a valid public key into the EC2 user’s authorized_keys on the broken volume: sudo cp ~/.ssh/authorized_keys /mnt/tempfix/home/ec2-user/.ssh/authorized_keys
  	7.	Fixed the permissions and ownership.
	8.	Unmounted the volume, reattached it to the original instance, and started it back up.
	9.	Successfully SSH’d back in using the new key.

# Why I Did This

This was part of my hands-on AWS practice to build real support troubleshooting skills. I didn’t just follow a script, I broke things on purpose and had to figure out how to recover access like I would in a real support role.

# What I Learned
	•	How to mount volumes properly
	•	What to look for when troubleshooting EC2 access issues
	•	How to safely work with file permissions and SSH key injection
	•	Confidence working through problems 

