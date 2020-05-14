<!--
![Microsoft Cloud Workshops](https://github.com/Microsoft/MCW-Template-Cloud-Workshop/raw/master/Media/ms-cloud-workshop.png 'Microsoft Cloud Workshops')

<div class="MCWHeader1">
Modern cloud apps
</div>

<div class="MCWHeader2">
 Whiteboard design session trainer guide
</div>

<div class="MCWHeader3">
March 2020
</div>

Information in this document, including URL and other Internet Web site references, is subject to change without notice. Unless otherwise noted, the example companies, organizations, products, domain names, e-mail addresses, logos, people, places, and events depicted herein are fictitious, and no association with any real company, organization, product, domain name, e-mail address, logo, person, place or event is intended or should be inferred. Complying with all applicable copyright laws is the responsibility of the user. Without limiting the rights under copyright, no part of this document may be reproduced, stored in or introduced into a retrieval system, or transmitted in any form or by any means (electronic, mechanical, photocopying, recording, or otherwise), or for any purpose, without the express written permission of Microsoft Corporation.

Microsoft may have patents, patent applications, trademarks, copyrights, or other intellectual property rights covering subject matter in this document. Except as expressly provided in any written license agreement from Microsoft, the furnishing of this document does not give you any license to these patents, trademarks, copyrights, or other intellectual property.

The names of manufacturers, products, or URLs are provided for informational purposes only and Microsoft makes no representations and warranties, either expressed, implied, or statutory, regarding these manufacturers or the use of the products with any Microsoft technologies. The inclusion of a manufacturer or product does not imply endorsement of Microsoft of the manufacturer or product. Links may be provided to third party sites. Such sites are not under the control of Microsoft and Microsoft is not responsible for the contents of any linked site or any link contained in a linked site, or any changes or updates to such sites. Microsoft is not responsible for webcasting or any other form of transmission received from any linked site. Microsoft is providing these links to you only as a convenience, and the inclusion of any link does not imply endorsement of Microsoft of the site or the products contained therein.

© 2020 Microsoft Corporation. All rights reserved.

Microsoft and the trademarks listed at https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/Usage/General.aspx are trademarks of the Microsoft group of companies. All other trademarks are property of their respective owners.

**Contents**

# Trainer information

Thank you for taking time to support the whiteboard design sessions as a trainer!

## Role of the trainer

An amazing trainer:

- Creates a safe environment in which learning can take place.

- Stimulates the participant's thinking.

- Involves the participant in the learning process.

- Manages the learning process (on time, on topic, and adjusting to benefit participants).

- Ensures individual participant accountability.

- Ties it all together for the participant.

- Provides insight and experience to the learning process.

- Effectively leads the whiteboard design session discussion.

- Monitors quality and appropriateness of participant deliverables.

- Effectively leads the feedback process.

## Whiteboard design session flow

Each whiteboard design session uses the following flow:

**Step 1: Review the customer case study (15 minutes)**

**Outcome**

Analyze your customer's needs.

- Customer's background, situation, needs and technical requirements

- Current customer infrastructure and architecture

- Potential issues, objectives and blockers

**Step 2: Design a proof of concept solution (60 minutes)**

**Outcome**

Design a solution and prepare to present the solution to the target customer audience in a 15-minute chalk-talk format.

- Determine your target customer audience.

- Determine customer's business needs to address your solution.

- Design and diagram your solution.

- Prepare to present your solution.

**Step 3: Present the solution (30 minutes)**

**Outcome**

Present solution to your customer:

- Present solution

- Respond to customer objections

- Receive feedback

**Wrap-up (15 minutes)**

- Review preferred solution

## Before the whiteboard design session: How to prepare

Before conducting your first whiteboard design session:

- Read the Student guide (including the case study) and Trainer guide.

- Become familiar with all key points and activities.

- Plan the point you want to stress, which questions you want to drive, transitions, and be ready to answer questions.

- Prior to the whiteboard design session, discuss the case study to pick up more ideas.

- Make notes for later.

## During the whiteboard design session: Tips for an effective whiteboard design session

**Refer to the Trainer guide** to stay on track and observe the timings.

**Do not expect to memorize every detail** of the whiteboard design session.

When participants are doing activities, you can **look ahead to refresh your memory**.

- **Adjust activity and whiteboard design session pace** as needed to allow time for presenting, feedback, and sharing.

- **Add examples, points, and stories** from your own experience. Think about stories you can share that help you make your points clearly and effectively.

- **Consider creating a "parking lot"** to record issues or questions raised that are outside the scope of the whiteboard design session or can be answered later. Decide how you will address these issues, so you can acknowledge them without being derailed by them.

***Have fun**! Encourage participants to have fun and share!*

**Involve your participants.** Talk and share your knowledge but always involve your participants, even while you are the one speaking.

**Ask questions** and get them to share to fully involve your group in the learning process.

**Ask first**, whenever possible. Before launching into a topic, learn your audience's opinions about it and experiences with it. Asking first enables you to assess their level of knowledge and experience, and leaves them more open to what you are presenting.

**Wait for responses**. If you ask a question such as, "What's your experience with (fill in the blank)?" then wait. Do not be afraid of a little silence. If you leap into the silence, your participants will feel you are not serious about involving them and will become passive. Give participants a chance to think, and if no one answers, patiently ask again. You will usually get a response.

# Modern cloud apps whiteboard design session student guide

## Abstract and learning objectives

In this whiteboard design session, you will work with a group to design a solution to modernize CSLA's e-commerce and back-end services, while maintaining existing PCI compliance. To ensure compliance, you will ensure data privacy and protection across all aspects of the system, in transit and at rest. The goal is to use Azure PaaS services for the public-facing and back-end websites, while providing a way for the on-premises components to securely communicate with these services. You will also design fault-tolerance and a regional failover plan of the Azure components.

By the end of this whiteboard design session, you will have a better understanding of how to modernize a legacy web app by retargeting it for the cloud, taking advantage of the many services Azure provides to enhance functionality and secure your solution's components by following best practices for PCI compliance and security.

## Step 1: Review the customer case study

**Outcome**

Analyze your customer's needs.

Timeframe: 15 minutes

Directions: With all participants in the session, the facilitator/SME presents an overview of the customer case study along with technical tips.

1. Meet your table participants and trainer.

2. Read all the directions for steps 1-3 in the student guide.

3. As a table team, review the following customer case study.

### Customer situation

The Contoso Sports League Association (CSLA) is one of the largest sports franchises. They have over 100 championships in their history and a huge, passionate fan base. They run a highly successful e-commerce website that sells merchandise to their legions of sports fans. The website is built using ASP.NET Core and currently hosted in a co-location.

They accept payment by credit card and owing to their high annual volume (in the tens of millions, processing about 50K per day) of transactions, need to ensure that they are Payment Card Industry Data Security Standards (PCI DSS) Level 1 compliant. Their website hosts the shopping cart and checkout process, but they defer the credit card authorization and capture responsibilities of the credit card processing to a third-party payment gateway. This payment gateway provides a web application programming interface (API) that is invoked over Transport Layer Security (TLS) from Contoso server-side logic. The call includes the credit card holder data (name, number, and so on) and returns a status indicating a success or failure in authorizing and capturing payment against the credit card. It is called after the customer clicks checkout, as a part of processing the order. They currently store their customer and profile data in SQL Server 2014.

In addition to the public facing e-commerce website, they have a backend website that supports their call center. Call center employees use this admin website to view customer orders. Customers can call in to the call center to place orders and pay for orders with their credit cards by phone.

CSLA manages the order fulfillment process. When an order arrives, they store the order details in their SQL database, and send a message for each order to their inventory management system running the warehouse. CSLA experiences a roughly 12-hour window that spans east to west coast business hours, during which they get most of their orders. The warehouse receives the message (which simply contains the order ID from the database), pulls up the order details identified in the message (by a lookup against the database), and then for each item in the order queues up a separate process to locate the item in inventory or place an order for it with their supplier. Once this initial status for each item in the order is collected, the inventory status is updated in the database and a confirmation email is sent to the customer indicating the estimated delivery date of their completed order (and if any items are in backorder). This inventory lookup rarely takes more than a few hours and never more than a day.

They have reached a point where managing their server infrastructure is becoming a real challenge. Contoso wants to understand more about platform as a service (PaaS) solutions. They wonder if PaaS could help them focus their efforts more on the core business value rather than infrastructure. They have observed that Azure has received PCI compliance certification and are interested in moving their solution to Azure. "We're finding that with every upgrade, we're spending more and more engineering time on infrastructure and less on the experience that matters most to our fan base," says Miles Strom, Chief Executive Officer (CEO) of Contoso Sports League Association, "we need to rebalance those efforts."

One example is in how they manage the usernames and passwords for call center operators and support staff, as applied to the call center admin website. Today they have a homegrown solution that stores usernames and passwords in the same database used for storing merchandise information. They have experimented with other third-party solutions in the past, and their employees found it jarring to see another company's logo displayed when logging into their own call center website. In creating their identity solution, they want to ensure they can brand the login screens with their own logo. Additionally, Contoso is concerned about hackers from foreign countries/regions gaining access to the administrator site. Before they choose an identity solution, they would like to see how it indicates such attempts.

There is one architectural enhancement Contoso would like to make in the transition to a PaaS solution. When a visitor loads the home page, it gets the list of featured products on offer (consisting of the product image, title, and URL) from the Offers service. The home page does it using a client-side GET request against an ASP.NET Web API service that is executed as the page loads in the browser. Contoso anticipates growing the functionality of this service and would like to scale it independently of the website.

Contoso is also looking to augment their data analytics story by introducing a data warehouse to enable them to analyze their historical data over time, particularly as their number of transactions soars in the cloud. They would like to plan for a solution that moves the data from their OLTP database into their data warehouse on a nightly basis, ideally with the minimum amount of infrastructure or development effort.

### Customer needs

1. Make architectural decisions that help to minimize engineering around infrastructure in favor of those that deliver core business value. Contoso is interested in understanding more about PaaS solutions.

2. Maintain existing PCI compliance.

3. Ensure data privacy and protection across all aspects of the system, in transit and at rest.

4. They want to be able to scale their offers' API independently of the website.

5. Ensure that they retain their core functionality, even if the way it is accomplished under the covers might change.

6. Provide a better solution for the management of usernames and passwords.

7. Provide a regional database failover plan that will enable the customer to initiate the failover to another region, allowing their various web applications and other hosted services to roll over to a synchronized database at minimal cost.

8. A data warehouse for analyzing their transaction history.

### Customer objections

1. It is not clear to us from the Azure Trust Center just how Azure helps our solution become PCI compliant.

2. Can we provide a solution that scales to meet our public demand, but is also secure for use by our call center and warehouse?

3. Our PCI compliance requires us to have a quarterly audit and to conduct occasional penetration tests. Is it supported by Azure?

4. Can we audit the Azure data center?

5. In the past, we have relied on SOASTA CloudTest to design and execute our web load tests at scale. In moving to Azure, are we still take advantage of CloudTest?

6. Our previous infrastructure did not have great performance monitoring of our websites. What options would you recommend we investigate that would work with our web apps in Azure?

7. We have heard that Azure's data warehouse can be paused. Does that mean we must store all our data in Azure Storage first before we can pause the instances and risk losing our data?

8. We know it's possible to use Azure SQL Database as our data warehouse. What should we consider when deciding between this and Azure Synapse Analytics?

### Infographic for common scenarios

![This diagram is of a Common scenario for an E-Commerce Website. The diagram begins with an end user, includes a services tier, internet tier, and data tier, and ends at an Enterprise. The diagram also includes Microsoft Azure, and Azure Virtual Network.](media/image2.png 'Common scenario for an E-Commerce Website')

## Step 2: Design a proof of concept solution

**Outcome**

Design a solution and prepare to present the solution to the target customer audience in a 15-minute chalk-talk format.

Timeframe: 60 minutes

**Business needs**

Directions:  With all participants at your table, answer the following questions and list the answers on a flip chart:

1. Who should you present this solution to? Who is your target customer audience? Who are the decision makers?

2. What customer business needs do you need to address with your solution?

**Design**

Directions: With all participants at your table, respond to the following questions on a flip chart:

*High-level architecture*

1. Without getting into the details, the following sections will address the details, diagram your initial vision for handling the top-level requirements for the e-commerce website, call center website, and inventory lookup process. You will refine this diagram as you proceed.

*Order fulfillment*

1. How would you recommend CSLA manage the inventory lookup queues? How would you help CSLA decide between Azure Queues and Service Bus? Be sure to consider details implied by CSLA's requirements such as volume, message lifetime, and sizing. Explain the details of any computations you make.

*Notifications*

1. How would you recommend CSLA manage notifying customers as their order in the CSLA orders database is processed? Are there specific Azure services that can be used? Include details on how this would be implemented and integrated into the proposed solution for CSLA.

*Offers service*

1. Would you propose Contoso use the Azure App Service API app to meet their requirements for the Offers service?

2. If so, what specific configurations would you need to make to support your proposed topology? Specifically, how would you implement the changes and configurations required to allow for inter-app communication between the e-commerce application and the Offers service?

*Geo-resiliency*

1. How would you implement high availability for the orders database to guard against regional data center outages? Be specific on how you would configure SQL Database and Azure Storage.

2. What process would you recommend to the customer to failover in the event of an outage, ensuring their web applications and associated Azure services change over to a secondary region?

3. How long would a failover take and how much data could be lost, in terms of time?

*Access control*

1. With respect to managing access to the call center website, explain how you would recommend Contoso implement a solution that meets their requirements. Be specific about both the implementation and the process you would use to gain Contoso's acceptance of the proposed solution.

*Enabling PCI compliance*

1. Keeping only the e-commerce website and handling of cardholder data in scope for PCI, consider the following in your design:

    - Are web apps deployed in Azure App Service Environments an option?

    - Explain how using Azure App Service Environments could address the PCI requirements.

    - Keeping in mind the best choice for securing inbound and outbound traffic for an App Service Environment, detail all inbound and outbound traffic for this solution that allows it to be PCI compliant and allows it to operate within Azure. It should include traffic into and out of the solution, outbound for the e-commerce website, and any other traffic between the apps within the solution.

    - Make sure to describe in detail the network topology you are using.

    - For any inbound and outbound application communications you are securing, please detail the specific mechanisms you will use to do so.

    - If your approach includes configuration scripts, please provide an example of the scripts.

2. Would you recommend they use Azure virtual machines? Why or why not?

*Data warehouse*

1. How would you recommend Contoso implement their data warehouse?

2. How would Contoso schedule nightly data transfers from their OLTP database to their data warehouse?

**Prepare**

Directions: With all participants at your table:

1. Identify any customer needs that are not addressed with the proposed solution.

2. Identify the benefits of your solution.

3. Determine how you will respond to the customer's objections.

Prepare a 15-minute chalk-talk style presentation to the customer.

## Step 3: Present the solution

**Outcome**

Present a solution to the target customer audience in a 15-minute chalk-talk format.

Timeframe: 30 minutes

**Presentation**

Directions:

1. Pair with another table.

2. One table is the Microsoft team and the other table is the customer.

3. The Microsoft team presents their proposed solution to the customer.

4. The customer makes one of the objections from the list of objections.

5. The Microsoft team responds to the objection.

6. The customer team gives feedback to the Microsoft team.

7. Tables switch roles and repeat Steps 2-6.

## Wrap-up

Timeframe: 15 minutes

Directions: Tables reconvene with the larger group to hear the facilitator/SME share the preferred solution for the case study.

## Additional references

| Description                                                  | Links        |
| :------------------------------------------------------------ | :----------- |
| Compliance Commitments                                       |                              <http://azure.microsoft.com/en-us/support/trust-center/services/>                              |
| Azure App Services                                           |                 <https://azure.microsoft.com/en-us/documentation/articles/app-service-value-prop-what-is/>                  |
| Azure Service Environment (ASE)                              |            <https://azure.microsoft.com/en-us/documentation/articles/app-service-app-service-environment-intro/>            |
| Integrate ILB ASE with Azure Application Gateway             |             <https://docs.microsoft.com/en-us/azure/app-service/environment/integrate-with-application-gateway>             |
| Configuring ASE Network Security Groups                      |            <https://docs.microsoft.com/en-us/azure/app-service/environment/network-info#network-security-groups>            |
| Geo Distributed Scale with ASE                               | <https://docs.microsoft.com/en-us/azure/app-service/environment/app-service-app-service-environment-geo-distributed-scale>  |
| Azure Trust Center                                           |                                  <http://azure.microsoft.com/en-us/support/trust-center/>                                   |
| Azure PCI Attestation of Compliance                          |   <http://download.microsoft.com/download/7/1/E/71E02A19-D1A4-448F-8CEA-D6A19398ABDA/Azure%20PCI%20AOC%20Feb%202015.pdf>    |
| PCI DSS v3.0                                                 |                               <https://www.pcisecuritystandards.org/documents/PCI_DSS_v3.pdf>                               |
| Azure Data Factory                                           | <https://azure.microsoft.com/en-us/documentation/articles/data-factory-data-movement-activities/#data-factory-copy-wizard/> |
| Azure SQL Database                                           |                <https://docs.microsoft.com/en-us/azure/sql-database/sql-database-geo-replication-overview/>                 |
| Designing highly available services using Azure SQL Database |     <https://docs.microsoft.com/en-us/azure/sql-database/sql-database-designing-cloud-solutions-for-disaster-recovery>      |
| SQL Database auto-failover groups | <https://docs.microsoft.com/en-us/azure/sql-database/sql-database-auto-failover-group?tabs=azure-powershell> |


# Modern cloud apps whiteboard design session trainer guide

## Step 1: Review the customer case study

- Check in with your table participants to introduce yourself as the trainer.

- Ask, "What questions do you have about the customer case study?"

- Briefly review the steps and timeframes of the whiteboard design session.

- Ready, set, go! Let the table participants begin.

## Step 2: Design a proof of concept solution

- Check in with your tables to ensure that they are transitioning from step to step on time.

- Provide some feedback on their responses to the business needs and design.

    - Try asking questions first that will lead the participants to discover the answers on their own.

- Provide feedback for their responses to the customer's objections.

    - Try asking questions first that will lead the participants to discover the answers on their own.
    
## Step 3: Present the solution

- Determine which table will be paired with your table before Step 3 begins.

- For the first round, assign one table as the presenting team and the other table as the customer.

- Have the presenting team present their solution to the customer team.

    - Have the customer team provide one objection for the presenting team to respond to.

    - The presentation, objections, and feedback should take no longer than 15 minutes.

    - If needed, the trainer may also provide feedback.

## Wrap-up

- Have the table participants reconvene with the larger session group to hear the facilitator/SME share the following preferred solution.

## Preferred target audience

Miles Strom, CEO of Contoso Sports League Association

The primary audience are the business decision makers and technology decision makers. Usually we talk to the infrastructure managers who report to the chief information offer (CIO), or to application sponsors (like a vice president \[VP\] line of business \[LOB\], or chief marketing officer \[CMO\]), or to those that represent the business unit IT or developers that report to application sponsors.

## Preferred solution

*High-level architecture*

1. Without getting into the details, (the following sections will address the details), diagram your initial vision for handling the top-level requirements for the e-commerce website, call center website, and inventory lookup process. You will refine this diagram as you proceed.

    The Contoso Sports League Association (CSLA) was motivated to move its solution to Azure. After analyzing their requirements across the e-commerce, inventory, and customer support apps, they built their solution from the following high-level designs.

    They decided on a solution that at a high level appears as follows:

    ![Diagram of the preferred solution. From a high-level, web apps hosting the e-commerce and call center websites access APIs hosted in API Apps, all hosted within an App Service Environment to enable secure communication. Access to call center website available through VPN connection only.](media/preferred-solution.png 'Preferred solution diagram')

    From a high-level, they have Web Apps hosting the e-commerce and call center websites, API Apps hosting web services and Logic Apps hosting integration with SMS. Azure Traffic Manager is used for routing to the appropriate region for high availability. The Web and API Apps can be hosted within an Internal Load Balanced (ILB) App Service Environment (ASE) that enables them to take advantage of Network Security Groups to lock down inbound and outbound communication to the App Services it hosts. A Web Application Firewall (WAF) provided by an Azure App Gateway is hosted in its own subnet and NSGs. Internet traffic flows through the WAF to the e-commerce website (hosted within the ASE), which only allows inbound traffic from the WAF. When customers visit the website, they are presented orders whose data comes from the Offers Service REST API hosted within an API App. Orders come in from customers via the publicly accessible endpoint of the e-commerce website. The credit card is validated as a part of the checkout process by making a call to a third-party payment gateway. Once authorized and payment is captured, the order data is stored in the orders database on SQL DB and the inventory lookup message is sent to the Inventory Lookup queue. An Azure Function hosts the process for creating the PDF receipts for customer purchases. Customers are notified via SMS as their order is processed. This process involves a process running in a Logic App that integrates the SQL DB with a third-party solution for sending SMS text messages.

    Inventory lookup requests are queued from the e-commerce website to the queue in Azure Storage queues. The on-premises inventory app reads from this queue to kick off its internal lookup processes and writes the status back to the orders database.

    Call center operators access the call center website which, owing to the NSGs configured, is only available across the virtual private network (VPN) connection.

>**Note**: The preferred solution is only one of many possible, viable approaches.

*Order fulfillment*

1. How would you recommend CSLA manage the inventory lookup queues? How would you help CSLA decide between Azure Queues and Service Bus? Be sure to consider details implied by CSLA's requirements such a volume, message lifetime, and sizing. Explain the details of any computations you make.

    Given that CSLA did not provide specific requirements that imply a need for the more advanced queuing features that Service Bus offers (such as topics, larger message sizes, longer message lifetime, and so on), CSLA should consider using Azure Queues because it meets their requirements and is the most cost effective.

    Their volume is low, at 50K transactions per day, it translates to 50K messages per day. Their actual load per unit of time depends on their actual peak order times that is implied to be akin to 9 a.m.to 9 p.m. EST. Assuming a consistent load during business hours, that equates to about 4,000 messages per hour, which is well below what Azure Queues can support (2,000 messages per second or approximately 120,000 messages per hour for messages sized below 1 kilobyte \[KB\]).

    The case study states that rarely does an inventory lookup message take longer than a few hours and never more than a day. It means that they will never encounter the 7-day lifetime limit required by messages in Azure Queues.

    As for the individual message size, since it is just the order ID from the database, it is unlikely to be a field larger than 64 KB (the maximum message size supported by Azure Queues), or even 1 KB (the size at which Azure Queues can handle 2,000 messages per second).

*Notifications*

1. How would you recommend CSLA manage notifying customers as their order in the CSLA orders database is processed? Are there specific Azure services that can be used? Include details on how this would be implemented and integrated into the proposed solution for CSLA?

    Contoso can implement a logic app to notify customers of their order status.

    The logic app would include a frequency trigger to execute a stored procedure at an interval that will identify orders that should receive SMS notifications and update them as they are processed.

    A Twilio connector could act as the action to perform that sends the SMS message when the frequency trigger executes the stored procedure. CSLA would sign up for a free Twilio trial to get an API key. Then they would provision a Twilio connector within the logic app, and add the credentials. Then CSLA would select a Send Message action using data provided in the result set from the stored procedure, specifically the customer's phone number and their first name to include in the message, "Hello Satya, your order has shipped!"

    >**Note**: It currently involves extending the Logic App code for the Twilio connector.

*Offers service*

1. Would you propose Contoso use the Azure App Service API app to meet their requirements for the Offers service?

    Contoso could meet their requirement of scaling the Offers API independently from the main website by separating it out from the website project into its own Web API project and deploying that project to an Azure App Service API App.

2. If so, what specific configurations would you need to make to support your proposed topology? Specifically, how would you implement the changes and configurations required to allow for inter-app communication between the e-commerce application and the Offers service?

    For the home page to be able to successfully retrieve the data from the now separate Web API (for example, it is located in another origin), cross origin resource sharing (CORS) would need to be configured.

    The API app would need to be enabled for CORS, and the domains used to access the website in the list of allowed origins would need to be listed.

    Second, the Web API code would need to be updated to include the System.Web.Http.Cors package, where CORS would need to be enabled in the WebApiConfig.cs file, and the EnableCors attribute would need to be applied to the controllers or actions of the Offers service allowing the aforementioned origins and allow the GET method.

    If Contoso chooses to open access of the Offers service for integration by partners they should also consider implementing API management in front of their API App hosted Web API. This would enable them to lock down access by requiring a key, apply policy (such as rate limiting requests), and monitor usage by API customers.

*Geo-resiliency*

1. How would you implement high availability for the orders database to guard against regional data center outages? Be specific on how you would configure SQL Database and Azure Storage_

    Azure SQL Database auto-failover groups is a SQL Database feature designed to automatically manage geo-replication relationship, connectivity, and failover at scale. With it, the customers gain the ability to automatically recover multiple related databases in the secondary region after catastrophic regional failures or other unplanned events that result in full or partial loss of the SQL Database service's availability in the primary region. Additionally, they can use the readable secondary databases to offload read-only workloads. Because auto-failover groups involve multiple databases, they must be configured on the primary server. Both primary and secondary servers must be in the same subscription. Auto-failover groups support replication of all databases in the group to only one secondary server in a different region. Active geo-replication, without auto-failover groups, allows up to four secondaries in any region.

    Provision the Azure Storage Account with RA-GRS redundancy with a primary and secondary geographic location matching those of the SQL databases, so that in the event of an outage all backup regions have copies of the data. It may affect your choice of SQL database secondary regions because the primary/secondary regions pairs for storage are predefined and not user selectable (e.g., West US primary will use East US as secondary). The replication between the primary storage account region and secondary storage account region is asynchronous to it does not impact the latency of requests made against the primary region, albeit some data loss might be possible if it has not replicated to the secondary region in the event of a disaster.

    Finally, deploy copies of the App Services to the backup regions. You will have to consider a process of how you update these instances when the primary region gets updates. These can initially be deployed to resources with minimal scale out instance sizes, and increased when failover event occurs.

2. What process would you recommend to the customer to failover in the event of an outage, ensuring their web applications and associated Azure services change over to a secondary region?

    When using auto-failover groups (in-preview) to manage database recovery and any outage that impacts one or several of the databases in the group results in automatic failover. You can configure the auto-failover policy that best meets your application needs, or you can opt out and use manual activation. Whether you use manual or automatic failover activation, failover switches all secondary databases in the group to primary. After the database failover is completed, the DNS record is automatically updated to redirect the end-points to the new region.

    Azure Traffic Manager can be used along with health probes to monitor the App Services hosted within each region. Traffic Manager routes all internet traffic to the Application Gateway WAF, which in turn securely connects into the ILB App Service Environment to the e-commerce website. If the health probes indicate a certain number of failures within a region, it automatically starts routing traffic to the secondary region. This topology can also be used for horizontally scaling out apps located within the geo-distributed ASEs, enabling extreme load handling. For geographic redundancy, the application's resources are deployed to Region 1 and 2.

    ![All internet traffic is routed through Traffic Manager, which will send traffic to a secondary region if the primary region is out](media/traffic-manager-region-failover.png 'Regional failover of app services with Traffic Manager')

    Understand that for Azure Storage, the geo-failover process is controlled by Azure. in the event of a major disaster that affects the primary location, Azure will first try to restore the data in the primary location. Failing that, affected customers will be notified via their subscription contact information. As part of the failover, the customer's "account.\<service\>.core.windows.net" DNS entry would be updated to point from the primary location to the secondary location. In other words, the connection information to Azure Storage does not need to be changed in the application configuration.

3. How long would a failover take and how much data could be lost, in terms of time?

    The amount of time a failover takes is the Recovery Time Objective (RTO) and the amount of data loss that might transpire due to any replication latency is the Recovery Point Objective (RPO).

    For SQL Database on the Premium Tier, the RTO is less than 30 seconds and the RPO is less than 5 seconds.

    For Azure Storage, the RTO is about 24 hours and the RPO is typically less than 15 minutes, although this has no explicit SLA. Given the potentially long RTO and RPO for Azure Storage, Contoso might consider using RA-GRS storage and when a failover happens use the RA-GRS for read and a separate storage account for the writing of new files.

*Access control*

1. With respect to managing access to the call center website, explain how you would recommend Contoso implement a solution that meets their requirements. Be specific about both the implementation and the process you would use to gain Contoso's acceptance of the proposed solution_

    Contoso could capitalize on Azure Active Directory to manage the user accounts for the call center staff. They would need to provision an Azure Active Directory tenant in the Premium Tier to provide the branding. Once they have the tenant, they can create login screen branding by using the management portal.

    ![Use the Azure Active Directory Status section to configure custom branding for your company.](media/image4.png 'Status section')

    From there they specify images for the banner logo, a tile logo, and large illustration, and provide some custom text.

    ![In the Configure company branding blade, select a file to use as the large image that displays to the left of the custom login form.](media/image5.png 'Configure company branding blade')

    It would result in something like the following for Contoso:

    ![Screenshot of the Contoso sign-in webpage.](media/image6.png 'Contoso sign-in webpage')

    With respect to addressing Contoso's concerns over foreign hackers, Azure Active Directory can help by identifying logins from multiple geographic locations by using the report "Sign ins from multiple geographies." To demonstrate the function of it to Contoso, one approach to accomplish a login from a foreign IP is to spin up a virtual machine in Azure in a foreign geography, remote desktop into it, open the browser, and navigate to the Contoso admin site and log in. Then log in from a local machine at the same time. Within an hour or two the suspicious login would be listed in the report.

    Provided that the call center administrator website is deployed to a web app and that currently anyone listed as a user in Azure Active Directory is a user who should have access to the call center website, since the case study does not stipulate any other more granular requirements, the setup for integrating Azure Active Directory access control requires no code on the part of Contoso, just configuration. This configuration is accomplished using the Azure portal (at https://portal.azure.com), navigating to the web app, and on the Settings blade selecting Authentication/Authorization. Then in the Authentication/Authorization blade, choose Login with Azure Active Directory, and then configure the Azure Active Directory authentication provider to create a new application in AAD or to use an existing application.

    ![On the Azure Portal, Authentication/Authorization blade, App Service Authorization is set to On, Users must Log in with Azure Active Directory when their request is not authenticated, and Authentication Provider is Azure Active Directory.](media/image7.png 'Azure Portal, Authentication/Authorization blade')

    Once applied, any access to the call center admin website will automatically be redirected to first log in through Azure Active Directory, and users would need to be created in Azure Active Directory to acquire access.

*Enabling PCI compliance*

1. Keeping only the e-commerce website and handling of cardholder data in scope for PCI, consider the following in your design:

    - Are web apps deployed in Azure App Service Environments an option?

    - Explain how using Azure App Service Environments could address the PCI requirements.

    - Keeping in mind the best choice for securing inbound and outbound traffic for an App Service Environment, detail all inbound and outbound traffic for this solution that allows it to be PCI compliant and allows it to operate within Azure. It should include traffic into and out of the solution, outbound for the e-commerce website, and any other traffic between the apps within the solution.

    - Make sure to describe in detail the network topology you are using.

    - For any inbound and outbound application communications you are securing, please detail the specific mechanisms you will use to do so.

    - If your approach includes configuration scripts, please provide an example of the scripts.

    While web apps are certified as PCI compliant, they are not immediately PCI compliant when used by the customer. The PCI requirements 1.2.1, 1.3.3, and 1.3.5 require restricting outbound access to only that which is necessary for the cardholder environment. In the case of CSLA, it means that the only outbound communication allowed should be to Azure (for monitoring) and to the payment gateway. Web apps in the Standard Tier have no mechanism for restricting the outbound traffic.

    To remedy this, the web and API App Services should be hosted within an App Service Environment (ASE), using Isolated Tiers. ASE v2 is an App Service feature that provides a fully isolated and dedicated environment for securely running App Service apps at high scale. The ASE itself provides a hosting infrastructure that is deployed within a subnet of a Virtual Network (VNET). The ASE exposes only an Internal Load Balancer (ILB) endpoint for access to the App Service instances it hosts. Then, an Application Gateway of the Web Application Firewall (WAF) SKU should be deployed between the public IP address used by Internet clients to access the website and the ILB ASE endpoint. The ASE and the Application Gateway are deployed to two different subnets. Network Security Groups (NSG) are configured so that the subnet that contains the ASE only allows access from the subnet which contains the Application Gateway.

    If restricting the _inbound_ communication (for example limiting by IP, port, protocol) to a web app from the Internet, then you need to:

    - Provision an ILB ASE, which will create an Azure Virtual Network.

    - Provision the app hosting plan from the ASE pool of resources, in an Isolated Tier.

    - Provision a web app in that App Service plan (no need to create a point-to-site VPN connection for the web app).

    - Provide an internet routable domain name to be used with the app in the ILB App Service Environment.

    - Provide a public DNS name that is used later to point to the Application Gateway.

    - Create a separate subnet from the one the ILB App Service Environment uses. This new subnet will be used for the Azure Application Gateway.

    - Create an Application Gateway inside the separate subnet, and configure it to point to the public web app within the ILB ASE. You must select the WAF tier during creation.

    - Configure the web app to honor the custom domain name and edit the public DNS host name that points to the Application Gateway.

    - Create an NSG and apply it to the virtual network subnet in which the ASE runs (by default the rules included will prevent access from the Internet).

    - The NSG contains a default rule that enables the IPs in the VNet to talk to the ASE subnet. Another default rule enables the load balancer, also known as the public VIP, to communicate with the ASE.

    - Add a rule to the NSG allowing Internet access to the ports 454-455. To see the ports, select App Service Environment > IP addresses.

    If you are interested in restricting the _outbound_ communication from a web app to a service on the Internet, then you need to:

    - Configure the ASE, virtual network, Azure Application Gateway, App Service plan, and web app as above.

    - Add two outbound rules to the NSG: one that allows access to permitted service and another that denies all outbound Internet.

    - Configure your outbound security rules to enable network access to the ASE dependencies. If you block any of them, your ASE stops working. Reference: <https://docs.microsoft.com/en-us/azure/app-service/environment/network-info#network-security-groups>

    For CSLA's situation, inbound access to the e-commerce web app does not need to be restricted, but the outbound communication to the payment gateway does need to be restricted.

    To meet the antivirus requirement, you need only deploy to Azure since that requirement is itself met by Azure and managed against the virtual machines running your web app on your behalf.

    By structuring the web app so all it does it handle the e-commerce transaction, you would meet the server specialization requirement. By capitalizing on web apps, you are inherently addressing the patching requirement since Azure handles that for you (except any custom code or libraries your application may use).

    There is no need to store cardholder data in this scenario, so by having SSL the requirement for protection of data in transit and at rest is also met.

2. Would you recommend they use Azure virtual machines? Why or why not?

    While virtual machines could certainly be used to enable a PCI compliant solution, they would not meet the customer requirement for minimizing infrastructure efforts.

*Data warehouse*

1. How would you recommend Contoso implement their data warehouse?

    They could use Azure Synapse Analytics.

2. How would Contoso schedule nightly data transfers from their OLTP database to their data warehouse?

    They would need to provision an instance of Azure Data Factory, and then utilize the Azure Data Factory Copy Wizard to setup a recurring copy from their SQL Database instance to existing tables in Azure Synapse Analytics. They could enable PolyBase in the Copy Wizard to speed up the copying process.

## Checklist of preferred objection handling

1. It is not clear to us from the Azure Trust Center just how Azure helps our solution become PCI compliant.

    The Azure Trust Center helps you understand what Azure services have been certified for PCI compliance. For example, the services with which you could build a PCI compliant solution, but it does not describe how you build a PCI compliant solution on Azure. To fully accomplish a PCI compliant solution, you must address the requirements of PCI according to how you are handling cardholder data and the scope of your services. In many cases, Azure's PCI compliance attestations will be enough to satisfy aspects of PCI compliance for your solution, but there are at minimum some items which you must handle as a part of building your application, it is up to you to define and enforce secure password policies.

2. Can we provide a solution that scales to meet our public demand, but is also secure for use by our call center and warehouse?

    Yes. Azure can provide a solution that is both scalable and secure.

3. Our PCI compliance requires us to have a quarterly audit and to conduct occasional penetration tests. Is this supported by Azure?

    Although prior approval is not required, you may still formally document upcoming penetration testing engagements against Azure by filling out the Azure Service Penetration Testing Notification Form (<https://portal.msrc.microsoft.com/en-us/engage/pentest>).

    - Penetration testing must be conducted in accordance with our terms and conditions and comply with the Microsoft Cloud Unified Penetration Testing Rules of Engagement (<https://technet.microsoft.com/mt784683>).

    - Tests that would cause a Denial of Service (DoS) are prohibited.

4. Can we audit the Azure data center?

    No. Our independent audits and certifications are shared with customers in lieu of individual customer audits. These certifications and attestations accurately represent how we obtain and meet our security and compliance objectives, and serve as a practical mechanism to validate our promises for all customers. Allowing potentially thousands of customers to audit our services would not be a scalable practice and might compromise security and privacy. Our independent third-party validation program includes audits that are conducted on an annual basis to provide verification of Azure security controls.

5. In the past, we have relied on SOASTA CloudTest to design and execute our web load tests at scale. In moving to Azure, are we still able to capitalize on CloudTest?

    Yes. Azure is a supported cloud provider for CloudTest, and your applications hosted in Azure can have load and performance tests conducted against them from SOASTA's global network of cloud resources, while monitoring results in their big-data, real-time streaming analytics platform.

6. Our previous infrastructure did not have great performance monitoring of our websites. What options would you recommend we investigate that would work with our web apps in Azure?

    Web apps in Azure include first-class support for both Microsoft Application Insights and NewRelic Application Performance Monitoring, both of which enable you to collect performance telemetry from your web apps as they are running. You can view and analyze traces from both server-side and browser-side telemetry, diagnose errors, and set alerts from within the Azure Portal. Contoso can also capitalize on Log Analytics, a feature of Microsoft Operations Management Suite, by having the Application Insights logs or the Web App Diagnostic logs pushed to a Storage Account and then picked up and made searchable using the Custom Log. Alternately, they can also push their New Relic logs into Log Analytics, as well giving them a single pane of glass to do all their monitoring through Operations Management Suite.

7. We have heard that Azure's data warehouse can be paused. Does that mean we must store all our data in Azure Storage first before we can pause the instances and risk losing our data?

    Azure Synapse Analytics uses storage in two ways, and both enable the data to exist even while the SQL DW instance is paused. For data that is managed by Azure Synapse Analytics (e.g., it is inserted directly into relational or columnar tables), it is stored in Azure Premium Storage. For data supporting external tables in SQL DW, this data resides in Azure Standard Storage and is referenced via PolyBase, a component of Azure Synapse Analytics.

8. We know it's possible to use Azure SQL Database as our data warehouse. What should we consider when deciding between this and Azure Synapse Analytics?

    It is true that Azure SQL Database can be used as a data warehouse. This is considered an SMP-based warehouse, or symmetric multiprocessing. Azure Synapse Analytics is classified as an MPP-based warehouse, or massively parallel processing. As a rule, SMP-based warehouses are best suited for small to medium data sets (up to 4-100 TB), while MPP is often used for big data. The delineation between small/medium and big data is partly to do with your organization's definition and supporting infrastructure.

    Beyond data sizes, the type of workload pattern is likely to be a greater determining factor. For example, complex queries may be too slow for an SMP solution, and require an MPP solution instead. MPP-based systems are likely to impose a performance penalty with small data sizes, due to the way jobs are distributed and consolidated across nodes. If your data sizes already exceed 1 TB and are expected to continually grow, consider selecting an MPP solution. However, if your data sizes are less than this, but your workloads are exceeding the available resources of your SMP solution, then MPP may be your best option as well. Given this, consider Azure Synapse Analytics for small and medium datasets, where the workload is compute and memory intensive.

    Azure Synapse Analytics provides CSLA with a datastore that contains pre-aggregated data using column names that make sense to business users and analysts, a restructured schema to simplify data relationships, and consolidated tables. It also keeps historical data separate from the source transaction systems for performance reasons.

## Customer quote (to be read back to the attendees at the end)

"I can sleep better at night knowing that our e-commerce solution is scalable to handle our biggest days, doesn't sacrifice our required PCI compliance, and actually lowers our infrastructure burden."

Miles Strom, CEO of Contoso Sports League Association

-->
![Microsoft Cloud Workshops](https://github.com/Microsoft/MCW-Template-Cloud-Workshop/raw/master/Media/ms-cloud-workshop.png 'Microsoft Cloud Workshops')

<div class="MCWHeader1">
最新のクラウド アプリ
</div>

<div class="MCWHeader2">
 ホワイトボード設計セッション トレーナー用ガイド
</div>

<div class="MCWHeader3">
2020 年 3 月
</div>

このドキュメントに記載されている情報 (URL や他のインターネット Web サイト参照を含む) は、将来予告なしに変更することがあります。別途記載されていない場合、このソフトウェアおよび関連するドキュメントで使用している会社、組織、製品、ドメイン名、電子メール アドレス、ロゴ、人物、場所、出来事などの名称は架空のものです。実在する商品名、団体名、個人名などとは一切関係ありません。お客様ご自身の責任において、適用されるすべての著作権関連法規に従ったご使用をお願いいたします。著作権法による制限に関係なく、マイクロソフトの書面による許可なしに、このドキュメントの一部または全部を複製したり、検索システムに保存または登録したり、別の形式に変換したりすることは、手段、目的を問わず禁じられています。ここでいう手段とは、複写や記録など、電子的、または物理的なすべての手段を含みます。

マイクロソフトは、このドキュメントに記載されている内容に関し、特許、特許申請、商標、著作権、またはその他の無体財産権を有する場合があります。別途マイクロソフトのライセンス契約上に明示の規定のない限り、このドキュメントはこれらの特許、商標、著作権、またはその他の知的財産権に関する権利をお客様に許諾するものではありません。

製造元名、製品名、URL は、情報提供のみを目的としており、これらの製造元またはマイクロソフトのテクノロジを搭載した製品の使用について、マイクロソフトは、明示的、黙示的、または法令によるいかなる表明も保証もいたしません。製造元または製品に対する言及は、マイクロソフトが当該製造元または製品を推奨していることを示唆するものではありません。掲載されているリンクは、外部サイトへのものである場合があります。これらのサイトはマイクロソフトの管理下にあるものではなく、リンク先のサイトのコンテンツ、リンク先のサイトに含まれているリンク、または当該サイトの変更や更新について、マイクロソフトは一切責任を負いません。リンク先のサイトから受信した Web キャストまたはその他の形式での通信について、マイクロソフトは責任を負いません。マイクロソフトは受講者の便宜を図る目的でのみ、これらのリンクを提供します。また、リンクの掲載は、マイクロソフトが当該サイトまたは当該サイトに掲載されている製品を推奨していることを示唆するものではありません。

© 2019 Microsoft Corporation. All rights reserved.

Microsoft および <https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/Usage/General.aspx> (英語) に掲載されているその他の商標は、マイクロソフト グループ各社の商標です。その他すべての商標は、その所有者に帰属します。

**目次**

<!-- TOC -->

- [トレーナー情報](#トレーナー情報)
  - [トレーナーの役割](#トレーナーの役割)
  - [ホワイトボード設計セッションの流れ](#ホワイトボード設計セッションの流れ)
  - [ホワイトボード設計セッション開始前: 準備について](#ホワイトボード設計セッション開始前:-準備について)
  - [ホワイトボード設計セッション進行中: ホワイトボード設計セッションの効果的を高めるためのヒント](#ホワイトボード設計セッション進行中:-ホワイトボード設計セッションの効果的を高めるためのヒント)
- [最新のクラウド アプリホワイトボード設計セッション生徒用ガイド](#最新のクラウド-アプリホワイトボード設計セッション生徒用ガイド)
  - [要約と学習目標](#要約と学習目標)
  - [ステップ 1: 顧客事例の確認](#ステップ-1:-顧客事例の確認)
    - [顧客の状況](#顧客の状況)
    - [顧客のニーズ](#顧客のニーズ)
    - [顧客の反論](#顧客の反論)
    - [一般的なシナリオのインフォグラフィック](#一般的なシナリオのインフォグラフィック)
  - [ステップ 2: 概念実証ソリューションの設計](#ステップ-2:-概念実証ソリューションの設計)
  - [ステップ 3: ソリューションのプレゼンテーション](#ステップ-3:-ソリューションのプレゼンテーション)
  - [まとめ](#まとめ)
  - [参考資料](#参考資料)
- [最新のクラウド アプリホワイトボード設計セッション トレーナー用ガイド](#最新のクラウド-アプリホワイトボード設計セッション-トレーナー用ガイド)
  - [ステップ 1: 顧客事例の確認](#ステップ-1:-顧客事例の確認-1)
  - [ステップ 2: 概念実証ソリューションの設計](#ステップ-2:-概念実証ソリューションの設計-1)
  - [ステップ 3: ソリューションのプレゼンテーション](#ステップ-3:-ソリューションのプレゼンテーション-1)
  - [まとめ](#まとめ-1)
  - [想定される顧客担当者](#想定される顧客担当者)
  - [想定されるソリューション](#想定されるソリューション)
  - [想定される反論への対応のチェックリスト](#想定される反論への対応のチェックリスト)
  - [顧客の声 (最後に参加者にもう一度読んでいただく)](#顧客の声-(最後に参加者にもう一度読んでいただく))

<!-- /TOC -->

# トレーナー情報<a name="トレーナー情報"></a>

お忙しい中、トレーナーとしてホワイトボード設計セッションにお力添えいただきありがとうございます。

## トレーナーの役割<a name="トレーナーの役割"></a>

トレーナーには以下のことが求められます。

- 学習を安全に行える環境を作成すること。

- 参加者の思考を促すこと。

- 参加者を学習プロセスに積極的に参加させること。

- 学習プロセスを管理すること (時間を守る、トピックに沿う、参加者のメリットになるように調整する)。

- 個々の参加者が確実に理解できるようにすること。

- 参加者全員をまとめること。

- 学習プロセスに関連する知見や経験を提示すること。

- ホワイトボード設計セッションの議論を効果的にリードすること。

- 参加者の成果物の品質と適切であるかどうかを監督すること。

- フィードバック プロセスを効果的にリードすること。

## ホワイトボード設計セッションの流れ<a name="ホワイトボード設計セッションの流れ"></a>

各ホワイトボード設計セッションは以下の手順で進められます。

**ステップ 1: 顧客事例の確認 (15 分)**

**成果**

顧客のニーズを分析する。

- 顧客の背景、状況、ニーズ、技術的要件

- 顧客の現在のインフラストラクチャとアーキテクチャ

- 想定される問題、反論、障害

**ステップ 2: 概念実証ソリューションの設計 (60 分)**

**成果**

ソリューションを設計し、15 分の講義形式で提供先の顧客の担当者に行うソリューションのプレゼンテーションに向けて準備する。

- 提案先の顧客の担当者を把握します。

- ソリューションで対応する顧客のニーズを把握します。

- ソリューションを設計し、図示します。

- ソリューションのプレゼンテーションに向けて準備します。

**ステップ 3: ソリューションのプレゼンテーション (30 分)**

**成果**

顧客に向けてソリューションのプレゼンテーションを行う。

- ソリューションのプレゼンテーションを行います。

- 顧客からの反論に対応します。

- フィードバックを受けます。

**まとめ (15 分)**

- 採用されたソリューションを再検討します。

## ホワイトボード設計セッション開始前: 準備について<a name="ホワイトボード設計セッション開始前:-準備について"></a>

ホワイトボード設計セッションを開始する前に、以下の準備を行います。

- 生徒用ガイド (顧客事例を含む) とトレーナー用ガイドを熟読します。

- すべてのキー ポイントと作業についてよく理解します。

- 重点を置くポイント、参加者から引き出したい質問、伝え方を計画し、質問に答えられるように準備します。

- ホワイトボード設計セッションを開始する前に顧客事例について検討し、アイデアをさらに掘り出します。

- 後で利用できるようにメモを取ります。

## ホワイトボード設計セッション進行中: ホワイトボード設計セッションの効果を高めるためのヒント<a name="ホワイトボード設計セッション進行中:-ホワイトボード設計セッションの効果的を高めるためのヒント"></a>

**トレーナー用ガイド**を参照して、トピックに沿って進めながらタイミングを計ります。

ホワイトボード設計セッションの**詳細をすべて覚えることはありません**。

参加者が作業を行っている間に**その先を見れば、内容を思い出す**ことができます。

- 必要に応じて**作業とホワイトボード設計セッションのペース**を調整して、プレゼンテーション、フィードバック、共有の時間を確保します。

- 自身の経験から**例、注意点、筋書きを追加**します。注意点を明確化し効果的に伝えられるような筋書きを考えましょう。

- **「一時退避所」を設けて**、ホワイトボード設計セッションの範囲外の問題や疑問が発生したらいったん保留し、後で回答できるようにします。このような問題を解決する方法を決めておくと、トピックから脱線することなく対応することができます。

***セッションを楽しみましょう**。全員で楽しむように参加者に働きかけます。*

**参加者に積極的な参加を促します。**自身の知識を話すときにも、常に参加者の積極的な参加を促しましょう。

**参加者に質問を投げかけて**、グループが積極的に学習プロセスに参加するようにします。

可能な限り**最初に質問する**ようにします。トピックの内容に入る前に、そのトピックに関する参加者の意見や経験を把握します。最初に質問すると、参加者の知識や経験のレベルを評価できるうえ、参加者がトレーナーの意見に対してオープンに対応できます。

**回答を待ちます**。「(○○の) 経験は?」といった質問を投げかけた後は、答えが返ってくるまで待ちます。多少の沈黙が生まれてもかまいません。慌ててトレーナーが沈黙を破ると、参加者は積極的な参加を求められているわけではないと感じ、受身の姿勢になりがちです。参加者に考えるきっかけを与え、回答がないようなら再度質問を繰り返しましょう。そうすればたいていは回答が得られます。

# 最新のクラウド アプリホワイトボード設計セッション生徒用ガイド<a name="最新のクラウド-アプリホワイトボード設計セッション生徒用ガイド"></a>

## 要約と学習目標<a name="要約と学習目標"></a>

このホワイトボード設計セッションでは、CSLA の eコマース サービスとバックエンド サービスを刷新したソリューションをグループで設計します。ソリューションは、変更前と同様に PCI に準拠するものとします。コンプライアンスを遵守するため、システム全体で通信中と格納中のどちらの状態のデータもプライバシーを守り、保護する必要があります。目標は、外部に公開する Web サイトとバックエンド Web サイトに Azure PaaS サービスを使用すること、およびオンプレミス コンポーネントとこれらのサービスの間に安全な通信方法を実装することです。また、フォールト トレランスでリージョン内のフェールオーバーに対応した Azure コンポーネントを設計することが求められます。

このホワイトボード設計セッションを修了すると、レガシ Web アプリをクラウド向けに刷新する方法、および各種 Azure サービスを利用してソリューションのコンポーネントの機能や安全性を強化する方法を、PCI 準拠やセキュリティのベスト プラクティスに従いながら習得できます。

## ステップ 1: 顧客事例の確認<a name="ステップ-1:-顧客事例の確認"></a>

**成果**

顧客のニーズを分析する。

時間: 15 分

指示: セッション参加者全員が集まり、進行役または SME が顧客事例の概要と技術的なヒントを提示します。

1. 自班の参加者とトレーナーが集まります。

2. 生徒用ガイドのステップ 1 ～ 3 の指示をすべて読みます。

3. 班全体で下記の顧客事例を確認します。

### 顧客の状況<a name="顧客の状況"></a>

Contoso Sports League Association (CSLA) は大手スポーツ フランチャイズで、これまでに 100 以上の選手権を開催しており、熱心なファンが非常に多く存在します。同社が運用する eコマース Web サイトも好調で、かなりの数のスポーツ ファンが商品を購入しています。サイトは ASP.NET Core で構築されていて、現在はコロケーションでホストされています。

このサイトはクレジット カード払いに対応しており、年間トランザクション数が膨大であるため (年間数千万件、1 日あたり約 5 万件)、Payment Card Industry Data Security Standards (PCI DSS) Level 1 に準拠する必要があります。この Web サイトではショッピング カートと精算処理をホストしていますが、クレジット カード処理の認証と取得はサードパーティの支払いゲートウェイに任せています。支払いゲートウェイでは Web アプリケーション インターフェイス (API) が提供され、Contoso のサーバー側スクリプトから Transport Layer Security (TLS) を通じて呼び出すことができます。呼び出しにはクレジット カード所有者のデータ (氏名や番号など) が含まれ、クレジット カードの認証や支払い請求が成功したか失敗したかを示す状態が返されます。また、顧客がチェックアウトをクリックした後に注文処理の一部として呼び出されます。現在、顧客データやプロファイル データは SQL Server 2014 に格納されています。

外部に公開する eコマース Web サイト以外に、コール センターをサポートするバックエンド Web サイトも存在します。コール センター担当者は、この管理 Web サイトで顧客からの注文を表示します。またコール センターでは、顧客からの電話で注文を受けたりクレジット カードでの支払いに対応したりしています。

CSLA では、注文調達プロセスを管理しています。注文を受けると、その詳細を SQL Database に格納し、倉庫の運用に使用される在庫管理システムに各注文のメッセージを送信します。CSLA の営業時間は米国東部から西部まで約 12 時間におよび、注文のほとんどはその間に発生します。データベースから倉庫に送られるメッセージには、注文 ID のみが含まれます。倉庫ではメッセージの注文 ID を基にデータベースを検索して注文の詳細を取得し、注文の各アイテムを個別のプロセスとしてキューに入れ、アイテムを在庫から探したり供給元に発注したりします。注文の各アイテムの初期状態が収集されたら、データベースの在庫状態が更新され、完了した注文の配送予定日 (および入荷待ちアイテムの有無) を含む確認メールが顧客に送信されます。在庫の検索はほとんどの場合数時間程度で完了し、1 日以上かかることはありません。

Contoso では、サーバー インフラストラクチャの管理負荷が深刻な問題となっています。また、サービスとしてのプラットフォーム (PaaS) ソリューションについて理解を深めたいと考えています。同社では、PaaS ソリューションがインフラストラクチャのために割く労力を軽減し、重要なビジネス価値の提供に集中するために役立つかどうかを検討しており、Azure が PCI コンプライアンス認定を受けていることを知って、自社ソリューションを Azure に移行することに興味を示しています。Contoso Sports League Association 最高経営責任者 (CEO) の Miles Strom 氏は次のように述べています。「アップグレードのたびにインフラストラクチャのエンジニアリングに要する時間が増えて、ファンの皆様への影響が大きいエクスペリエンスにかける時間が減っていることがわかりました。このバランスを改めなければなりません」

その例の 1 つが、Azure をコール センター管理 Web サイトに導入した場合にコール センター担当者やサポート スタッフのユーザー名とパスワードを管理する方法です。現在は自社開発ソリューションを使用しており、ユーザー名とパスワードは商品情報が格納されているものと同じデータベースに保存されています。過去にはサードパーティのソリューションを試したこともありましたが、コール センター管理 Web サイトにログインするときに他社のロゴが表示されるのが煩わしく感じられました。新たに作成する ID ソリューションでは、自社のロゴをあしらった独自デザインのログイン画面を使用したいと考えています。また、外国や他地域のハッカーから管理サイトに侵入されるリスクについても憂慮しており、ID ソリューションを選定する前に、このような攻撃がどのように示されるかを確認したいと考えています。

Contoso は、PaaS ソリューションへの移行にあたってアーキテクチャを強化したい点があります。ユーザーがホーム ページを読み込んだときに、Offers サービスが推薦する注目商品 (商品画像、見出し、URL を含む) のリストを取得するようにします。ブラウザーにホーム ページが読み込まれると、クライアントから ASP.NET Web API サービスへの GET 要求が実行され、注目商品が取得されます。このサービスは成長が予想されるため、Web サイトと独立してスケーリングできるようにします。

このほか、データ ウェアハウスを導入してデータ分析機能を強化し、クラウドでトランザクション数が急増したときを中心に履歴データを随時分析できるようにすることを目指しています。OLTP データベースのデータを夜間に自社データ ウェアハウスに移行するソリューションを計画しており、理想的にはインフラストラクチャや開発の負担を最小限に抑えたいと考えています。

### 顧客のニーズ<a name="顧客のニーズ"></a>

1. インフラストラクチャのエンジニアリングを最小限に抑えて重要なビジネス価値の提供のために労力を活用できるようにするアーキテクチャを決定する。Contoso は PaaS ソリューションについて理解を深めたいと考えています。

2. PCI コンプライアンスの遵守を維持する。

3. システム全体で通信中と格納中のどちらの状態のデータもプライバシーを守り、保護する。

4. 商品推薦 API (Offers API) を Web サイトと独立してスケーリングできるようにする。

5. 目に見えない部分を変更して目的を達成する場合でも主要機能を維持する。

6. ユーザー名とパスワードの管理ソリューションを改良する。

7. リージョン単位でのデータベース フェールオーバー プランを導入し他のリージョンにフェールオーバーできるようにして、各種 Web アプリケーションやその他のホストされているサービスを同期されているデータベースに最小限のコストで引き継げるようにする。

8. データ ウェアハウスのトランザクション履歴を分析できるようにする。

### 顧客の反論<a name="顧客の反論"></a>

1. Azure トラスト センターを見ても、自社ソリューションを PCI に準拠させるにあたって Azure がどのように役立つのかわからなかった。

2. ソリューションをスケーリングして顧客の需要に対応しながら、同時にコール センターや倉庫のセキュリティを守ることができるか?

3. PCI コンプライアンスに準拠するには四半期ごとの監査が必要であり、侵入テストの実施が求められる場合もある。これは Azure で可能か?

4. Azure データ センターは監査可能か?

5. 過去に、Web サイトの大規模負荷テストの設計と実行に SOASTA CloudTest を利用した。Azure に移行しても引き続き CloudTest を使用できるか?

6. 従来のインフラストラクチャでは Web サイトのパフォーマンス監視機能が不十分だった。自社 Web アプリと連携する Azure のオプションにはどのようなものがあるか?

7. Azure のデータ ウェアハウスは一時停止できると聞いた。インスタンスを一時停止する前に Azure Storage の自社データをすべて保存する必要があるのか、またデータを損失するリスクがあるのか?

8. Azure SQL Database を自社データ ウェアハウスとして使用可能であることは理解した。Azure Synapse Analytics と比較する場合、どのような点について考慮すればよいか?

### 一般的なシナリオのインフォグラフィック<a name="一般的なシナリオのインフォグラフィック"></a>

![eコマース Web サイトの一般的なシナリオを示した図。エンド ユーザーから始まり、サービス層、インターネット層、データ層を経由して自社につながっている。また、Microsoft Azure と Azure Virtual Network が含まれている](media/image2.png 'eコマース Web サイトの一般的なシナリオを示した図')

## ステップ 2: 概念実証ソリューションの設計<a name="ステップ-2:-概念実証ソリューションの設計"></a>

**成果**

ソリューションを設計し、15 分の講義形式で提供先の顧客の担当者に行うソリューションのプレゼンテーションに向けて準備する。

時間: 60 分

**ビジネス ニーズ**

指示: 班の参加者全員で以下の質問に回答し、フリップ チャートに回答の一覧を記載します。

1. ソリューションを提案する相手は? 提案先の顧客の担当者は? 意思決定者は?

2. このソリューションで解決が必要な顧客のビジネス ニーズは?

**設計**

指示: 班の参加者全員でフリップ チャートに記載された以下の質問に回答します。

*アーキテクチャの概要*

1. 詳細については後のセクションで扱うため、ここでは詳細には触れずに、eコマース Web サイト、コール センター Web サイト、在庫の検索プロセスの大まかな要件に対応する初期構想を図示します。この図の内容は、進行に合わせて修正します。

*注文品の調達*

1. 在庫検索キューの管理方法をどのように CSLA に推薦するか、および CSLA が Azure Queues と Service Bus のいずれかを選定する際にどのように助言するかについて検討します。処理量、メッセージの有効期間、規模などを基に、CSLA の要件について考慮します。各項目の算出方法について説明します。

*通知*

1. CSLA の注文データベースで注文が処理されたときの顧客への通知を管理する方法、およびこれに利用できる Azure サービスについて検討します。CSLA に提案するソリューションへの実装や統合の詳細についても考慮します。

*Offers サービス*

1. Offers サービスの要件に対応するため、Contoso に Azure App Service API アプリの使用を提案することを検討します。

2. 提案する場合は、そのトポロジに適合する構成の詳細を検討します。特に、eコマース アプリケーションと Offers サービスのアプリケーション間の通信を許可するために必要な変更や構成を実装する方法について考慮します。

*地理的な回復性*

1. リージョン単位でデータ センターが停止した場合に備えて注文データベースに高可用性を実装する方法について検討します。特に、SQL Database と Azure Storage の構成を明確に決定します。

2. サービス停止発生時に Web アプリケーションや関連する Azure サービスの変更をセカンダリ リージョンにフェールオーバーするプロセスについて、どの方法を推薦するかを検討します。

3. フェールオーバーに要する時間やデータ損失が発生する時間の長さについて検討します。

*アクセス制御*

1. コール センター Web サイトへのアクセスの管理について、Contoso の要件を満たすソリューションを実装する方法をどのように推薦するかを検討します。実装方法と、提案したソリューションを Contoso が採用するように推薦する方法の両方を明確にします。

*PCI コンプライアンスの遵守*

1. PCI 遵守の観点からカード所有者のデータを保持するのは処理時のみ、eコマース Web サイト内のみに制限するため、以下の点を考慮して設計します。

    - Web アプリを Azure App Service Environment にデプロイすることを考慮します。

    - PCI の要件に準拠するにあたって Azure App Service Environment がどのように役立つか説明します。

    - App Service Environment の送受信トラフィックのセキュリティに最適化するため、PCI への準拠に必要なすべての送受信トラフィックの詳細を示し、Azure で運用できるようにします。これには、ソリューションの送受信トラフィック、eコマース Web サイトへの送信トラフィック、ソリューション内のアプリ間通信のトラフィックが含まれます。

    - 使用するネットワーク トポロジの詳細を説明できるようにします。

    - アプリケーション通信の全送受信トラフィックのセキュリティを守るために使用するメカニズムを詳細に示します。

    - 構成スクリプトを作成する場合は、スクリプトの例を示します。

2. Azure 仮想マシンの使用を推奨するかどうか検討します。また、推奨する理由、しない理由を説明します。

*データ ウェアハウス*

1. データ ウェアハウスの実装方法をどのようにして勧めるか検討します。

2. 夜間に OLTP データベースから自社データ ウェアハウスにデータを転送するようにスケジュールを設定する方法について検討します。

**準備**

指示: 班の参加者全員と以下を行います。

1. 提案したソリューションでは解決されない顧客のニーズを把握します。

2. ソリューションのメリットを把握します。

3. 顧客の反論に対応する方法を検討します。

15 分の講義形式で顧客に行うソリューションのプレゼンテーションに向けて準備します。

## ステップ 3: ソリューションのプレゼンテーション<a name="ステップ-3:-ソリューションのプレゼンテーション"></a>


**成果**

15 分の講義形式で提供先の顧客の担当者にソリューションのプレゼンテーションを行う。

時間: 30 分

**プレゼンテーション**

指示:

1. 他の班と組みます。

2. 一方の班はマイクロソフト チームを、もう一方の班は顧客を担当します。

3. マイクロソフト チームは、提案するソリューションのプレゼンテーションを顧客に向けて行います。

4. 顧客側は、反論リストの中からいずれかの反論を行います。

5. マイクロソフト チームは反論に対応します。

6. 顧客側はマイクロソフト チームにフィードバックを提供します。

7. 役割を入れ替えてステップ 2 ～ 6 を繰り返します。

## まとめ<a name="まとめ"></a>

時間: 15 分

指示: 各班が集まり、進行役や SME が事例に適したソリューションを発表します。

## 参考資料<a name="参考資料"></a>

| 説明                                                  | リンク        |
| :------------------------------------------------------------ | :----------- |
| コンプライアンスへの取り組み                                       |                              <https://www.microsoft.com/ja-jp/trust-center/compliance/compliance-overview>                              |
| Azure App Service                                           |                 <https://azure.microsoft.com/ja-jp/documentation/articles/app-service-value-prop-what-is/>                  |
| Azure Service Environment (ASE)                              |            <https://azure.microsoft.com/ja-jp/documentation/articles/app-service-app-service-environment-intro/>            |
| ILB ASE を Azure Application Gateway と統合する            |             <https://docs.microsoft.com/ja-jp/azure/app-service/environment/integrate-with-application-gateway>             |
| ASE ネットワーク セキュリティ グループを構成する                      |            <https://docs.microsoft.com/ja-jp/azure/app-service/environment/network-info#network-security-groups>            |
| ASE を使用して地理的分散を実現する                               | <https://docs.microsoft.com/ja-jp/azure/app-service/environment/app-service-app-service-environment-geo-distributed-scale>  |
| Azure トラスト センター                                           |                                  <http://azure.microsoft.com/ja-jp/support/trust-center/>                                   |
| Azure PCI のコンプライアンス認定証 (英語)                         |   <http://download.microsoft.com/download/7/1/E/71E02A19-D1A4-448F-8CEA-D6A19398ABDA/Azure%20PCI%20AOC%20Feb%202015.pdf>    |
| PCI DSS v3.0 のドキュメント                                                |                               <https://www.pcisecuritystandards.org/documents/PCI_DSS_v3_2_1_JA-JP.pdf>                               |
| Azure Data Factory                                           | <https://azure.microsoft.com/ja-jp/documentation/articles/data-factory-data-movement-activities/#data-factory-copy-wizard/> |
| Azure SQL Database                                           |                <https://docs.microsoft.com/ja-jp/azure/sql-database/sql-database-geo-replication-overview/>                 |
| Azure SQL Database を使用して高可用性サービスを設計する |     <https://docs.microsoft.com/ja-jp/azure/sql-database/sql-database-designing-cloud-solutions-for-disaster-recovery>      |
| SQL Database 自動フェールオーバー グループ | <https://docs.microsoft.com/ja-jp/azure/sql-database/sql-database-auto-failover-group?tabs=azure-powershell> |


# 最新のクラウド アプリホワイトボード設計セッション トレーナー用ガイド<a name="最新のクラウド-アプリホワイトボード設計セッション-トレーナー用ガイド"></a>

## ステップ 1: 顧客事例の確認<a name="ステップ-1:-顧客事例の確認-1"></a>

- 自班の参加者と対面し、トレーナーとして自己紹介します。

- 「この顧客事例について不明な点を挙げてください」と問いかけます。

- ホワイトボード設計セッションのステップと時間を大まかに確認します。

- これで準備完了です。自班の参加者にセッションを始めていただきます。

## ステップ 2: 概念実証ソリューションの設計<a name="ステップ-2:-概念実証ソリューションの設計-1"></a>

- 各ステップを時間どおりに進められるように自班の参加者と協調します。

- ビジネス ニーズや設計に関する参加者からの回答にフィードバックを返します。

    - 参加者が自身で答えにたどり着くように導く質問を、最初に投げかけるようにします。

- 顧客の反論への対応に対してフィードバックを返します。

    - 参加者が自身で答えにたどり着くように導く質問を、最初に投げかけるようにします。
    
## ステップ 3: ソリューションのプレゼンテーション<a name="ステップ-3:-ソリューションのプレゼンテーション-1"></a>

- ステップ 3 を始める前に、自班と組む相手の班を決めます。

- 1 巡目にプレゼンテーションを行う班と顧客側を演じる班を割り当てます。

- プレゼンテーション チームは、顧客チームにソリューションのプレゼンテーションを行います。

    - 顧客チームはプレゼンテーション チームに反論を 1 つ提示し、プレゼンテーション チームはこれに対応します。

    - プレゼンテーションから反論、フィードバックの提供までを 15 分以内にまとめます。

    - 必要に応じてトレーナーもフィードバックを提供します。

## まとめ<a name="まとめ-1"></a>

- 班員は大きなセッション グループに再び合流し、ソリューションに関する以下の想定について進行役や SME から説明を受けます。

## 想定される顧客担当者<a name="想定される顧客担当者"></a>

Miles Strom 氏 (Contoso Sports League Association、CEO)

主な対象はビジネスおよびテクノロジの意思決定者となります。通常は、最高情報責任者 (CIO) に報告を行うインフラストラクチャ管理者、アプリケーションのスポンサー (事業部門担当 \[LOB\] バイス プレジデント \[VP\] や最高マーケティング責任者 \[CMO\])、アプリケーションのスポンサーに報告を行う事業部門の IT 担当者や開発者が対象となります。

## 想定されるソリューション<a name="想定されるソリューション"></a>


*アーキテクチャの概要*

1. 詳細については後のセクションで扱うため、ここでは詳細には触れずに、eコマース Web サイト、コール センター Web サイト、在庫の検索プロセスの大まかな要件に対応する初期構想を図示します。この図の内容は、進行に合わせて修正します。

    Contoso Sports League Association (CSLA) は、自社ソリューションを Azure に移行したいと考えていました。eコマース、在庫管理、カスタマー サポートの各アプリの要件を分析した結果、後述の概要設計に基づいてソリューションを構築することになりました。

    ソリューションの概要は以下のように決まりました。

    ![想定されるソリューションの図。大まかに、eコマースとコール センターの Web サイトをホストする Web アプリは、API アプリでホストされる API にアクセスする。通信の安全を確保するため、すべてのアプリが App Service Environment でホストされる。コール センター Web サイトへのアクセスは VPN 接続経由のみが許可される](media/preferred-solution.png '想定されるソリューションの図')

    大まかに見ると、eコマースとコール センターの Web サイトをホストする Web アプリ、Web サービスをホストする API アプリ、SMS をホストするロジック アプリが存在します。高可用性を得るため、トラフィックは Azure Traffic Manager で適切なリージョンにルーティングされます。Web アプリと API アプリは、ネットワーク セキュリティ グループを使用できるように Internal Load Balancer (ILB) が有効化された App Service Environment (ASE) でホストされ、そこでホストされる App Service への送受信トラフィックはロックダウンされます。Azure Application Gateway の Web Application Firewall (WAF) は、自身のサブネットと NSG の内部でホストされます。インターネット トラフィックは、WAF を経由して ASE でホストされている eコマース Web サイトに送られます。このサイトでは、WAF からの受信トラフィックのみが許可されます。顧客が Web サイトにアクセスすると、API アプリでホストされる Offers サービスの REST API で取得されたデータに基づいて注文が表示されます。注文は、eコマースのパブリック エンドポイントからアクセスした顧客から送られてきます。クレジット カードの検証は、チェックアウト プロセスの中でサードパーティの支払いゲートウェイを呼び出して実行されます。認証と支払いが完了したら、注文データは SQL DB の注文データベースに格納され、在庫検索メッセージが在庫検索キューに送られます。Azure Function では、顧客が購入した商品の PDF 受領書を作成する処理がホストされます。注文が処理されると、SMS で顧客に通知が送られます。この処理には、SMS のテキスト メッセージを送信するサードパーティ ソリューションと SQL DB を統合するロジック アプリが含まれています。

    在庫検索の要求は、eコマース Web サイトから Azure Storage キューに送られます。オンプレミスの在庫管理アプリがこのキューを読み取って内部の検索プロセスを開始し、状態を注文データベースに返して書き込みます。

    コール センター担当者からコール センター Web サイトへのアクセスは、NSG が構成されているため、仮想プライベート ネットワーク (VPN) 接続のみが許可されます。

>**注**: この事例はさまざまな方法で実現できます。ここで想定するソリューションはその一例です。

*注文品の調達*

1. 在庫検索キューの管理方法をどのように CSLA に推薦するか、および CSLA が Azure Queues と Service Bus のいずれかを選定する際にどのように助言するかについて検討します。処理量、メッセージの有効期間、規模などを基に、CSLA の要件の詳細について考慮します。各項目の算出方法について説明します。

    CSLA が提示した要件は Service Bus で提供される範囲 (トピック、メッセージのサイズや有効期間) に収まっており、これ以上高度なキュー機能は不要なため、要件を満たしつつコスト効率が最も高い Azure Queues を推薦します。

    処理量は少なく、トランザクションは 1 日あたり 5 万件、つまりメッセージ 5 万件程度です。時間あたりの負荷は、注文が集中する時間を米国東部時間の午前 9 時から午後 9 時、営業時間内の負荷が一定であると仮定すると、1 時間あたりのメッセージ数は約 4,000 件となります。Azure Queues では、1 キロバイト \[KB\] 未満のメッセージであれば最大で 1 秒あたり 2,000 件 (1 時間あたり約 12 万件) 処理できるため、十分な余裕があります。

    また、この事例では在庫検索メッセージの処理に要する時間はほとんどが数時間以内で、1 日以上かかることはありません。Azure Queues のメッセージ有効期間は 7 日間であるため、これについても問題はありません。

    メッセージの内容はデータベースから取得した注文 ID のみであるため、1 件あたりのサイズは、Azure Queues のメッセージ最大サイズである 64 KB はもちろんのこと、Azure Queues が 1 秒あたり 2,000 件の速度で処理できる 1 KB も下回ると予想されます。

*通知*

1. CSLA の注文データベースで注文が処理されたときの顧客への通知を管理する方法、およびこれに利用できる Azure サービスについて検討します。CSLA に提案するソリューションへの実装や統合の詳細についても考慮します。

    Contoso では、注文の状態を顧客に通知するロジック アプリを実装します。

    このロジック アプリには一定頻度のトリガーがあり、注文を認識するストアド プロシージャが一定間隔で実行されます。注文が処理されると、SMS で通知が送信され、データが更新されます。

    Twilio コネクタは、前述のトリガーがストアド プロシージャを実行したときに SMS メッセージを送信するアクションとして使用できます。今回は、Twilio の無料試用版にサインアップして API キーを取得します。その後、ロジック アプリに Twilio コネクタをプロビジョニングし、資格情報を追加します。次に、ストアド プロシージャから返された、顧客の電話番号や名前を含む結果セットのデータに基づくメッセージ送信アクションを選択します。メッセージには「Hello Satya, your order has shipped!」というように顧客の名前が埋め込まれます。

    >**注**: これには、Twilio コネクタに対応するためロジック アプリのコードを拡張する作業が含まれます。

*Offers サービス*

1. Offers サービスの要件に対応するため、Contoso に Azure App Service API アプリの使用を提案することを検討します。

    Offers API を Web サイトのプロジェクトから分離させてそれ自体の Web API プロジェクトに組み込み、そのプロジェクトを Azure App Service API アプリにデプロイすると、Offers API とメインの Web サイトのスケーリングを独立させるという要件を満たすことができます。

2. 上記を提案する場合は、そのトポロジに適合する構成の詳細を検討します。特に、eコマース アプリケーションと Offers サービスのアプリケーション間の通信を許可するために必要な変更や構成を実装する方法について考慮します。

    独立した Web API (異なるオリジンに存在する場合など) からホーム ページに最新データを取得するには、クロス オリジン リソース共有 (CORS) を構成する必要があります。

    この場合、API アプリで CORS を有効化し、許可された各オリジンの Web サイトにアクセスする際に使用されるドメインのリストを作成することが必要です。

    また、Web API のコードを更新し System.Web.Http.Cors パッケージを追加すること、WebApiConfig.cs ファイルで CORS を有効化すること、EnableCors 属性を Offers サービスのコントローラーやアクションに適用して前述のオリジンと GET メソッドを許可することが必要です。

    パートナー製品と統合するため Offers サービスへのアクセスを外部に許可する場合は、API アプリでホストされる Web API の管理機能を実装することも考慮します。この機能では、キーを必須にしてアクセスをロック ダウンしたり、要求の帯域制限などのポリシーを適用したり、API ユーザーによる使用状況を監視したりできます。

*地理的な回復性*

1. リージョン単位でデータ センターが停止した場合に備えて注文データベースを高可用性化する方法について検討します。特に、SQL Database と Azure Storage の構成を明確に決定します。

    Azure SQL Database の機能の 1 つである自動フェールオーバー グループでは、大規模環境で geo レプリケーションのリレーションシップ、接続、フェールオーバーを自動的に管理できます。この機能を使用すると、プライマリ リージョンで致命的な障害や予期しない事態が発生してリージョン内のすべてまたは一部の SQL Database サービスが停止した場合に、関連する複数のデータベースをセカンダリ リージョンに自動的に復旧できます。また、データの読み取りのみが必要なワークロードで読み取り専用のセカンダリ データベースを使用し、負荷を分散することができます。自動フェールオーバー グループには複数のデータベースが存在し、これらをすべてプライマリ サーバーで構成する必要があります。プライマリ サーバーとセカンダリ サーバーは、同一サブスクリプションに属している必要があります。自動フェールオーバー グループでは、1 グループ内のすべてのデータベースを、他のリージョンに存在する 1 つのセカンダリ サーバーに複製できます。有効な geo レプリケーションで自動フェールオーバー グループが構成されていない場合は、任意のリージョンに存在するセカンダリを 4 つまで使用できます。

    サービスが停止した場合にもコピーされたデータがすべてのバックアップ リージョンに保持されるように、SQL Database のプライマリ リージョンとセカンダリ リージョンを使用した RA-GRS による冗長構成の Azure ストレージ アカウントをプロビジョニングします。ストレージのプライマリ リージョンとセカンダリ リージョンのペアは事前に定義されていて (例: プライマリが米国西部の場合のセカンダリは米国東部) ユーザーは選択できません。SQL Database のセカンダリ リージョンはこの定義に従って指定します。リージョンをまたいだプライマリ ストレージとセカンダリ ストレージの間でのレプリケーションは非同期であり、プライマリ ストレージに送られた要求のレイテンシには影響しません。ただし、障害発生時にセカンダリ ストレージにコピーされていなかったデータの損失が発生する可能性があります。

    最後に、App Service のコピーをバックアップ リージョンにデプロイします。プライマリ リージョンのインスタンスが更新されたときにセカンダリ リージョンのインスタンスを更新する方法について、考慮する必要があります。初回デプロイ時には最小限のサイズのインスタンスを使用し、フェールオーバー発生時にスケール アウトすることができます。

2. サービス停止発生時に Web アプリケーションや関連する Azure サービスの変更をセカンダリ リージョンにフェールオーバーするプロセスについて、どの方法を推薦するかを検討します。

    グループ内の単一または複数のデータベースに影響を与えるサービス停止やデータベース復旧を自動フェールオーバー グループ (プレビュー期間中) で管理すると、フェールオーバーが自動的に実行されます。この機能では、自社アプリケーションのニーズに最適な自動フェールオーバー ポリシーを構成することも、ポリシーを使用せずに手動で有効化することもできます。フェールオーバーを手動で実行する場合でも自動実行する場合でも、グループ内のすべてのセカンダリ データベースがプライマリに変更されます。データベースがすべてフェールオーバーされると、DNS レコードが自動的に更新され、新しいリージョンのエンドポイントにリダイレクトされるようになります。

    Azure Traffic Manager を正常性プローブと併用すると、各リージョンでホストされている App Service を監視できます。インターネット トラフィックはすべて Traffic Manager により Application Gateway WAF にルーティングされ、ILB App Service Environment を通じて安全に接続されている eコマース Web サイトに送られます。正常性プローブによりリージョン内で一定数のエラーが検出されると、トラフィックのルーティング先が自動的にセカンダリ リージョンに変更されます。このトポロジは、地理的に分散された ASE に配置されたアプリケーションを水平方向にスケール アウトする場合にも利用可能で、非常に大きな負荷も処理できます。地理的冗長性を得るためには、アプリケーションのリソースをリージョン 1 とリージョン 2 にデプロイする必要があります。

    ![インターネット トラフィックはすべて Traffic Manager によりルーティングされる。プライマリ リージョンが停止するとセカンダリ リージョンにトラフィックが送られる](media/traffic-manager-region-failover.png 'Traffic Manager によるリージョン単位の App Service のフェールオーバー')

    Azure Storage の地理的フェールオーバー プロセスは、Azure により制御されます。大災害が発生してプライマリ リージョンが影響を受けた場合、まずはプライマリ リージョンでデータの復旧が試みられます。これが失敗した場合、サブスクリプションに登録された連絡先に通知が送られます。フェールオーバー プロセスの中で、顧客の DNS エントリ (account.\<service\>.core.windows.net) がプライマリ リージョンのものからセカンダリ リージョンのものに更新されます。このため、アプリケーションで構成されている Azure Storage への接続情報を変更する必要はありません。

3. フェールオーバーに要する時間やデータ損失が発生する時間の長さについて検討します。

    フェールオーバーに要する時間は目標復旧時間 (RTO) で示され、レプリケーションの遅延によりデータを損失する可能性がある時間の長さは目標復旧時点 (RPO) で示されます。

    Premium レベルの SQL Database の場合、RTO は 30 秒以下、RPO は 5 秒以下です。

    Azure Storage の場合、RTO は約 24 時間、RPO は通常 15 分未満ですが SLA で明示的に示されているわけではありません。Azure Storage の RTO と RPO は長くなる可能性があるため、Contoso では RA-GRS ストレージを採用し、フェールオーバー発生時には RA-GRS を読み取り専用として、別のストレージ アカウントを新規ファイルの書き込み用として使用します。

*アクセス制御*

1. コール センター Web サイトへのアクセスの管理について、Contoso の要件を満たすソリューションを実装する方法をどのように推薦するかを検討します。実装方法と、提案したソリューションを Contoso が採用するように推薦する方法の両方を明確にします。

    Contoso は、コール センター担当者のユーザー アカウントの管理に Azure Active Directory を導入することを検討しています。この場合、ブランドを構成するには Premium レベルの Azure Active Directory テナントをプロビジョニングする必要があります。テナントをプロビジョニングすると、ブランドを適用したログイン画面を管理ポータルで作成できます。

    ![Azure Active Directory の [状態] セクションで自社のカスタム ブランドを構成する](media/image4.png '[状態] セクション')

    ここでバナーのロゴ画像、タイルのロゴ画像、大きいイラスト、およびカスタム テキストを指定します。

    ![[会社のブランドを構成する] ブレードで、カスタム ログイン フォームの左側に表示する大きな画像のファイルを選択する](media/image5.png '[会社のブランドを構成する] ブレード')

    Contoso のログイン画面の例を以下に示します。

    ![Contoso のサインイン Web ページのスクリーンショット](media/image6.png 'Contoso のサインイン Web ページ')

    他地域のハッカーによるリスクについては、Azure Active Directory の「複数の地域からのサインイン」レポートでログインを特定できます。Contoso にこの機能のデモを示す方法の例を説明します。まず他地域の IP からログインするため、Azure 仮想マシンを他の地域で作成し、リモート デスクトップで接続してブラウザーを開き、Contoso の管理サイトにログインします。これと同時に、ローカル マシンからもログインします。1 ～ 2 時間程度で、不審なログインのリストがレポートに出力されます。

    コール センター管理 Web サイトが Web アプリにデプロイされていて、現時点では Azure Active Directory のリストに掲載されているすべてのユーザーがコール センター管理 Web サイトへのアクセス許可を所有しており、今回はこれ以上詳細な要件はないため、Contoso 側では構成を行うだけでよく、Azure Active Directory のアクセス制御のコードを作成する必要はありません。構成は、Azure Portal (https://portal.azure.com) で Web アプリの [設定] ブレードにアクセスし、[認証/承認] から行います。[認証/承認] ブレードで [Azure Active Directory でのログイン] を選択し、Azure Active Directory の認証プロバイダーを構成して、AAD でアプリケーションを新規作成するかまたは既存のアプリケーションを使用します。

    ![Azure Portal の [認証/承認] ブレードで [App Service の認証] がオンに設定されている。要求が認証されない場合は [Azure Active Directory でのログイン] を選択し [認証プロバイダー] に Azure Active Directory を選択する必要がある](media/image7.png 'Azure Portal の [認証/承認] ブレード')

    構成完了後は、コール センター管理 Web サイトへのアクセスはすべて自動的に Azure Active Directory による最初のログインにリダイレクトされます。アクセス許可を取得するには、Azure Active Directory でユーザーを作成する必要があります。

*PCI コンプライアンスの遵守*

1. PCI 遵守の観点から、カード所有者のデータを保持するのは処理時のみ、eコマース Web サイト内のみに制限するため、以下の点を考慮して設計します。

    - Web アプリを Azure App Service Environment にデプロイすることを考慮します。

    - PCI の要件に準拠するにあたって Azure App Service Environment がどのように役立つか説明します。

    - App Service Environment の送受信トラフィックのセキュリティに最適化するため、PCI への準拠に必要なすべての送受信トラフィックの詳細を示し、Azure で運用できるようにします。これには、ソリューションの送受信トラフィック、eコマース Web サイトへの送信トラフィック、ソリューション内のアプリ間通信のトラフィックが含まれます。

    - 使用するネットワーク トポロジの詳細を説明できるようにします。

    - アプリケーション通信の全送受信トラフィックのセキュリティを守るために使用するメカニズムを詳細に示します。

    - 構成スクリプトを作成する場合は、スクリプトの例を示します。

    Web アプリは PCI 準拠の認定を受けていますが、それだけでは顧客が使用する場合に必ずしも PCI に準拠するとは限りません。PCI 要件 1.2.1、1.3.3、1.3.5 では、カード所有者の環境で必要な場所以外への送信アクセスを禁止しています。CSLA の例では、送信アクセスが許可されるのは Azure (監視用) と支払いゲートウェイへの通信のみです。Standard レベルの Web アプリには、送信トラフィックを制限するメカニズムがありません。

    App Service の Web アプリと API アプリを App Service Environment (ASE) の Isolated レベルでホストすると、これを修正できます。ASE v2 は App Service の機能で、完全に分離された専用環境で大規模な App Service アプリを安全に実行できます。ASE 自体が、Virtual Network (VNET) のサブネット内にデプロイされたホスティング インフラストラクチャを備えています。外部から ASE がホストする App Service インスタンスへのアクセス経路は、Internal Load Balancer (ILB) エンドポイントのみに限定されます。Application Gateway の Web Application Firewall (WAF) SKU は、Web サイトにアクセスするインターネット クライアントのパブリック IP アドレスと ILB ASE エンドポイントの間にデプロイされます。ASE と Application Gateway は、2 つの異なるサブネットの間にデプロイされます。ネットワーク セキュリティ グループ (NSG) は、ASE 側のサブネットが Application Gateway 側のサブネットからのアクセスのみを許可するように構成されています。

    インターネットから Web アプリへの受信トラフィックを制限する (IP、ポート番号、プロトコルなどによる制限) には、以下が必要です。

    - ILB ASE をプロビジョニングする。Azure Virtual Network が作成されます。

    - リソースの ASE プールから Isolated レベルにアプリケーション ホスティング プランをプロビジョニングする。

    - App Service プランに Web アプリをプロビジョニングする (Web アプリのポイント対サイト VPN の作成は不要)。

    - ILB App Service Environment のアプリで使用する、インターネットでルーティング可能なドメイン名を用意する。

    - パブリック DNS 名を用意する。後ほど Application Gateway を指定する際に使用します。

    - ILB App Service Environment で使用するものと別にサブネットを作成する。このサブネットは Azure Application Gateway に使用します。

    - 新規作成したサブネットに Application Gateway を作成し、ILB ASE 内のパブリック Web アプリに接続するように構成する。作成時には WAF SKU を選択する必要があります。

    - Web アプリを構成してカスタム ドメイン名を有効化し、Application Gateway を指定するパブリック DNS のホスト名を編集する。

    - NSG を作成して、ASE が実行されている仮想ネットワークのサブネットに適用する (既定ではインターネットからのアクセスを禁止するルールが含まれている)。

    - NSG に、VNet 内の IP から ASE サブネットへの通信を許可するルール、およびパブリック VIP と呼ばれるロード バランサーと ASE の通信を許可するルールが既定で含まれている

    - ポート 454、455 へのインターネット アクセスを許可するルールを NSG に追加する。[App Service Environment]、[IP アドレス] の順に選択すると、ポートを確認できます。

    Web アプリからインターネット上のサービスへの送信トラフィックを制限するには、以下が必要です。

    - ASE、仮想ネットワーク、Azure Application Gateway、App Service プラン、および上記の Web アプリを構成する。

    - NSG に 2 つのルール (指定したサービスへのアクセスを許可するルール、およびそれ以外のインターネットへの送信接続を拒否するルール) を追加する。

    - ASE の依存関係へのネットワーク アクセスを許可する送信接続のセキュリティ ルールを構成する。上記の接続のいずれかをブロックすると、ASE は動作を停止します。参考: <https://docs.microsoft.com/ja-jp/azure/app-service/environment/network-info#network-security-groups>

    CSLA の例では、eコマース Web アプリへの受信トラフィックを制限する必要はありませんが、支払いゲートウェイへの送信トラフィックは制限する必要があります。

    ウイルス対策要件については、Azure 自体が要件を満たしておりユーザーに代わって Web アプリを実行している仮想マシンを管理するため、Azure にデプロイするだけで対応できます。

    eコマースのトランザクションがすべて Web アプリで処理されるようにストラクチャを構築すると、サーバー仕様の要件に対応できます。Azure が修正プログラムを適用するように Web アプリを構成することもできるため、パッチ適用の要件にも対応できます (アプリケーションでカスタム コードやライブラリを使用することもできます)。

    このシナリオではカード所有者のデータを格納する必要がないため、SSL を提供すると通信中および格納中のデータの保護要件にも適応できます。

2. Azure 仮想マシンの使用を推奨するかどうか検討します。また、推奨する理由、しない理由を説明します。

    仮想マシンを使用するとソリューションを PCI に準拠させることはできますが、インフラストラクチャ関連の労力を最小化するという顧客の要件には適合しません。

*データ ウェアハウス*

1. データ ウェアハウスの実装方法をどのようにして勧めるか検討します。

    Azure Synapse Analytics を使用できるかどうか検討します。

2. 夜間に OLTP データベースから自社データ ウェアハウスにデータを転送するようにスケジュールを設定する方法について検討します。

    Azure Data Factory インスタンスをプロビジョニングし、Azure Data Factory コピー ウィザードを使用して SQL Database インスタンスを Azure Synapse Analytics の既存のテーブルに反復的にコピーするようにセットアップします。コピー ウィザードで PolyBase を有効化すると、コピー処理を高速化できます。

## 想定される反論への対応のチェックリスト<a name="想定される反論への対応のチェックリスト"></a>

1. Azure トラスト センターを見ても、自社ソリューションを PCI に準拠させるにあたって Azure がどのように役立つのかわからなかった。

    Azure トラスト センターでは、どの Azure サービスが PCI に準拠しているかを知ることはできます。PCI に準拠したソリューションの構築に利用可能なサービスが紹介されてはいますが、PCI に準拠したソリューションを Azure で構築する方法が説明されているわけではありません。ソリューションを完全に PCI に準拠させるためには、カード所有者のデータの取り扱い方法やサービスの範囲に応じて PCI の要件に独自に対応する必要があります。多くの場合、Azure の PCI コンプライアンス認定証だけでもソリューションが PCI 要件を満たすことができますが、安全なパスワード ポリシーを定義して強制適用するなど、少なくともいくつかの項目をアプリケーション構築時に扱う必要があります。

2. ソリューションをスケーリングして顧客の需要に対応しながら、同時にコール センターや倉庫のセキュリティを守ることができるか?

    はい、できます。Azure では、スケーラブルで安全なソリューションを構築できます。

3. PCI コンプライアンスに準拠するには四半期ごとの監査が必要であり、侵入テストの実施が求められる場合もある。これは Azure で可能か?

    事前の承認は不要ですが、Azure サービスの侵入テスト通知フォーム (<https://portal.msrc.microsoft.com/ja-jp/engage/pentest>) を記入すると、事前に Azure への侵入テストの実施を正式に書面で提出していただくことができます。

    - 侵入テストは使用条件に従い、Microsoft Cloud 統合侵入テストの実施ルール (<https://technet.microsoft.com/mt784683>) に基づいて実施する必要があります。

    - サービス拒否攻撃 (DoS) を引き起こすテストは禁止されています。

4. Azure データ センターは監査可能か?

    いいえ。ユーザーによる監査に代わって、マイクロソフトによる独立した監査と認定証が共有されます。これらの認定や認定証は、マイクロソフトがセキュリティやコンプライアンスの目標をどのようにして達成したかを示しており、すべてのお客様に向けたお約束を検証する実際的なメカニズムとしての役割を果たします。数千以上のお客様にマイクロソフトのサービスの監査を許可することは規模的に現実的ではなく、セキュリティやプライバシーに関するリスクの原因にもなります。独立した第三者による検証プログラムには年次監査も含まれていて、Azure のセキュリティ管理が検証されています。

5. 過去に、Web サイトの大規模負荷テストの設計と実行に SOASTA CloudTest を利用した。Azure に移行しても引き続き CloudTest を使用できるか?

    はい、できます。Azure は CloudTest のサポート クラウド プロバイダーであり、Azure でホストされているアプリケーションは SOASTA が所有するクラウド リソースのグローバル ネットワークを利用して負荷テストやパフォーマンス テストを実施し、同社のリアルタイム ストリーミング ビッグデータ分析プラットフォームで結果を監視することができます。

6. 従来のインフラストラクチャでは Web サイトのパフォーマンス監視機能が不十分だった。自社 Web アプリと連携する Azure のオプションにはどのようなものがあるか?

    Azure の Web アプリでは、Microsoft Application Insights と New Relic アプリケーション パフォーマンス監視の両方が高度にサポートされていて、実行中の Web アプリからパフォーマンス テレメトリを収集できます。Azure Portal では、サーバー側とブラウザー側の両方のテレメトリのトレース、および診断エラーの表示と分析、アラートの設定が可能です。Microsoft Operations Management Suite の 1 機能である Log Analytics を導入すると、Application Insights のログや Web Apps の診断ログをストレージ アカウントにプッシュして、カスタム ログにより検索性を付与することもできます。このほか、New Relic のログを Log Analytics にプッシュしたり、Operations Management Suite で 1 つのウィンドウから監視したりできます。

7. Azure のデータ ウェアハウスは一時停止できると聞いた。インスタンスを一時停止する前に Azure Storage の自社データをすべて保存する必要があるのか、またデータを損失するリスクがあるのか?

    Azure Synapse Analytics では、ストレージを 2 つの方法で利用します。どちらの方法でも、SQL DW インスタンスが停止しているときでもデータを永続化できます。Azure Synapse Analytics で管理されるデータ (リレーショナル テーブルや列形式テーブルに直接挿入される) の場合、Azure Premium Storage に格納されます。SQL DW の外部テーブルをサポートしているデータの場合、Azure Standard Storage に格納され、Azure Synapse Analytics コンポーネントの 1 つである PolyBase から参照されます。

8. Azure SQL Database を自社データ ウェアハウスとして使用可能であることは理解した。Azure Synapse Analytics と比較する場合、どのような点について考慮すればよいか?

    Azure SQL Database は、データ ウェアハウスとして使用できます。これは対象型マルチプロセッシング (SMP) ベースのデータ ウェアハウスです。Azure Synapse Analytics は超並列処理 (MPP) ベースのデータ ウェアハウスです。通常、SMP ベースのデータ ウェアハウスは小規模から中規模 (最大 4 ～ 100 TB) のデータ セットに適し、MPP ベースはビッグ データに使用されます。小/中規模データ セットとビッグ データの境目は、企業の定義やサポートするインフラストラクチャによっても変化します。

    データ サイズ以外に、ワークロード パターンの種類も定義に大きく影響します。たとえば、複雑なクエリは SMP ソリューションでは十分な速度が得られず、MPP ソリューションが必要となります。MPP ベースのシステムではジョブを複数ノードで分散・集約するため、データ サイズが小さいとパフォーマンスが低下しやすくなります。データ サイズが既に 1 TB を超過していてさらに増大することが予想される場合、MPP ソリューションの使用を検討します。データ サイズがこれよりも小さくても、SMP ソリューションではワークロードのリソースが不十分な場合、MPP を使用したほうがよい場合もあります。以上から、Azure Synapse Analytics は演算処理とメモリの負荷が高い小規模から中規模のデータ セットに適しています。

    CSLA では、Azure Synapse Analytics を使用して、事前に集約されたデータをデータ ストアに格納します。このデータ ストアは、企業のユーザーやアナリストにとってわかりやすい列名、およびデータのリレーションシップを簡素化するために再構築されたスキーマを使用し、集約されたテーブルを備えています。また、パフォーマンスを考慮し、履歴データをトランザクション システム本体とは独立して保持します。

## 顧客の声 (最後に参加者にもう一度読んでいただく)<a name="顧客の声-(最後に参加者にもう一度読んでいただく)"></a>

_「負荷が急激に増大した日にも対応できるほど eコマース ソリューションがスケーラブルであり、PCI 準拠要件を損なうことがなく、インフラストラクチャ関連の労力も軽減されたため、夜に安心して眠ることができます」_

Miles Strom 氏 (Contoso Sports League Association、CEO)