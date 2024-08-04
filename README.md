<br>

<h1 align="center">Stage II - Building the SOC - Part 1</h1>

<br>

<h2 align="center">Log Analytics Workspace & Microsoft Sentinel (SIEM) Setup + Geo IP Data Ingestion</h2>

<br>

<p align="center">
<img width="700" src="https://github.com/user-attachments/assets/b7cded74-c328-4778-a585-8befccdcc6c7" alt="Banner"/>

<br />

<br />


<details close> 
<summary> <h2>1️⃣ Create Log Analytics Workspace</h2> </summary>
<br>

Create a New **Log Analytics Workspace**:

<br>

![azure portal](https://github.com/user-attachments/assets/5a321762-df1d-4523-a4e2-393aa02d4a07)

<br>

Add **Microsoft Sentinel** to our ```LAW-Cyber-Lab``` **Log Analytics Workspace**:

<br>

![azure portal](https://github.com/user-attachments/assets/e3bbd331-af14-4cfd-bfd2-e2f39396e82e)

<br>

✅ We can confirm that **Microsoft Sentinel** was successfully added to our LAW:

<br>

![azure portal](https://github.com/user-attachments/assets/1d6a255b-1e7e-43ed-8a4d-ca20ccb58141)

<br>

  </details>

<h2></h2>

<details close> 
<summary> <h2>2️⃣ Create Microsoft Sentinel Watchlist</h2> </summary>
<br>

In **Microsoft Sentinel** ➜ Create a new **Watchlist for Geo IP Data**.

We'll name the Watchlist: ```geoip```

Set the **"Alias"** as ```geoip``` as well.

<br>

![azure portal](https://github.com/user-attachments/assets/6d5868e0-20b9-4b2a-adb7-2aee958ebd60)

<br>

Under the **"Source"** tab:

  - Upload the **Geo IP data CSV File**

  - Set the **Search Key** to ```network```
  
  - Click **"Review + create"**

<br>

![azure portal](https://github.com/user-attachments/assets/22b73a75-4af4-4270-8d7d-21102eba3990)

<br>

>   <details close> 
>   
> **<summary> 💡 </summary>**
> 
> This Watchlist will help us correlate **Security Events** to **Geographic Locations** later in the lab.
> 
>   </details>

<br>

Once the watchlist begins uploading ➜ Sentinel will start **Ingesting the Data**.

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

<br>

<br>

<br>

<br>

<br>
  
<br>

