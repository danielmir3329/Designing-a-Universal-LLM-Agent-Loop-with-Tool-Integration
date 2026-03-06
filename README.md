# Universal LLM Agent Loop with Tool Integration

This project demonstrates how to build a **provider-agnostic LLM agent loop** that can call tools, execute functions, and return final answers using a shared interface. The notebook shows how to separate the **agent logic**, **tool definitions**, and **LLM provider clients** so the same loop can work across multiple model providers with minimal code changes.

The main idea is simple: an agent sends a user message to an LLM, checks whether the model wants to call a tool, executes that tool, sends the result back to the model, and repeats until a final answer is produced. By standardizing this workflow, the project makes it easier to reuse the same architecture with different LLM backends.
 
## Project Goals

The notebook is designed to:

- Explain the mental model behind tool-calling agents
- Define tools in a provider-independent structure
- Create a shared client abstraction for multiple LLM providers
- Implement a reusable agent loop
- Demonstrate tool execution with example prompts
- Show how to switch providers without rewriting the core agent logic

## Key Features

- **Universal tool schema** using a common Python dataclass
- **Reusable agent loop** that works across supported providers
- **Tool-calling support** for weather and math examples
- **LLM client abstraction** for cleaner architecture
- **Provider swap flexibility** with minimal code changes
- **Hands-on notebook examples** for testing single-tool, multi-tool, and no-tool scenarios

## Project Structure

The notebook is organized into the following conceptual sections:

1. **Setup**  
   Installs dependencies and configures API access.

2. **Mental Model**  
   Explains how a tool-calling agent works as a loop.

3. **Tool Definitions**  
   Introduces a universal `Tool` structure and example tool functions.

4. **LLM Client Abstraction**  
   Defines a common interface for model providers.

5. **Provider Implementations**  
   Includes implementations for Gemini and Anthropic clients.

6. **Agent Loop**  
   Builds the reusable orchestration logic that drives the agent.

7. **Testing and Examples**  
   Runs the agent on sample user prompts.

## Technologies Used

- **Python**
- **Jupyter Notebook**
- **google-genai**
- **anthropic**
- **Dataclasses**
- **JSON Schema-style tool definitions**

## Example Tools in the Project

The notebook includes two example tools:

- **`get_weather`**  
  Returns mock weather information for a city

- **`calculate`**  
  Evaluates a math expression

These examples keep the project easy to understand while still showing the full architecture needed for real-world tool calling.

## Agent Workflow

The universal agent loop follows this pattern:

1. Receive a user message
2. Send the message and tool schemas to the LLM
3. Detect whether the model requested one or more tools
4. Execute the requested tool functions
5. Send tool results back to the model
6. Repeat until the model returns a final answer or the maximum number of turns is reached

This design mirrors how modern LLM agents operate in production environments.

## Supported Provider Pattern

The notebook shows how to implement the same interface for different providers. In this project, the architecture includes:

- **Gemini client**
- **Anthropic client**

Because both clients follow the same interface, the core agent loop does not need to change when switching providers. Only the client instantiation line changes.

## Why This Project Matters

Many LLM projects become difficult to maintain because provider-specific logic is mixed directly into the application flow. This notebook solves that problem by separating concerns:

- **tools** define what the agent can do
- **clients** define how each provider communicates
- **the agent loop** defines how reasoning and action happen

That separation makes the system more modular, reusable, and easier to extend.

## Results Demonstrated

The notebook includes example runs for:

- a weather question
- a math calculation
- a multi-tool prompt
- a prompt that requires no tool usage



## Installation

```bash
pip install google-genai anthropic
