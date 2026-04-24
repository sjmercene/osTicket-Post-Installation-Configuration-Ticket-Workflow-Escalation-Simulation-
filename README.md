##  Post-Installation Configuration & Help Desk Simulation

After successfully installing osTicket, I went on to configure the system to simulate a small real-world IT help desk environment. The purpose of this was to gain hands-on experience in how ticketing systems operate within a small organisation scenario.

I set up key components including roles, departments, and teams, and created agents and users to mirror a real support structure. I then tested the system by creating and managing tickets to understand how issues are logged, assigned, escalated, and resolved.

---

### Roles (Access Control)

I created a role called **Supreme Admin** to control agent permissions within the system.

Roles define what actions agents are allowed to perform. For this lab, I enabled full permissions to allow complete system access during testing.

This helped me understand how access control works in a help desk environment. In real-world scenarios, organisations follow the principle of least privilege, where users are only given the permissions necessary for their role.

---

### 🏢 Departments (Ticket Routing)

To simulate a real business environment, I created a department called **IT Support**.

Departments are used to route tickets to the appropriate team. In this case, all technical issues submitted by users are directed to IT Support.

I also observed default departments such as **Support (Default)** and chose not to remove them. These can act as fallback routing options if configuration is incomplete, which reflects how real systems maintain redundancy.

---

### 👥 Teams (Escalation Structure)

I created a team called **Level II Support** to simulate an escalation structure within the help desk.

Teams allow agents to collaborate and handle more complex issues. This setup represents how higher-level support staff handle advanced technical problems after escalation.

This helped me understand how help desk systems organise support tiers.

---

### 👨‍💻 Agents (Help Desk Staff)

I created agent accounts to simulate IT support staff.

Example configuration:

- **John Smith**
- **Jane Doe (Level II Support)**

Each agent was assigned:

- Role → Supreme Admin  
- Department → IT Support  
- Team → Level II Support  

Agents are responsible for managing and resolving tickets. This step demonstrated how roles, departments, and teams work together to control access and responsibilities.

I also performed an agent password reset, which reflects a common help desk task related to account management.

---

### 👤 Users (Customers)

I created user accounts to simulate employees submitting support requests:

- Mike Johnson → `mike@company.com`  
- Sarah Lee → `sarah@company.com`  

Users represent individuals who generate tickets when issues occur. Unlike agents, users do not have permissions or system access — they only interact with the system by submitting requests.

This helped reinforce the difference between customers and help desk staff.

---

### ⏱️ SLA Plans (Ticket Prioritisation)

I configured SLA (Service Level Agreement) plans to define ticket urgency and response times:

- SEV-A (Critical) → 1 hour  
- SEV-B (Medium) → 4 hours  
- SEV-C (Low) → 8 hours  

SLA plans are used to prioritise tickets based on business impact. This reflects real-world environments where critical issues must be resolved faster than less urgent ones.

---

## 🎫 Ticket Workflow Testing

### ✅ Ticket Verification

I created a test ticket as a user and verified that it appeared in the Agent Panel.

This confirmed that the system was correctly receiving and routing tickets from users to help desk staff, validating end-to-end functionality.

---

### 🔄 Basic Ticket Lifecycle (Mike Johnson)

I simulated a complete help desk workflow:

- User submitted a ticket  
- Ticket was assigned to an agent  
- SLA (SEV-B) was applied  
- Agent responded professionally  
- Issue was resolved  
- Ticket was closed  

This demonstrated the full lifecycle of a ticket from creation to resolution.

---

### 🚀 Escalation Scenario (Sarah Lee)

To simulate a more realistic scenario, I created a ticket where a user could not log into their workstation.

The workflow included:

- Assigning a high-priority SLA (SEV-A)  
- Adding internal notes for investigation  
- Escalating the ticket to a Level II agent  
- Responding to the user with updates  
- Identifying the root cause (account lockout)  
- Resolving the issue and restoring access  
- Closing the ticket  

This demonstrated a real-world escalation process and how support teams collaborate to resolve complex issues.

---

## 🛠️ Additional Troubleshooting (Post-Install)

### Email Notification Error

**Problem:**  
PHP warning when creating or replying to tickets:
mail() failed to connect to mailserver (localhost:25)

**Cause:**  
osTicket attempted to send email notifications using the PHP mail() function, but no SMTP/mail server was configured in the lab environment.

**Solution:**  
Disabled email alerts and notifications in:

Admin Panel → Settings → Tickets

**Result:**  
Ticket creation and replies continued to work normally despite the warning, confirming that the issue was related to missing email infrastructure rather than core system functionality.

---

### Ticket Lock Warning

**Problem:**  
"Unable to lock the ticket. Someone else could be working on the same ticket."

**Cause:**  
This occurs when osTicket detects multiple sessions or possible concurrent access to the same ticket.

**Fix:**  
Refreshing the page or reopening the ticket resolved the issue.

**Insight:**  
This demonstrated how help desk systems implement concurrency control to prevent multiple agents from editing the same ticket at the same time.

---

## 🎯 Key Takeaways

This phase helped me understand:

- How help desk systems structure access using roles and permissions  
- How tickets are routed using departments  
- How escalation works using teams  
- The difference between users and agents  
- How SLA plans define urgency and response expectations  
- How tickets move through a full lifecycle (open → assigned → resolved → closed)  
- How to troubleshoot real-world issues such as missing dependencies and system warnings  

---
