# C2
C2 notes on how to use and setup 

A command and control server is used as an interface to upload and control various post-exploitation tools without interacting with the target itself. Consider C2 as a means for mass-management of exploited targets for further usage - be it lateral movement, information gathering, or otherwise. 

### Table of content

- [Free C2 Frameworks](#Free-C2-Frameworks)
  - [Metasploit](#Metasploit)
  - [Armitage](#Armitage)
  - [Powershell Empire and Starkiller](#Powershell-Empire-and-Starkiller)
    - [Installing Starkiller](#Installing-Starkiller)
    - [Installing Empire](#Installing-Empire)
    - [Setting Up Starkiller](#Setting-Up-Starkiller)
    - [Uploading a C2 agent with Starkiller](#Uploading-a-C2-agent-with-Starkiller)
    - [Creating our Listener](#Creating-our-Listener)
    - [Generating the Stager](#Generating-the-Stager)
  - [Covenant](#Covenant)
  - [Sliver](#Sliver)

- [Paid C2 Frameworks](#Paid-C2-Frameworks)
  - [Cobalt Strike](#Cobalt-Strike)
  - [Brute Ratel](#Brute-Ratel)




# Free C2 Frameworks

## Metasploit

## Armitage

## Powershell Empire and Starkiller

#### Installing Starkiller 

1.) cd /opt

2.) Download an up to date version of starkiller from the BC-Security Github repo - https://github.com/BC-SECURITY/Starkiller/releases 

3.) chmod +x starkiller-1.3.2.AppImage

4.) sudo ./starkiller-1.3.2.AppImage --no-sandbox    


#### Installing Empire

1.) cd /opt

2.) git clone https://github.com/BC-SECURITY/Empire.git

3.) cd Empire    

4.) sudo ./setup/install.sh    

5.) then start the powershell-empire server


#### Setting Up Starkiller

1.) cd /opt

2.) cd Empire

3.) sudo ./empire --rest

4.) cd ..

5.) sudo ./starkiller-1.3.2.AppImage --no-sandbox    

6.) Login to Starkiller

Default Credentials:

    uri: 127.0.0.1:1337

    user: empireadmin

    pass: password123

![image](https://user-images.githubusercontent.com/24814781/184546443-9a830855-44f0-422f-828c-0ee5ae63ad7f.png)

If you properly setup Starkiller and Empire you will be met with a listeners panel after logging in.

![image](https://user-images.githubusercontent.com/24814781/184546864-714a8f9b-19a8-4dfd-a0d4-6ce96b69eeda.png)


#### Uploading a C2 agent with Starkiller

Starkiller uses a listener and a stager to create an agent the listener does exactly as it sounds like it, it listens on a given port for a connection back from your agent. The stager is like a payload that you send to the target to get an agent back.

#### Creating our Listener

1.) Go to the listeners tab and select CREATE LISTENER.

![image](https://user-images.githubusercontent.com/24814781/184546910-b35f87ff-7e2f-490f-b546-bf35a4bfcfa3.png)

2.) Select your listener type. we demo htttps for now 

![image](https://user-images.githubusercontent.com/24814781/184546925-e2e8a9e2-4778-4991-85f7-71f033f1c7de.png)

3.) Configure your listener, the only two options you will need to change are the host IP and the host port.

![image](https://user-images.githubusercontent.com/24814781/184546930-4ab138e7-b703-4f15-a33c-03009c64b8fe.png)

4.) After pressing submit we now have an active listener on port 53.

![image](https://user-images.githubusercontent.com/24814781/184546938-5c52570b-d48d-4f4a-8f72-dc15e4a23361.png)

#### Generating the Stager

1.) Go to the stagers tab and select GENERATE STAGER.

![image](https://user-images.githubusercontent.com/24814781/184546967-174897f6-8496-41e6-b7fb-aa44e791c67c.png)

2.) Select your stager type, for our demo, we’ll use windows/launcher_bat.

![image](https://user-images.githubusercontent.com/24814781/184546974-d1bc2653-8ad4-4e63-8977-51356670930c.png)

3.) Set the listener to the listener we made previously.

![image](https://user-images.githubusercontent.com/24814781/184546986-37ecdfde-718f-431d-a8db-b209a808b43d.png)

4.) We now have a stager ready to deploy to our target depending on the stager type you selected you will have to either download or copy and paste the stager to the target machine.

![image](https://user-images.githubusercontent.com/24814781/184546995-d4481952-7cc4-4746-b261-263d0d02424c.png)



### Covenant

### Sliver 

### Paid C2 Frameworks

### Cobalt Strike

### Brute Ratel
