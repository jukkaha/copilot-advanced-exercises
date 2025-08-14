---
mode: 'agent'
tools: ['query']
description: 'Generate or update the ER diagram of the database using Mermaid syntax.'
---
Use the #query tool to get a description of the PostgreSQL database schema.
Then generate an Entity Relationship diagram based on the schema. Use Mermaid
syntax to create the diagram. Create the diagram in a file called ER.md.
Create the file if it doesn't exist yet or update the existing file.