## Activity File: Part 2 - Defend Your SOC

- VSI recently experienced several cyberattacks, likely from their adversary JobeCorp.

- Fortunately, your SOC team had set up several monitoring solutions to help VSI quickly identify what was attacked.

- These monitoring solutions will also help VSI create mitigation strategies to protect the organization.

You have been provided two logs files of suspicious activity:

  - One for a Windows server
  - One for an Apache web server

### Windows Server Logs 

Load the logs in your Splunk environment. 

   - Select all default options provided.
   - **Important:** For the time range, always select **All Time**.   

Now you will review the reports you created in Part 1 and analyze the results. 

#### Report Analysis for Severity

1. Access the **Reports** tab and select **Yours** to view the reports created from Part 1.
2. Select the report you created to analyze the different severities.
3. Select **Edit** > **Open in Search**.
4. Take note of the percentages of different severities.
   - informational: 93.094039%
   - high: 6.905961%
5. Change the source from `windows_server_logs.csv` to "`source="windows_server_attack_logs.csv`
6. Select **Save**.

Review the updated results and answer the following question:

- Did you detect any suspicious changes in severity?
  - Yes, High severity increased to 20.222060%

#### Report Analysis for Failed Activities

1. Access the **Reports** tab and select **Yours** to view the reports created from Part 1.
2. Select the report you created to analyze the different activities.
3. Select **Edit** > **Open in Search**.
4. Take note of the failed activities percentage.
   - success: 97.019312
   - failure: 2.980688
5. Change the source from `windows_server_logs.csv` to "`source="windows_server_attack_logs.csv`.
6. Select **Save**.


Review the updated results and answer the following question:

- Did you detect any suspicious changes in failed activities?
  - success: 98.436712
  - failure 1.563288
  - No, failed windows activities actually dropped 1%

---

Now you will review the alerts you created in Part 1 and analyze the results. 

#### Alert Analysis for Failed Windows Activity

1. Access the **Alerts** tab and select **Yours** to view the alerts created in Part 1.

2. Select the alert for suspicious volume of failed activities.

3. Select  **Open in Search**.

4. Change the source from `windows_server_logs.csv` to "`source="windows_server_attack_logs.csv`.

Review the updated results and answer the following questions:

- Did you detect a suspicious volume of failed activity?
  - Yes
- If so, what was the count of events in the hour(s) it occurred?
  - 35 events
- When did it occur?
  - 4 AM on Wednesday, March 25, 2020
- Would your alert be triggered for this activity?
  - Yes, threshold was set to 15
- After reviewing, would you change your threshold from what you you previously selected?
  - Could slightly lower for possibility of catching activity sooner.

#### Alert Analysis for Successful Logons

1. Access the **Alerts** tab and select **Yours** to view the alerts created in Part 1.

2. Select the alert of  suspicious volume of successful logons.

3. Select  **Open in Search**.

4. Change the source from `windows_server_logs.csv` to "`source="windows_server_attack_logs.csv`.

Review the updated results, and answer the following questions:

- Did you detect a suspicious volume of successful logons?
  - Yes
- If so, what was the count of events in the hour(s) it occurred?
  - 196 events followed by 77 events
- Who is the primary user logging in?
  - user_j (70.396%)
- When did it occur?
  - 7 AM on Wednesday, March 25, 2020 (196)
  - 8 AM on Wednesday, March 25, 2020 (77)
- Would your alert be triggered for this activity?
  - Yes
- After reviewing, would you change your threshold from what you you previously selected?
  - No, threshold is set to 25 which is slightly above normal logins

#### Alert Analysis for Deleted Accounts

1. Access the **Alerts** tab and select **Yours** to view the alerts created in Part 1.

2. Select the alert of suspicious volume of deleted accounts.

3. Select  **Open in Search**.

4. Change the source from `windows_server_logs.csv` to "`source="windows_server_attack_logs.csv`.

Review the updated results and answer the following question:

1. Did you detect a suspicious volume of deleted accounts?
   - No, activity for deleted accounts seems the same.

---

 Now you will set up a dashboard and analyze the results. 

#### Dashboard Setup

1. Access the **Windows Server Monitoring** dashboard.
   - Select **Edit**.

2. Access each panel you created and complete the following:
   - Select **Edit Search**.

   - Change the source from: `windows_server_logs.csv` to `source="windows_server_attack_logs.csv`.

   - Select **Apply**.

   - Save the dashboard.
   - Edit the time on the dashboard to be **All Time**.

#### Dashboard Analysis for Time Chart of Signatures

Analyze your new dashboard results and answer the following questions:

  - Does anything stand out as suspicious?
    - Yes
  - What signatures stand out?
    - A user account was locked out
    - An attempt was made to reset an accounts password
  - What time did it begin/stop for each signature?
    - A user account was locked out: March 24, 2020 8:00 PM to 11:00 PM
    - An attempt was made to reset an accounts password: March 25, 2020 4:00 AM to 7:00 AM
  - What is the peak count of the different signatures?
    - A user account was locked out: 896
    - An attempt was made to reset an accounts password: 1,258

#### Dashboard Analysis for Users  

Analyze your new dashboard results and answer the following questions:

  - Does anything stand out as suspicious?
    - Yes
  - Which users stand out?
    - user_a
    - user_k
  - What time did it begin and stop for each user?
    - user_a: 8:00 PM to 11:00 PM
    - user_k: 4:00 AM to 7:00 AM
  - What is the peak count of the different users?
    - user_a: 984
    - user_k: 1,256    

#### Dashboard Analysis for Users with Bar, Graph, and Pie Charts     

Analyze your new dashboard results, and answer the following questions:

  - Does anything stand out as suspicious?
    - Yes
  - Do the results match your findings in your time chart for users?
    - Yes

#### Dashboard Analysis for Users with Statistical Charts

Analyze your new dashboard results, and answer the following question:

  - What are the advantages and disadvantages of using this report, compared to the other user panels you created?

    - Advantage is it shows each user and the number of counts. Disadvantage is no visualization and does not break down what each count is.

     

---

### Apache Web Server Logs

Load the logs in your Splunk environment. 

  - Select all default options provided.
  - **Important:** For the time range, always select **All Time**.

Now you will review the reports you created in Part 1 and analyze the results. 

#### Report Analysis for Methods

1. Access the **Reports** tab and select **Yours** to view the reports created from Part 1.

2. Select the report that analyzes the different HTTP methods.

3. Select **Edit** > **Open in Search**.

4. Take note of the percent/count of the various methods.

5. Change the source from: `source=apache_logs.txt` to `source="apache_attack_logs.txt`.

6. Select **Save**.

Review the updated results and answer the following questions:

1. Did you detect any suspicious changes in HTTP methods? If so which one?
   - Yes, HTTP POST
2. What is that method used for?
   - POST is an HTTP method used to send data to a server to create/update a resource.

#### Report Analysis for Referrer Domains

1. Access the **Reports** tab and select **Yours** to view the reports created from Part 1.

2. Select the report that analyzes the different referrer domains.

3. Select **Edit** > **Open in Search**.

4. Take note of the different referrer domains.

5. Change the source from: `source=apache_logs.txt` to `source="apache_attack_logs.txt`.

6. Select **Save**.

Review the updated results, and answer the following question:

1. Did you detect any suspicious changes in referrer domains?
   - No

#### Report Analysis for HTTP Response Codes

1. Access the **Reports** tab and select **Yours** to view the reports created from Part 1.

2. Select the report that analyzes the different HTTP response codes.

3. Select **Edit** > **Open in Search**.

4. Take a note of the different HTTP response codes.
5. Change the source from: `source=apache_logs.txt` to `source="apache_attack_logs.txt`.

6. Select **Save**.

Review the updated results and answer the following question:

1. Did you detect any suspicious changes in HTTP response codes?
   -  No

---

Now you will review the alerts you created in Part 1 and analyze the results. 

#### Alert Analysis for International Activity

1. Access the **Alerts** tab and select **Yours** to view the alerts created in Part 1.

2. Select the alert of suspicious volume of international activity.

3. Select  **Open in Search**.

4. Change the source from: `source=apache_logs.txt` to `source="apache_attack_logs.txt`.

Review the updated results and answer the following questions:

- Did you detect a suspicious volume of international activity?
  - Yes
- If so, what was the count of the hour it occurred in?
  - 1,369 events at 4 PM on Wednesday, March 25, 2020
- Would your alert be triggered for this activity?
  - Yes
- After reviewing, would you change the threshold you previously selected?
  - I would slightly increase threshold from 100 to limit alert fatigue. 

 #### Alert Analysis for HTTP POST Activity

1. Access the **Alerts** tab and select **Yours** to view the alerts created in Part 1.

2. Select the alert of suspicious volume of HTTP POST activity.

3. Select  **Open in Search**.

4. Change the source from: `source=apache_logs.txt` to `source="apache_attack_logs.txt`.

Review the updated results, and answer the following questions:

- Did you detect any suspicious volume of HTTP POST activity?
  - Yes
- If so, what was the count of the hour it occurred in?
  - 1,296 events
- When did it occur?
  - 4 PM on Wednesday, March 25, 2020
- After reviewing, would you change the threshold that you previously selected?
  - No, original threshold was set to 5 due to most events being under threshold

---

 Now you will set up a dashboard and analyze the results. 


#### Dashboard Setup

- Access the dashboard for Apache Webserver Monitoring.

- Select **Edit**.

- Access each panel and complete the following:

  - Select **Edit Search**.

  - Change the source from: `source=apache_logs.txt` to `source="apache_attack_logs.txt`

  - Select **Apply**.

- Save the whole dashboard.

- Edit the time on the whole dashboard to be **All Time**.

#### Dashboard Analysis for Time Chart of HTTP Methods

Analyze your new dashboard results and answer the following questions:

- Does anything stand out as suspicious?
  - Yes
- Which method seems to be used in the attack?
  - POST
- At what times did the attack start and stop?
  - 3:00 PM to 5:00 PM
- What is the peak count of the top method during the attack?
  - 1,296

#### Dashboard Analysis for Cluster Map

Analyze your new cluster map results and answer the following questions:

- Does anything stand out as suspicious?
- Which new city, country on the map has a high volume of activity?
  - Kiev, Ukraine
- What is the count of that city?
  - 872

#### Dashboard Analysis for URI Data

Analyze your dashboard panel of the URI data and answer the following questions:

- Does anything stand out as suspicious?
  - Yes
- What URI is hit the most?
  - /VSI_Account_logon.php
- Based on the URI being accessed, what could the attacker potentially be doing?
  - Overload the system and cause employee lock outs of accounts.

---

© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.
