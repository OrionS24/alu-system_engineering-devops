# SSH Remote Connection Script

## Description
A simple Bash script that connects to a remote server using SSH with a private key for authentication.

## Prerequisites
- An SSH key pair generated (`ssh-keygen -t ed25519`)
- The private key must be placed at `~/.ssh/school` on your local machine
- Access permissions granted on the remote server for your public key

## Usage
Make the script executable, then run it:

```bash
chmod +x connect.sh
./connect.sh
```

## What it does
The script connects to a remote Ubuntu server (`184.72.205.5`) via SSH, authenticating using the private key located at `~/.ssh/school` instead of a password.

## Security Note
This script references a private key file (`~/.ssh/school`) but does **not** include the key itself. Never commit private key files to version control. Each user must generate and place their own key locally before running this script.

## Author
ORION SERUVUMBA
