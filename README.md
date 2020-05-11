# QuickSquid
Sick of waiting for Tor pages to load? Tired of Tuxler users torrenting the collective works of [Chuck Tingle](https://en.wikipedia.org/wiki/Chuck_Tingle#Bibliography) over your internet connection? If so, you've come to the right place. Using QuickSquid, you can turn any Ubuntu box into your own private proxy in under five minutes.


**Steps:**  
  1) [Create a Ubuntu server with port 80 open](#1-creating-a-ubuntu-server)
  2) [Download `initproxy`](#2-downloading-initproxy)
  3) [Run `initproxy`](#3-running-initproxy)
  

### 1) Creating a Ubuntu server
If you've already got a server set up, you can skip this step. 

If not, no problem; you can easily create one for free by signing up for [Google Cloud](https://cloud.google.com/). This should give you $300 in free credits -- more than enough to run several proxies for months. 

Once you've signed up, create a new project. Then, go to Compute Engine and create a new VM instance. Configure your settings to look like this:

![](https://i.imgur.com/J929UF7.png)

Once that's done, create the server and connect to it using the SSH button:

![](https://i.imgur.com/d90bCtp.png)

Great! Once you're here, starting the proxy is only a few lines away.

### 2) Downloading `initproxy`
This can be done in multiple ways. A few of the more convenient are listed below:

  1) **git clone** You can clone this Git repository using
  ```
  apt install git -y
  git fetch https://github.com/CocoPommel/QuickSquid
  ```
  2) **File transfer/SCP** Download the file onto your own machine, then SCP to your server [or use Google Cloud's convenient file transfer utility](https://cloud.google.com/compute/docs/instances/transfer-files#transferbrowser)
  3) **Copy and paste (the caveman method)** Copy the text in `initproxy`, paste it in a file using your text editor of choice, and make the file executable:
  ```
  nano initproxy
  *paste text, save*
  chmod 777 initproxy
  ```
  
### 3) Running `initproxy`
Once you have the executable, all that's left is to run it. A short guide to commands is below (if you're looking for a quickstart, the best answer is: `sudo ./initproxy your_ip`)

**Creating a proxy that's accessible from one IP:**  
    `sudo ./initproxy xxx.xxx.xxx.xxx"`
  
**Creating a proxy that's accessible from multiple IPs on the commandline:**  
`sudo ./initproxy xxx.xxx.xxx.xxx yyy.yyy.yyy.yyy zzz.zzz.zzz.zzz`

**Creating a proxy that's accessible from multiple IPs in a text file:**  
`sudo ./initproxy -f filename.txt`

**Creating a proxy that's accessible from any IP:**  
`sudo ./initproxy -o`

**Doing any of the above on a different port:**  
`sudo ./initproxy -f filename.txt -p 1330`

**Doing any of the above, but automatically confirm all dialogues**  
`sudo ./initproxy -y -o -p 1330`

**Help:**  
`sudo ./initproxy -h`
