# Linux-Sever-Setup-Using-CLI
# Generate a key pair to securely access the EC2 instance via SSH, and save the private key to your local computer
aws ec2 create-key-pair --key-name LinuxEC2KP --query 'KeyMaterial' --output text > LinuxEC2KP.pem
# Modify the PEM file permissions to read-only to prevent unintentional modifications.
chmod 400 LinuxEC2KP.pem
# Create a Security Group to allow HTTP and SSH from everywhere
aws ec2 create-security-group --group-name Allow-http_SSH-SG --description " Allow HTTP and SSH connection to EC2 instance"
# use this command to get the group-ID which you will use it later to add inbound rules
aws ec2 describe-security-groups --filters "Name=group-name,Values=Allow-http_SSH-SG"
# Add Inbound Rules to Security Group
aws ec2 authorize-security-group-ingress --group-id “replace me with the group-id” --protocol tcp --port 22 --cidr 0.0.0.0/0
aws ec2 authorize-security-group-ingress --group-id “replace me with the group-id” --protocol tcp --port 80 --cidr 0.0.0.0/0

