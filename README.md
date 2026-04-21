
# Improving AI Chatbot Response Accuracy with LangChain Tooling

## Overview
This project explores the performance of Large Language Models (LLMs) and their capabilities in solving complex problems. The goal of this project was to demonstrate how tool integration can improve the accuracy and reliability of AI chatbot responses.

---
![Standalone LLM vs agent performance](https://raw.githubusercontent.com/bchafe/improving-chatbot-accuracy/refs/heads/main/images/llm-agent-performance.png)

## Objectives
- Deploy and run local LLMs inside Google Colab
- Improve LLM response accuracy using external tools
- Evaluate performance of standalone LLMs vs tool-enabled agents
- Demonstrate practical applications of LLM orchestration

## Key Concepts
Traditional LLMs:
 - Generate responses based on training data
 - Can produce incorrect or outdated answers

 Tool-augmented LLMs:
 - Dynamically call external tools (e.g., calculators, APIs)
 - Produce more accurate and verifiable outputs

 This project demonstrates how combining LLM reasoning with tools leads to more reliable results.
 
## Example
### "What is 1184758 multiplied by 8375948? Respond with the answer only."
**Without tools:**

> 9723380939572  ❌

**With tools:**

> 9923471400584 ✔

 ## Tools & Technologies
 - Python
 - LangChain
 - Ollama
 - Pandas
 - Matplotlib
 - Seaborn

 ## Methodology
 ### 1. Standalone LLM
 - Configured a basic LLM using Ollama
 - Tested the LLM's ability to:
    - Sum a set of numbers
    - Multiply two large numbers
    - Count the number of letters in a word

### 2. Tool Integration
- Integrated custom tools using LangChain
- Enabled the agent to:
	- Perform accurate calculations
	-  Count letter occurrences in a word

### 3. Prompt Design
- Designed prompts to test model's ability to solve complex problems
- Standarized prompts across all experiment groups to control for variability
- Instructed the model to only provide the final answer, simplifying parsing and verification

## Model Configuration
- Model: [Qwen 3.5 9B](https://ollama.com/library/qwen3.5:9b) (Ollama)
- Temperature: 0.5 (balancing consistency and flexibility in responses) 
- Max Tokens: 4096

## Experimental Setup
- Experiment groups:
	1. Standalone LLM (reasoning mode off)
	2. Standalone LLM (reasoning mode on)
	3. LangChain agent with tooling & reasoning enabled

- Wrote functions to:
	- Execute repeated trials across test cases
	- Validate response accuracy
	- Display performance metrics (response time, token usage)
	- Store results in structured Pandas DataFrames for analysis

## Evaluation
- Compared responses:
	- Agent with tooling vs standalone LLM
- Assessed improvements in:
	- Accuracy
	- Consistency
	- Response time
	- Token usage

## Results
### Experiment 1: Multiplying Large Numbers
| Experiment Group           | Accuracy | Avg Response Time | Avg Token Usage |
|----------------------------|----------|-------------------|-----------------|
| Standalone (Reasoning OFF) | 0%       | 0.98 seconds      | 14              |
| Standalone (Reasoning ON)  | 0%       | 170.08 seconds    | 4096            |
| Agent with Tooling         | 100%     | 11.51 seconds     | 730             |

### Experiment 2: Counting Letters in a Word
| Experiment Group           | Accuracy | Avg Response Time | Avg Token Usage |
|----------------------------|----------|-------------------|-----------------|
| Standalone (Reasoning OFF) | 0%       | 0.43 seconds      | 2               |
| Standalone (Reasoning ON)  | 40%      | 140.48 seconds    | 3405            |
| Agent with Tooling         | 100%     | 45.31 seconds     | 1086            |


### Summary of Results
- Tool-augmented LLM consistently produced **more accurate and reliable responses**
- Significant improvement in response time and token usage for complex problems
- Reduced hallucinations compared to standalone LLM responses


## Limitations
- Increased system complexity compared to standalone LLMs
- Tool usage introduces computational overhead for simple queries
- Large toolsets may negatively impact performance

## Future Improvements
- Integrate API-based tooling (e.g., Wolfram Alpha) to expand problem-solving capabilities
- Implement regex-based parsing to handle variations in response formatting
- Evaluate performance using standardized AI benchmarks for more systematic comparison

## Key Takeaways
This project highlights the importance of combining LLMs with external tools to build more reliable AI chatbots. It demonstrates how orchestration frameworks like LangChain can bridge the gap between ease of use and accurate solutions to complex problems.

## How to Run
### Google Colab (Recommended)
1. [Open this notebook](https://colab.research.google.com/drive/18728gyZcs7p4vDUWDDNaZSOrQjpkMd8j?usp=sharing) in Google Colab
2. Run each code cell in order, or click 'Run All' to automatically run all cells

**PLEASE NOTE:** Running all cells in this notebook may take **up to an hour** to complete. If you plan on running this notebook in Colab, I highly recommend you switch to a T4 GPU runtime. You can do so by clicking `Runtime` -> `Change runtime type` in the menu bar at the top of the page.

### Running the notebook locally
Running this notebook locally is not currently supported, but I can't stop you from trying. You'll probably have the best results on a Debian based Linux distro. You might need to install Ollama manually. You'll also need curl installed on your system, or you could modify the `start_ollama_server()` function to omit the curl call.


