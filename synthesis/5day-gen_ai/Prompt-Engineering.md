# Prompt Engineering Guide

## Prompting Techniques

### **1. General/Zero-shot Prompting**
- Direct instruction/question without examples.
- Based on pre-trained knowledge.
- Works well for factual responses but lacks specificity.

### **2. One/Few-shot Prompting**
- Provides high-quality examples to guide output.
- Includes edge cases to refine responses.
- Ideal for structured outputs (e.g., JSON format expectations).

### **3. System Contextual and Role Prompting**
- Defines assistant’s role, response style, and constraints.
- Example: *Act as a Senior Data Engineer when answering.*
- Helps align responses to domain-specific requirements.

### **4. Stepback Prompting**
- Asks a broader question first to build context before refining the query.
- Improves model comprehension and output relevance.

### **5. Chain-of-Thought (CoT) Prompting**
- Guides the model through a step-by-step reasoning process.
- Increases transparency in how responses are generated.
- *Self-consistency:* Generates multiple responses and selects the best.
- Useful for mathematical reasoning and logical tasks.

### **6. Tree of Thoughts (ToT)**
- Explores multiple possible reasoning paths instead of a single one.
- Increases problem-solving capabilities compared to CoT.
- Useful for complex decision-making and planning.

### **7. ReAct (Reason & Act)**
- Combines reasoning with external tools (APIs, search engines, code execution, etc.).
- Example: *Generates code, tests it, and refines it iteratively.*
- Can interact dynamically with external knowledge sources.

### **8. Automatic Prompt Engineering (AP)**
- Asks the model to generate multiple prompts for a task.
- Evaluates prompt performance for best results.
- Automates optimization of prompt wording for maximum efficiency.

### **9. Code Prompting**
- Enhances code generation, debugging, and explanation.
- Useful for translating and commenting code.
- Speeds up development but requires validation of outputs.

### **10. Multimodal Prompting**
- Includes images, videos, or audio as input alongside text.
- Expands capabilities beyond text-based tasks.

---
## Best Practices

- Prefer **instructions over constraints**.
- Be **clear and concise** using strong keywords.
- Use **JSON repair libraries** to fix structured output issues.
- Specify **expected output format/schema** (e.g., JSON, XML).
- Test prompts iteratively to refine effectiveness.
- Provide feedback loops for continuous improvement.

---
## Sampling Control

### **Token Selection Process**
1. **Top-K Filtering:** Considers the top *K* most probable next tokens.
2. **Top-P (Nucleus) Sampling:** Selects from the most probable tokens based on cumulative probability.
3. **Temperature:**
   - Low = Deterministic & precise (e.g., 0.1)
   - High = More creative but less predictable (e.g., 0.9)

### **Recommended Configurations**
- **Balanced:** Creativity + Coherence
  - `Temperature: 0.2`, `Top-P: 0.95`, `Top-K: 30`
- **Highly Creative:**
  - `Temperature: 0.9`, `Top-P: 0.99`, `Top-K: 40`
- **Deterministic:**
  - `Temperature: 0.1`, `Top-P: 0.9`, `Top-K: 20`

### **Repetition Loop Bug**
- Occurs at very high or very low temperatures.
- Can result in repeated phrases or infinite loops.
- Solutions:
  - Adjust temperature.
  - Introduce **penalty terms** for repeated phrases.
  - Use **stop sequences** to prevent infinite loops.
  - Monitor token patterns for early detection of looping behavior.

<br>

> **Note :**
> This document has been rewrote using AI \
> Made by Quentin Barthélemy (BlueHowl)