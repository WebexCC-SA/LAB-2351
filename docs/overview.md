# Overview

## Learning Objectives

Get ready for an exciting, hands-on lab where you’ll unlock the power of contact center routing models to revolutionize both customer experience (CX) and employee experience (EX)! In this interactive session, you'll dive straight into practical solutions and real-world examples that show how simple, yet powerful routing methods can transform customer interactions. By the end of this lab, you’ll not only understand but be ready to implement teams-based and skills-based routing. Whether you are optimizing workflows or creating seamless customer journeys, this lab will set you up to make an immediate impact! 
 
Join us as we dive into the world of advanced routing techniques in a dynamic, fictitious telecommunications company’s contact center! Here, you'll navigate through two business queues: Technical Support, Order Inquiry.  

**Team-Based Routing:** Work together with a group of agents *specializing in similar tasks* to expertly manage the queue. Create a customer experience when there is repeatability and predictability to the operations 

**Skill-Based Routing:** Unlock the power of personalized service by *assigning specific skill requirements* **to contacts** based on customer attributes. Fine-tune the routing process to maximize efficiency and enhance satisfaction at every customer interaction touchpoint! 

Before you begin, take a look at the [Topologies](topologies.md) section for an overivew of what the lab will set you up for.

Here are some frequent terms, portals and web pages you will encounter during the course of this lab

**Team** - 
A team is a group of agents at a specific site who handle a particular type of contact. Teams are organized based on the nature of the customer interactions they manage, which can range from billing inquiries to technical support or specialized customer service. Teams are structured to leverage the collective expertise of agents, ensuring that customer queries are addressed efficiently and effectively. 

Example:  

At Acme’s various sites, teams are structured as follows: 

    Chicago Site:  

        Chi_TechnicalSupport: Handles all technical-related customer interactions.  

        Chi_Billing: Handles all billing transactions.  

        Chi_General: Handles all queries apart from Billing and Technical.  

 

    Bangalore Site:  

        Bgl_TechnicalSupport: Handles all technical-related customer interactions.  

        Bgl_Billing: Handles all billing transactions.  

        Bgl_General: Handles all queries apart from Billing and Technical.  

When a customer initiates a billing inquiry, the contact center system first attempts to route the call to the Bgl_Billing team due to Bangalore’s lower operational costs. If the Bangalore agents are busy or unavailable, the system then routes the call to the Chi_Billing team. This hierarchy ensures cost-effective handling of contacts while maintaining high service standards. 

Key points:  

    Agents can be assigned to multiple teams but can service only one team at a time.  

    The organization of teams within each site allows for tailored responses to specific customer needs, enhancing overall service quality and efficiency. 

 

**Skill** 
A "Skill" in a contact center refers to a specific competency, expertise, or knowledge area that an agent possesses, which is necessary to handle particular types of customer interactions. Skills can encompass various attributes such as language proficiency, technical knowledge, product expertise, or any other specialization required to resolve customer inquiries effectively. 

Key Points: 

    *Assignment to Contacts:* Unlike traditional queue-based routing systems where calls or contacts are routed to queues, skills are assigned directly to the contact. This ensures that the customer is connected to the most suitable agent based on the required skill set rather than just a general queue. 

    *Dynamic Matching:* The contact center system dynamically matches the contact's required skills with the agent's skills, ensuring that the customer is served by the most capable agent available. 

    *Enhanced Customer Experience:* By assigning skills to contacts, the contact center enhances customer satisfaction through more personalized and efficient service. 

**Skill Profile**

A "Skill Profile" is a collection or configuration of multiple skills that define the capabilities and expertise of an agent / team or a set of criteria for routing contacts. This profile is used to match agents to contacts based on the skills required to handle specific types of interactions. 

Key Points: 

    *Combination of Skills:* A skill profile typically includes various skills combined in a way that reflects the comprehensive abilities needed for specific roles or tasks within the contact center. 

    *Customized Routing:* The skill profile is used to tailor the routing process, ensuring that contacts are directed to agents whose skill profiles best match the needs of the interaction. 

    *Optimized Resource Allocation:* By defining and utilizing skill profiles, the contact center can optimize the allocation of agents, improving overall efficiency and effectiveness. 

 
Additional Considerations 

    *Retention of Skills During Blind Transfers:* In scenarios where a contact is transferred blindly to another queue, the system retains the skills originally assigned to the contact. This ensures continuity in service and prevents the skill attributes from being reset inadvertently. 

    *Use of Transfer/Consult to Entry Point (IVR) for reprogramming Skills:* To reassign the skills of a contact, it is recommended to use the Transfer or Consult to the Entry Point (EP) method. This action ensures that the contact’s skill requirements are reassessed, and the appropriate skills are assigned based on the new context or interaction requirements. 

In modern contact centers, the assignment of skills to contacts rather than queues enhances routing precision and customer satisfaction. Skills define specific competencies necessary for handling interactions, while skill profiles represent a comprehensive set of skills for routing and resource allocation. The retention of skills during blind transfers ensures continuity and using the Transfer/Consult to EP method allows for proper reassignment of skills when needed. 

**Site** 
A site is a physical contact center location under the control of the enterprise or an outsourcer. Each site represents a distinct operational unit where agents are based and handle customer interactions. Sites can be geographically dispersed to optimize operational efficiency, localize services, and cater to specific regional markets or time zones. 

Example:  

An enterprise like Acme might have multiple sites, such as: 

    Chicago, USA 

    Manila, Philippines 

    Bangalore, India 

 
Each of these locations operates as an independent site with its own set of resources and personnel. 

**Queue**
A queue is where active contacts are held while they await handling by an agent. Contacts are moved from the entry point into a queue where they remain until the system matches them with the most suitable agents.  

**Entry Point**
An entry point is the initial landing place for customer contacts on the Webex Contact Center. It serves as the first interaction interface where customer contacts are received and processed. For voice interactions, this typically involves one or more toll-free or dial numbers associated with the entry point. During this phase, IVR (Interactive Voice Response) call treatment is performed, guiding the customer through options and preliminary information gathering while the call is in the entry point. 

**Flow Designer** - Is the UI for building (voice) call flows. Today this handles only voice. In the future this will be used to orchestrate digital contacts as well

**Control Hub** - Is the administration interface for Webex CC. The Control Hub is integrated with the Webex common identity and is the central location for provisioning of Webex CC, Webex calling, webex meeting and managing users, permissions and authorization

**Flow builder** - Is the UI for building digital channel flows. 

**Webex Connect** - Is the engine that drives digital contacts through the workflow

**Webex Engage** - Is the embedded widget into the Webex agent desktop that presents digital contacts to the agent


