# Chatting with AI and vibe coding 
Taken/adapted from:

https://code.visualstudio.com/docs/chat/chat-overview

https://code.visualstudio.com/docs/agents/overview

## Objectives 
- Using AI productively
- Using chat in VS Code
- Running Agents
- Guidance and ethics of using AI

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

## Use chat in VS Code
A new-ish feature in VS Code is an integrated chat. The panel can be added by going to the "View" drop-down menu and selecting "Chat". This should open a side bar with a little text box at the bottom. 
You will need to select an AI model (e.g., Copilot or chatGPT). If you are able to set this up, you can then use the chat to ask questions about your code or error. It is useful but shouldn't be your default.

## Building and running Agents
Agentic coding has also blown up in recent times, and this is the use of AI agents to complete coding and software tasks without (much) prompting. Rather than having a back and forth with a chat bot, here you 
give the "bot" aka agent a high-level goal. The AI then can gather context and plan the work. Note, it can also edit files, run commands, and iterate on the result which could be good but also requires careful checks. 
Agents are known to delete things! But current versions require that you decide on some changes but you still need to be cautious about the level of autonomy you provide it.  

## Guidance and ethics
Although it sounds great to be able to vibe code your way through assignments and boring tasks, you will miss out on the learning process if you default to AI all the time. 

