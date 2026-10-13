FeedbackIQ — AI Analysis Specification

1. Objective

Convert unstructured customer feedback into consistent, structured insights that product managers can review and use for further investigation.

2. Input

The AI receives a collection of feedback statements.

Example:

"The payment failed but money was deducted."

3. Required Output

For each feedback statement, return:

- feedback_id
- category
- sentiment
- severity
- pain_point
- recommended_action
- supporting_evidence

4. Allowed Categories

- Performance
- Usability
- Payments
- Product Discovery
- Customer Support
- Other

Use Other when the feedback does not fit the available categories.

5. Sentiment Labels

- Positive
- Neutral
- Negative
- Mixed

6. Severity Labels

- Critical: Potential financial loss, serious transaction failure, or another issue requiring urgent investigation.
- High: Major disruption to an important user task.
- Medium: Noticeable friction with a possible workaround.
- Low: Minor inconvenience or positive feedback.

Severity is an initial assessment for investigation, not a confirmed measure of business impact.

7. Analysis Rules

1. Classify the issue based on the meaning of the feedback, not isolated keywords.
2. Do not invent customer details or events.
3. Keep the pain point concise and specific.
4. Recommendations must relate to the reported issue.
5. Supporting evidence must quote or accurately reference the supplied feedback.
6. If the feedback is ambiguous, indicate uncertainty instead of inventing an explanation.
7. Do not treat AI-generated recommendations as verified product decisions.

8. Example

Input

"The payment failed but money was deducted."

Expected Output

{
"feedback_id": "F002",
"category": "Payments",
"sentiment": "Negative",
"severity": "Critical",
"pain_point": "Payment failure with possible deduction",
"recommended_action": "Investigate transaction status reconciliation and customer communication",
"supporting_evidence": "The feedback reports a failed payment and a deduction"
}

9. Evaluation

Compare AI classifications with the manually assigned synthetic benchmark labels.

Measure:

- Category accuracy
- Sentiment accuracy
- Severity accuracy
- Recommendation usefulness through manual review
- Invalid or incomplete AI response rate

Document errors and limitations. Do not claim accuracy or impact before testing.

10. Product and Safety Constraints

- Use synthetic feedback during development.
- Keep API keys on the server side.
- Limit request size and frequency.
- Handle malformed responses and API failures.
- Provide sample results without requiring live AI calls.
- Do not expose personal or confidential information.
