# **1. Structure**  
## **1.1 Simulated Enviorment**  
I'm planning to create a simulated map in Unity. In order to align with the real world, creating more objects to enrich the world is required.  
## **1.2 The design logic for Persona(Characters)**  
How to make the charaters more like human beings is an important task in this research. In the past, we'll have to predefine the features(e.g., a dict) of each characters, and the features
can only be changed according to the script.  

Unfortunately, dynamically adding new key into the features is impossible at this stage. However, I introduced  **GPT4_generate_persona** to 
generate the characters automatically, which introduce the first uncertainty into this research.  
## **1.3 How to make two Characters to have a conversation**
I introduce **persona_to_persona_chat** method which allows us to simulate a conversation between two characters. Compare with the original research, now two characters would answer algining
with their backgrounds(features dict)  

**Example:**  
1. Alex rejected to lend money to Lea since he doesn't have enough money as well.
2. Lea invited Alex to a church  since they're all Christians.

Here I use Langchain's conversation extension, which allows us to save and reuse this conversation for further use(e.g., summarizing for diary)

## **1.4 Retrieve information from the conversation**  
In order to get up-to-date features, updating features dynamically is required. However, Tracking the features' changes is very costly. I planned to update the features only when a conversation
or an event occured.  

**Pipeline:**  
1. Summarize the conversation by calling **summarize_after_chat**, which is a GPT-based model generating a summarize with tag(e.g., <wealthAfter></wealthAfter>)
2. Retrieve the tag from the summary and update the features.

## **1.5 Diary system**  
Diary is a key feature in this research. 
1. **events:** Record what just happened.
2. **to_do_list:** Record what should do next.

I expect what happened(events) would impact the reaction between two characters. On top of that, characters should decide what to do next basing
on the to-do list...or probably not? Even real human beings cannot follow it www 


