# Lab 4 – Working with Amazon Elastic Block Store (EBS)

## Author

* **Name**: HARIRAM R
* **Register Number**: 212224240050
* **Date of Submission**: 27.02.2026

---

## Objective

The objective of this experiment is to understand how Amazon Elastic Block Store (EBS) provides persistent block-level storage for EC2 instances. This lab focuses on creating and attaching an EBS volume, formatting and mounting it on an EC2 instance, storing data, and verifying data persistence after instance reboot.

---

## Prerequisites

* Basic understanding of cloud computing concepts
* AWS account or AWS Academy Lab access
* An existing EC2 instance (Amazon Linux 2 preferred)
* Basic knowledge of Linux commands

---

## Tools Used

* AWS Management Console
* Amazon EC2
* Amazon EBS
* SSH Client (Terminal / PuTTY)

---

## Tasks Performed

### Task 1: Explore Amazon EBS

Explore the Amazon EBS service through the EC2 dashboard. Observe different volume types such as General Purpose SSD (gp2/gp3), Provisioned IOPS SSD, Throughput Optimized HDD, and Cold HDD.

---

### Task 2: Create an EBS Volume

Create a new EBS volume in the same Availability Zone as the EC2 instance. Choose an appropriate size and volume type.

---

### Task 3: Attach EBS Volume to EC2 Instance

Attach the created EBS volume to the running EC2 instance as an additional block device.

---

### Task 4: Format the EBS Volume

Connect to the EC2 instance using SSH and format the attached volume with a file system (for example, ext4).

---

### Task 5: Mount the EBS Volume

Mount the formatted volume to a directory in the EC2 instance (for example, /data or /mnt/ebs).

---

### Task 6: Store Data in EBS Volume

Create files and directories inside the mounted EBS volume and store sample data.

---

### Task 7: Verify Data Persistence

Reboot the EC2 instance and verify that the data stored in the EBS volume is still available after reboot.

---

## Workflow (Student Explanation)

(Write the steps you followed in your own words)

1. The EC2 Dashboard was accessed through the AWS Management Console to explore the Amazon EBS volume types.
2. A new EBS volume was created by selecting the volume type, size, and the same Availability Zone as the EC2 instance.
3. The created EBS volume was attached to the running EC2 instance as an additional block device.
4. The attached volume was formatted using the ext4 file system and mounted to a directory in the EC2 instance.
5. Sample data was stored in the mounted volume, and after rebooting the instance, data persistence was verified successfully.

---

## Output Screenshots (Attach 3)

### Screenshot 1: EBS Volume Created


<img width="1919" height="1008" alt="Screenshot 2026-02-27 111450" src="https://github.com/user-attachments/assets/cf3a246c-ebe1-4db4-8b31-a6f134e0204b" />


---

### Screenshot 2: EBS Volume Attached to EC2

<img width="1914" height="1014" alt="Screenshot 2026-02-27 111653" src="https://github.com/user-attachments/assets/54538fe1-842c-45b6-9d81-68d445b44a8a" />


---

### Screenshot 3: Mounted Volume with Data

<img width="1919" height="1022" alt="Screenshot 2026-02-27 112450" src="https://github.com/user-attachments/assets/24554748-874c-4a8b-ab18-3b0dc8619011" />


---

## Result / Conclusion

This experiment demonstrated how Amazon EBS provides persistent storage for EC2 instances. By creating, attaching, formatting, and mounting an EBS volume, and by verifying data after reboot, the concept of durable block storage in the cloud was clearly understood.
