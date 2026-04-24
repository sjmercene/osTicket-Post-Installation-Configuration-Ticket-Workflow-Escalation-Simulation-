#  Post-Installation Configuration & Help Desk Simulation

After successfully installing osTicket, i went on to configure the system to simulate a small real-world IT help desk environment. The purpose of this was to gain hands-on experience in how ticketing systems operate within a small organisation scenario.

I set up key components such as roles, departments, and teams, and created agents and users to simulate a real help desk environment. I then tested the system by creating and managing tickets to see how issues are logged, assigned, escalated, and resolved in practice.

---

### Roles (Access Control)

I first created a role called **Supreme Admin** to manage agent permissions within the system.

<img src="https://github.com/sjmercene/osTicket-Post-Installation-Configuration-Ticket-Workflow-Escalation-Simulation-/blob/sjmercene-osTicket-Post-configuration-Images/Role%20Name.JPG" width="700">

**Screenshot:** `Supreme Admin role configured with full permissions`

<br>

While configuring this, i was able to see how roles directly control what actions an agent can perform within the system, such as managing tickets and accessing different settings.

In a real-world environment, this would not be configured with full access. Organisations typically follow the principle of least privilege, where permissions are restricted based on the user’s role to reduce security risks.

---

### Departments (Ticket Routing)

To simulate a real business environment, I created a department called **IT Support**.

<img src="https://github.com/sjmercene/osTicket-Post-Installation-Configuration-Ticket-Workflow-Escalation-Simulation-/blob/sjmercene-osTicket-Post-configuration-Images/Creating%20Department%20IT%20Support.JPG" width="700">

**Screenshot:** `IT Support department configuration`

<br>

I created a department called **IT Support** to handle user-submitted technical issues within the system (roleplay).

While configuring this, i learned how departments are used to route tickets to the appropriate team based, depending on the type of request.

Note i kept the default department **Support (Default)** as a fallback option. This ensures a safety net incase i misconfigure the evvironment im playing around with.

---

### 👥 Teams (Escalation Structure)

I created a team called **Level II Support** to simulate an escalation structure within the help desk.

while setting this up, i learned that teams is used to allow agents from different departments to collaborate and handle more complex issues.

this reflects how higher-level support tiers take over tickets that require more advanced troubleshooting tasks after escalation.

---

### Agents (Help Desk Staff)

I now created agent accounts to simulate a roleplay of IT support staff within the system.

**My configuration i used:**

- **John Smith**
- **Jane Doe (Level II Support)**

each agent was assigned:

- role → Supreme Admin  
- department → IT Support  
- team → Level II Support  

while setting this up, i saw how roles, departments, and teams work together to control what each agent can access and which tickets they are responsible for.

I also had to perform an agent password reset after forgetting Jane Doe’s login details. this reflects a common help desk task related to account and access management.

---

### 👤 Users (Customers)

I created user accounts to simulate employees submitting support requests:

- Mike Johnson → `mike@company.com`  
- Sarah Lee → `sarah@company.com`  

while setting this up, i saw how users interact with the system differently from agents, as they can only submit and track tickets rather than access or manage the system.

this highlights the separation privilege between customers and help desk staff within a ticketing environment.

---

### ⏱️ SLA Plans (Ticket Prioritisation)

i configured SLA (Service Level Agreement) plans to define ticket urgency and response times to further simulate the environment:

- SEV-A (Critical) → 1 hour  
- SEV-B (Medium) → 4 hours  
- SEV-C (Low) → 8 hours  

while setting this up, i saw how SLA plans control how quickly tickets need to be responded to and resolved based on their priority.

this shows how higher-impact issues are handled more urgently, while lower-priority requests are given longer response times.

---

##  Ticket Workflow Testing

### ✅ Ticket Verification

I now created a test ticket role playing as the user `Mike Johnson` and verified that it appeared in the Agent Panel.

<img src="https://github.com/sjmercene/osTicket-Post-Installation-Configuration-Ticket-Workflow-Escalation-Simulation-/blob/sjmercene-osTicket-Post-configuration-Images/Ticket%20Working.JPG" width="650">

**Screenshot:** `Ticket successfully created and visible in Agent Panel.`

This confirmed that the system was working correctly, receiving and routing tickets from users to help desk staff, validating full functionality.

---

### 🔄 Basic Ticket Lifecycle Testing (Mike Johnson)

In this simulated test i completed a help desk workflow containing:

- User submitted a ticket  
- Ticket was assigned to an agent  
- Agent responded professionally  
- Issue was resolved  
- Ticket was closed  

This demonstrated the full lifecycle of a ticket from creation to resolution.

---

### Escalation Scenario (Sarah Lee)

To simulate a more realistic scenario, I created a ticket where a user could not log into their workstation.

The workflow included:

- assigning a high-priority SLA (SEV-A Critical)  
- adding internal notes for investigation (to simulate communication between agents)  
- escalating the ticket to a Level II agent (Jane Doe)  
- responding to the user with updates  
- identifying the root cause (account lockout)  
- resolving the issue and restoring access (simulated)  
- closing the ticket  

<img src="https://github.com/sjmercene/osTicket-Post-Installation-Configuration-Ticket-Workflow-Escalation-Simulation-/blob/sjmercene-osTicket-Post-configuration-Images/Escalating%20Sarahs%20Ticket.JPG" width="700">

**Screenshot:** `SLA plan applied and escalation initiated`

<img src="https://github.com/sjmercene/osTicket-Post-Installation-Configuration-Ticket-Workflow-Escalation-Simulation-/blob/sjmercene-osTicket-Post-configuration-Images/Closed%20Ticket%20Sarah.JPG" width="700">

**Screenshot:** `Shows full ticket lifecycle including escalation, agent response, and resolution`

this demonstrated how tickets are escalated between support levels and how agents communicate and resolve issues within a structured workflow.

---

## 🛠️ Additional Troubleshooting (Post-Install)

### Email Notification Error

**Problem:**  
While creating or replying to tickets, a PHP warning appeared:
mail() failed to connect to mailserver (localhost:25)

**Cause:**  
I investigated the warning and found that osTicket was attempting to send email notifications using the PHP mail() function. since no SMTP or mail server was configured in the lab environment, the request to localhost:25 failed.

**Solution:**  
I disabled email alerts and notifications via:

`Admin Panel → Settings → Tickets`

**Result:**  
In my observations Tickets continued to function normally, confirming the issue was related to missing email configuration rather than the core application.

---

### Ticket Lock Warning

**Problem:**  
Message appeared when trying to edit a ticket: 

`"Unable to lock the ticket. Someone else could be working on the same ticket."`

**Cause:**  
I encountered this issue while accessing the same ticket multiple times and noticed that osTicket restricted further actions. based on this behaviour, it appeared the system was preventing multiple active sessions or concurrent edits on the same ticket.

**Fix:**  
Refreshing the page or reopening the ticket cleared the session and allowed normal interaction.


**Insight:**  
This showed how help desk systems implement basic control to prevent multiple agents from editing the same ticket at the same time.

---

## Key Takeaways

With this home lab, i gained a clearer understanding of how a help desk system operates in practice.

- how roles and permissions control agent access within the system  
- how departments are used to route tickets to the appropriate team  
- how escalation works through team structures and higher-level support  
- the difference between users (customers) and agents (support staff)  
- how SLA plans affect ticket priority and response expectations  
- how tickets move through a full lifecycle from creation to resolution  
- how to identify and troubleshoot common issues such as configuration errors and system warnings  

---
