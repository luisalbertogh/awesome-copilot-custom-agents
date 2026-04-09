# awesome-copilot-custom-agents

[![awesome-copilot-custom-agents](https://img.shields.io/badge/github-Awesome_Custom_Agents-blue?logo=github)](https://github.com/luisalbertogh/awesome-copilot-custom-agents)
[![Copilot Agents](https://img.shields.io/badge/Copilot-Agent-586123)](https://docs.github.com/en/copilot/how-tos/use-copilot-agents/coding-agent/create-custom-agents?versionId=free-pro-team%40latest&productId=copilot&restPage=reference%2Ccustom-agents-configuration)
[![Copilot Skill](https://img.shields.io/badge/Copilot-Skill-5865F2)](https://docs.github.com/en/copilot/concepts/agents/about-agent-skills?versionId=free-pro-team%40latest&productId=copilot&restPage=reference%2Ccustom-agents-configuration)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

Custom agents, instructions, skills and more for your DevOps agents.

## :question:  What is the content about?

It is about customizations based on *well-known prompt engineering techniques and standards* accepted by most of the current AI agents that can be applied to tailor the usage of those **AI agents** to steer them towards specific tasks and output retrievals.

The following featured content can be found:

- **Custom Agents**: Pre-configured agents for specific tasks.
- **Prompts**: Ready-to-use prompts for various scenarios.
- **Instructions**: Guidelines to optimize agent performance.
- **Claude rules**: Like instructions but aimed at Claude Code usage.
- **Skills**: Ready-to-use sets of skills supported by AI agents like Copilot or Claude.
- **MCP**: MCP configurations to use together with previous skills and custom agents (as a reference).
- **Others**: Additional tools or resources used to play with AI agents (Docker files, etc).

## :rocket:  How to use it?

- Clone the repository.
- Copy the content you wished to use to your local AI environment.
- Tweak it to your needs and start using it.

### Usage with VS Code and Copilot

I have used these customizations with the below setup:

- VS Code `1.108.2` (or upper).
- Custom prompts, instructions and agents are copied to `%APPDATA%/Code/User/prompts` (in theory this is configurable using the Copilot settings, but that is the default location for my installation).
- Custom skill must be copied to `%USERPROFILE%/.copilot/skills` to make them available for all your projects. For individual projects, place them under `.github/` in each repository

If the previous is done:

- **Custom agents** will show up as an agent option from the Copilot console.

    ![Custom agents](./docs/pics/custom-agents.png)

- **Custom prompts and instructions** will be also available from the respective dropdowns in the Copilot console or they can be invoked using the proper syntax (for *prompts*). Custom instructions should be automatically loaded by the agent based on the provided prompt and the custom instructions metadata.

    ![Custom prompt](./docs/pics/custom-prompt.png)

- **Custom skills** will be visible to any agent. Ask the agent to indicate what skills are available, for example.

    ![Custom skills](./docs/pics/ask-skills.png)

### Usage with Claude Code

Most of the resources are also valid for Claude Code. Just place them where Claude can find them. To use them inside VSCode with the Claude Code extension:

- For user level (valid for ALL your projects) place then under Custom skill must be copied to `%USERPROFILE%/.claude/`. For example, for the skills, place them under `%USERPROFILE%/.claude/skills`, etc.

At project level, resources will go under `.claude/` for Claude Code, or under `.github/` for Copilot.

## :scroll: The collection

The following can be found within this repository.

### Custom agents

Under the `agents` folder, the below custom agents:

| Agent Name | Agent Definition | Purpose | MCP Tools |
|------------|------------------|---------|-------|
| Context7 Agent | [context7.agent.md](./agents/context7.agent.md) | Invoke [Context7](https://context7.com/) API to retrieve latest updates on proposed software libraries and tools. Originally obtained from [here](https://github.com/github/awesome-copilot/blob/main/agents/context7.agent.md). | Context7 MCP server |
| AWS Solutions Architect Agent | [awsarch.agent.md](./agents/awsarch.agent.md) | Specialized **AWS solutions architect** with extra capabilities to draft a global AWS solution. Create documentation and render all the necessary diagrams. If asked, scaffold Terraform code to kick off the project. | AWS Knowledge MCP server, AWS Documentation MCP server, custom D2 skill, custom Terraform skill |
| Azure Solutions Architect Agent | [azurearch.agent.md](./agents/azurearch.agent.md) | Specialized **Azure solutions architect** with extra capabilities to draft a global Azure solution. Create documentation and render all the necessary diagrams. Scaffold Terraform code to kick off the project. | Context7, Microsoft Learn, azure-mcp-server/azureterraformbestpractices, azure-mcp-server/get_azure_bestpractices, custom D2 skill, custom Terraform skill |

### Custom skills

Under the skills folder, the below custom skills for usage with AI agents can be found:

| Skill Name | Skill Definition | Purpose |
|------------|------------------|---------|
| D2 Skill | [d2-sketcher](./skills/d2-sketcher/SKILL.md) | Generate diagrams using [D2](https://d2lang.com/) language. |
| Microsoft docs | [microsoft-docs](./skills/microsoft-docs/SKILL.md) | Query official Microsoft documentation to understand concepts, find tutorials, and learn how services work. |
| IaC Skill | [iac-skill](./skills/iac-skill/SKILL.md) | Apply best practices and recommendations when working with Terraform (*Opentofu and Terragrunt to come*) |
| AWS CDK Development | [aws-cdk-development](./skills/aws-cdk-development/SKILL.md) | Best practices and recommendations on AWS CDK development for IaC on AWS |
| Python Code Style | [python-code-style](./skills/python-code-style/SKILL.md) | Python code style recommendations [IT NEEDS FURTHER REVIEW] |

### Custom instructions and Claude rules

Under the `instructions` folder, the below custom instructions can be found:

| Instruction Name | Instruction Definition | Purpose |
|------------------|------------------------|---------|
| Markdown Instruction | [markdown.instruction.md](./instructions/markdown.instructions.md) | Guidelines to write Markdown files. Originally from [here](https://github.com/github/awesome-copilot/blob/main/instructions/markdown.instructions.md). Also as Claude rule [here[(./claude-rules/markdown-stules.md)|
| Azure DevOps Pipelines | [azure-devops.instruction.md](./instructions/azure-devops.instructions.md) | Best practices for Azure DevOps Pipeline YAML files. Originally from [here](https://github.com/github/awesome-copilot/blob/main/instructions/azure-devops-pipelines.instructions.md).|

### Custom prompts

Under the `prompts` folder, the below custom prompts can be found:

| Prompt Name | Prompt Definition | Purpose |
|-------------|-------------------|---------|

## :computer: MCP servers

**MCP servers** are a very valuable tool that will enhance the performance and accuracy of the AI agents when used. Some of the previous agents will leverage MCP servers to retrieve additional information or more up-to-date and accurate details on the treated topics, like software libraries, official documentation, recommended practices, etc.

For the MCP servers used with the custom agents defined in this repository, a reference to the corresponding setup can be found under the `mcp` folder. **This is done on a Windows environment using VS Code**. Nevertheless, it is recomended to inspect the official websites for those servers to get the latest update and a detailed explanation on how to configure them for the different environments.

> **IMPORTANT** MCP servers should be automatically started by the agents when needed. Nevertheless, ensure the MCP servers are running properly before prompting the agent if you want to use them!
