# Copilot Hackathon - Advances Track
Exercises for the GitHub Copilot Hackathon - Advanced Track

## Part 1 exercises
Individually done exercises of part 1 of the one day workshop.

### Create a new project
* **Purpose:** Setup a new project to work with for the following exercises
* **Steps:**
    1. Decide a topic for your application. If you need inspiratio, [see here](EXERCISE_APP_IDEAS.md).
    2. Use programming languages and tech stack you're familiar with to work on your project. Initialize the project using npm, dotnet, create-react-app, mvn archtypes etc. to initialize a new project. 
    2. Initialize a local git repository for the project.
    3. Create a .gitignore file for the project. This is important since Copilot automatically [ignores files listed in .gitignore from the workspace index](https://code.visualstudio.com/docs/copilot/reference/workspace-context#_what-content-is-included-in-the-workspace-index)

### Copilot Settings
* **Purpose:** Familiearize yourself with the configration options for Copilot, confifgure Copilto according to your needs, enable custom instructions.
* **Steps:**
    1. Open VS Code settings
    2. Type Copilot in the search field
    3. Go through the following settings and understand their purpose.
        - GitHub › Copilot: Enable
        - GitHub › Copilot › Chat › Agent: Auto Fix
        - GitHub › Copilot › Next Edit Suggestions: Enabled
        - Chat › Agent: Enabled
    4. Make sure the following setting is enabled
        - GitHub › Copilot › Chat › Code Generation: Use Instruction Files
    5. See the following settings and click on "edit in settings.json" Think about what kind of additions would be useful in your technological environment.
        - GitHub › Copilot › Chat › Review Selection: Instructions
        - GitHub › Copilot › Chat › Code Generation: Instructions

### Custom instructions
* **Purpose:** Create a custom instructions file for the project to help Copilot understand your coding conventions.
* **Steps:**
    1. Create a folder .github at the root of your project
    2. Create a file called copilot-instructions.md in the new folder. This is your project specific *custom instructions file* that should be added to the version control and shared among the team members.
    3. Ask Copilot to generate contents for the file using the Ask mode (select "Ask" in the chat window). To get better results, explain Copilot what kind of project you are planning to build.
    4. See Copilot's suggestions and adjust them according to your preferences. Add e.g. the following:
        - High-level description of the purpose of the application
        - Key technologies and frameworks
        - Project strucure
        - Variable, function etc. naming convention
        - (Patterns)
    5. Close custom instructions file. Ask something about your project from Copilot and make sure that the custom-instructions.md is added automatically to every promopt you make.

### Implement features using Agent mode
* **Purpose:** Use agent mode to implement a couple of use cases in your application.
* **Steps:**
    1. Decide the first UI elements, API endpoints or other features you want to implement. Use Copilot's Agent mode to implement the features.
    2. Try out different models while working with agent mode:
        * Claude 3.7 Sonnet
        * Claude 3.7 Sonnet Thinking
        * GPT-4.1
        * o3/04 mini
    3. Pay attention to the proactive and interactive nature of the Agent mode:
        * Agent mode uses the search index to search relevant content from the workspace
        * If it needs to use a tool, it asks for the permission from the user
        * It notices if it produces compilation errrors and proposes fixes to them automatically
        * 
    2. 

### Debugging
* **Purpose:**  If/when you run into problems while developng your application, use Copilot's features to debug your code and undertand error messagrs and stack traces.
    1. #problems: shows the current errors and warnings in your workspace
    2. #terminalLastCommand: adds last command and its output to the context. Great way to quickly understand failed terminal commands.
    3. #terminalSelection: select text from terminal to add it into the prompt context. Great way to debug e.g. an error in development server output or to target the prompt to a specific line of the output of a failed terminal command.

### Prompt files
* **Purpose:** Use prompt files to not repeat yourself when writing prompts for specific kinds tasks and workflows.
* **Steps:**
    1. In VS Code, use cmbinatin Shift+Command/Control+P to open the command palette.
    2. Type Chat: new prompt file
    3. Select prompts
    4. Give a name to the prompt file
    5. Think about what kind of prompt files would be useful at your work and create a prompt file according to yur needs.
    6. Test your prompt file in the chat by typing / and the name of your prompt file.
    7. See the documentation for instructions on how to use e.g. user input in prompt files.
    8. Example prompt file:
        ```md
        ---
        mode: 'agent'
        tools: ['githubRepo', 'codebase']
        description: 'Generate a new React form component'
        ---
        Your goal is to generate a new React form component based on the templates in #githubRepo contoso/react-templates.

        Ask for the form name and fields if not provided.

        Requirements for the form:
        * Use form design system components: [design-system/Form.md](../docs/design-system/Form.md)
        * Use `react-hook-form` for form state management:
        * Always define TypeScript types for your form data
        * Prefer *uncontrolled* components using register
        * Use `defaultValues` to prevent unnecessary rerenders
        * Use `yup` for validation:
        * Create reusable validation schemas in separate files
        * Use TypeScript types to ensure type safety
        * Customize UX-friendly validation rules
        ```

### Model Context Protocol recap and Postgres MCP server installation

* **Purpose:** Understand how MCP servers work, how they can be run locally, familiarize with the selection of MCP servers.
* **MCP Recap:**
    * MCP (Model Context Protocol) servers provide a standardized way to interact with various tools, services, and systems.
    * MCP server is run locally on the developer's workstation e.g. as a docker container (remote servers also possible suign HTTP)
    * Developers can initialize and manage MCP servers directly from their IDE or command-line tools.
    * MCP allows seamless integration of external tools and data sourvces with Copilot. They support multiple types of integrations, including databases, APIs, and cloud services.
    * MCP servers enable real-time exploration, execution, and interaction with connected resources.
    * A wide variety of MCP servers are aldready available. **Caution must be taken when running MCP servers** found on the web because of potentially insecure or malicious implementations
* **Steps:**
    1. VS Code => Shift+Control+P (Win) or Shift+CMD+P (Mac)
    2. \> MCP: Add server...
    3. Docker image => mcp/postgres
    4. "Install mcp/postgres from mcp?" => select "Allow"
    5. Postgres URL: postgresql://postgres:postgres@host.docker.internal:5432/library_app
    6. "Enter Server ID" => "Postgres"
    7. "Choose where to save the configuraton" => select "Workspace settings"
    8. mcp.json should be opened by the IDE
    9. Start the server by clicking on the play button in mcp.json
    10. The tools provided by the MCP server should be now available in the tools menu in the Agent mode prompt box (make sure Agent mode is selected, then click on the wrench icon). You can enable or disable tools by ticking/unticking the boxes.


### Testing the PostgreSQL MCP server
* **Purpose:** Try out and test the PostgreSQL MPC server agains a database
* **Prerequisities:**
    * Docker installed.
* **Steps:**
    * cd mcp-exercise
    * docker compose up db
    * Copilot Chat => Agent Mode Selected
    * Make sure from the tools menu that the Postgres MCP Server and its tool "query" are enabled
    * Prompt: "#query what's the schema of my database?"
    * Prompt "Show all book loans"
    * Prompt: "Show all users who have at least one loan"
    * Think about how the information provided by the MCP server could be utilised in prompts? How could it help build complete, AI poweered development flows?

### Using PostgreSQL MCP Server together with prompt files
* **Purpose:** Use a prompt file to automate the generation of ER-diagram based on the database schema.
* **Steps:**
    1. Create a new prompt file (see the instructions above)
    2. Copy-paste this into the file:
    ```md
        ---
        mode: 'agent'
        tools: ['query']
        description: 'Generate or update the ER diagram of the database using Mermaid syntax.'
        ---
        Use #query tool to get description of the PostgreSQL database schema.
        Then generate an Entity Relationship diagram based on the schema. Use Mermaid
        syntax to create the diagram. Create the diagram in file called ER.md.
        Create the file if it doesn't exist yet or update the existing file.
    ```
    3. Test the prompt file by typing /er in the agent mode. Refine the prompt if Copilot is not able to fulfil the purpose of the prompt.
    4. If you want to see the resulted Mermaid diagram, push the file to a GitHub repository and open the file.

### Other MCP Servers
* **Purpose:** Try out and test the PostgreSQL MPC server agains a database
* **Steps:**
    1. Browse to http://mcp.so
    2. Take a look at some of the other MCP servers available. Try to find ones that you could use to integrate Copilot with your development tools. Some suggestions:
        * [Slack](https://mcp.so/server/slack/modelcontextprotocol)
        * [GitHub](https://mcp.so/server/github/modelcontextprotocol)
        * [GitLab](https://mcp.so/server/gitlab/modelcontextprotocol)
        * [Playwright](https://mcp.so/server/playwright-mcp/microsoft)
        * [Perplexity](https://mcp.so/server/perplexity/ppl-ai)


### PostgreSQL MCP Trouble shooting
If you are having trouble connecting to your MCP server, try the following configurations:

Mac
```json
{
    "servers": {
        "postgres": {
            "command": "docker",
            "args": [
                "run",
                "-i",
                "--rm",
                "mcp/postgres",
                "postgresql://postgres:postgres@host.docker.internal:5432/library_app"
            ]
        }
    }
}
```

Linux
```json
{
    "servers": {
        "postgres": {
            "command": "docker",
            "args": [
                "run", 
                "-i", 
                "--rm", 
                "mcp/postgres", 
                "postgresql://postgres:postgres@172.17.0.1:5432/taptodine"]
            }
    }
}
```
#### No docker?
If you don't have Docker installed and can't install it, you can use npm to run the server.

```json
{
    "servers": {
        "postgres": {
            "command": "npx",
            "args": [
                "-y",
                "@modelcontextprotocol/server-postgres",
                "postgresql://localhost/mydb"
            ]
        }
    }
}
```
To run the database locally without Docker, you can either use Podman to run the docker-compose.yml file
or install the database on your workstation using PostgreSQL installers. You can also use any test database
yiu are currently using for work. 