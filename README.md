# Linux-Sever-Setup-Using-CLI
# Generate a key pair to securely access the EC2 instance via SSH, and save the private key to your local computer
aws ec2 create-key-pair --key-name LinuxEC2KP --query 'KeyMaterial' --output text > LinuxEC2KP.pem
# Modify the PEM file permissions to read-only to prevent unintentional modifications.
chmod 400 LinuxEC2KP.pem
