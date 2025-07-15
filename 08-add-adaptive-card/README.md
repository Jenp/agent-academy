# Enhance user interactions in Topics with Adaptive Cards

## Lesson chapters

- [What is an Adaptive Card?](#-what-is-an-adaptive-card)
    - [Why Adaptive Cards matter in Copilot Studio](#why-adaptive-cards-matter-in-copilot-studio)
- [Is _JSON_ a person?](#-is-json-a-person)
- [I see another option for building an adaptive card using _formula_](#-i-see-another-option-for-building-an-adaptive-card-using-formula)
    - [How Power Fx works in Adaptive Cards](#how-power-fx-works-in-adaptive-cards)    
    - [Why it's useful](#why-its-useful)
- [Building with the Adaptive Card Designer](#️-building-with-the-adaptive-card-designer)
- [Understanding the Adaptive Card Designer](#-understanding-the-adaptive-card-designer)
- [Common use cases](#-common-use-cases)
- [Best practices](#-best-practices)
- [Lab 08 - Add apative cards and enhance topic capabilities](#-lab-08---add-adaptive-cards-and-enhance-topic-capabilities)
    - [Use case](#-use-case)
    - [Prerequisites](#prerequisites)
    - [8.1 Add an adaptive card to display available devices](#81-add-an-adaptive-card-to-display-available-devices)
    - [8.2 Add a condition node to enable users to request a device](#82-add-a-condition-node-to-enable-users-to-request-a-device)
    - [8.3 Create a new topic with an adaptive card for user to submit their request](#83-create-a-new-topic-with-an-adaptive-card-for-user-to-submit-their-request)
    - [8.4 Update _Available devices_ topic to redirect to the newly created topic](#84-update-available-devices-topic-to-redirect-to-the-newly-created-topic)
- [Additional learning](#-additional-learning)

## 🤔 What is an Adaptive Card?

An **Adaptive Card** is way to create interactive, visually rich UI elements that can be embedded in apps like Microsoft Teams, Microsoft Outlook or agents. It is a structured JSON object that defines the layout and content of a card:

- What elements appear on the card - text, images, buttons
- How those elements are arranged
- What actions users can take such as submitting a form or opening a link

    ![Adaptive Card](assets/8.0_01_AdaptiveCard.png)

### Why Adaptive Cards matter in Copilot Studio

Imagine you're building an agent that asks users for their name, email, or feedback. If you just use plain text, the conversation can feel boring or hard to follow. That’s where Adaptive Cards come in!

1. **Makes conversations interactive** - instead of sending text as messages to the user, you can show buttons, forms, images and more.
    - Example: a card can ask the user to fill in their name and email in a clean form.

1. **Look great everywhere** - Adaptive Cards automatically match the style of the app they're in, such as Microsoft 365 Copilot chat or Microsoft Teams. You don't need to worry about dark mode, font, or layouts - it adapts.

1. **Easy to build with JSON** - you define the card using JSON code (think _recipie_ for the UI). Copilot Studio helps you preview your card before adding it to the topic.

1. **Collect and use data** - you can use card to ask questions, collect answers, and use that ata in the conversation flow.
    - Example: Ask for a user's phone number, then show a confirmation card with their phone number.

1. **Boost user experience** - cards make your agent feel more interactive. It's a more clean, clickable, and user-friendly type of interface.

## 🐱 Is _JSON_ a person?

Pronounced as "Jason," it's not a person 😅

JSON, otherwise known as _JavaScript Object Notation_ is a lightweight format used to structure data. It's easy to read and write, and looks like a series of key-value pairs inside curly braces {}.

This is one of the options to use when adding an adaptive card to your topic.

![Adaptive card node properties](assets/8.0_02_AdaptiveCardPropertiesPane.png)

## 👀 I see another option for building an adaptive card using _formula_

Remember how we learnt about Power Fx in [Lesson 07 - Add new topic with trigger and nodes](/07-add-new-topic-with-trigger/README.md/#️-using-power-fx-in-your-nodes)? The same can be applied in Adaptive Cards within Copilot Studio. 

As a recap,

> Power Fx is a low-code programming language used to add logic and dynamic behaviour to your agent. It's the same language used in Microsoft Power Apps, and it's designed to be simple and Excel-like, making it easy for developers and non-developers.

### How Power Fx works in Adaptive Cards

When you design an Adaptive Card in Copilot Studio, you can use Power Fx formulas to:

- Dynamically insert values such as user names, dates or status.
- Format text or numbers such as show currency or round numbers.
- Show or hide elements based on conditions.
- Customize responses based on user input, variables, outputs from conversation nodes.

For example,

"<samp>Hello</samp>" & `System.User.DisplayName`

This formula combines the word "Hello" with the user's name dynamically.

### Why it's useful

1. **Personalization**

    You can tailor message to each user, making interactions feel more natural and relevant.

1. **Dynamic content**

    Cards can display real data from variables and outputs from conversation nodes.

1. **Smart logic**

    You can control what users see or interact with based on conditions, improving usability and reducing errors.

1. **Low-code friendly**

    Power Fx is a low-code programming language. As mentioned earlier, it's readable, intuitive and similar to Excel formuals.

## 👷🏻‍♀️ Building with the Adaptive Card Designer

The **Adaptive Card Designer** is a visual tool that lets you build interactive message cards using drag-and-drop elements like text, images, buttons, and inputs. Its purpose is to help you create rich, dynamic messages without writing complex code, making it easier to design user-friendly interfaces.

The designer tool helps you build the card visually, but behind the scenes, it’s generating the JSON object for you. You can also switch to _formula_ which enables Power Fx expressions to be used in the card to display data from else where.

## 🎨 Understanding the Adaptive Card Designer

![Adaptive Card Designer](assets/8.0_03_AdaptiveCardPropertiesPane.png)

**A) Card Elements**

These are the building blocks of your adaptive card. You can drag and drop elements such as the following:

- **TextBlock** to display text.
- **Image** to show show pictures.
- **FactSet** for key-value pairs.
- **Input fields** to display text boxes, date pickers, toggles.
- **Actions** to display buttons such as _Submit_, _Open URL_, or _Show Card_.

Each element has its own purpose and can be styled or configured.

**B) Card viewer**

This is the **Preview** area where you see how your card will look like in real time. As you add or edit elements, the viewer updates instantly to reflect changes. This enables you to make iterative updates and see the design output at the same time.

**C) Card structure**

This shows the **hiearchy and layout** of your card. For example:

- A card might start with a **TextBlock** for the title.
- Then a **ColumnSet** with an image on one side and text on the other.
- Followed by a **FactSet** and some **Action buttons**.

It helps you understand how elements are nested and organized.

**D) Element properties**

When you click on any element in the card, this panel lets you **customize its settings**:

- Change text size, weight, or color.
- Set image URLs or alt text.
- Configure input options like placeholder text or default values.

This is where you fine-tune each element.

**E) Card Payload Editor**

This is the **raw JSON code** behind your card. Advanced users can edit this directly to:

- Use templating features.
- Copy/paste card definitions.

Even if you're new to the Adaptive Card designer, it's helpful to see how the visual design translates into codes.

## 🌵 Common use cases

The following are common use cases for Adaptive Cards in Copilot Studio when used in the **Send a message** or **Ask a question** nodes.

1. **Forms and data collection**

    Use adaptive cards to collect structured input from users, such as:
    - Leave requests
    - Feedback forms
    - Contact information
    - Appointment scheduling

1. **Displaying dynamic information**

    Shows users personalized or real-time data in a clean, readable format from enterprise sources such as ServiceNow, SAP, Dynamics 365, SharePoint etc.

    - Order summaries
    - Account balances
    - Ticket or case status
    - Upcoming events or deadlines

1. **Interactive choices**

    Let users make selections directly in the conversation:

    - Choose from a list of options, for example product categories, support topics.
    - Confirm or cancel action.
    - Rate a service or experience.

1. **Triggering actions**

    Include buttons that trigger further steps in the conversation internally or externally.

    - "Sumbit request"
    - "View details"

## ⭐ Best practices

Here are some best practices for creating Adaptive Cards for agents in Copilot Studio.

1. **Keep it simple and focused**

    - Design cards with a clear purpose, don’t overload them with too many elements.
    - Use concise text and intuitive layouts to guide users through the interaction.

1. **Be intentional with inputs**

    - Include only the necessary input elements such as text, date choices, to avoid overwhelming users.
    - Use labels to make inputs easy to understand.

1. **Structure for readability**

    - Use **TextBlocks** for headings and instructions.
    - Group related elements using **Containers** or **ColumnSets** to improve visual flow.

1. **Make Action elements clear**

    - Use **Action.Submit** and or **Action.OpenUrl** with clear button titles like "Submit Request" or "View Details"
    - Avoid vague labels like "Click here"

1. **Design for adaptability**

    - Assume the card may be viewed on different screen sizes.
    - Avoid fixed widths and use flexible layouts like **ColumnSets** for responsiveness.

1. **Use dynamic content when possible**

    - Bind card elements to variables or outpus from nodes using Power Fx to personlize the user experience.
    - For example, show the user's name or current status dynamically.

## 🧪 Lab 08 - Add adaptive cards and enhance topic capabilities

We're now going to learn how to enhance our topic with adaptive cards and using advanced functionality of topics and nodes. 

- [8.1 Add an adaptive card to display available devices](/08-add-adaptive-card/README.md/#81-add-an-adaptive-card-to-display-available-devices)
- [8.2 Add a condition node to enable users to request a device](/08-add-adaptive-card/README.md/#82-add-a-condition-node-to-enable-users-to-request-a-device)
- [8.3 Create a new topic with an adaptive card for user to submit their request](/08-add-adaptive-card/README.md/#83-create-a-new-topic-with-an-adaptive-card-for-user-to-submit-their-request)
- [8.4 Update _Available devices_ topic to redirect to the newly created topic](/08-add-adaptive-card/README.md/#84-update-available-devices-topic-to-redirect-to-the-newly-created-topic)

### ✨ Use case

**As an** employee

**I want to** request a device

**So that I** can request a device from the list of available devices

Let's begin!

### Prerequisites

1. **SharePoint list**

    We'll be using the **Devices** SharePoint list from [Lesson 00 - Course Setup - Step 3: Create new SharePoint site](/00-course-setup/README.md/#step-3-create-new-sharepoint-site). 
    
    If you have not set up the **Devices** SharePoint list, please head back to [Lesson 00 - Course Setup - Step 3: Create new SharePoint site](/00-course-setup/README.md/#step-3-create-new-sharepoint-site).

1. **Contoso Helpdesk Copilot**

    We're going to use the same agent created previously in [Lesson 06 - Create a custom agent using natural language with Copilot and grounding it with your data](/06-create-agent-from-conversation/README.md).

### 8.1 Add an adaptive card to display available devices

1. In the **Available devices** topic delete the **Send a message** node that contains the JSON response of the _Get items_ SharePoint connector action in the body of the message.

    ![Delete Send a message node](assets/8.1_01_DeleteSendMessageNode.png)

1. Select the **+ icon** and select **Send a message** node.

    ![Add Send a message node](assets/8.1_02_AddSendAMessageNode.png)

1. Select *+ Add* and select **Adaptive card**.

    ![Select adaptive card](assets/8.1_03_SelectAdaptiveCard.png)

1. We're now going to edit the JSON. Select **Edit adaptive card**.

    ![Add Send a message node](assets/8.1_04_EditAdaptiveCard.png)

1. This is the **Adaptive Card Designer** where you can design your card and see the card design in-real time. 

    Try dragging and dropping the TextBlock and FactSet card elements to the authoring canvas - the card viewer area. Notice how the card structure and card payload editor updates as the two card elements were added. You can directly update the card payload editor and the element properties pane.

    ![Drag and drop card elements](assets/8.1_05_DragAndDropCardElements.png)

1. Select **Preview** to view the card in different widths.

    ![Select preview](assets/8.1_06_PreviewAdaptiveCard.png)

1. The preview will load where you'll see different card output by widths.

    ![Preview card at different widths](assets/8.1_07_PreviewCardWidths.png)

1. Exit out of **Preview** by selecting the **x icon** and select **Undo** in the designer to remove the two card elements previously added.

    ![Undo](assets/8.1_08_Undo.png)

1. Click into the **Card payload editor** and select all lines using the Windows keyboard shortcut of _Ctrl + A_ or using the Mac keyboard shortcut of _Command + A_, followed by deleting the lines.

    ![Clear lines](assets/8.1_09_01_CTRLA.png)

    Paste the JSON from the [Available devices .JSON file](assets/8.1_AvailableDevices.json).

    ![Paste JSON](assets/8.1_09_02_PasteJSON.png)

1. Notice how the **Card Preview** now includes elements that display an image, the model, the manufacturer and the color of the device. Select **Save**. 

    ![Select Save](assets/8.1_10_SaveJSONAdaptiveCard.png)

1. Close the Adaptive Card properties pane by selecting the **X icon**.

    ![Close pane](assets/8.1_11_ExitAdaptiveCardProperties.png)

1. The **Send a message** node will now display the adaptive card in the authoring canvas. Select **Save** to save the topic.

    ![Save topic](assets/8.1_12_ViewAndSave.png)

1. Let's next test our initial adaptive card design. **Refresh** the test pane and enter the following,

    ```
    I need a laptop
    ```

    ![Test adaptive card](assets/8.1_13_TestAdaptiveCard.png)

1. Select laptop from the list and you'll next see the available devices adaptive card. This is the JSON structure we'll use for our adaptive card which we now need to bind to the output of the **Get items** SharePoint connector action from the previous node we configured in [Lab 07 - Add a new topic with conversation nodes, 7.3 Add node - Add a tool using a connector](/07-add-new-topic-with-trigger/README.md/#73-add-node---add-a-tool-using-a-connector).

    ![Select preview](assets/8.1_14_AdaptiveCardTestResult.png)

1. Let's now update our card to use **Power Fx formulas**. **Refresh** the test pane and select the **X icon** in the Activity map.

    ![Refresh test pane adn close Activity map](assets/8.1_15_RefreshAndCloseActivityMap.png)

1. Select the adaptive card in the authoring canvas and select the **chevron** icon to switch from **JSON** to **Formula**. Select **Formula**.

    ![Select Formula](assets/8.1_16_SwitchToFormula.png)

1. Click into the **Card payload editor** and select all lines using the Windows keyboard shortcut of _Ctrl + A_ or using the Mac keyboard shortcut of _Command + A_, followed by deleting the lines. 

    ![Select all and delete lines](assets/8.1_17_CTRLA.png)

1. Paste the Formula from the [Available Devices formula file](assets/8.1_AvailableDevicesFormula.txt).

    ![Select preview](assets/8.1_18_PasteFormula.png)

1. Let's take a closer look at the Power Fx functions used. To loop through the items returned in the **Get items** SharePoint connector action, we're using the `For All` function that lets you perform an action on each item in a list or table. 

    > Think of it like saying: _"For each item in this list, do something with it."_

    In our use case, we're going to loop through each of the SharePoint list items returned in the **Get items** SharePoint connector action stored in the global variable, `Global.VarDevices`, via the `value` property of the JSON response. 
    
    > We created this global variable in [Lab 07 - Add a new topic with conversation nodes, 7.3 Add node - Add a tool using a connector](/07-add-new-topic-with-trigger/README.md/#73-add-node---add-a-tool-using-a-connector).

    ![Power Fx expression](assets/8.1_19_01_PowerFxExpression.png)

    We'll loop through each SharePoint list item to display the device _image_, _model_, _manufacturer_ and _color_. Since we binded the items property in the card to the `value` property of our SharePoint JSON response stored in the global variable, we can now simply reference the properties that we want. 
    
    Below is a screenshot of where the reference to the `Image` property is used in the **image element** of the adaptive card.

    ![Image property](assets/8.1_19_02_PowerFxExpression.png)

    Below is a screenshot of where the references to the `Model` and `Manufacturer.Value` preoperties is used in the **Input.ChoiceSet elements** of the adaptive card.

    ![Model and Manufacturer properties](assets/8.1_19_03_PowerFxExpression.png)

1. Let's now save our topic and test our agent. Close the **Card Content** modal by selecting the **X icon** and select the **X icon** in the **Adaptive Card properties** pane.

    ![Close Adaptive Card properties pane](assets/8.1_20_ExitFromAdaptiveCardPropertiesPane.png)

1. Select **Save** to save the topic.

    ![Save topic](assets/8.1_21_SaveTopic.png)

1. **Refresh** the test pane and enter the following,

    ```
    I need a device
    ```

    ![Test topic](assets/8.1_22_TestTopic.png)

1. Select laptop from the list and you'll next see the available devices adaptive card. This time, it's displaying the data from the Devices SharePoint list using the JSON response of the **Get items** SharePoint connector action stored in the global variable that we binded the adaptive card to using Power Fx. 

    ![Formula adaptive card test result](assets/8.1_23_AdaptiveCardTestResult.png)

1. **Refresh** the test pane and **close** the Activity map.

    ![Refresh and close Activity map](assets/8.1_24_RefreshAndCloseActivityMap.png)

Awesome! 🙌🏻 You've designed and added your first Adaptive Card to your topic for your agent in Copilot Studio.

### 8.2 Add a condition node to enable users to request a device

We'll now add logic for the user to request a device from the list where the status equals _Available_. To achieve this, we're going to add an **Ask a Question** node and a **Condition** node. 

Let's start with the question node.

1. In our **Available devices** topic, we'll add an **Ask a Question** node below the **Send a message** node with the adaptive card.

    ![Select Ask a Question node](assets/8.2_01_AddAskAQuestionNode.png)

1. We'll now define the node. For the question, enter the following.

    ```
    Would you like to request one of these available devices?
    ```

    Next, select **+ New option** as we'll add a value for the user to select.

    ![Configure Question node](assets/8.2_02_DefineQuestionNode.png)

1. Enter `Yes` as the first value for the user to select.

    ![Yes option](assets/8.2_03_AddYesOption.png)

1. Select **+ New option** to add another value. Enter `No` as the second value for the user to select.

    ![No option](assets/8.2_04_AddNoOption.png)

1. We'll now rename the output variable. Select the variable to load the **Variable properties** pane and name the variable as the following.

    ```
    VarRequestDevice
    ```
    ![Rename variable](assets/8.2_05_RenameVariable.png)

1. Close the **Variable properties** pane.

    ![Close variable properties pane](assets/8.2_06_CloseVariablePropertiesPane.png)

1. We'll next add logic to our topic by selecting the **Add a condition** node.

    ![Add a condition](assets/8.2_07_AddAConditionNode.png)

1. In the Condition node, we need to configure the logic. First we select a variable by selecting the **greater-than symbol**.

    ![Select variable](assets/8.2_08_SelectAVariable.png)

1. Select the **VarRequestDevice** variable previously created. This is the variable that stores the Yes/No selected value from the **Ask a Question** node.

    ![Select VarRequestDevice variable](assets/8.2_09_SelectVarRequestDeviceVariable.png)

1. Leave the condition set to **is equal to** since our logic is based on the Yes/No value the user selects from the **Ask a Question** node. In the value dropdown field, select **Yes**. 

    ![Define Yes condition node](assets/8.2_10_YesCondition.png)

1. We've now defined this Condition node to execute only when the **VarRequestDevice variable value equals Yes**. Select **Save** to save the topic.

    ![Save Topic](assets/8.2_11_SaveTopic.png)

### 8.1 Create a new topic with an adaptive card for user to submit their request

We'll create a new topic that will handle a user's device request. This new topic will contain an **Ask with adaptive card** node to enable user interaction with the agent.

Let's begin!

1. Select the **Topics** tab.

    ![Select Topics tab](assets/8.3_01_SelectTopicsTab.png)

1. Select **+ Add a topic from blank**.

    ![Add new topic form blank](assets/8.3_02_AddATopicFromBlank.png)

1. Name the topic as the following,

    ```
    Request device
    ```

    ![Request device](assets/8.3_03_RenameTopic.png)

1. In the **Trigger** node, we're going to change the trigger type. Select the **opposite arrows icon** and select the trigger type, **It's redirected to**.

    ![Change trigger](assets/8.3_04_ChangeTrigger.png)

1. Next, add an **Ask with adaptive card** node. This node will display an interactive card for the user to select which device they would like to request.

    ![Select Ask with adaptive card node](assets/8.3_05_AskWithAdaptiveCard.png)

1. Select the node and the **Adaptive Card Node properties** pane will appear. Select **Edit adaptive card**.

    ![Edit adaptive card](assets/8.3_06_EditAdaptiveCard.png)

1. The **Adaptive card designer** will load. Click into the **Card payload editor** and select all lines using the Windows keyboard shortcut of _Ctrl + A_ or using the Mac keyboard shortcut of _Command + A_, followed by deleting the lines.

    ![Clear card payload editor](assets/8.3_07_01_CTRLA.png)

    Paste the JSON from the [Request devices .JSON file](assets/8.3_RequestDevice.json).

    ![Paste JSON](assets/8.3_07_02_PasteJSON.png)

1. Notice how the **Card Preview** now includes elements that display some text and a list of available devices.

    This JSON is currently a placeholder and preview to what we'll use as the base for our card but in the form of a formula rather than JSON since we're going to reference the **global variable**, `Global.VarDevices`, that stores the response of the **Get items** SharePoint connector action.

    Select **Save** and select **Close** to exit from the Adaptive card designer modal.

    ![Select Save](assets/8.3_08_Save.png)

1. In the authoring canvas of the topic, you'll see the adaptive card.

    ![Adaptive card](assets/8.3_09_DeviceSelection.png)

1. Scroll to the bottom of the node and you'll see output variables. The `commentsId` and the `deviceSelctionId` were defined in the element properties. These two variables will store values from the card elements the users interact with. These values will be used downstream in the topic, which we'll learn about in the next lesson's lab.

    ![Node variable outputs](assets/8.3_10_Outputs.png)

1. Let's next update the card from JSON to formula as we'll use Power Fx again to loop through the items returned in the **Get items** SharePoint connector action, stored in the **global variable**, `Global.VarDevices`, via the `value` property of the JSON response.

    > We created this global variable in [Lab 07 - Add a new topic with conversation nodes, 7.3 Add node - Add a tool using a connector](/07-add-new-topic-with-trigger/README.md/#73-add-node---add-a-tool-using-a-connector).

    Select the card in the **Ask with Adaptive Card** node, followed by selecting the **chevron** icon and select **Formula**.

    ![Select Topics tab](assets/8.3_11_SelectFormula.png)
    
1.  Click into the **Card payload editor** and select all lines using the Windows keyboard shortcut of _Ctrl + A_ or using the Mac keyboard shortcut of _Command + A_, followed by deleting the lines. 

    ![Select all and delete lines](assets/8.3_12_01_CTRLA.png)

    Paste the Formula from the [Requst Devices formula file](assets/8.3_RequestDeviceFormula.txt).

    ![Select preview](assets/8.3_12_02_PasteFormula.png)

1. In the formula, we'll loop through each SharePoint list item using the `For All` function to display the values of model in the title of the choice option, and the SharePoint item ID is referenced as the value.

    ![Formula](assets/8.3_13_PowerFxFormula.png)

1. **Close** the card modal.

    ![Close](assets/8.3_14_Exit.png)

1. **Close** the **Adaptive Card Node properties** pane.

    ![Close Adaptive Card Node properties pane](assets/8.3_15_ExitFromAdaptiveCardPropertiesPane.png)

1. **Save** the topic.

    ![Save topic](assets/8.3_16_SaveTopic.png)

### 8.4 Update _Available devices_ topic to redirect to the newly created topic

Now that we created the new topic to redirect to, we need to update our original topic, _Available devices_ to point to it.

1. Select the *back arrow** icon to view the list of topics.

    ![Back to view topics](assets/8.4_01_Back.png)

1. Select the **Available devices** topic.

    ![Select Available devices](assets/8.4_02_SelectAvailableDevicesTopic.png)

1. Scroll down to the **Condition** node of the **Yes** path and select the **+ icon** to add a new topic.

    ![Add new node](assets/8.4_03_AddTopic.png)

1. Select **Topic management**, followed by selecting **Go to another topic** and then select **Request device**.

    When **Condition** node of the **Yes** path has been processed, the agent will redirect from the **Available devices** topic to the **Request devices** topic. 

    ![Redirect to Request device topic](assets/8.4_04_RedirectToRequestDevice.png)

1. **Save** the topic.

    ![Save topic](assets/8.4_05_SaveTopic.png)

1. Let's now test our the redirection from the _Available devices_ topic to the _Request devices_ topic. **Refresh** the test pane.

    ![Refresh test pane](assets/8.4_06_RefreshTopic.png)

1. Select the **Activity map** icon in the test pane, followed by enabling **Track between topics**. This will allow us to see the _Available devices_ topic redirected to the _Request devices_ topic.

    ![Enable track between topics setting](assets/8.4_07_TrackBetweenTopics.png)

1. OK, we're good to test! Enter the following in the test pane.

    ```
    I need a new device
    ```

    ![Test topic](assets/8.4_08_TestRedirectTopic.png)

1. Select **laptop** and we'll see our adaptive card display next. Below the adaptive card, we'll see a question that displays the two values of **Yes** and **No**. Select **Yes** to process the **Yes** path of the **Condition** node.

    ![Question node](assets/8.4_09_ConditionSelectYes.png)

1. We'll see the activity map update where it'll display the **Request device** topic. Select one of the devices from the **choices** card input and add a comment in the **text** input field (Additional Information) of the card. Then select **Submit Request** button.

    ![Question node](assets/8.4_10_RedirectedToRequestDeviceTopic.png)

1. We've now succesfully tested our _Available devices_ topic redirecting to the _Request devices_ topic. Ignore the escalation message if you do see this appear in the test pane. We'll be adding more enhancements to this topic in the next lesson's lab so this can be ignored.

    ![Test result](assets/8.4_11_TestResult.png)

1. Refresth the test pane.

    ![Refresh test pane](assets/8.4_12_RefreshTestPane.png)

## Next lesson
Congratulations! 👏🏻 You've learnt how to add adaptive cards using Power Fx formulas to display data from variables, and you also learnt how to redirect from one topic to another. Creating bite sized topics makes your agent more organized, but also helps guide users through different parts of the conversation flow with the agent.

This is the end of **Lab 08 - Enhance user interactions with Adaptive Cards**, select the link below to move to the next lesson. We'll expand on the use case in this lab in the following lesson's lab.

⏭️ [Move to **Add an agent flow to your Topic for automation** lesson](/09-add-an-agent-flow/README.md)


## 📚 Additional learning
🔗 [Using Adaptive Cards in Copilot Studio](https://learn.microsoft.com/en-us/microsoft-copilot-studio/guidance/adaptive-cards-overview?WT.mc_id=power-170631-ebenitez)

🔗 [Add an adaptive card in Send a message node](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-send-message#add-an-adaptive-card?WT.mc_id=power-170631-ebenitez)

🔗 [Create expressions using Power Fx](https://learn.microsoft.com/en-us/microsoft-copilot-studio/advanced-power-fx?WT.mc_id=power-170631-ebenitez)

📺 [Building Adaptive Cards with Power FX](https://aka.ms/ai-in-action/copilot-studio/ep8)


