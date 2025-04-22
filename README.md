# Power BI Dashboard Automation Agent

## Overview

This AI agent automates the creation of simple Power BI dashboards using a Python-based system that interfaces with Power BI Desktop. It leverages the Claude-3-7-Sonnet model from Anthropic for intelligent tool usage, along with OpenCV for image processing, EasyOCR for text recognition, and PyAutoGUI for simulating mouse and keyboard interactions.

**Note**: This agent is in the pilot phase and serves as a proof-of-concept for automating Power BI dashboard creation. It can handle basic tasks, such as creating bar charts from CSV files, but may not perform reliably for complex requests. Always supervise the agent's actions to prevent unintended outcomes.

## Setup Instructions

1. **Anthropic API Key**:

   - Create an account at Anthropic Console.

   - Obtain an API key and set it as an environment variable:

     ```
     ANTHROPIC_API_KEY=your_api_key
     ```

## Technical Details

### Image Processing

The agent takes regular screenshots of the main monitor to assess its environment and determine the next action. To optimize costs and avoid exceeding token limits, it processes screenshots locally using:

- **EasyOCR**: Extracts text from screenshots.
- **OpenCV**: Performs template matching to identify icons.

This abstracted information (text and icon data) is sent to the Claude model, reducing token usage and improving processing speed. However, this approach is less accurate than the LLM's native image analysis. Future improvements may combine local processing with LLM image analysis for better performance, especially for complex dashboards.

### Limited Computer Interaction

Unlike advanced LLM computer usage capabilities (see Anthropic's Computer Use documentation), this agent has restricted control over mouse and keyboard actions to enhance safety. It is limited to:

- Mouse click and double-click actions.

These constraints, combined with local screenshot processing, provide better control and guardrails to minimize errors. Future versions may expand computer usage capabilities to support more complex dashboard creation.

### Available Tools

The agent has four tools:

1. Open the Power BI application.
2. Find and click specific items on the monitor.
3. Find and click specific icons on the monitor.
4. Perform OCR and template matching to identify text and icons.

For more details on Claude's tool use capabilities, refer to Anthropic's Tool Use Documentation.

## Precautions

- This agent is a proof-of-concept and may not handle all requests accurately.
- Always monitor the agent’s actions to avoid unintended consequences.
- Use caution when testing, as the agent interacts with your system via mouse and keyboard simulations.

## Future Improvements

- Enhance image processing by combining local techniques with LLM capabilities.
- Expand computer usage tools to support more complex dashboard creation while maintaining safety guardrails.