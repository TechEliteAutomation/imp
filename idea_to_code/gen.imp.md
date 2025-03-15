### Implementation Document Generator

---

#### Purpose:
The "Markdown Generator Agent" is designed to receive user input in the form of a textual query and then output a detailed markdown document. This document will contain an exhaustive and technically precise implementation outline based on the input query. The agent will integrate with the Gemini API, producing logically-structured content that can be used for documentation, project planning, or system architecture.

---

### High-Level Workflow:

1. **Receive User Input:**
   - Input type: Textual query (e.g., "job analyzer", "data processor")
   - Purpose: Generate a markdown document with a precise, technical outline based on the query.

2. **Gemini API Integration:**
   - Interface: The agent will make a request to the Gemini API for generating content.
   - Query Construction: The query to the Gemini API will be formulated with specific constraints on the format, including:
     - Strict logical structure
     - Minimal ambiguity
     - Precision and adherence to formal logic notation when applicable
   - Response Handling: 
     - Extract relevant, structured content from the Gemini API's response.
     - Filter out unnecessary or excessive explanations.

3. **Markdown Generation:**
   - Structure: The agent will format the Gemini API response into a markdown document, following the specified structure:
     - **Title**: Reflecting the input query (e.g., "Job Analyzer Implementation Outline")
     - **Introduction**: Concise overview of the query's technical requirements.
     - **Components**: Detailed breakdown of each system component, functionality, dependencies, and technologies.
     - **Implementation Phases**: Clear stages of development, including setup, execution, and optimization.
     - **Best Practices/Guidelines**: Include essential guidelines or considerations for each phase.
     - **Conclusion**: Wrap up with any necessary final thoughts or recommendations.

4. **Export to File:**
   - Output format: Markdown file (.md)
   - File Naming Convention: Based on the input query (e.g., `job_analyzer.md`)

---

### Components Breakdown:

1. **Input Parsing**:
   - Input format: A single text query, parsed and sanitized.
   - Example Input: "Job analyzer"

2. **Gemini API Response**:
   - Request URL: `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash-exp:generateContent`
   - Request Body: JSON object with the query, conversation history (if applicable), and response modifier.
   - Response Structure:
     - A structured response containing a "parts" array, which holds the desired content.
     - Example: The output content would strictly adhere to logical precision, with minimal explanation.

3. **Markdown Construction**:
   - **Header**:  
     - Title in H1 format (`# Job Analyzer Implementation Outline`)
     - Optional: Brief description of the query's technical background.
   - **Introduction**:  
     - Define the core objective of the query.
   - **Detailed Sections**:
     - **System Components**: Technical analysis of the system's parts, their interactions, and key considerations.
     - **Implementation Phases**: Clear breakdown of the development process.
     - **Technologies & Dependencies**: List of tools, libraries, and frameworks.
     - **Best Practices**: Operational guidelines.
   - **Footer**:  
     - Summary of the system’s purpose and integration considerations.

4. **Edge Cases & Error Handling**:
   - Missing API Key: Raise a `ValueError` and prompt the user to provide the key.
   - API Errors: Handle unexpected errors with detailed messages.
   - Input Validation: Ensure that inputs are sanitized and formatted correctly.

---

### File Export:

1. **Export Location**: Output the markdown file to a specified directory (e.g., `/output/job_analyzer.md`).
2. **Naming**: Use the query as the base file name (e.g., `job_analyzer.md`).

--- 

### Error Handling:
- **Missing API Key**: Ensure that the `GEMINI_API_KEY` is set in the environment.
- **API Response Errors**: Handle HTTP errors with informative messages.
- **Input Validation**: Reject non-textual inputs or malformed queries.

---

### Conclusion:

The "Markdown Generator Agent" utilizes the Gemini API to produce a structured, technically-precise markdown document based on user input, offering an efficient way to document and plan technical implementations. The generated markdown is highly detailed, aligned with formal logic, and can be adapted for various use cases such as project planning or system documentation.
