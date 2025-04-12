# SIEM LAB

## Objective

The SIEM Lab project aims to establish a controlled environment for simulating and detecting cyber attacks. The primary focus was to ingest and analyze logs within a Security Information and Event Management (SIEM) system, generating test telemetry to mimic real-world attack scenarios. This hands-on experience was designed to deepen understanding of network security, attack patterns, and defensive strategies.

### Skills Learned

- Advanced understanding of SIEM concepts and practical application.
- Proficiency in analyzing and interpreting network logs.
- Ability to generate and recognize attack signatures and patterns.
- Enhanced knowledge of network protocols and security vulnerabilities.
- Development of critical thinking and problem-solving skills in cybersecurity.

### Tools Used

- Microsoft Sentenial (SIEM) system for log ingestion and analysis.
- Remote Desktop Connection to remote into the VM.

## Steps
Microsoft Sentential SIEM LAB

1)	The first step I took was creating a Resource Groups in Azure.
I named my group gdhsoclab and put it in the East US 2 Region.

<img width="468" alt="image" src="https://github.com/user-attachments/assets/2c44197a-40be-4692-b47a-224c4ed8aa5d" />

 
2)	After creating the gdhsoclab Resource group. I navigated to Virtual Network.
a.	I created a virtual network called VNETSCOLAB and clicked review + create.

<img width="468" alt="image" src="https://github.com/user-attachments/assets/d623d236-f6f1-442e-8418-f426aa5bc373" />

<img width="468" alt="image" src="https://github.com/user-attachments/assets/02d577f0-9023-4cb9-9a35-418585e04cb0" />

3)	I went back to Resource Groups and clicked gdhsoclab to confirm that the VNETSOCLAB VN is setup for use. 

 <img width="468" alt="image" src="https://github.com/user-attachments/assets/2bd008db-b529-4b14-8c9f-19786866b561" />


4)	Next I’ll be navigating to Virtual Machines to setup AD-NET2.
I mapped the Virtual Machine to the VN gdhsoclab.
 
 <img width="468" alt="image" src="https://github.com/user-attachments/assets/ce59524a-5f1a-4183-a6a2-430d5f4288f1" />


<img width="465" alt="image" src="https://github.com/user-attachments/assets/89ce6efd-5a73-42ee-b815-1bf1b8cdf682" />


5)	I also setup a user and password to login to this VM later on
 
<img width="468" alt="image" src="https://github.com/user-attachments/assets/cc34a075-bbe5-425e-b01a-7fba9c92d85b" />



6)	In this next step I on the networking tab I sent the VN as VNETSOCLAB and checked the Delete public IKP and NIC when VM is deleted.
 
<img width="468" alt="image" src="https://github.com/user-attachments/assets/717a33f5-490e-4f84-9558-8efad8634121" />

7)	On the monitoring tab I disabled Boot Diagnostics an d then clicked review + create.
 

<img width="465" alt="image" src="https://github.com/user-attachments/assets/da048f60-20d9-4e87-b14a-376972a7fdfe" />


8)	The VM has been deployed and is ready to use but….
 
<img width="468" alt="image" src="https://github.com/user-attachments/assets/2c63a6f6-3e7b-4932-baef-01316d5d9683" />

9)	I will be going back to Resource Groups and opening up the  Network Security Group AD-NET2-nsg and delete the RDP Security rule.  
 

<img width="468" alt="image" src="https://github.com/user-attachments/assets/2dd0e7c5-6e75-4f2f-96fd-992723e31d13" />


<img width="468" alt="image" src="https://github.com/user-attachments/assets/39fa0996-e9f6-4674-bc69-219a188113b8" />

<img width="468" alt="image" src="https://github.com/user-attachments/assets/acdd8c95-7e12-4828-a017-18c119a9d5e1" />


10)	Next I will be navigating to Settings- Inbound security rules
 
<img width="468" alt="image" src="https://github.com/user-attachments/assets/1ec5f113-eb81-4a88-8f1f-a6aa51d2be39" />



11)	I clicked add and proceeded with the steps below. 
 
<img width="468" alt="image" src="https://github.com/user-attachments/assets/7cacb7a2-55e8-4c5d-8b0a-b42568f8d5ed" />



12)	I changed the source and destination to Any and put an asterisk to allow any port ranges and named the security rule DANGER.
 
<img width="468" alt="image" src="https://github.com/user-attachments/assets/bbee354d-ade8-40bc-8f57-e04b0b6f22d4" />



13)	The DANGER security protocol is now active.
 
<img width="468" alt="image" src="https://github.com/user-attachments/assets/da79c155-da18-4a3b-aebe-0ca5da673176" />



14)	I went back to the Virtual Machine and copied the Public IP address.
 
<img width="468" alt="image" src="https://github.com/user-attachments/assets/5179fd26-89bb-42b7-aae5-89e138366b72" />




15)	I then went over to my Parallels VM to use Remote desktop Connection to login to my VM and set Firewall settings. I turned the Firewall state Off on the Domain Profile, Private Profile, and Public Profile. Which will allow people to attempt to login to my VM.

 <img width="468" alt="image" src="https://github.com/user-attachments/assets/1963b98d-8f53-4ad1-80e9-675d6d2fc2bd" />


16)	I had to make sure that my VM could be pinged so I went to the terminal and pinged the IP Address.
 

<img width="468" alt="image" src="https://github.com/user-attachments/assets/89fd91d6-a358-4e19-9c99-999d8dbabf56" />


17)	Next I  created a Log Analytics Workspace within Azure called LOGAN1.
 <img width="468" alt="image" src="https://github.com/user-attachments/assets/d04d045a-c70d-4545-87f2-df0d3d23770b" />





18)	After the Log Analysis Workspace was deployed, I went to Microsoft Sentential to create a SIEM where I used my LOGAN1 workspace.
 
<img width="468" alt="image" src="https://github.com/user-attachments/assets/23fab9ff-4b85-4d69-8eb2-ceb13f26f6f6" />




19)	 After adding LOGAN1 in Microsoft Sentential. I install Windows Security Events and selected Windows Security Events via AMA and clicked open connecter page.

 <img width="468" alt="image" src="https://github.com/user-attachments/assets/8fd7d390-b84f-4e5c-9c80-6dd90fa8767e" />

<img width="468" alt="image" src="https://github.com/user-attachments/assets/15a7647f-aa9b-45db-babd-8eea8bae2f47" />




20)	I selected create data collection rule. 
 

<img width="468" alt="image" src="https://github.com/user-attachments/assets/f3372dd2-86fa-43bb-95be-706ac189cf44" />


<img width="468" alt="image" src="https://github.com/user-attachments/assets/3c236e17-b475-4121-82d4-5fe8d4dccc28" />


<img width="468" alt="image" src="https://github.com/user-attachments/assets/4069e5cc-48a5-4b1f-8918-6c4d1f9bc043" />


<img width="468" alt="image" src="https://github.com/user-attachments/assets/b5c3a5d3-4640-49e9-8c04-ec44ae9c2ce0" />

<img width="468" alt="image" src="https://github.com/user-attachments/assets/a6e8422b-6595-406f-a842-0057ee76d737" />


21)	The data collection rule was created successfully and shows up under the VM.
 
<img width="468" alt="image" src="https://github.com/user-attachments/assets/b38007f8-3030-4191-9dd5-d670e8e3b3c6" />





22)	Now I can see the logs and who logs is based on the query I used to filter log events.
I used a KPL query because it specifically filters the logs for failed login attempts based on the parameters I want to see. This is how you monitor logs using a VM using Microsoft Sentential.

 
<img width="468" alt="image" src="https://github.com/user-attachments/assets/a87feecb-11dc-4089-b5e9-3d522c12b974" />

 


