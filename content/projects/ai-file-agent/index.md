# AI Filesystem Assistant

[< Back Home](/)

I wanted to understand what actually happens when an AI model can do more than just generate text.

I built a command-line AI assistant that can inspect files, modify them, and execute Python programs using tools exposed through the Gemini API.

The important part wasn't just giving the model access to these capabilities, it was making sure these capabilities were **controlled**.

## Tech Stack

- Python
- Google Gemini API
- Function / tool calling
- Linux
- Git / GitHub

## How It Works

The assistant uses an iterative tool-calling loop.

The user provides a request which is sent to Gemini along with a set of available tools.  If Gemini decides that it needs to perform an operation, the application executes the requested function and sends the result back to the model.  

The process continues until the model can provide a _final_ response.  

```
            User Request
                |
                v
            Gemini API
                |
                v
         --- Tool Call? --- No -----> Response
       /             ^
     Yes              \
      |                \
      v             Gemini API
   Validate             ^
      |                 |
      v                 |
Execute tool -----> Tool Result
```

## Tool Registry

The available tools are kept separate from the model orchestration code.  

Each tool has its own implementation and schema, while a central function registry determines which functions the model is allowed to call.  

The current tools include:

- Reading directory information
- Reading file contents
- Writing files
- Running Python files

This separation allows me to add new capabilities without having to rewrite the agent's core execution loop.  

## Keeping AI In Its Sandbox

Giving an AI model the ability to manipulate files is useful.  Giving it the ability to manipulate _any file it wants_ is considerably less useful.

Every filesystem operation is restricted to a designated working directory.  Paths are resolved and validated before an operation is allowed to proceed, preventing requests from escaping that directory.  

The agent also validates function calls and handles errors explicitly, so invalid requests become tool results that the model can respond to rather than crashing the application.

## Running Code

The assistant can also execute Python programs inside its working directory.  

Execution is performed through a subprocess with captured output and a timeout that allows the agent to inspect the result without allowing a runaway process to indefinitely halt the application until my token limits reset.  

This was one of the more interesting parts of the project because it moved the agent beyond simply manipulating text files and into actually interacting with a running program.  

![AI assistant describing a program's function](/images/ai-overview.png)

![AI assistant fixing a script bug](/images/ai-fixing-calc.png)

## The Good

- Hands-on experience with Gemini's function-calling API
- Modular tool architecture
- Explicit validation and error handling
- A real application rather than a standalone API experiment

## The Bad

- The agent is limited to a small set of tools
- It only operates within its designated working directory
- The model can still misunderstand a request or make a questionable decision

### The Ugly

The agent can write code and then _run that code_.  

Which is either a handy feature or the start of a terrible idea, depending how carefully you build the walls around it.

[< Back Home](/)
