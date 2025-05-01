Here are the commonly used `scp` (secure copy) commands for transferring files between your local machine and a remote EC2 instance (both directions):

---

### ✅ **From EC2 (Remote) to Local:**

```bash
scp -i /path/to/key.pem ec2-user@<EC2-PUBLIC-IP>:/remote/path/to/file /local/destination/path
```

**Example:**
```bash
scp -i ~/keys/my-ec2-key.pem ec2-user@3.120.45.67:/home/ec2-user/data.txt ~/Downloads/
```

---

### ✅ **From Local to EC2 (Remote):**

```bash
scp -i /path/to/key.pem /local/path/to/file ec2-user@<EC2-PUBLIC-IP>:/remote/destination/path
```

**Example:**
```bash
scp -i ~/keys/my-ec2-key.pem ~/Documents/app.zip ec2-user@3.120.45.67:/home/ec2-user/
```

---

### ⚠️ Notes:
- Replace `ec2-user` with the correct username (`ubuntu` for Ubuntu instances).
- Ensure the destination directory has the right permissions.
- `-i` flag is for your PEM private key used to access the EC2 instance.
- If you're copying **directories**, add `-r`:

```bash
scp -i /path/to/key.pem -r /local/folder ec2-user@<EC2-IP>:/remote/path/
```

Would you like a quick script to automate this with variables?
