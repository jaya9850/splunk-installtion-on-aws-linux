# splunk-installtion-on-aws-linux
step by step guide for this 
cd /opt/
wget -O splunk-9.0.1-82c987350fde-Linux-x86_64.tgz "https://download.splunk.com/products/splunk/releases/9.0.1/linux/splunk-9.0.1-82c987350fde-Linux-x86_64.tgz"


tar xvzf splunk-9.0.1-82c987350fde-Linux-x86_64.tgz
cd splunk/
cd bin/


sudo ./splunk start --accept-license
sudo ./splunk enable boot-start
http://3.237.40.224:8000
