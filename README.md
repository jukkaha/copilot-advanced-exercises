# Copilot Hackathon - Advances Track
Exercises for the GitHub Copilot Hackathon - Advanced Track

## Part 1 exercises
Individually done exercises of part 1 of the one day workshop.

### Create a new project
* **Purpose:** Setup a new project to work with for the following exercises
* **Steps:**
    1. Create a new empty projeft using a language and frameworks you're familiar with. The topic can be e.g. a REST API, web UI, or a command line tool.
    2. Initialize a local git repository for the project
    3. 

### Copilot Settings
* **Purpose:** Familiearize yourself with the configration options for Copilot, confifgure Copilto according to your needs, enable custom instructions.
* **Steps:**
    1. Open VS Code settings
    2. Type Copilot in the search field
    3. Go through the following settings and understand their purpose.
        - GitHub › Copilot: Enable
        - GitHub › Copilot › Chat › Agent: Auto Fix
        - GitHub › Copilot › Next Edit Suggestions: Enabled
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
    1. Feature implementatin. Pay attention to the proactive and interactive nature of the Agent mode. Model suggestion.
    2. /tests and /testframework
    3. Edits to refactor the tests with the code
    4. Use #terminalLastCommand and #terminalSelection in debgging
    

### Prompt files
* **Purpose:** Create prompt files to help in running repetative prompts
* **Steps:**

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
    5. Postgres URL: postgresql://postgres:changethis@host.docker.internal:5432/app
    6. "Enter Server ID" => "Postgres"
    7. "Choose where to save the configuraton" => select "Workspace settings"
    8. mcp.json should be opened by the IDE
    9. Start the server by clicking on the play button in mcp.json
    10. The tools provided by the MCP server should be now available in the tools menu in the Agent mode prompt box (make sure Agent mode is selected, then click on the wrench icon). You can enable or disable tools by ticking/unticking the boxes.


### Testing the PostgreSQL MCP server
* **Purpose:** Try out and test the PostgreSQL MPC server agains a database
* **Steps:**
    * ToDo: instructions for running a PostgreSQL DB using Docker Compose (contains DB initiation scripts and test data)
    * Try out the tool e.g. with the following prompt: "What is the schema of my database #query"
    * Think about how the information provided by the MCP server could be utilised in prompts? How could it help build complete, AI poweered development flows?

### Other MCP Servers
* **Purpose:** Try out and test the PostgreSQL MPC server agains a database
* **Steps:**
    * Browse to http://mcp.so
    * ToDo: find MCP servers that could help you in development

