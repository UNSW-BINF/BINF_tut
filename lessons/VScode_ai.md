# Chatting with AI and vibe coding 
Taken/adapted from:

https://code.visualstudio.com/docs/chat/chat-overview

https://code.visualstudio.com/docs/agents/overview

## Objectives 
- Using AI productively
- Using chat in VS Code
- Running Agents
- Guidance and ethics of using AI
  
### Use chat in VS Code
A new-ish feature in VS Code is an integrated chat. The panel can be added by going to the "View" drop-down menu and selecting "Chat". This should open a side bar with a little text box at the bottom. 
You will need to select an AI model (e.g., Copilot or chatGPT). If you are able to set this up, you can then use the chat to ask questions about your code or error. It is useful but shouldn't be your default.

### Building and running Agents
Agentic coding has also blown up in recent times, and this is the use of AI agents to complete coding and software tasks without (much) prompting. Rather than having a back and forth with a chat bot, here you 
give the "bot" aka agent a high-level goal. The AI then can gather context and plan the work. Note, it can also edit files, run commands, and iterate on the result which could be good but also requires careful checks. 
Agents are known to delete things! But current versions require that you decide on some changes but you still need to be cautious about the level of autonomy you provide it.  

### Guidance and ethics
Although it sounds great to be able to vibe code your way through assignments and boring tasks, you will miss out on the learning process if you default to AI all the time. 

## Setting up 
VSCode supports Local, GitHub Copilot, Anthropic Claude, and OpenAI Codex *agent harnesses*. 
It also provides a Cloud target for running an available cloud agent remotely. 
An agent harness coordinates an agent session, including tool calls, context, and code changes. 
We are going to use GitHub Copilot in this tutorial. 

### Github Copilot
1. Hover over the Copilot icon in the Status Bar and select Use AI Features.
2. Choose a sign-in method and follow the prompts.
- If you already have a Copilot subscription for your account, VS Code will use that subscription.
- If you don't have a Copilot subscription yet, you'll be signed up for the Copilot Free plan and get a monthly allowance of inline suggestions and AI credits
  
### Removing AI features 
To disable the built-in AI, use the _chat.disableAIFeatures_ setting, similar to how you configure other features in VS Code through the settings.   
This disables and hides features like chat or inline suggestions in VS Code and disables the Copilot extensions. You can configure the setting at the workspace or user level.
This setting is available in the Settings editor (Ctrl+,), or you can edit the settings.json file in the workspace.

### Session controls and permissions 

| Control	| What it determines | Default | 
| ------------- | ------------- | ------------- |
| Session Target | Which harness runs the session and where its tools operate | Copilot |  
| Agent	| Which instructions, tools, and behavior apply | Agent or Plan |
| Language model |	How the agent reasons, how quickly it responds, and how it consumes AI credits | Auto |  
| Permissions	| Which actions require your confirmation | Manual |
| Code isolation	| Whether changes go into the current folder or another Git | Current folder | 

## Quickstart!
### Step 1: Create a project folder
- Run the following command in your terminal to create the project folder and then open to work within this folder in VScode. 
```
mkdir agent-quickstart
```
- Then select File > Open Folder from the menu, and then open the agent-quickstart folder. If VSCode asks whether you trust the folder, select Manage from the notification, and then select Trust. 

### Step 2: Building an app in chat view
The Chat view lets you work with agents alongside your editor within a specific project. 
This approach is useful for coding tasks where agents assist you in real-time while you develop your code.
- Open the Chat view with Ctrl+Alt+I, and then select New Chat (+).
- Enter the following prompt in the chat and press Enter:
```
Create a task list web app in a single index.html file with embedded CSS and JavaScript. Let me add, complete, and delete tasks. Save the tasks in local storage so they persist after a page reload. Use no external libraries.
```
- The agent will run the task, and stop to request permission to edit or write files. It might also ask to validate/test which is important in development. If it did not do so, type in the prompt below. 
```
Open index.html in the integrated browser and validate the app.
Add a task, mark it complete, and delete it. Then add another task,
reload the page, and verify that the task persists. If any step fails,
fix the issue and repeat the complete flow.
```

### Step 3: Verify the result yourself
- The agent's validation report helps you find problems, but it doesn't replace your own review. In the integrated browser:
- Add a task and mark it complete.
- Reload the page and confirm that the task and its completed state persist.
- Delete the task and confirm that it doesn't return after another reload.
If a check fails, describe what you observed in chat and ask the agent to fix and retest it. Review the resulting diff before you commit the changes.

### Step 4: Stop, revise, or undo the work
- Ask the agent to make some modifications, like background colour, font size or adding emojis
- Play around and see what you can create!

### Step 5: Building an app in agent view
- Now we can do the same thing but in a dedicated agent-first interface. 
- Empty your quickstart folder (or make a new folder).
- Hover over the little hexagon in the title bar and select "Open in Agents"
- Select "New" at the top left sidebar, and select your emptied or new folder.
- As before, manage the Trust settings for this.
- Select the Copilot session target and the Agent role.
- Keep Manual permissions selected and use Auto for the language model if it is available.
- As before we need to send in a prompt. Let's use the same:
```
Create a task list web app in a single index.html file with embedded CSS and JavaScript. Let me add, complete, and delete tasks. Save the tasks in local storage so they persist after a page reload. Use no external libraries.
```
- Follow the agent's progress and review each approval request before you accept it. 

### Step 6: Check the code yourself
- Open the Changes panel in the right sidebar (Ctrl+Shift+G) and select index.html to review the generated code.
- If you're not happy with a specific part of the result, select it in the diff view and enter feedback to send it to the agent.
- Let's modify the title to say "TO DO list". Scroll down to the heading section, and give feedback to the agent to change the title.
- Click submit after you enter the feedback. The agent should run and you can then click on the "Taskflow" tab to see the updates.

### Step 7: Logging off 
- Open Command Palette Press Ctrl + Shift + P (Windows/Linux) or Cmd + Shift + P (Mac).
- Search for Account Management Type Accounts: Manage Accounts and select it.
- Sign Out In the list of accounts, locate your GitHub or GitHub Copilot Chat account. Click Sign Out.


## Just vibes: getting help with bioinformatics pipelines and code
Eventually, you will need to write out your own pipelines or develop your own software. It might be tempting to go straight to a bot, especially since you don't have to do much! But there is a lot more at stake with academic research - results need to be correct and it is might be difficult to judge/test your code without more knowledge about what is going on and what would make sense. 
Nevertheless, there are ways to make some of the tasks related to a project or coding task much easier. 
### Data pre-processing
A key part of any bioinformatics research is collecting and pre-processing data. In some of the previous tasks, we read in some datasets and checked/changed missing data. We can do this through the agent/chat mode by writing the prompts that will give us some of the additional checks we would do ourselves. Because you know what should be done (i.e., you've done it yourself before!), this is a productivity short-cut. 
- Make a new folder and copy over the "DatasaurusDozen.txt" from the data wrangling tutorial (https://unsw-binf.github.io/BINF_tut/lessons/python_datafun.html).
- Open that folder to work within it, and as before, manage the "Trust" settings. 
- In the chat prompt, type in a prompt to:
  - Make a python script to read in the "DatasaurusDozen.txt"
  - Printout information about the data like column names, fractions of missing data, what data types are present etc.
  - Output a text file with the mean, standard deviation, and correlations of the data.
- Run the script and check the outputs.

### Q1: How does it compare?
> How does the script and the output compare to yours from Week 4? What prompt(s) worked best? List all the steps/prompts and changes you had to make. 

### Data analysis 
- Copy over the "R_dataviz.Rdata" file from Week 8. Recall this file is in R so there will be some extra/different steps.  
- Prompt the agent/chat to write a second script to read this file in. This script could be an R script, but you might want a notebook/markdown book instead.
- Or, better yet, see if there is a way to convert it to be used in a python/jupyter notebook.
- Write a few prompts to answer all the questions and analysis for your Week 8 output.  

### Q2: How does it compare?
> How does the script and the output compare to yours from Week 8? What prompt(s) worked best? List all the steps/prompts and changes you had to make. How easy was it to do the analysis compared to before, knowing what you had to do?  


### Q3: What other analysis can you do - dataset X? 
> Think of three additional things you might want to do with dataset X that you do not know how to do (or have not done before). Write the prompts to do this. How would you check that the outputs are correct? 

### Q4: What other analysis can you do - dataset Y? 
> Think of three additional things you might want to do with dataset Y that you do not know how to do (or have not done before). Write the prompts to do this. How would you check that the outputs are correct here?  

 
  

  

