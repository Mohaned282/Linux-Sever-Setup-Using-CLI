# Linux-Sever-Setup-Using-CLI
# create pulblic key to access EC2 instance via SSH
aws ec2 create-key-pair --key-name LinuxEC2KP --query 'KeyMaterial' --output text > LinuxEC2KP.pem
# change the pem permission to be read olny, no one we be anble to change the pem key file
chmod 400 LinuxEC2KP.pem
