---
title: Boosting sales productivity with watsonx Orchestrate <br/>Technical Sales Level 3 demo
layout: demoscript
banner: images/Script-banner.png
browsingselfservice: 2
nocodeeditor: 3
outputtomarketing: 4
---

<span id="top"></span>
<inline-notification text="<strong>Attention: L3 learning plan updates 17th Jan 2025.</strong> This demo was removed from the L3 learning plan on the 17th of January. This demo can still be used to complete the learning plan, but the new demo introduces new capabilities such as AI chat, conversational search and AI guided actions."></inline-notification>

<details markdown="1">

<summary>1 – Introduction</summary>

This demo shows you how to present watsonx Orchestrate’s core capabilities and its value proposition using a business scenario set in an insurance sales office. You’ll see how individual skills are used, take a brief look at decision automation, then implement an upsell process for a hypothetical insurance brokerage by combing skills together into a sequence called a skill flow.

In this hypothetical insurance brokerage, sales agents spend their time across many tasks while constantly context switching between multiple applications to do their jobs. A large part of any successful insurance seller’s time should be spent servicing existing clients, but an important part of being a great sales agent is finding new business and building pipeline.

Prior to watsonx Orchestrate, agents in this insurance office dedicated a few hours per week to sending prospecting emails for upsell and cross-sell opportunities, as well as building pipeline. To do this, a typical insurance seller would:

1.	Search the customer relationship management (CRM) system for customers that meet certain cross-sell criteria.
2.	Determine the best cross-sell products to offer each customer.
3.	Write a customized email from a template.
4.	Send the email to the selected customer.
<br/><img src="images/Script-1.png" width="800" /><br><br/>
Unfortunately, agents in this office are facing several challenges that prevent them from performing at their best:
- Effectively searching their CRM system for sales opportunities is time consuming and requires a lot of skill… skills that not everyone on the team possesses, especially new hires who need to be trained.<br/>
- Matching customer circumstances to the most optimal and competitive products is time consuming and requires expert product knowledge. The information about products, customers, and policies is spread over multiple systems and spreadsheets.<br/>
- Multiple systems and applications are used to perform customer outreach (a CRM search, Outlook, and so on). It takes time to switch between these applications to find the required information. Data is copied and pasted between applications and inevitably errors are made.<br/>
- Multiple systems and applications are used to perform customer outreach (a CRM search, Outlook, and so on). It takes time to switch between these applications to find the required information. Data is copied and pasted between applications and inevitably errors are made.<br/>
- There isn’t time to create a personalized email for each customer. Instead, sellers use templates…but they know that the emails that are produced this way are often ignored by their customers because they are not engaging.<br/>

This demo shows how the prospecting work in this scenario can be done more effectively with watsonx Orchestrate by creating a sequence of skills that perform the multiple steps of the upsell process using a skill flow. A skill flow is a sequence of skills where the inputs and outputs of individual skills are wired together to reduce data entry.

Here is what this demonstration highlights:
- First, data is extracted from a system that leverages a pre-configured search to find customers with recent life events.
- Then, these customers are matched to the most suitable and competitive products by using an AI-infused automation that represents the digitized business knowledge of a product expert.
- Finally, instead of using an email template, a built-in skill that uses the IBM Granite generative AI model is used to create a marketing email. This model is designed for the enterprise and trained on trusted enterprise data, so it can be trusted to produce content suitable for business use cases.

Let’s get started.
 
<br/>

**[Go to top](#top)**

</details>

<span id="spanID"></span>
<details markdown="1">


<summary>2 – Review individual skills </summary>

<br/>


| :--- | :--- |
| **Narration** | IBM watsonx Orchestrate comes with a catalog of out-of-the-box skills, such as Workday, Monday, Outlook, etc. Additional skills can be added to the catalog that work with existing services using OpenAPI or run on IBM Cloud Pak for Business Automation. Let’s begin by opening the catalog.|
| **Action** &nbsp; 2.0.1 | Click the **navigation hamburger** menu icon **(A)**, then select **Skill catalog (B)** from the left menu.<br/><img src="images/Script-2-0-1.png" width="800" />|
| **Action** &nbsp; 2.0.2 | When the **Choose a skill set to view skill catalog** window opens, select the **Personal skills tile (A)**, then click **Go to skill catalog (B)**.<br/><img src="images/Script-2-0-2.png" width="800" />|
| **Narration** | Skills are grouped by application, such as Microsoft Teams or Salesforce. New skills are added to the watsonx Orchestrate catalog with each release. <br/><br/>When an out-of-the-box skill is not available, builders can create new skills from several sources, including: <br/> 1. **Open APIs**: Skills are generated from OpenAPI specifications.<br/> 2. **Embedded Automations**: Decision and workflow skills are created by using the built-in automation builder.<br/> 3. **IBM Cloud Pak for Business Automation/RPA**: Skills are generated for automation services and robotic process automation (RPA) bots. <br/> 4. **Composite skill flows**: Individual skills are combined into a sequence.<br/><br/>OpenAPI is a specification for documenting and standardizing the design and behavior of web APIs. An OpenAPI file provides the detailed outline of how a particular API works, including its operations, endpoints, data types, request and response formats and authentication methods.<br/><br/> Decision automations and skill flows are covered in a later section, but first you’ll see how an individual skill based on an OpenAPI performs a customer search in this fictitious insurance company used at the start of the upsell process.|


| **2.1** | **Customer search** |
| :--- | :--- |
| **Narration** |  The first task in the upsell process is to perform a predefined search against the customer system to find customers that have recent life events. This functionality is provided to users through the **Get a list of customers** skill.<br/><br/>Let’s open the chat window to run this skill.|
| **Action** &nbsp; 2.1.1 | Click the **hamburger navigation** menu icon **(A)** and select **Chat (B)** from the left menu.<br/><img src="images/Script-2-1-1.png" width="800" /> |
| **Action** &nbsp; 2.1.2 | Click the **Skills** menu and select **Personal skills** if not already selected. <br/><img src="images/Script-2-1-2.png" width="800" />|
| **Narration** |In watsonx Orchestrate, skills are organized into apps. Users can click on their app tiles to run the skills they contain, or they can type a phrase to run the skill, such as **Write an upsell email for my customers**.  |
| **Action** &nbsp; 2.1.3 | Click on the tile **Get a list of customers with …** tile to run the skill and fetch customers from the CRM system.<br/><img src="images/Script-2-1-3.png" width="800" /> |
| **Narration** | The results from this skill are shown in a table. All the listed customers have recent life events that could be used for cross-sell and upsell purposes. This skill has used a predefined search against the CRM system and provides an insurance seller with a list of potential upsell opportunities. This took just a few seconds and was done without having to use the CRM system directly or require CRM expertise. This skill is already useful as a standalone skill, but as we will soon see, combining its output with other skills can make it far more useful and powerful.<br/><img src="images/Script-2-1-3-bis.png" width="800" /> |

| **2.2** | **Product upsell automation** |
| :--- | :--- |
| **Narration** | The next skill is the upsell skill. This skill uses an embedded decision automation engine to match customers to upsell and cross-sell offers. <br/><br/>This skill is run by clicking on its corresponding tile or by entering a prompt such as **“upsell”** into the chat window.|
| **Action** &nbsp; 2.2.1 | Enter **“upsell”** into the chat prompt and press **Enter** key **(A)**. Alternatively click on the tile associated with the skill **(B)**. <br/><img src="images/Script-2-2-1.png" width="800" /> |
| **Narration** | To use this skill, the user must enter details about a customer, such as a recent life event, their age, and any current products they have purchased. In this example, just the name is provided so that a default response is returned. |
| **Action** &nbsp; 2.2.2 | Enter a person’s name into the **name** field **(A)**, then click the **Apply** button **(B)**. <br/><img src="images/Script-2-2-2.png" width="800" /> |
| **Narration** | The results from the ‘Product Upsell’ automation are displayed. These results contain a product recommendation for the selected customer and were provided almost instantly. This is another huge time saving for the sales agent; but in addition to the product recommendation the results also contain a prompt that can be used by a foundation model such as IBM Granite, to generate a personalized marketing email. <br/><br/>Just like the customer search skill, the value of this skill is obvious, because manual data entry is time consuming and can introduce errors, the full value of this skill isn't realized… but watsonx Orchestrate can autofill this information once the skill is part of a skill flow.<br/><img src="images/Script-2-2-2-bis.png" width="800" /> |

| **2.3** | **Email generation** |
| :--- | :--- |
| **Narration** | The last individual skill is **Generate an email**. This skill uses the IBM Granite foundation model to generate an email based on a prompt. <br/><br/>This skill is run by clicking on its corresponding tile or by entering a prompt such as **“generate an email”** into the chat window.|
| **Action** &nbsp; 2.3.1 | Enter **“generate an email”** into the chat prompt and press **Enter** key **(A)**. Alternatively click on the tile associated with the skill **(B)**. <br/><img src="images/Script-2-3-1.png" width="800" />|
| **Action** &nbsp; 2.3.2 | Copy the **prompt** text produced by the **L3_Upsell** skill **(A)** and paste it into the **Input instruction** panel **(B)**, then click **Apply (C)**. <br/><img src="images/Script-2-3-2.png" width="800" /> |
| **Narration** | Content generation will take approximately 30 seconds. IBM watsonx Granite is used to generate the email body. This model is trained on trusted enterprise data, with additional layers of protection, so you can be certain it will not produce harmful or inappropriate content. The generated email is displayed, and also confirmation that it came from the IBM Granite model.<br/><img src="images/Script-2-3-2-bis.png" width="800" />|

<br/>

**[Go to top](#top)**

</details>

<span id="spanID"></span>
<details markdown="1">

<summary>3 – Explore decision automation </summary>

<br/>

| :--- | :--- |
| **Narration** |The ‘L3_Upsell’ automation skill represents the digitized knowledge of a product expert and matches customers to upsell and cross-sell offers. It does this using prescriptive AI, where the decision-making process used by an expert has been transformed into a decision model. Within the decision model, the product upsell logic is represented in natural language and decision tables that ensures that the logic remains clear and simple to non-technical users. Furthermore, the no-code tools in watsonx Orchestrate Automation Builder enable non-technical users to create, test and maintain the decision logic to adapt to changing circumstances. <br><br/>Let’s see how this skill’s business logic is managed with watsonx Orchestrates’ Automation Builder.|

| **Action** &nbsp; 3.1 | Click the **hamburger navigation** menu icon **(A)**, then select **Skill studio (B)** from the left menu.<br/><img src="images/Script-3-1.png" width="800" />|
| **Action** &nbsp; 3.2 | Select the **Projects** tab **(A)**, then enter the unique reference **“XXddmmyy”** that corresponds to your decision model in the **search** field **(B)** and press **Enter**, then click on the tile that corresponds to your automation **(C)**.<br/><img src="images/Script-3-2.png" width="800" /> |
| **Narration** | This decision model shows the structure of the decision-making process. Data feeding the model is shown at the bottom of the diagram and represented by the green input nodes. In this example, the input data is the customer record and the recent change. This data passes through intermediate decision nodes that incrementally infer new information by using business rules. The output decision node is shown with a dark blue line and produces the decision result. <br/><br/>In this example, the decision model determines the best product for the selected customer and produces a GenAI prompt along with some tuning parameters so that a generative AI model can create a marketing outreach email. <br/><br/>The decision nodes contain the business rules that perform the logic to build the prompt. The ‘Initial Instruction’ node uses the customer’s name to form the instructions that are passed to the generative model such as ‘You are an insurance salesman, write a marketing email for your customer John Collins’. The Product Recommendation node determines the most appropriate product to recommend to the customer based on their age, recent life events and existing products they hold.<br/><br/>The output from these intermediate decision nodes is brought together in the top node called **Upsell prompt**. This node produces the final output from the decision model based on the intermediate results.<br/><img src="images/Script-3-2-bis.png" width="800" /><br/><br/>The palette on the left of the canvas is used to add additional nodes to the model. These can be additional decisions and inputs. They can also include predictive models enabling you to blend prescriptive business rules and predictive models together, for example the predictive model could use a regression model to predict a best price, but then prescriptive business rules could be used as guardrails to ensure the price stayed within a certain range.<br/><br/>Decision models can also include nested models, and you can also include generative AI.<br/><br/>Let’s take a closer look at the product recommendation logic.|
| **Action** &nbsp; 3.3 | Click the **Product recommendation** node **(A)** then select the **Logic** tab **(B)** in the **Product recommendation** section that appears on the right.<br/><img src="images/Script-3-3.png" width="800" /> |
| **Narration** | The rules that are applied in this decision node are shown on the right of this screen. Note how there is a decision table called **Product recommendation**. This table houses the main logic, a business rule to check for duplicate recommendations for products already held, and a default rule that will apply if no other product recommendations can be made.<br/><br/>Let’s take a closer look at the product recommendation decision table.|
| **Action** &nbsp; 3.4 | Click the **Product recommendation** decision table.<br/><img src="images/Script-3-4.png" width="800" /> |
| **Narration** | Decision tables are useful when many rules will share the same structure and it is helpful to view them together. In this example, every row in the table represents a rule that reasons over the customers recent change, along with their age, to determine a product recommendation. In this example, the recent change and customer age are both used as condition columns and shown on the left. The column on the right is the action column and provides the product recommendation. <br/><br/>Decision tables can contain more condition columns and multiple action columns to represent complex logic, but the logic will remain clear and maintainable. Many decision tables can work together to implement very complex logic, whilst keeping the logic clear and readable to non-technical users. <br/><br/>IBM watsonx Orchestrate’s Automation builder also includes a preview capability to test the results produced by the decision model. Clicking the Play icon in the top-right corner opens the preview window.|
| **Action** &nbsp; 3.5 | Click the **Play** icon in the top-right corner of the screen. <br/><img src="images/Script-3-5.png" width="800" />|
| **Narration** | Run a test scenario. |
| **Action** &nbsp; 3.6 | Click the **Preview** button. <br/><img src="images/Script-3-6.png" width="800" />|
| **Narration** | The rules are run, and the results are displayed. At the top is the final output, but below this we can also see all the intermediate results as the data passed through the decision model. By clicking the show more link, we can expand the final output and see the complete information returned from the decision. This contains the product recommendation, the GenAI prompt and the min/max tokens that control the content length. |
| **Action** &nbsp; 3.7 | Click the **Show more** button. <br/><img src="images/Script-3-7.png" width="800" />|
| **Narration** | Many test scenarios can be created, these are run by selecting them and pressing preview. |
| **Action** &nbsp; 3.8 | Click the drop-down arrow **(A)** in the **Test data** section and select another scenario, then click the **Preview** button **(B)**.<br/><img src="images/Script-3-8.png" width="800" /> |
| **Narration** | Once the business logic is ready, it is deployed as a skill that can be invoked from the chat window directly, or it can be combined with other skills in a skill flow. |

<br/>

**[Go to top](#top)**

</details>

<span id="spanID"></span>
<details markdown="1">

<summary>4 – Combining skills into skill flows </summary>

<br/>


| :--- | :--- |
| **Narration** | Individual skills can be useful when used in isolation, but greater value can be unlocked when they are combined into skill flows.  |
| **Action** &nbsp; 4.1 | Click the **hamburger navigation** menu icon **(A)** and select **Skill studio (B)** from the left menu.<br/><img src="images/Script-4-1.png" width="800" /> |
| **Narration** | IBM watsonx Orchestrate provides access to a broad range of skills that help users perform their daily tasks. It comes with a collection of out-of-the-box, ready-to-use skills that range from working with productivity tools to providing deep analytical insights. <br/><br/>IBM watsonx Orchestrate developers, called ‘Builders,’ can create customized skills like the customer search and product upsell skills described earlier. As individual skills they are useful on their own, but combining them together can save an insurance sellers time, avoid errors, and produce better results. <br/><br/>Skill flows connect multiple skills together by using a low-code flow editor. In this example, a skill flow is created to combine the customer search skill with the product upsell decision and then generate a marketing email for a selected customer.<br/><br/>Let's create the skill flow now.|
| **Action** &nbsp; 4.2 | Click on **Create skill (A)**, then select **Skill Flow (B)**.<br/><img src="images/Script-4-2.png" width="800" /> |
| **Narration** | The skill flow requires a unique name. |
| **Action** &nbsp; 4.3 | Click the horizontal layout icon **(A)**. Click the Pencil icon **(B)** and when the **Edit Skill flow details** section opens on the right, enter a name for the skill flow using the template Upsell **XXddmmyy (C)**. Now click the **Save** button **(D)**. <br/><img src="images/Script-4-3.png" width="800" />|
| **Narration** | To add a skill, click the plus icon. |
| **Action** &nbsp; 4.4 | Click the **+** icon. <br/><img src="images/Script-4-4.png" width="800" /><inline-notification text=" You are using a shared demo tenant. Use the unique reference added to your skill names to find them in the catalog. It’s a good idea to keep this reference in your clipboard history so it can be pasted into the skill search panel."></inline-notification> |
| **Narration** | On demo tenants a unique reference is used to locate the demo skills in the catalog. (This is only necessary on demo tenants, ordinarily these skills would be found by using just their name.) |
| **Action** &nbsp; 4.5 | Enter the unique reference for your skills (**XXddmmyy**) into the **filter** panel and press **Enter** to filter the results.<br/><img src="images/Script-4-5.png" width="800" /> |
| **Narration** | The first skill we need performs a customer search and it’s contained in the **CRM** tile. <br/><br/> <inline-notification text="This skill collection contains one skills; <strong>Get Customers with recent life events …</strong> that performs the customer search."></inline-notification> |
| **Action** &nbsp; 4.6 | Click the **CRM** tile. <br/><img src="images/Script-4-6.png" width="800" /><br/><br/> <inline-notification text="This skill collection contains one skills; Get Customers with recent life events … that performs the customer search."></inline-notification>|
| **Narration** | Add the skill. |
| **Action** &nbsp; 4.7 | Click **Add Skill** within the **Get Customers with recent life events …** tile.<br/><img src="images/Script-4-7.png" width="800" />|
| **Narration** | Add the next skill by clicking the **Plus** icon again, searching with the unique reference, then adding the skill. |
| **Action** &nbsp; 4.8 | Click the **+** icon to the left of the end node.<br/><img src="images/Script-4-8.png" width="800" /> |
| **Action** &nbsp; 4.9 | Enter the unique identifier for your skills (**XXddmmyy**) and press **Enter** to filter the results. <br/><img src="images/Script-4-9.png" width="800" />|
| **Narration** | Add the upsell skill. |
| **Action** &nbsp; 4.10| Click on the **L3_Upsell** tile with the unique reference you used.<br/><img src="images/Script-4-10.png" width="800" /> |
| **Action** &nbsp; 4.11 | On the **L3_Upsell_XXddmmyy** tile, click **Add skill**.<br/><img src="images/Script-4-11.png" width="800" /> |
| **Narration** |Add the third skill by clicking the **Plus** icon again. |
| **Action** &nbsp; 4.12 | Click the **+** icon to the left of the end node.<br/><img src="images/Script-4-12.png" width="800" /> |
| **Action** &nbsp; 4.13 | Enter **“watsonx”** into the **Search** field and press **Enter** to filter the results.<br/><img src="images/Script-4-13.png" width="800" />|
| **Action** &nbsp; 4.14| Click the **watsonx.ai** collection tile.<br/><img src="images/Script-4-14.png" width="800" /> |
| **Narration** | Add the third skill. |
| **Action** &nbsp; 4.15 | Click **Add Skill** within the **Generate an email** tile.<br/><img src="images/Script-4-15.png" width="800" /> |
| **Narration** |In this demo, an input form is used instead of one of the built-in email skills. This is done to avoid some additional setup, but from the user’s perspective the results are the same. The input form contains the same fields as the built-in email skill and allow us to map the various skill outputs together to build the final output.<br/><br/>Let's add the custom form. |
| **Action** &nbsp; 4.16 | Click the + icon to the left of the end node.<br/><img src="images/Script-4-16.png" width="800" />|
| **Action** &nbsp; 4.17 | Type **“forms”** and press **Enter** to filter the results **(A)**, click **Custom forms (B)**.<br/><img src="images/Script-4-17.png" width="800" /> |
| **Action** &nbsp; 4.18 | Click **Add skill** within the **Input form** tile.<br/><img src="images/Script-4-18.png" width="800" /><br/><br/><inline-notification text="Your skill flow should now resemble the following example and have four skills."></inline-notification><br/><img src="images/Script-4-18-bis.png" width="800" />|
| **Narration** | Each skill can have one or more inputs and outputs. The skill flow editor allows builders to easily map the output from one skill into another. The first skill in this skill flow (**Get a list of customers with recent life events**) doesn’t require any configuration. But, the **L3_Upsell** skill needs to be configured to map the output from the **Get a list of customers** skill into its appropriate inputs. |
| **Narration** | The input form for this skill will also be hidden. |
| **Action** &nbsp; 4.19 | Configure the input form for **L3_Upsell** skill by performing the following steps: <br/>A. Select the **L3_Upsell_Master** tile.<br/>B. Click **Input** to select the input form.<br/>C. Turn on the **Hide this input form from the user** option.<br/><img src="images/Script-4-19.png" width="800" />|
| **Narration** | Now the data can be mapped, starting with the customer’s age. |
| **Action** &nbsp; 4.20 | Map the customer age input field of the skill by performing the following steps:<br/>A. Click the field **theCustomer.age**.<br/>B. Select **Get a list of customers with recent life events** from the available mappings.<br/><img src="images/Script-4-20.png" width="800" />|
| **Action** &nbsp; 4.21 | Scroll down and select **age**.<br/><img src="images/Script-4-21.png" width="800" /> |
| **Narration** |Mapping data can be done manually, but in some cases it’s easier to let the skill flow editor generate mapping suggestions for you. |
| **Action** &nbsp; 4.22 | Click **Generate mapping suggestions** (this can take up to 30 seconds).<br/><img src="images/Script-4-22.png" width="800" />|
| **Narration** | Not all mappings can be generated. Later in the skill flow there will be multiple options, and as such, manual mapping will be required. <br/><br/>Let's complete the final mapping for this skill and map the list of current products.|
| **Action** &nbsp; 4.23 | Map the remaining field. Scroll down and click **theCustomer.listOfCurrentProducts (A)**.<br/><img src="images/Script-4-23.png" width="800" />|
| **Action** &nbsp; 4.23a | Select **Get a list of customers with recent life events** from the mappings panel **(A)**. <br/><img src="images/Script-4-23a.png" width="800" />|
| **Action** &nbsp; 4.24 | Scroll and select **current_products** from the list of available mappings **(A)**, then click the cross to close the mapping panel **(B)**.<br/><img src="images/Script-4-24.png" width="800" />|
| **Narration** | The output form for the **L3_Upsell** skill requires no configuration, but typically this output would be hidden as the user doesn’t need to see or edit the results. It will be left visible in this demo so that when the skill flow runs the output will be available for review.<br/><br/>The **Generate an email** skill creates the email body from the prompt received from the **L3_Upsell** decision skill.  |
| **Action** &nbsp; 4.25 | Select the **Generate an email** tile in the skill flow **(A)**.<br/><img src="images/Script-4-25.png" width="800" />|
| **Narration** | Map the input field to take the prompt from the **L3_Upsell** skill. |
| **Action** &nbsp; 4.26 | Map the **Input instruction** field by performing the following steps:<br/>A. Click on the Input tab.<br/> B. Click on the **Input instruction** field.<br/>C. From **Available Mappings Skills** select the **L3_Upsell** skill.<br/><img src="images/Script-4-26.png" width="800" /><br/><br/>D. Select **prompt**.<br/><img src="images/Script-4-26-bis.png" width="800" />|
| **Narration** | The **Generate an email** output form can be hidden as the output will be available to view in the next skill. |
| **Action** &nbsp; 4.27 | Configure the **Generate an email** output form by performing the following steps: <br/>A. Select the **Output** tab to select the output form.<br/>B. Turn on the **Hide this input form from the user** option.<br/>C. Click the cross to close the mapping panel.<br/><img src="images/Script-4-27.png" width="800" />|
| **Narration** | Following email content generation, an input form will be used to display the output and allow the sales agent to check the output for accuracy. The agent can also make any modifications before the response is sent to their customer. <br/><br/>The form is built by repeatedly adding input fields. |
| **Action** &nbsp; 4.28| Configure the input form by performing the following steps: <br/>A. Scroll to the right to display the Input form.<br/>B. Select the **Input form** tile from the skill flow at the top of the screen.<br/><img src="images/Script-4-28.png" width="800" />|
| **Action** &nbsp; 4.28a| Enter a title for the form in the **Form title** field, for example **“Send email”**.<br/><img src="images/Script-4-28a.png" width="800" />|
| **Narration** |The form is built by repeatedly adding input fields. |
| **Action** &nbsp; 4.29|Add a field to the form by performing the following steps: <br/> A. Click **Add input field**.<br/>B. Select the **Single line text** option under the **Add input field** section that appears on the right side of the screen<br/>C. Click the **Next** button.<br/><img src="images/Script-4-29.png" width="800" />|
| **Narration** |The new input field will receive the email address of the selected customer. |
| **Action** &nbsp; 4.30| Label the input field by performing the following steps:<br/>A. Enter the value **“To”** into the **Display text** field in the **Add input field** section on the right side of the screen.<br/>B. Click the **Apply** button.<br/><img src="images/Script-4-30.png" width="800" />|
| **Narration** |The subject field can now be added to the form by repeating the same steps. |
| **Action** &nbsp; 4.31| Repeat steps **4.29 and 4.30** to create a **Subject** field.|
| **Action** &nbsp; 4.31a| Click **Add input field**.<br/><img src="images/Script-4-31a.png" width="800" />|
| **Narration** |Next, a field for the email body is added to the form, this field will be a **Paragraph text** field. |
| **Action** &nbsp; 4.32|Add a field to the form by performing the following steps: <br/>A. Select the **Paragraph text** option in the Add input field section on the right side of the screen.<br/>B. Click the **Next** button.<br/><img src="images/Script-4-32.png" width="800" />|
| **Narration** |This input field will receive the email body generated by watsonx.ai.|
 **Action** &nbsp; 4.33| Label the input field by performing the following steps: <br/> A.   Enter the value **“Email body”** into the **Display text** field.<br/>B. Click the **Apply** button.<br/><img src="images/Script-4-33.png" width="800" /><br/><br/> <inline-notification text="Your form should now resemble the example below with <strong>To, Subject</strong> and <strong>Email body</strong> fields."></inline-notification><br/><img src="images/Script-4-33-bis.png" width="800" />|
| **Narration** | To complete the form the mappings must be added. |
| **Action** &nbsp; 4.34 | Configure the mappings for the input form by performing the following steps:<br/>A. Click the **To** field.<br/>B. From **Available Mappings**, select **Get a list of customers with recent life events XXddmmyy**.<br/><img src="images/Script-4-34.png" width="800" /><br/><br/>C. Select the **email** mapping.<br/><img src="images/Script-4-34-bis.png" width="800" />|
| **Narration** | A default value will be used to populate the **Subject** field. |
| **Action** &nbsp; 4.35 | Provide a default value for the **Subject** field by performing the following steps:<br/>A. Hover to the right of the **Subject** field and click the corresponding **Pencil** icon when it appears.<br/><img src="images/Script-4-35.png" width="800" /><br/><br/>B. Under **Subject**, enter a default value, **“Your insurance”**.<br/><img src="images/Script-4-35-bis.png" width="800" />|
| **Narration** | The text produced from the Generate an email skill will be used to populate the **Email body** field.|
| **Action** &nbsp; 4.36 | Map the value for the Email body by performing the following steps:<br/>A. Click on the **Email body** field.<br/><img src="images/Script-4-36.png" width="800" /><br/><br/>B. In the Available mappings section, select **Generate an email**.<br/><img src="images/Script-4-36a.png" width="800" /><br/><br/>C. Select **generated_text**.<br/><img src="images/Script-4-36b.png" width="800" />|
| **Narration** | This completes the skill flow creation. In the next section, you will save this skill flow and then publish it, so it is available for use by any seller at the insurance company.  |


**[Go to top](#top)**

</details>

<span id="spanID"></span>
<details markdown="1">

<summary>5 – Saving and publishing the skill flow </summary>

<br/>

| :--- | :--- |
| **Narration** | Before the new skill flow can be used, it must be enhanced and published. Enhancement allows you to fine-tune how the skill is presented and train the conversational interface to recognize when the skill should be used. First, save the skill flow.|
| **Action** &nbsp; 5.1 | A. Scroll to the top of the page and click on the **Actions** button drop down.<br/>B. Select **Save** or **Save as draft**. <br/><img src="images/Script-5-1.png" width="800" /> |
| **Narration** | Next use the **Enhance** window to enter training phrases and publish the skill flow.  |
| **Action** &nbsp; 5.2 | Open the Enhance window by performing the following steps:<br/>A. Click the **Actions** button drop down.<br/>B. Select **Enhance**.  <br/><img src="images/Script-5-2.png" width="800" /> |
| **Narration** | Using the **Enhance** window, phrases are entered that are used to train the conversational interface to recognize when the skill should be used. Multiple phrases can be entered to train the conversational interface. In a real project, several alternative phrases would be used to train the AI to ensure the skill is activated.  |
| **Action** &nbsp; 5.3 | Enter a training phrase by performing the following steps:><br/>A. Select the **Phrases** tab. <br/><img src="images/Script-5-3.png" width="800" /><br/><br/>B. Enter a phrase to trigger the skill flow, for example: **“write an upsell email to my customers” (B)**, then click **Publish (C)**. <br/><img src="images/Script-5-3-bis.png" width="800" /> |
| **Narration** | Before the skill flow can be run, it must be added into your personal skill set from the skill catalog. |
| **Action** &nbsp; 5.4 | Click the **hamburger navigation** menu icon **(A)** and click **Skills catalog (B)** from the left menu. <br/><img src="images/Script-5-4.png" width="800" /> |
| **Narration** | The unique reference used to name the skill flow can be used to find it in the skill catalog. |
| **Action** &nbsp; 5.5 | Find the skill flow by performing the following steps:<br>A. Enter your unique skill reference (**XXddmmyy**) in the **Search** panel and press **Enter**.<br/>B. Click the **Skill flows** tile in the **Apps** section.<br/><img src="images/Script-5-5.png" width="800" />|
| **Narration** | When the catalog entry for skill flows is displayed, the unique reference can be used again.|
| **Action** &nbsp; 5.6 | Add the skill flow by performing the following steps:<br/>A. Enter your unique skill reference (**XXddmmyy**) in the **Search** panel again and press **Enter**.<br/>B. Click **Add skill**.<br/><img src="images/Script-5-6.png" width="800" />|
| **Narration** | The skill flow has been added to the personal skills collection and should be available in the main chat window.|
| **Action** &nbsp; 5.7 | Return to the Chat window by performing the following steps:><br/>A. Click the **hamburger navigation** menu icon from the left menu.<br/>B. Select **Chat**.<br/><img src="images/Script-5-7.png" width="800" /><br/><br/>C. Confirm that a tile representing your skill flow has been added <br/><img src="images/Script-5-7-bis.png" width="800" /><br/><inline-notification text="If you have created more than one skill flow, the new skill flow will be grouped with other skill flows in a parent Skill Flow tile."></inline-notification> |

<br/>

**[Go to top](#top)**

</details>

<span id="spanID"></span>
<details markdown="1">

<summary>6 – Using the skill flow </summary>

<br/>

| :--- | :--- |
| **Narration** | Before you run the new skill flow let’s summarize what you’ve seen so far:<br/>- Individual skills performing useful but isolated functions, such as customer search and product upsell.<br/>- A brief look into decision automation, and how business logic can be represented with a decision model. <br/>- Implemented a simple workflow using skill flows to connect skills together.<br/><br/>The skill flow is complete and published for sales agents to use.  Now let’s assume the persona of an insurance seller to see how the upsell process has been transformed with watsonx Orchestrate.|
| **Action** &nbsp; 6.1 |Open the Chat window (if not already open) by clicking the **hamburger navigation** menu icon **(A)** and select **Chat (B)** from the left menu. <br/><img src="images/Script-6-1.png" width="800" /> |
| **Action** &nbsp; 6.2 | Perform the following steps:<br/>A. Type the command **“write an upsell email to my customers”**.<br/>B. Click the **Send** arrow.<br/><br/> <inline-notification text="You can also click the skill tile that corresponds to the skill flow you created to invoke this skill."></inline-notification><br/><img src="images/Script-6-2.png" width="800" />|
| **Narration** | IBM watsonx Orchestrate runs the skill flow, retrieving a list of customers with recent life events. The retrieved customer data is neatly displayed in a table within the chat interface.<br/><br/>The agent reviews the list of customers and pursues a cross-sell opportunity with **Janet Thomas**, who has recently turned 64, as depicted in the **Recent Change** field.|
| **Action** &nbsp; 6.3 | Select the radio button associated with **Janet Thomas (A)** from the table.<br/><img src="images/Script-6-3.png" width="800" /> |
| **Narration** | Next, the agent needs to determine which products to recommend for Janet based on her circumstances and recent life event.<br/><br/>The customer details from the CRM system are automatically submitted into watsonx Orchestrate’s built-in decision engine and the upsell recommendations are displayed. Behind the scenes, the decision engine applies business logic that considers many different attributes specific to this customer (Janet Thomas), such as age, life event, and current coverage to determine the best product that the insurance agent should suggest to this customer.|
| **Action** &nbsp; 6.4 | Click the **Apply** button. <br/><img src="images/Script-6-4.png" width="800" />|
| **Action** &nbsp; 6.5 | Two skills have run in quick succession, scroll back so that the upsell decision output is displayed.<br/><img src="images/Script-6-5.png" width="800" /> |
| **Narration** | In this case, the decision engine recommended the **Silver Travel Insurance Plan**, and based on this, it has also created a prompt for a generative AI model to create the marketing upsell email. |
| **Action** &nbsp; 6.6 | Review the prompt then scroll to the bottom of the chat window to review the input for the generative AI model.<br/><img src="images/Script-6-6.png" width="800" />|
| **Action** &nbsp; 6.7 |Perform the following steps:<br/><br/>A. Review the prompt created for the customer (**Janet Thomas**).<br/>B. Click the **Apply** button.<br/><img src="images/Script-6-7.png" width="800" />|
| **Narration** | Clicking **Apply**, submits the prompt into the Generate an email skill, and this will take approximately thirty seconds to complete. For this particular skill, watsonx Orchestrate is working asynchronously, it’s not blocking and waiting for a response that may otherwise time-out. Instead, it is notified by the long running activity when the work is finished and then resumes the skillflow. During this waiting time, the user is able to do other work, and can jump back to this task once the response is received. <br/><br/>The response created for the customer (Janet Thomas) is returned and displayed. The customer email address, subject and email body are pre-filled, allowing the user to review the generated content for accuracy and add any further information to ensure the proposal is relevant to the customer. |
| **Action** &nbsp; 6.8 | Review the generated email. <br/><img src="images/Script-6-8.png" width="800" />|


<br/>

**[Go to top](#top)**

</details>

<span id="spanID"></span>
<details markdown="1">

<summary>7 – Summary </summary>

<br/>

Using an upsell/cross-sell example, this lab showed how watsonx Orchestrate provides a conversational interface for insurance sales agents to perform daily repetitive tasks and reduce the time it takes to complete common business tasks, such as searching through CRM reports for sales opportunities.

A pre-configured CRM search saved time and helped agents find upsell opportunities. Product expertise was used to create a watsonx Orchestrate automation that provides optimal product recommendations based on client circumstances. It then combined these recommendations with client details into a prompt that was submitted into an IBM generative AI model. The result was a client proposal derived from accurate client data, expert product knowledge and a trusted foundation model trained on enterprise data, ready for the agent for review.

By providing a catalog of skills, watsonx Orchestrate eliminated the need for this insurance agent to manually move data and context switch between different back-end applications. IBM watsonx Orchestrate streamlined this agent’s work by sequencing a series of skills within a skill flow, boosting their productivity, reducing errors, and enabling them to focus on higher value work.



<br/>

**[Go to top](#top)**

</details>

<span id="spanID"></span>
<details markdown="1">

<summary>8 – After your demo </summary>

<br/>

The watsonx Orchestrate environment used for the demo is shared by many users. After completing your demo, it is important to take a few minutes to remove any skills or automations you created during the demo. 
1. Click the **hamburger navigation** menu icon **(A)**, then click on **Skill studio (B)** from the left menu.<br/><img src="images/Script-8-1.png" width="800" /><br/><br/>
2. Select **Skills and apps** (A), **Skills (B)**, enter your unique reference, then press **Enter (C)**. After completing this demo there should be three skills. Click the ellipsis (three vertical dots) in the right-hand column for each skill **(D)** and select **Delete this skill (E)**. Take care to ensure you are only deleting your skills.<br/><img src="images/Script-8-2.png" width="800" /><br/><br/>
3. Click the **Automations** tab **(A)**. Enter your skill reference in the search panel and press **Enter (B)**. Click the ellipsis (three vertical dots) **(C)** and select **Delete (D)**.<br/><img src="images/Script-8-4.png" width="800" />

<br/>

**[Go to top](#top)**

</details>
