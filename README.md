# backend_node_postgresql
RESTful backend to support PostgreSQL using Node.js and JS  
Step 1: upload the zip file into Rocky Linux 8.10 as below :

scp D:\jhu\New_Gemini_React_howTo\backend\gemini.zip root@192.168.56.103:\tmp
[root@localhost tmp]# pwd
/tmp
[root@localhost tmp]# ll
total 56
-rw-r--r--. 1 root root 48903 Dec 22 20:02 gemini.zip
[root@localhost tmp]# unzip gemini.zip
[root@localhost tmp]# cd gemini
[root@localhost gemini]#
[root@localhost gemini]#
[root@localhost gemini]# ll
total 112
drwxr-xr-x. 6 root root    122 Dec 10  2024 api
drwxr-xr-x. 2 root root     37 Nov 18  2024 _config
-rw-r--r--. 1 root root    577 Nov 19  2024 index.js
-rw-r--r--. 1 root root    526 Dec  3  2024 package.json
-rw-r--r--. 1 root root 100700 Dec  3  2024 package-lock.json
-rw-r--r--. 1 root root   1613 Dec 20  2024 ReactProjectDesign.txt
[root@localhost gemini]#

Install Node.hs as below:

 List available modules:
bash
sudo dnf module list nodejs
Enable a specific version (e.g., 16):
bash
sudo dnf module enable nodejs:16
Install:
bash
sudo dnf install -y nodejs

If you got error like "Could not resolve host: mirrors.rockylinux.org " , to revole it as below:

Edit /etc/resolv.conf and temporarily add Google's DNS servers:
bash
nameserver 8.8.8.8
nameserver 8.8.4.4

Verify installation:
bash
node --version
npm --version

Step 2: Prepare the Application



