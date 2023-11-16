--- /Users/talesh/Desktop/OWASP/mine/1_0_vulns/LLM06_SensitiveInformationDisclosure.md
+++ /Users/talesh/Desktop/OWASP/mine/1_1_vulns/LLM06_SensitiveInformationDisclosure.md
@@ -1,20 +1,20 @@
-## Sensitive Information Disclosure
+## LLM06: Sensitive Information Disclosure
 
-**Description:**
+### Description
 
-LLM applications have the potential to reveal sensitive information, proprietary algorithms, or other confidential details through their output. This can result in unauthorized access to sensitive data, intellectual property, privacy violations, and other security breaches. It is important for consumers of LLM applications to be aware of how to safely interact with LLMs and identify the risks associated with unintentionally inputting sensitive data that it may be returned by the LLM in output elsewhere.
+LLM applications have the potential to reveal sensitive information, proprietary algorithms, or other confidential details through their output. This can result in unauthorized access to sensitive data, intellectual property, privacy violations, and other security breaches. It is important for consumers of LLM applications to be aware of how to safely interact with LLMs and identify the risks associated with unintentionally inputting sensitive data that may be subsequently returned by the LLM in output elsewhere.
 
-To mitigate this risk, LLM applications should perform adequate data sanitization to prevent user data from entering the training model data. LLM application owners should also have appropriate Terms of Use policies available to make consumers aware of how their data is processed and the ability to opt-out of having their data included in the training model.
+To mitigate this risk, LLM applications should perform adequate data sanitization to prevent user data from entering the training model data. LLM application owners should also have appropriate Terms of Use policies available to make consumers aware of how their data is processed and the ability to opt out of having their data included in the training model.
 
-The consumer-LLM application interaction forms a two-way trust boundary, where we cannot inherently trust the client->LLM input or the LLM->client output. It is important to note that this vulnerability assumes that certain pre-requisites are out of scope, such as threat modeling exercises, securing infrastructure, and adequate sandboxing. Adding restrictions within the system prompt around the types of data the LLM should return can provide some mitigation against sensitive information disclosure, but the unpredictable nature of LLMs means such restrictions may not always be honoured and could be circumvented via prompt injection or other vectors.
+The consumer-LLM application interaction forms a two-way trust boundary, where we cannot inherently trust the client->LLM input or the LLM->client output. It is important to note that this vulnerability assumes that certain prerequisites are out of scope, such as threat modeling exercises, securing infrastructure, and adequate sandboxing. Adding restrictions within the system prompt around the types of data the LLM should return can provide some mitigation against sensitive information disclosure, but the unpredictable nature of LLMs means such restrictions may not always be honored and could be circumvented via prompt injection or other vectors.
 
-**Common Examples of Vulnerability:**
+### Common Examples of Vulnerability
 
 1. Incomplete or improper filtering of sensitive information in the LLM’s responses.
 2. Overfitting or memorization of sensitive data in the LLM’s training process.
 3. Unintended disclosure of confidential information due to LLM misinterpretation, lack of data scrubbing methods or errors.
 
-**How to Prevent:**
+### Prevention and Mitigation Strategies
 
 1. Integrate adequate data sanitization and scrubbing techniques to prevent user data from entering the training model data.
 2. Implement robust input validation and sanitization methods to identify and filter out potential malicious inputs to prevent the model from being poisoned.
@@ -23,19 +23,17 @@
    2. Access to external data sources (orchestration of data at runtime) should be limited.
    3. Apply strict access control methods to external data sources and a rigorous approach to maintaining a secure supply chain.
 
-**Example Attack Scenarios:**
+### Example Attack Scenarios
 
 1. Unsuspecting legitimate user A is exposed to certain other user data via the LLM when interacting with the LLM application in a non-malicious manner.
+2. User A targets a well-crafted set of prompts to bypass input filters and sanitization from the LLM to cause it to reveal sensitive information (PII) about other users of the application.
+3. Personal data such as PII is leaked into the model via training data due to either negligence from the user themselves, or the LLM application. This case could increase the risk and probability of scenario 1 or 2 above.
 
-2. User A targets a well crafted set of prompts to bypass input filters and sanitization from the LLM to cause it to reveal sensitive information (PII) about other users of the application.
+### Reference Links
 
-3. Personal data such as PII is leaked into the model via training data due to either negligence from the user themselves, or the LLM application. This case could increase risk and probability of scenario 1 or 2 above.
-
-**Reference Links:**
-
-1. [AI data leak crisis: New tool prevents company secrets from being fed to ChatGPT](https://www.foxbusiness.com/politics/ai-data-leak-crisis-prevent-company-secrets-chatgpt) A blog explaining the risks associated to users unintentionally leaking sensitive data into LLM's and the consequences of when this information is fed into training data.
-2. [Lessons learned from ChatGPT’s Samsung leak](https://cybernews.com/security/chatgpt-samsung-leak-explained-lessons/) A write up on an incident caused due to an employee unintentionally leaking source code into an LLM's training data due to misuse and unawareness, leading to this being leaked across other use-case interactions with the LLM.
-3. [Cohere - Terms Of Use](https://cohere.com/terms-of-use) An example terms of use notice made available to users of an LLM to identify how data is processed.
-4. [A threat modeling example](https://aivillage.org/large%20language%20models/threat-modeling-llm/) for LLM applications to assess the understanding of a systems’ goals from a business objective, mapping out the components responsible for them and recursively identifying system and performance criteria down to the essence of the implementation. Thus, the exercise aims to pre-anticipate and assess vulnerabilities to remediate and|or reduce risk.
-5. [OWASP AI Security and Privacy Guide](https://owasp.org/www-project-ai-security-and-privacy-guide/) which is separate from this project.
-6. [Ensuring the Security of Large Language Models](https://www.experts-exchange.com/articles/38220/Ensuring-the-Security-of-Large-Language-Models-Strategies-and-Best-Practices.html): Strategies and best practices, including Homomorphic Encryption.+1. [AI data leak crisis: New tool prevents company secrets from being fed to ChatGPT](https://www.foxbusiness.com/politics/ai-data-leak-crisis-prevent-company-secrets-chatgpt): **Fox Business**
+2. [Lessons learned from ChatGPT’s Samsung leak](https://cybernews.com/security/chatgpt-samsung-leak-explained-lessons/): **Cybernews**
+3. [Cohere - Terms Of Use](https://cohere.com/terms-of-use) **Cohere**
+4. [A threat modeling example](https://aivillage.org/large%20language%20models/threat-modeling-llm/): **AI Village**
+5. [OWASP AI Security and Privacy Guide](https://owasp.org/www-project-ai-security-and-privacy-guide/): **OWASP AI Security & Privacy Guide**
+6. [Ensuring the Security of Large Language Models](https://www.experts-exchange.com/articles/38220/Ensuring-the-Security-of-Large-Language-Models-Strategies-and-Best-Practices.html): **Experts Exchange**
