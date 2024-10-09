<script>
 function update () {
    const form = document.forms['attendee-form'];
    if (form) {
      form.addEventListener('submit', function (event) {
        event.preventDefault();
        const inputs = Array.from(form.querySelectorAll('input'));
        const values = inputs.reduce((acc, input) => {
          acc[input.id + '_out'] = input.value;
          return acc;
        }, {});

        Object.entries(values).forEach(([id, value]) => {
          const elements = document.getElementsByClassName(id);
          Array.from(elements).forEach(element => {

            console.log(element.innerHTML);
            if(Number(element.innerHTML) > 99 ){
               console.log(`Got a 99+ attendee: ${element.innerHTML}`);
               element.innerHTML = value;
             }
            else{
               console.log(`Got a sub 99 attendee: ${element.innerHTML}`);
               if(element.innerHTML.includes('gmail.com'))
               {
                element.innerHTML = `0${value}`;
                }
               else{
                element.innerHTML = value;
               }
                }
          });
        });
        const attendeeIDInput = form.elements['attendeeID'];
       if (attendeeIDInput && attendeeIDInput.value !== 'Your_Attendee_ID') {
          localStorage.setItem('attendeeID', attendeeIDInput.value);
        }
      });
    }
  };
</script>
<style>
  /* Style for the button */
  button {
    background-color: black; /* Set the background color to black */
    color: white; /* Set the text color to white */
    border: none; /* Remove the border */
    padding: 10px 20px; /* Add some padding for better appearance */
    cursor: pointer; /* Show a pointer cursor on hover */
  }

   /* Style for the input element */
  input[type="text"] {
    border: 2px solid black; /* Set the border thickness to 2px */
    padding: 5px; /* Add some padding for better appearance */

</style>

Please **`submit the form below with your Attendee or pod ID`**. All configuration entries in the lab guide will be renamed to include your pod ID.
 {: .block-warning }

<script>
document.forms["attendee-form"][1].value = localStorage.getItem("attendeeID") || "Your Attendee ID" 
</script>
<form id="attendee-form">
  <label for="attendee">Attendee ID:</label>
  <input type="text" id="attendee" name="attendee" onChange="update()"><br>
<br>
  <button onclick="update()">Save</button>
</form>

<br/>


!!! Note
    The input in the images that follow are only examples. They do not reflect the input you need to use in the lab exercises. In some cases, the input in the images may not follow the same attendee or pod ID from previous images. They are for representation only

## Enhancing the caller experience: The foundation of call routing techniques

Imagine you are calling your telecom provider about a technical issue. You hope to get connected with the right agent quickly. But depending on the nature of your inquiry, the system can either route you directly to a specialized technical team or to an order status team if your issue is related to a product delivery. 

### Teams based routing / Longest available routing

In this setup, specific teams are aligned to handle certain types of calls – like a technical team for troubleshooting or an order status team for inquiries about shipments. Teams-Based Routing allows us to organize agents into these groups called Teams and ensure the caller receives the right expertise. 

#### Multimedia profile

**What is it?**

A Multimedia Profile defines the various channels through which an agent can communicate with customers. Think of it as a toolbox filled with different tools (or channels) that agents can use to assist customers. Each tool is designed for specific tasks, making the agent more versatile and effective.

**How does it work?**

- Channel Assignment: Each agent can be assigned to specific channels based on their roles and preferences. For instance, one agent might handle phone calls and chats, while another might focus on emails and social media interactions.
- Team-Based Approach: Teams can have a collective Multimedia Profile, allowing for a broader range of customer interactions. For example, a technical support team might manage both chat and phone calls, ensuring coverage across all channels.

**Configuration**

Login into Control Hub [https://admin.webex.com](https://admin.webex.com)

![login into control hub](../assets/teams/mmp_1.png)

Look for the contact center option in the left pane under **SERVICES – Contact Center**

![contact center left pane](../assets/teams/mmp_2.png)

Navigate to **DESKTOP EXPERIENCE - Multimedia Profiles** and click **Create Multimedia Profile** on the top right corner of the page

![create MMP](../assets/teams/mmp_3.png)

Create a new MMP profile with a name MMP_<w class = "attendee_out">attendeeID</w> where <w class = "attendee_out">attendeeID</w> is your 3-digit attendee ID

![create MMP](../assets/teams/mmp_4.png)

Set the **Blended** in the More Details section and set the Voice to 1, Chat, Email and Social all to 3

Click **Create**

You have now configured a multimedia profile for the agent to handle 1 voice and 3 each of other digital channels simultaneously.

#### Site

**What is it?**

Consider a company operating in various regions, each with a unique geographical location where agents are based. These locations can range from bustling urban centers to quieter suburban areas, affecting how services are delivered and how agents interact with customers. The resources, technologies, and local knowledge available at each location play a crucial role in enhancing customer service.

**Configuration**

Under **USER MANAGEMENT** on the left pane navigate to **Sites**

Click **Create Site** on the top right corner to create a new site East_<w class = "attendee_out">attendeeID</w> and choose the **Multimedia Profile** you created in the previous step MMP_<w class = "attendee_out">attendeeID</w>

Click **Create**

![Site](../assets/teams/site_1.png)

Repeat the above steps to create a West_<w class = "attendee_out">attendeeID</w>

![Site](../assets/teams/site_2.png)

#### Teams and agents

**What is a team?**

Agents who specialize in similar tasks are grouped together into **Teams**. For example, all the agents who handle technical issues form a Technical Team, and those who deal with order inquires make up the Order Status Team. This way, when a caller needs help, the system directs the call to the right team of experts. 

By organizing agents into teams, we ensure that callers are handled efficiently by agents with the right knowledge. So, if you need help fixing your phone, you’ll be connected to a technical expert instead of someone who only knows about orders. 

As part of this setup, when agents log in to the system, they choose the team to login which is assigned to the agent. For instance, if the agent is part of the East Technical Team, they login under that team’s profile. This way, the system knows which team they belong to and routes calls to them accordingly. 

**Configuration**

Under **USER MANAGEMENT** in the left pane navigate to **Teams** and click **Create Team.**
Create the TechnicalSupport_<w class = "attendee_out">attendeeID</w> team where <w class = "attendee_out">attendeeID</w> is your pod ID. Choose the EastCoast_<w class = "attendee_out">attendeeID</w> site and ![Team](../assets/teams/team_1.png) and **Create** the team.

![Team](../assets/teams/team_1.png)

![Team](../assets/teams/team_2.png)

On the next screen, click **Done**

Now create another TechnicalSupport_<w class = "attendee_out">attendeeID</w> team and assign it to the WestCoast site

![Team](../assets/teams/team_3.png)

![Team](../assets/teams/team_4.png)

#### Setup Auxiliary codes

Idle or wrap up codes are two types of Auxiliary codes. 
- **Idle codes** typically indicate why an agent is not available to handle customer contacts such as during a lunch break or meeting. 
- **Wrap-up codes** indicate the result of the customer interaction, for example, the agent escalated the contact, or sold a service.

Navingate to **DESKTOP EXPERIENCE - Idle/Wrap-up Codes** and click on **Create Idle/Wrap-up Code**

Create one or **TechncialSupport**

![Idle code](../assets/teams/19.png)

Click `Create`

Create another one for **BillingInquiry**

![Idle code](../assets/teams/20.png)

Once these wrap-up codes are created we need to make them available to agents. This is done through `Desktop Profiles` that the agents get assigned

Under **DESKTOP EXPERIENCE - Desktop Profiles** select the **Agent-Profile (Auto WrapUp)** and click on the **Idle/Wrap-up Codes**

![Wrap-up codes](../assets/teams/21.png)

Ensure that the **Wrap-up Codes** is selected as **Specific** and select the new wrap-up codes that we created in the previous step. You may need to make one of the wrap-up codes as default

The system will also choose **All** Idle codes available for the agent to indicate their unavailability for handling customer contacts

#### Setup Agents

Under **USER MANAGEMENT** in the left pane navigate to **Contact Center Users**.
Search for attendeeID in the search box of the Contact Center Users page. attendeeID is your pod ID.
Click on the agent created for your pod and configure them for Contact Center.

Search for <w class = "attendee_out">attendeeID</w> in the search box of the Contact Center Users page. <w class = "attendee_out">attendeeID</w> is your pod ID.

![Agent](../assets/teams/agent_1.png)
![Agent](../assets/teams/agent_2.png)

Now click **Save**

Configure the same for the second Agent:

![Agent](../assets/teams/agent_3.png)
![Agent](../assets/teams/agent_4.png)

#### Verify access to the agent desktop

> Please use Google Chrome as the web browser when using webRTC as the voice endpoint

!!! Note
    Since we will be using the same Chrome browser for different roles we will use the **Chrome Browser user profiles** to allow multiple logins into the different components of the Webex contact center. For the control hub, use the Administrator profile created for you in the Chrome browser. Always offer Chrome to **remember your credentials and password** for this lab


Use a different Chrome browser profile for each agent

![Chrome Profiles](../assets/voice_configuration/16.png)

Navigate to **<https://desktop.wxcc-us1.cisco.com>** and login using the agent configured to the Technical_support team

Remember to login using the below configurations

![Agent login](../assets/teams/12.png)

Once logged in click on the Agent initials on the top right to verify your successful login

![Post agent login](../assets/teams/13.png)

Test the login for the other agents using their respective web browser profiles of Google Chrome

In this section you have understood how to access the Control Hub, configure the agents needed for the rest of this lab exercise and log them in with some help from the Chrome browser profiles.

#### Queues

A Queue is like a virtual ordered line that callers are placed in while waiting for an agent to become available. Think of it like standing in line to enter a movie hall. The system organizes all incoming calls into different queues based on the type of request. For example, callers from east coast requiring technical support go into the TechnicalSupport_East, while those from West Coast are placed in the TechnicalSupport_West Queue. 

Once we’ve defined queues for different call types, we need to assign teams to handle those queues. This is done using Call Distribution Group (CDG). The Call Distribution Group allows us to assign one or more teams to a single queue. For example, both the technical teams could be associated to their respective queues. 

**Why CDGs matter**

This setup ensures that when a caller enters the East Coast Technical Queue, they are directed to agents in the East Coast. If you want to get more flexible, you can assign multiple teams to one queue. For instance, if the East Coast queue is often overloaded, another team can be added during configuration to expand the pool of agents.  

But what if the East Coast queue is free, whereas West Coast Queue is filling up. This is where **Rank Queues** comes into play. We can assign a priority to the queues from the perspective of the team. We can let teams choose the order in which they will service the queues they are responsible for. For example, the East Coast Technical Team will always prioritize their own queue first, but if they have no calls waiting, they can assist with the West Coast Queue. 

**Why Rank Queues Matter**

This setup makes sure the team focusses on their specialized tasks first. But in the case of idle time, they can help with other queues, like the West Coast Queue, ensuring maximum efficiency across the teams. 

**Create Queues**

Login into Control Hub https://admin.webex.com with your administrator credentials to begin our configuration.
Navigate to **Contact Center - CUSTOMER EXPERIENCE - Queues** and click **Create Queue.**

![queue](../assets/teams/q_1.png)

Create the <w class = "attendee_out">attendeeID</w>Q_TechSupport with the below settings (it is easier to search for queues when the attendee ID is prefixed to the queue name instead of after it)

![queue](../assets/teams/q_2.png)

Now click **Create Group** under **Call Distribution**

![queue](../assets/teams/q_3.png)

Click **Create Group** again and add the West Coast Team as a backup.

Select **Priority** as `2` and for **Switch to this group after** select `10` seconds

![queue](../assets/teams/q_4.png)

Click **Save**

Under **Advanced Settings**, configure the parameters as below and click **Create**

![queue](../assets/teams/q_5.png)

Repeat the same steps to configure the Technical Support Queue for the West Coast. 

![queue](../assets/teams/q_6.png)

**Rank Queues**

Under **USER MANAGEMENT** click on **Teams** and search for your TechnicalSupport_<w class = "attendee_out">attendeeID</w> team

You will see two teams of the same name but for different sites. Click on one team and setup Rank queues

![queue](../assets/teams/rank_1.png)

Click **Select queues**

Select both the queues created above and then click on Select the queue.

For the East Coast team, pick the priority of 1 for the East Coast queue and priority 2 for the West Coast team. 

![queue](../assets/teams/rank_2.png)
