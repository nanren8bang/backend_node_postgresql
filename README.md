Google: how to deploy node.js application on rocky linux 8

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

Create a directory for your app:
bash
mkdir -p /tmp
cd /tmp
Transfer your application files (using git or scp).
scp D:\jhu\New_Gemini_React_howTo\backend\gemini.zip root@192.168.56.103:\tmp
unzip gemini.zip
cd gemini
ll 
[root@localhost gemini]# ll
total 112
drwxr-xr-x. 6 root root    122 Dec 10  2024 api
drwxr-xr-x. 2 root root     37 Nov 18  2024 _config
-rw-r--r--. 1 root root    577 Nov 19  2024 index.js
-rw-r--r--. 1 root root    526 Dec  3  2024 package.json
-rw-r--r--. 1 root root 100700 Dec  3  2024 package-lock.json
-rw-r--r--. 1 root root   1613 Dec 20  2024 ReactProjectDesign.txt



Install dependencies: All dependencies are listed in package.json file 
npm install
all dependencies will be install in sub folder named as "node_modules".


Noew , run “node index.js” to start Gemini backend 

[root@localhost gemini]# pwd
/tmp/gemini
[root@localhost gemini]# ll
total 104
drwxr-xr-x.   6 root root   122 Dec 10  2024 api
drwxr-xr-x.   2 root root    37 Nov 18  2024 _config
-rw-r--r--.   1 root root   577 Nov 19  2024 index.js
drwxr-xr-x. 204 root root  8192 Dec 23 03:50 node_modules
-rw-r--r--.   1 root root   526 Dec  3  2024 package.json
-rw-r--r--.   1 root root 78593 Dec 23 03:50 package-lock.json
-rw-r--r--.   1 root root  1613 Dec 20  2024 ReactProjectDesign.txt
[root@localhost gemini]# node index.js
Here is  routes.js location: /tmp/gemini/api
Load service and router for: user from ./
/tmp/gemini/node_modules/tedious/lib/connection.js:243
  _cancelAfterRequestSent;
                         ^

SyntaxError: Unexpected token ;
    at Module._compile (internal/modules/cjs/loader.js:723:23)
    at Object.Module._extensions..js (internal/modules/cjs/loader.js:789:10)
    at Module.load (internal/modules/cjs/loader.js:653:32)
    at tryModuleLoad (internal/modules/cjs/loader.js:593:12)
    at Function.Module._load (internal/modules/cjs/loader.js:585:3)
    at Module.require (internal/modules/cjs/loader.js:692:17)
    at require (internal/modules/cjs/helpers.js:25:18)
    at Object.<anonymous> (/tmp/gemini/node_modules/tedious/lib/tedious.js:57:42)
    at Module._compile (internal/modules/cjs/loader.js:778:30)
    at Object.Module._extensions..js (internal/modules/cjs/loader.js:789:10)
[root@localhost gemini]#



Or :

Step 3: Run the Application with PM2 
PM2 is a process manager that ensures your app restarts if it crashes or if the server reboots. 
Install PM2 globally:
sudo npm install -g pm2
Start your application:
bash
pm2 start app.js --name "my-app"
Ensure PM2 starts on boot:
bash
pm2 startup systemd
pm2 save
