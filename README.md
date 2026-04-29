# Lab: Automating Incident Response with Splunk SOAR

## Objective
This lab demonstrates how to automate initial investigative steps within **Splunk SOAR**. We will focus on a **"Suspicious Tool Usage"** event involving `wevtutil.exe`—a native Windows utility often leveraged by threat actors to clear event logs and obfuscate their activities.

---

## Task 1: Incident Triage
1. Navigate to the **Analyst Queue** in Splunk SOAR.
2. Locate the container labeled **"Suspicious Tool Usage."** The presence of `wevtutil` suggests a potential anti-forensics attempt. Malicious actors use this tool to edit or manipulate Windows logs to cover their tracks after making unauthorized system changes.
3. Select the investigation to begin the automation process. 
4. In the right-hand fly-out menu, click **View Details**.

<img width="3828" height="1903" alt="picture1" src="https://github.com/user-attachments/assets/f70a6758-2883-45b6-b5be-9ba22945c37e" />


---

## Task 2: Executing the Playbook
1. Within the investigation container, navigate to the **Automation** tab.
2. Click the **Run Playbook** button to view the available automation workflows.

<img width="3823" height="1567" alt="pic2" src="https://github.com/user-attachments/assets/1d903157-cb32-4a08-850d-61a0ed15694e" />


3. From the dialog box, select the **"Geolocate Destination Address"** playbook.
4. Click **Run Playbook** to execute the automation.

---

## Task 3: Analyzing Playbook Logic and Results
The selected playbook executes two primary functional blocks:
* **Enrichment:** Utilizes a geolocation API to resolve the IP address found in the finding's `destinationAddress` field.
* **Documentation:** Automatically appends a custom note to the **Info** panel, providing the analyst with immediate geographic context.

<img width="3828" height="1888" alt="pic3" src="https://github.com/user-attachments/assets/23aeadd3-c8a4-4270-87ed-c3102d25639c" />


> [!NOTE]
> In this simulated environment, the Google Maps visual preview does not render. To verify the data, click the **`</>` (Code View)** button to inspect the raw **JSON API response** containing the captured geographic coordinates and metadata.

<img width="3796" height="1887" alt="pic4" src="https://github.com/user-attachments/assets/3ef11faa-86f8-4b01-849a-71c968e73728" />


---

## Task 4: Playbook Customization
If the workflow requires modification (e.g., adding a threat intelligence lookup via VirusTotal or an automated isolation step):
1. Click the **Open Playbook** button to enter the **Visual Playbook Editor (VPE)**.

<img width="2011" height="873" alt="pic5" src="https://github.com/user-attachments/assets/7ff300f8-25b0-4c71-a270-f26bdc637579" />


2. From the VPE, you can manage the process flow, drag-and-drop new action blocks, or adjust logic paths to refine the automation.

<img width="3796" height="1488" alt="pic6" src="https://github.com/user-attachments/assets/3bcf8ead-2d2e-4a9a-9e71-3e79a6eca6d5" />


