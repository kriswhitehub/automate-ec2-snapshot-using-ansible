## Automating EC2 EBS Snapshot with Ansible

![AmazonEC2](images/amzonec2.png)        ![Ansible](images/ansiblelogo.png)             ![EBS](images/ebslogo.jpg)



1. Create EC2 Instance.
 ![AmazonEC2](images/snapshot-step-1.png)


2. Collect Volume ID.
 ![AmazonEC2](images/snapshot-step-3.png)


3. Verify Snapshots.
 ![AmazonEC2](images/snapshot-step-4.png)


4. snapshot.yaml

  ```bash

   ---
- name: Snapshot EBS and Launch New EC2 Instance
  hosts: localhost
  gather_facts: no
  vars:
    ansible_python_interpreter: /usr/bin/python3.9  # Adjust the path to your Python interpreter
  tasks:
    - name: AWS Snapshot
      ec2_snapshot:
       aws_access_key: "key"
       aws_secret_key: "key"
       region: us-east-1
       volume_id: vol-02c4ffe165d750381
       description: 11th-of-February-2024-Snapshot
   
   ```

5. Playbook Results.
![AmazonEC2](images/snapshot-step-6.png)


6. Validate Snapshot.
![AmazonEC2](images/snapshot-step-7.png)
