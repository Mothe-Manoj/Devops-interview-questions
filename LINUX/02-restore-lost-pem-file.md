### Can you restore a lost PEM file? If not, how can you still access the EC2 instance?


No, you cannot restore a lost PEM file — it’s not stored on AWS or recoverable.
However, you can regain access by using a workaround: create a new key pair, attach it to the instance via a temporary EC2 rescue process, and restore SSH access.

### Step 1: Create a new key pair
``` 
aws ec2 create-key-pair --key-name new-key --query 'KeyMaterial' --output text > new-key.pem
chmod 400 new-key.pem
```

### Step 2: Stop the affected instance

``` aws ec2 stop-instances --instance-ids i-xxxxxxxxxxxxxxx```

### Detach the root EBS volume from the stopped instance

- Go to EC2 > Volumes
- Find the volume attached to your instance (usually /dev/xvda)
- Detach it

### Step 4: Attach the volume to a temporary (working) instance

### Step 5: SSH into the temporary instance

``` 
sudo mkdir /mnt/recovery
sudo mount /dev/xvdf1 /mnt/recovery
```

Edit the authorized_keys file on the broken instance's volume:

``` sudo nano /mnt/recovery/home/ec2-user/.ssh/authorized_keys ```

Add the public key from your new key pair (new-key.pub)


### Step 6: Detach the volume from the  instance
### Step 7: Start the original instance and SSH with new key

## Prevention Tips:

- Always back up PEM files in a secure location (like a password manager).
- Create a secondary user with a different key for backup access.
- Use EC2 Instance Connect for temporary browser-based access (only works for Amazon Linux 2+ and enabled roles).