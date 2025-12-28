Prompt-to-create-OPAL-122825


You will be analyzing code or technical specifications and generating comprehensive instructions that OPAL Google can use to create an application. OPAL needs detailed, structured technical specifications that cover all aspects of the application including architecture, UI/UX, data models, components, and services.

First, here is an optional description of what the application should accomplish:
<app_description>
{{APP_DESCRIPTION}}
</app_description>

Now, here is the code or technical specification you need to analyze:
<code_or_spec>
{{CODE_OR_SPEC}}
</code_or_spec>

Your task is to generate a comprehensive technical specification document that OPAL Google can use to reconstruct the application. Follow these guidelines:

**Analysis Process:**
Before writing the specification, analyze the provided code/spec in a <scratchpad> to identify:
- The core purpose and functionality of the application
- Technology stack and frameworks used
- Key components and their relationships
- Data models and types
- UI/UX patterns and design system
- External APIs or services integrated
- Security and configuration requirements

**Required Specification Sections:**

Your output must include these sections (adapt based on what's relevant to the provided code):

1. **Executive Summary**: Brief overview of the application's purpose, key features, and target use case

2. **Technology Stack**: List all frameworks, libraries, APIs, models, and tools used. Include version numbers when available.

3. **Data Models**: Define all interfaces, types, enums, and data structures. Use code blocks with proper syntax.

4. **UI/UX & Theming**: Describe the design system, color palette, layout structure, typography, and any special visual patterns.

5. **Component Specifications**: For each major component, document:
   - Responsibility/Purpose
   - State management
   - Key features and functionality
   - Props/inputs
   - Implementation details
   - User interactions

6. **Service Layer**: Document all service functions, API integrations, and utility functions including:
   - Function signatures
   - Parameters and return types
   - Purpose and behavior
   - Error handling

7. **Security & Configuration**: Cover API keys, permissions, environment variables, and data handling practices.

8. **Dependencies**: List all external packages with version numbers.

**Formatting Requirements:**
- Use clear hierarchical numbering (1, 1.1, 1.2, etc.)
- Include code blocks with language specification (e.g., ```typescript)
- Use bullet points for lists
- Bold important terms and section headers
- Be specific about implementation details (don't just say "handles user input" - explain HOW)

**Level of Detail:**
The specification should be detailed enough that:
- A developer unfamiliar with the project could rebuild it
- An AI system like OPAL could generate the complete application
- All business logic and user flows are clearly documented
- Edge cases and error handling are addressed

**Handling Incomplete Information:**
If the provided code/spec is missing critical information:
- Note what's missing in your specification
- Make reasonable assumptions based on common patterns
- Mark assumptions clearly with "Assumed:" or "Inferred:"

Write your complete technical specification inside <specification> tags. Ensure it is well-structured, comprehensive, and ready for OPAL to use for application generation.
