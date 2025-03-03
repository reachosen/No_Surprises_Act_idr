# No_Surprises_Act_idr
No Surprises Act - Independent Dispute Resolution Support
# IDR Support System with Groq AI

This Python script implements an Independent Dispute Resolution (IDR) support system for healthcare billing disputes under the No Surprises Act. It leverages the Groq API for generative AI to analyze claim data and provide insights for IDR consideration.

## Features

-   **Claim Analysis:** Analyzes healthcare claims based on description, billed amount, Qualified Payment Amount (QPA), provider experience, and emergency status.
-   **Supporting Data Integration:** Integrates supporting data such as median rates, historical outcomes, and external trends to provide context.
-   **Groq AI Integration:** Utilizes the Groq API with the `llama3-70b-8192` model to generate detailed, impartial analyses.
-   **CPT Code Extraction:** Extracts CPT codes from claim descriptions using regular expressions.
-   **Test Cases:** Includes predefined test cases to validate the system's functionality.
-   **Reporting:** Generates formatted reports with analysis results and expected insights.

## Prerequisites

-   Python 3.6+
-   `requests` library: `pip install requests`
-   A Groq API key (set as environment variable `GROQ_API_KEY`).

## Setup

1.  **Install Dependencies:**

    ```bash
    pip install requests
    ```

2.  **Set Groq API Key:**

    -   Obtain your Groq API key from the Groq platform.
    -   Set the API key as an environment variable named `GROQ_API_KEY`.

    -   On Linux/macOS:
        ```bash
        export GROQ_API_KEY="your_groq_api_key"
        ```
    -   On Windows:
        ```bash
        set GROQ_API_KEY=your_groq_api_key
        ```
    ```

## Code Structure

-   `Claim` and `SupportingData` dataclasses: Define data structures for claim and supporting data.
-   `GroqAI` class: Handles communication with the Groq API for claim analysis.
-   `IDRSupportSystem` class: Manages the IDR process, including CPT code extraction, data retrieval, and report generation.
-   `test_cases` dictionary: Contains predefined test cases for system validation.
-   `main()` function: Executes the test cases and prints the generated reports.

## Usage

1.  **Define Claim Data:** Prepare claim data in a dictionary format, similar to the `test_cases` structure.
2.  **Create an `IDRSupportSystem` Instance:** Initialize the IDR support system.
3.  **Process Claims:** Call the `generate_report()` method with the claim data to generate an analysis report.

## Example

```python
from your_script_name import IDRSupportSystem

claim_data = {
    "description": "Out-of-network ER visit, CPT 99283, billed $1,500 due to emergency complexity and patient stabilization.",
    "billed_amount": 1500.0,
    "qpa": 1000.0,
    "provider_experience": 12,
    "is_emergency": True,
    "expected_insight": "Justified higher payment due to emergency context and expertise."
}

idr_system = IDRSupportSystem()
report = idr_system.generate_report(claim_data)
print(report)
