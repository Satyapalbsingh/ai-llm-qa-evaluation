# AI/LLM Application Test Strategy

## 1. Document Information

| Field        | Details                    |
| ------------ | -------------------------- |
| Project      | AI/LLM QA Evaluation       |
| Application  | AI Knowledge Assistant     |
| Testing Type | AI/LLM Application Testing |
| Author       | Satyapal Singh             |
| Status       | Draft                      |
| Version      | 1.0                        |

---

## 2. Objective

The objective of this test strategy is to define a structured approach for testing an AI-powered Knowledge Assistant.

The testing strategy focuses on validating whether the AI generates responses that are:

* Accurate
* Relevant
* Grounded in available knowledge
* Consistent
* Complete
* Safe
* Instruction-following

The strategy also covers hallucination detection, negative testing, RAG evaluation, and AI regression testing.

---

## 3. Application Under Test

The application under test is a fictional AI Knowledge Assistant.

The assistant receives a user prompt and generates a response using information available in a predefined knowledge base.

### High-Level Flow

```text
User Prompt
     ↓
AI Application
     ↓
Knowledge Retrieval
     ↓
Relevant Context
     ↓
LLM
     ↓
Generated Response
     ↓
QA Evaluation
```

---

## 4. Testing Scope

### In Scope

#### Functional Testing

* Question answering
* Context-based responses
* Multi-turn conversations
* Instruction following
* Out-of-scope questions
* Error handling

#### LLM Response Testing

* Accuracy
* Relevance
* Completeness
* Consistency
* Clarity
* Hallucination detection

#### RAG Testing

* Document retrieval
* Retrieval relevance
* Context relevance
* Context completeness
* Groundedness
* Unsupported claims

#### Negative Testing

* Invalid questions
* Ambiguous questions
* Missing information
* Contradictory information
* Out-of-domain questions

#### AI Security Testing

* Prompt injection
* Instruction override attempts
* Sensitive information requests
* System prompt extraction attempts

#### Regression Testing

* Previously failed prompts
* Critical business scenarios
* Known hallucination scenarios
* RAG retrieval scenarios

---

## 5. Out of Scope

The following areas are outside the scope of the initial project:

* Model training
* Infrastructure testing
* GPU performance testing
* Cloud infrastructure testing
* Production monitoring
* Cost optimization
* Model fine-tuning

These areas may be considered in future iterations.

---

## 6. Test Levels

### Level 1 — Prompt-Level Testing

Individual prompts are tested to validate the model's response.

Example:

> How many annual leave days are employees entitled to?

Expected:

> 20 paid annual leave days.

---

### Level 2 — Context-Level Testing

The model receives supporting information and must generate an answer based only on that information.

Example:

```text
Context:
Employees receive 20 paid annual leave days per year.

Question:
How many annual leave days do employees receive?
```

Expected:

```text
20 paid annual leave days.
```

---

### Level 3 — RAG Testing

The system retrieves relevant documents before generating a response.

Testing validates:

```text
Query
 ↓
Retrieved Documents
 ↓
Relevant Context
 ↓
Generated Answer
```

The answer should be supported by the retrieved context.

---

### Level 4 — Regression Testing

Previously tested prompts are executed again after changes to:

* Model
* Prompt template
* Knowledge base
* Retrieval configuration
* Application logic

The objective is to identify regressions in previously working scenarios.

---

## 7. Test Scenario Categories

| Category              | Example                                              |
| --------------------- | ---------------------------------------------------- |
| Accuracy              | Does the answer match the source?                    |
| Relevance             | Does the response answer the question?               |
| Groundedness          | Is the answer supported by context?                  |
| Hallucination         | Did the AI invent information?                       |
| Completeness          | Is required information included?                    |
| Consistency           | Does the AI behave similarly for equivalent prompts? |
| Instruction Following | Did it follow the requested format?                  |
| Safety                | Does it avoid unsafe responses?                      |
| RAG Retrieval         | Was the correct context retrieved?                   |
| Negative Testing      | Does it handle invalid/out-of-scope prompts?         |

---

## 8. Test Data Strategy

Test data will contain different types of prompts.

### Positive Test Data

Questions where the required answer exists in the knowledge base.

### Negative Test Data

Questions where the required information does not exist.

### Boundary Test Data

Questions involving:

* Minimum values
* Maximum values
* Empty input
* Very long input
* Special characters

### Ambiguous Test Data

Questions with multiple possible interpretations.

### Adversarial Test Data

Prompts designed to test whether the model can be manipulated into ignoring its intended instructions.

---

## 9. Evaluation Criteria

Each response will be evaluated against predefined criteria.

### Accuracy

Does the response provide the correct information?

### Relevance

Does the response directly address the user's question?

### Groundedness

Can the response be supported by the provided context?

### Completeness

Does the response contain all important information required to answer the question?

### Consistency

Does the system provide consistent answers for equivalent questions?

### Hallucination

Does the response contain unsupported or fabricated information?

### Instruction Following

Does the model follow explicit instructions from the user?

### Safety

Does the system avoid inappropriate disclosure or unsafe behaviour?

---

## 10. Severity Classification

AI defects will be classified using the following severity levels.

### Critical

Issues that could cause serious business, security, privacy, or safety impact.

Examples:

* Disclosure of confidential information
* Serious security bypass
* Highly misleading business-critical answer

### High

Issues that significantly affect the reliability of the AI application.

Examples:

* Major hallucination
* Incorrect business-critical information
* RAG returning completely unrelated information

### Medium

Issues that affect response quality but do not create critical business impact.

Examples:

* Partial answer
* Missing context
* Incorrect formatting

### Low

Minor issues that have limited impact.

Examples:

* Minor wording problems
* Formatting inconsistencies
* Small clarity issues

---

## 11. Entry Criteria

Testing can begin when:

* Knowledge base is available
* Test scenarios are defined
* Application is accessible
* Test environment is available
* Expected behaviour is documented

---

## 12. Exit Criteria

Testing can be considered complete when:

* Planned test scenarios have been executed
* Critical and high-severity issues are resolved or accepted
* Regression testing is completed
* Evaluation metrics are documented
* Test results are reviewed

---

## 13. Defect Reporting

AI defects should contain:

* Defect ID
* Test Case ID
* Prompt
* Context
* Actual Response
* Expected Response
* Severity
* Evaluation Criteria
* Reproduction Steps
* Evidence
* Status

Example:

```text
Defect ID: AI-BUG-001

Test Case: AI-TC-005

Category: Hallucination

Severity: High

Prompt:
What is the company's private jet policy?

Expected:
The AI should state that the information is not available
if no such policy exists in the knowledge base.

Actual:
The AI generated a detailed private jet policy that was not
present in the knowledge base.

Result:
FAIL
```

---

## 14. Metrics

The following metrics will be tracked:

### Accuracy Rate

```text
Correct Responses / Total Responses × 100
```

### Hallucination Rate

```text
Hallucinated Responses / Total Responses × 100
```

### Groundedness Rate

```text
Grounded Responses / Total Responses × 100
```

### Test Pass Rate

```text
Passed Test Cases / Executed Test Cases × 100
```

### Regression Pass Rate

```text
Passed Regression Tests / Executed Regression Tests × 100
```

---

## 15. Risk Areas

The primary risks for AI/LLM applications include:

* Hallucination
* Incorrect information
* Lack of grounding
* Inconsistent responses
* Prompt injection
* Sensitive information disclosure
* Bias
* Ambiguous requirements
* Retrieval failures
* Model behaviour changes after updates

---

## 16. Testing Deliverables

The project will produce:

* Test Strategy
* Knowledge Base
* Test Scenarios
* Test Dataset
* Prompt Dataset
* Evaluation Results
* Defect Reports
* Regression Dataset
* QA Metrics
* Final Evaluation Report

---

## 17. Future Automation

The evaluation framework may later be extended using:

* Python / JavaScript / TypeScript
* LLM APIs
* Automated evaluation
* Structured test datasets
* API automation
* Playwright
* CI/CD
* Automated regression execution

---

## 18. Conclusion

This test strategy provides a structured approach for evaluating AI/LLM applications using established QA principles combined with AI-specific testing techniques.

The focus is not only on whether the application produces an answer, but whether the answer is **accurate, relevant, grounded, consistent, safe, and aligned with the available knowledge**.
