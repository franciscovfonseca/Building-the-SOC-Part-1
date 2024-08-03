<br>

<h1 align="center">Stage II - Building the SOC - Part I</h1>

<br>

<h2 align="center">Log Analytics Workspace & Microsoft Sentinel (SIEM) Setup + Data Ingestion</h2>

![Banner](https://github.com/user-attachments/assets/e1ae7814-502d-4b8b-91c1-faf36eadfa36)
<br />
<br />


<details close> 
<summary> <h2>1️⃣ Create Log Analytics Workspace</h2> </summary>
<br>

![azure portal](https://github.com/user-attachments/assets/5a321762-df1d-4523-a4e2-393aa02d4a07)

<br>

### ❶ Add Sentinel to the Workspace.

<br>

![azure portal](https://github.com/user-attachments/assets/e3bbd331-af14-4cfd-bfd2-e2f39396e82e)

![azure portal](https://github.com/user-attachments/assets/1d6a255b-1e7e-43ed-8a4d-ca20ccb58141)

<br>

  </details>

<h2></h2>

<details close> 
<summary> <h2>2️⃣ Create Microsoft Sentinel Watchlist</h2> </summary>
<br>

In **Microsoft Sentinel** ➜ Create a new **Watchlist for Geo IP Data**.

This Watchlist will help us correlate **Security Events** ➜ to **Geographic Locations** later in the lab.

<br>

![azure portal](https://github.com/user-attachments/assets/6d5868e0-20b9-4b2a-adb7-2aee958ebd60)

<br>

Upload the Geo IP data and set the Search Key.

<br>

![azure portal](https://github.com/user-attachments/assets/22b73a75-4af4-4270-8d7d-21102eba3990)

<br>

Once the watchlist begins uploading ➜ Sentinel will start Ingesting the Data.

The Data will be available for Querying ➜ even Before Ingestion Completes.

<br>

![azure portal](https://github.com/user-attachments/assets/cbe9315a-b5d0-4d78-829c-81b830539bc0)

<br>

Query GeoIP Data using KQL.

<br>

![azure portal](https://github.com/user-attachments/assets/9ff99b31-a613-45da-8d3f-fcea31207091)

<br>

✅ Upload complete.

<br>

![azure portal](https://github.com/user-attachments/assets/69be1dd4-2b83-4d5f-be70-980945348c21)

<br>

  </details>

<h2></h2>

<details close> 
<summary> <h2>3️⃣ Enable Microsoft Defender for Cloud</h2> </summary>
<br>

![azure portal](https://github.com/user-attachments/assets/92c1c533-88a0-434d-a00e-a87bd24ec2d4)

<br>

### ❶ Enable Microsoft Defender for Cloud for Log Analytics Workspace

<br>

Open Microsoft Defender for Cloud:

<br>

![azure portal](https://github.com/user-attachments/assets/ea9306fc-dea8-45d9-9a96-74da3b332516)

<br>

Go to **"Environment settings"** ➜ Expand the ```∨``` next to the **"Cyber Lab"** Subscription.

All the way on the right side of the **"LAW-Cyber-Lab"** line ➜ click on ```...``` ➜ and then **"Edit settings"**:

<br>

![azure portal](https://github.com/user-attachments/assets/ea9306fc-dea8-45d9-9a96-74da3b332516)

<br>

First we'll go to the **"Defender plans"** tab.

We'll **Turn On** MDC for **"Servers"** and also for **"SQL servers on machines"** ➜ since we do have a SQL Server instance.

<br>

>   <details close> 
>   
> **<summary> 💡 </summary>**
> 
> This will allow us to **Collect Logs** from these resources.
> 
>   </details>

<br>

Make sure you click the 💾 **Save** button:

Then we'll go to the **"Data collection"** tab ➜ and check **"All Events"**

<br>

![azure portal](https://github.com/user-attachments/assets/ea9306fc-dea8-45d9-9a96-74da3b332516)

<br>

>   <details close> 
>   
> **<summary> 💡 </summary>**
> 
> This will allow us to **Collect All Events from the Windows Security Log**.
> 
> Which is like the **Windows Event Viewer**, where we can see people attempting to **Log Into our Windows Machines over the Internet**.
> 
> We're going to be able to **Collect Logs** from that and then **Forward Them to this Log Analytics Workspace**.
> 
>   </details>

<br>

Again ➜ click the 💾 **Save** button:

<br>

<h2></h2>

<br>

### ❷ Enable Microsoft Defender for Cloud for the Subscription

<br>

Back to **MDC** ➜ **"Environment settings"** blade.

This time for the **"Azure subsription 1"** line ➜ click on ```...``` ➜ and then **"Edit settings"**:

<br>

![azure portal](https://github.com/user-attachments/assets/ea9306fc-dea8-45d9-9a96-74da3b332516)

<br>

Now we'll **Turn On** MDC for **"Servers"**, **"Databases"**, **"Storage"** & **"Key Vault"**.

<br>

>   <details close> 
>   
> **<summary> 💡 </summary>**
> 
> We'll create a **Storage Account** and **Key Vault** instances in a subsequent lab.
> 
>   </details>

<br>

Next to Databases ➜ Select Types ➜ make sure **"SQL servers on Machines"** is toggled **ON**.

All else toggled **OFF** ➜  then click **"Continue"**

<br>

![azure portal](https://github.com/user-attachments/assets/ea9306fc-dea8-45d9-9a96-74da3b332516)

<br>

Then click on **"Settings >"** under **"Monitoring coverage"** for the **Servers**.

We'll now click on **"Edit configuration"** for the **Log Analytics agent**.

And for the **Workspace** ➜ pick our actual ```LAW-Cyber-Lab``` Workspace.

>   <details close> 
>   
> **<summary> 💡 </summary>**
> 
> We don't want it to automatically create a new LAW ➜ we want to use the one we created.
> 
> We're basically onboarding our Virtual Machines to our LAW and then forward the Logs to it
> 
>   </details>

Make sure you click **"Apply"** and then 💾 **Continue**:

<br>

![azure portal](https://github.com/user-attachments/assets/ea9306fc-dea8-45d9-9a96-74da3b332516)

<br>

After that we'll click on the 💾 **Save** button to save the **Defender plans for the Subscription**

<br>

>   <details close> 
>   
> **<summary> 💡 Note</summary>**
> 
> If you accidentally saved before configuring the LAW agent: Go back and change to custom, then go through your resources and delete resources that were automatically provisioned in the processes. 
> 
> To avoid future mixups, make sure there is only ONE LAW.
> 
>   </details>

<br>

<h2></h2>

<br>

### ❸ Enable Microsoft Defender for Cloud Continuous Export in Environment Settings

<br>

Still inside the **"Edit settings"** for the Subscription ➜ we'll go to the **"Continous export"** blade now.

Click on the **"Log Analytics workspace"** tab ➜ and make sure **"Export enabled"** is **Turned On**:

>   <details close> 
>   
> **<summary> 💡 </summary>**
> 
> Doing this will **Export Alerts into our LAW** so we can **Query Them Later**.
> 
> So if **Defender for Cloud** discovers there's some problem with our Environment, like a **Brute-Force Attack** going on, or there's a **Poor Configuration** for example ➜ MDC will **Export those Alerts into our LAW** ➜ which will let us **Query Them Later**
> 
>   </details>

![azure portal](https://github.com/user-attachments/assets/ea9306fc-dea8-45d9-9a96-74da3b332516)

So we'll enable ☑️ **Exported data types** for all of the following options:

>   <details close> 
>   
> **<summary> 💡 </summary>**
> 
> We haven't actually configured **"Regulatory compliance"** yet, but we'll do that in a future lab.
> 
> This will basically enable **NIST 800-53** for our Environment to see what controls are missing in certain areas.
> 
>   </details>

![azure portal](https://github.com/user-attachments/assets/ea9306fc-dea8-45d9-9a96-74da3b332516)

For the **"Export configuration"** option let's just configure it to our **Resource group** ```RG-Cyber-Lab```

And also for the **"Export target"** we'll select our **Target Workspace** ```LAW-Cyber-Lab-01```

>   <details close> 
>   
> **<summary> 💡 </summary>**
> 
> This is the target workspace where we want to **Export the Alerts to** ➜ so we have to select our **LAW**.
> 
>   </details>

We'll then click 💾 **Save**

![azure portal](https://github.com/user-attachments/assets/ea9306fc-dea8-45d9-9a96-74da3b332516)

<h2></h2>

  </details>

<br>






<br>


<br>


<br>


<br>














After both Virtual Machines are deployed, configure both Network Security Groups (NSGs) to allow All Inbound Traffic.

We're removing Rules for RDP and SSH and replacing them with the Custom Inbound Rule.

<br>

### ❶ Windows NSG Before:

<br>

![azure portal](https://github.com/user-attachments/assets/34e25bc2-63e1-433b-b72d-c5a75d19ecb0)

<br>

### ❷ Linux NSG Before:

<br>

![azure portal](https://github.com/user-attachments/assets/a1af7722-c438-40e7-a369-27810108be41)

<br>

### ❸ Custom Inbound Rule:

<br>

![azure portal](https://github.com/user-attachments/assets/5513f953-afcc-44fc-9d7e-07ad62007b57)

<br>

### ❹ Windows NSG After:

<br>

![azure portal](https://github.com/user-attachments/assets/abd7566e-4ad9-47c6-9dd0-2397b2866c17)

<br>

✅ At this point both NSGs are identical.

<br>

  </details>

<h2></h2>

<details close> 
<summary> <h2>3️⃣ Create Vulnerabilities</h2> </summary>
<br>
  
### ❶ Disable Windows Firewall

<br>

The goal is to **Expose These VMs to Threat Actors** and to make them both Discoverable and Reachable.

Doing so we can **Monitor, Log & Investigate Incidents** later.

By default **Windows Firewall**, blocks ICMP packets from the internet.

➜ You can see that the ```windows-vm``` is unreachable from another network:

<br>

![azure portal](https://github.com/user-attachments/assets/488bbf82-5741-419a-8416-0294ec8d1fe4)

<br>

So from here ➜ we'll **Disable the Firewall** (wf.msc).

<br>

#### ⏪ Before:

<br>

![azure portal](https://github.com/user-attachments/assets/fb0ebb4f-4300-47c5-829f-488e3acde199)

<br>

#### ⏩ After:

<br>

![azure portal](https://github.com/user-attachments/assets/f8f29dc1-808c-4af8-aeb0-799eab337147)

<br>

Pinging ```windows-vm``` again to test if it successfully Pings now:

<br>

![azure portal](https://github.com/user-attachments/assets/f1269b58-4d9f-484e-b64f-86f154d0dd93)

<br>

Connecting to the ```linux-vm``` via SSH using **PuTTy**:

<br>

![azure portal](https://github.com/user-attachments/assets/95257be6-27a0-4e26-979d-4a0166978be7)

![azure portal](https://github.com/user-attachments/assets/7f969ff1-6d7b-43c4-bf05-ac3fe37fe703)

<br>

Test pinging ```linux-vm``` externally:

<br>

![azure portal](https://github.com/user-attachments/assets/b298e521-bdbe-474a-8397-f8bdaf6c752d)

<br>

<h2></h2>

<br>

### ❷ Install MS SQL Server + Utilities

<br>

Next, download and install **[SQL Server Evaluation](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2019)**.

Select **Download Media**.

<br>

![azure portal](https://github.com/user-attachments/assets/9398f365-79d2-48d6-9f4c-c8041a41b014)

<br>

Select **ISO** and the **Download Location**.

<br>

![azure portal](https://github.com/user-attachments/assets/0f95a58f-5d5b-4464-b96b-1ff5756903ce)

<br>

Once the download completes ➜ go to the Download Location.

<br>

![azure portal](https://github.com/user-attachments/assets/6bcb5b94-7dd3-4a85-adef-2b0f7ea25d4d)

<br>

**Mount** the ISO:

<br>

![azure portal](https://github.com/user-attachments/assets/7d1d06dd-5754-4aa7-9e82-4dbc9f786877)

<br>

Run the installer:

<br>

![azure portal](https://github.com/user-attachments/assets/49419b03-5dc7-4e57-8361-9ee15b06c7d4)

<br>

Select **New SQL Server**:

<br>

![azure portal](https://github.com/user-attachments/assets/d99be1aa-f0bf-4e9b-83ac-fc2bb51ad223)

<br>

Include ☑️ **Database Engine Service**:

<br>

![azure portal](https://github.com/user-attachments/assets/382a927b-c164-424d-81a8-e470cf0f2572)

<br>

Select ⦿ Mixed Mode ➜ create a user and select **Add Current User** to also allow for Windows authentication using ```labuser```.

<br>

![azure portal](https://github.com/user-attachments/assets/5654185c-163b-4295-a2d9-a1fe437de2b5)

<br>

Once the installation completes, download and install **[MS SQL Management Studio (SMSS)](https://learn.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-ver16)**.

<br>

![azure portal](https://github.com/user-attachments/assets/9981e9ac-4d9d-4186-bb2d-1e76d3570f45)

![azure portal](https://github.com/user-attachments/assets/c974420c-2b62-4bb4-858a-fe2d4a1b918f)

<br>

Once the installation completes ➜ Restart the VM.

<br>

<h2></h2>

<br>

#### ➡️ Enable Logging on SQL Server

<br>

After restarting, follow the **[Microsoft documentation](https://learn.microsoft.com/en-us/sql/relational-databases/security/auditing/write-sql-server-audit-events-to-the-security-log?view=sql-server-ver16)** for adjusting settings to allow **SQL Server Logs** to be ported to **Windows Event Viewer**.

Provide full permission for the SQL Server service account **```NETWORK SERVICE```** to the registry hive.

<br>

![azure portal](https://github.com/user-attachments/assets/6002ba78-f307-4288-b152-0533bb24790c)

![azure portal](https://github.com/user-attachments/assets/c027d521-5540-497d-8ab8-18f05b9468a7)

<br>

Configure the audit object access setting in Windows using ```auditpol``` by executing the provided command line statement:

<br>

```commandline
auditpol /set /subcategory:"application generated" /success:enable /failure:enable
```

<br>

![azure portal](https://github.com/user-attachments/assets/c8be1cc2-0a60-4beb-ad55-91d91142232b)

<br>

**Launch SSMS** and log in to the **SQL Server**.

Then go to Properties ➜ Security ➜ Enable both

<br>

<h2></h2>

<br>

#### ⏪ Security Settings Before:

<br>

![azure portal](https://github.com/user-attachments/assets/63a62717-0df2-4749-a446-f4f10ce3faea)

<br>

#### ⏩ Security Settings After:

<br>

![azure portal](https://github.com/user-attachments/assets/2aa88224-0886-4024-91c1-2e1d59f09542)

<br>

Restart the SQL Server and try to **Generate some Failed Authentication Logs** ➜ by trying log into the SQL server with the Wrong Password.

<br>

![azure portal](https://github.com/user-attachments/assets/9f77c883-a52f-4428-9115-708ad6d26a8b)

<br>

Check **Event Viewer** to make sure the Logs are properly enabled and porting to Event Viewer successfully ✅

<br>

![azure portal](https://github.com/user-attachments/assets/2af91e5a-149c-4788-8e9c-76a2b50a0e42)

<br>

<h2></h2>

<br>

#### ➡️ Create Attack (Threat) VM

<br>

Create another Windows VM named ```attack-vm``` in a different Resource Group, Region, and Virtual Network.

All other settings can be the same or similar.

<br>

![azure portal](https://github.com/user-attachments/assets/af55023d-799a-4632-a7d1-037e05592337)

<br>

  </details>

<h2></h2>

<details close> 
<summary> <h2>4️⃣ Generate Logs</h2> </summary>
<br>

To make sure everything is working as expected, log into the ```attack-vm``` to Generate Failed Authentication Logs on both VMs.

<br>

![azure portal](https://github.com/user-attachments/assets/f14a74b2-9daa-4a59-9d26-5814f1e40ddd)

<br>

**Generating Failed RDP Logs** on ```windows-vm```

<br>

![azure portal](https://github.com/user-attachments/assets/b9c76e73-e537-490c-8d35-efa1a4e81810)

<br>

Using **PowerShell** to **Generate Failed Login Logs** on ```linux-vm```

<br>

![azure portal](https://github.com/user-attachments/assets/c6ee3ce8-b3ed-4136-b168-7f95c8047556)

<br>

**Installing SMSS** on ```attack-vm```

<br>

![azure portal](https://github.com/user-attachments/assets/77025612-fd99-45c6-b9b8-c0ae2eb1470e)

<br>

**Generating Failed Login Logs** for **MS SQL Server** on ```windows-vm```

<br>

![azure portal](https://github.com/user-attachments/assets/a33f9ecf-9c5f-4522-b3ec-ef42a949757c)

![azure portal](https://github.com/user-attachments/assets/810e3537-a5d2-46a5-ac2c-bf3e775c8710)

<br>

  </details>

<h2></h2>

<details close> 
<summary> <h2>5️⃣ Check Logs</h2> </summary>
<br>

Using **PowerShell** to **SSH into ```linux-vm```

<br>

![azure portal](https://github.com/user-attachments/assets/ef65d273-4e8f-4cb9-88a0-0d1848f2b256)

<br>

**Investigating the Logs** at ```/var/log/auth.log``` for Failed Authentication:

<br>

![azure portal](https://github.com/user-attachments/assets/27fe20a5-5604-4235-9897-f06d3c753eee)

<br>

<h2></h2>

<br>

#### ➡️ Checking Event Viewer on ```windows-vm```

<br>

In **Windows Event Viewer**, there are normally a lot of Logs

In the screenshots below the Logs are filtered by the specific events we're looking for.

- Windows Logs ➜ Security ➜ filtered by Event ID: **[4625](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-10/security/threat-protection/auditing/event-4625)**

<br>

![azure portal](https://github.com/user-attachments/assets/55c932fb-7ff0-4505-9378-522c51b2df44)

<br>

- Windows Logs ➜ Application ➜ filtered by Event ID: **[18456](https://learn.microsoft.com/en-us/sql/relational-databases/errors-events/mssqlserver-18456-database-engine-error?view=sql-server-ver16)**

<br>

![azure portal](https://github.com/user-attachments/assets/0c801721-2989-4d7d-90c2-c0ccd53d0fb7)

<br>

  </details>

<h2></h2>

<br>

<br>

<br>

<br>

<br>
  
<br>

