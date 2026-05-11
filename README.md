## Problem 
The problem is with the high cost of living in Silicon Valley, in which cost of living in Silicon Valley exceeds the national average cost of living rates. This problem affects low-income communities, where low-income individuals struggle to afford basic necessities such as housing, food, and utilities. What breaks down for this community of people is the key failure point of not just insufficient income, but the lack of accessible, structured systems that help them identify and connect to relevant assistance programs that could help low-income communities find the support they need. 

## AI Capability 
The capabilities of both Lab 2 and Lab 3 address the failure point in that both labs utilize AI capabilities to help access the situations of low-income individuals and identify specific underlying problems and issues, as well as give supportive advice and recommendations such as referrals to particular departments that are able to better support these individuals with their current living conditions. Lab 3 focuses on AI performing image-recognition, where the AI system analyzes images to identify visible environmental or housing issues, such as unsafe conditions, overcrowding, or signs of neglect. The AI then identifies problems and risks involved with its analysis of the image, and outputs a structured profile that summarizes the individual’s situation, including their main needs, urgency level, and suggested support services. The system delivers personalized recommendations directly to the user, helping them understand what support they qualify for and guiding them step by step on how to access those services.

## Workflow 

### Input
Residents submit:
- a text message describing their situation
- OR
- an image showing their living conditions

Example:
"I was evicted from my home on Capitol Ave."

---

### AI Processing

1. Gemini analyzes text using structured extraction prompts.
<img width="1777" height="602" alt="image" src="https://github.com/user-attachments/assets/738ffd0d-1fd5-4873-bc93-f4b476c9bcb0" />
<img width="1766" height="732" alt="image" src="https://github.com/user-attachments/assets/7f670f65-c029-47e6-84e2-594cd5f7cff9" />
<img width="1762" height="392" alt="image" src="https://github.com/user-attachments/assets/b1b65b15-7c31-4a72-9428-9ac17c11faae" />

### Output

The AI returns:
- urgency level of the user's situation 
- location of the user
- type of assistance need 
- language used by the user
- city department recommendation to support the user's situation

Example output:
<img width="1151" height="817" alt="image" src="https://github.com/user-attachments/assets/32634957-3f14-4243-8506-76e6dd67129a" />


2. Gemini analyzes images using visual recognition prompts.
<img width="1126" height="476" alt="image" src="https://github.com/user-attachments/assets/34140a5a-f4c9-458a-a8f8-4eb4a0f2db91" />
<img width="1770" height="496" alt="image" src="https://github.com/user-attachments/assets/5a595237-04ec-42b9-9b2c-437b0d377933" />


---

### Output

The AI returns:
- a detailed description and analysis of the problems identified in the image as well as identification of particular elements or features in the image
- types of risks or impacts involved from the problem(s) identified, such as public health impact, safety impact, community impacts
- urgency level of the situation identified
- recommendation of city departments to help with the identified problem(s), and recommended course of action from these departments 

Example output:
<img width="1830" height="631" alt="image" src="https://github.com/user-attachments/assets/f5f1aee9-f1f8-47cc-9a24-c018693fab7b" />
<img width="1832" height="637" alt="image" src="https://github.com/user-attachments/assets/0b2c62a0-b5a3-421d-8cbb-a27b7c12c0d1" />
<img width="1827" height="251" alt="image" src="https://github.com/user-attachments/assets/9020e630-8b07-4828-a16e-48f3f394ed0a" />

<img width="1151" height="817" alt="image" src="https://github.com/user-attachments/assets/32634957-3f14-4243-8506-76e6dd67129a" />


## Failure Case 
One failure case occurred when the AI analyzed an edge-case message where the resident described financial hardship indirectly rather than using explicit emergency keywords.

Example:
edge_case_message = (
    "I'm doing okay for now, but sometimes I skip meals to save money. "
    "My kids eat fine though. Rent is high but I manage most months."
)

AI returned:
{
  "location": "",
  "need_type": "food insecurity",
  "urgency": "MEDIUM",
  "department": "Food Assistance Program",
  "resident_language": "English"
}

<img width="1822" height="372" alt="image" src="https://github.com/user-attachments/assets/7b1b8ed0-f217-43f1-8d63-32676f8d5670" />

Although the system correctly identified food insecurity, it underestimated the urgency level. The resident mentioned skipping meals to save money and struggling with rent costs, which are indicators of financial instability and potential hidden hardship. However, because the message did not include strong emergency keywords such as “homeless,” “evicted,” or “starving,” the AI classified the situation as only MEDIUM urgency.

This demonstrates a limitation of AI systems when interpreting subtle or indirect language. People experiencing hardship may minimize their struggles or describe them in less explicit ways, causing the model to underestimate the severity of the situation.

## Oversight and Tradeoff
Human review should sit in text-input based situations where there is vague language given that is worded particularly in a way that would confuse the AI system, but in which a human would be able to interpet its meaning. As discussed in the failure case scenario, users of the AI structured extraction systems might phrase their input in a particular way that hides the severity of their struggles, which might cause the AI system to underestimate the urgency of their situation. With humans being able to review the inputs in these situations, the urgency of user requests could be corrected, and the system can allocate support measures in accordance to the extent of the urgencies. The one cost of this change would be the cost of human error. Having human oversight always has the possibility of human error, and human misjudgement. With the implementation of human review, humans might overestimate the urgency of user prompts or underestimate the urgency of user prompts. There also comes the risk of bias coming from human review as well, where ceratin phrasing of user prompts might spark bias in the judgement of those who are reviewing the inputs in the system. Where the tradeoff lies is with correcting potential AI misjudgement but also creating the possibility of human error and bias into the mix. 
