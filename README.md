**EC2 Lost SSH Key Recovery – AWS Troubleshooting Lab

This project simulates a real-world AWS scenario where the SSH key to an EC2 instance is lost. Instead of terminating the instance or rebuilding it, I recovered access by working directly with the attached EBS volume.

* What This Covers
	•	Mounting and working with EBS volumes from a rescue EC2
	•	Manually updating the authorized_keys file to restore SSH access
	•	Real troubleshooting steps you’d take in a Cloud Support role

* Steps I Took
	1.	Created an EC2 instance with a new key pair and confirmed SSH access.
	2.	Simulated a lost key by deleting the private key from my system.
	3.	Stopped the instance and detached its root EBS volume.
	4.	Launched a temporary “rescue” EC2 instance and attached the detached volume to it.
	5.	Mounted the broken volume:
