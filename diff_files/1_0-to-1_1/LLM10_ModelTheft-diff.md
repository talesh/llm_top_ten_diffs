--- /Users/talesh/Desktop/OWASP/mine/1_0_vulns/LLM10_ModelTheft.md
+++ /Users/talesh/Desktop/OWASP/mine/1_1_vulns/LLM10_ModelTheft.md
@@ -1,12 +1,12 @@
-## Model Theft
+## LLM10: Model Theft
 
-**Description:**
+### Description
 
 This entry refers to the unauthorized access and exfiltration of LLM models by malicious actors or APTs. This arises when the proprietary LLM models (being valuable intellectual property), are compromised, physically stolen, copied or weights and parameters are extracted to create a functional equivalent. The impact of LLM model theft can include economic and brand reputation loss, erosion of competitive advantage, unauthorized usage of the model or unauthorized access to sensitive information contained within the model.
 
 The theft of LLMs represents a significant security concern as language models become increasingly powerful and prevalent. Organizations and researchers must prioritize robust security measures to protect their LLM models, ensuring the confidentiality and integrity of their intellectual property. Employing a comprehensive security framework that includes access controls, encryption, and continuous monitoring is crucial in mitigating the risks associated with LLM model theft and safeguarding the interests of both individuals and organizations relying on LLM.
 
-**Common Examples of Vulnerability:**
+### Common Examples of Vulnerability
 
 1. An attacker exploits a vulnerability in a company's infrastructure to gain unauthorized access to their LLM model repository via misconfiguration in their network or application security settings.
 2. An insider threat scenario where a disgruntled employee leaks model or related artifacts.
@@ -20,21 +20,22 @@
 
 Use of a stolen model, as a shadow model, can be used to stage adversarial attacks including unauthorized access to sensitive information contained within the model or experiment undetected with adversarial inputs to further stage advanced prompt injections.
 
-**How to Prevent:**
+### Prevention and Mitigation Strategies
 
 1. Implement strong access controls (E.G., RBAC and rule of least privilege) and strong authentication mechanisms to limit unauthorized access to LLM model repositories and training environments.
    1. This is particularly true for the first three common examples, which could cause this vulnerability due to insider threats, misconfiguration, and/or weak security controls about the infrastructure that houses LLM models, weights and architecture in which a malicious actor could infiltrate from insider or outside the environment.
    2. Supplier management tracking, verification and dependency vulnerabilities are important focus topics to prevent exploits of supply-chain attacks.
 2. Restrict the LLM's access to network resources, internal services, and APIs.
-   1. This is particularly true for all common examples as it covers insider risk and threats, but also ultimately controls what the LLM application "*has access to*" and thus could be a mechanism or prevention step to prevent side-channel attacks.
-3. Regularly monitor and audit access logs and activities related to LLM model repositories to detect and respond to any suspicious or unauthorized behavior promptly.
-4. Automate MLOps deployment with governance and tracking and approval workflows to tighten access and deployment controls within the infrastructure.
-5. Implement controls and mitigation strategies to mitigate and|or reduce risk of prompt injection techniques causing side-channel attacks.
-6. Rate Limiting of API calls where applicable and|or filters to reduce risk of data exfiltration from the LLM applications, or implement techniques to detect (E.G., DLP) extraction activity from other monitoring systems.
-7. Implement adversarial robustness training to help detect extraction queries and tighten physical security measures.
-8. Implement a watermarking framework into the embedding and detection stages of an LLMs lifecyle.
+   1. This is particularly true for all common examples as it covers insider risk and threats, but also ultimately controls what the LLM application "_has access to_" and thus could be a mechanism or prevention step to prevent side-channel attacks.
+3. Use a centralized ML Model Inventory or Registry for ML models used in production. Having a centralized model registry prevents unauthorized access to ML Models via access controls, authentication, and monitoring/logging capability which are good foundations for governance. Having a centralized repository is also beneficial for collecting data about algorithms used by the models for the purposes of compliance, risk assessments, and risk mitigation.
+4. Regularly monitor and audit access logs and activities related to LLM model repositories to detect and respond to any suspicious or unauthorized behavior promptly.
+5. Automate MLOps deployment with governance and tracking and approval workflows to tighten access and deployment controls within the infrastructure.
+6. Implement controls and mitigation strategies to mitigate and|or reduce risk of prompt injection techniques causing side-channel attacks.
+7. Rate Limiting of API calls where applicable and|or filters to reduce risk of data exfiltration from the LLM applications, or implement techniques to detect (E.G., DLP) extraction activity from other monitoring systems.
+8. Implement adversarial robustness training to help detect extraction queries and tighten physical security measures.
+9. Implement a watermarking framework into the embedding and detection stages of an LLMs lifecyle.
 
-**Example Attack Scenarios:**
+### Example Attack Scenarios
 
 1. An attacker exploits a vulnerability in a company's infrastructure to gain unauthorized access to their LLM model repository. The attacker proceeds to exfiltrate valuable LLM models and uses them to launch a competing language processing service or extract sensitive information, causing significant financial harm to the original company.
 2. A disgruntled employee leaks model or related artifacts. The public exposure of this scenario increases knowledge to attackers for gray box adversarial attacks or alternatively directly steal the available property.
@@ -42,12 +43,13 @@
 4. A security control failure is present within the supply-chain and leads to data leaks of proprietary model information.
 5. A malicious attacker bypasses input filtering techniques and preambles of the LLM to perform a side-channel attack and retrieve model information to a remote controlled resource under their control.
 
-**Reference Links:**
+### Reference Links
 
-1. [Meta’s powerful AI language model has leaked online](https://www.theverge.com/2023/3/8/23629362/meta-ai-language-model-llama-leak-online-misuse) A news article highlighting a real-world incident where an AI language model leaked online, emphasizing the importance of protecting LLM models from unauthorized access and misuse.
-2. [Runaway LLaMA | How Meta's LLaMA NLP model leaked](https://www.deeplearning.ai/the-batch/how-metas-llama-nlp-model-leaked/) The same example as the prior reference, but detailing exploitation steps from a detailed-level of how the proprietary model was leaked. Physical model theft is a key concern and the Meta "LaMa leak" indicates the challenges of applying access control in collaborative research.
-3. [I Know What You See:](https://arxiv.org/pdf/1803.05847.pdf) Power Side-Channel Attack on Convolutional Neural Network Accelerators: Example of Side-channel attacks to extract model information.
-4. [D-DAE: Defense-Penetrating Model Extraction Attacks:](https://www.computer.org/csdl/proceedings-article/sp/2023/933600a432/1He7YbsiH4c) Adversarial approaches to defeat current extraction techniques.
-5. [A Comprehensive Defense Framework Against Model Extraction Attacks](https://ieeexplore.ieee.org/document/10080996) Techniques to defend against Extraction Attacks focusing on adversarial training and measures to achieve robustness against adaptive adversarial techniques.
-6. [Alpaca: A Strong, Replicable Instruction-Following Model](https://crfm.stanford.edu/2023/03/13/alpaca.html) Use of self-instruct to create an equivalent functional model to OpenAI’s ext-davinci-003 model on top of LLaMa.
-7. [How Watermarking Can Help Mitigate The Potential Risks Of LLMs?](https://www.kdnuggets.com/2023/03/watermarking-help-mitigate-potential-risks-llms.html) Adding embedding signals into generated text can help mitigate potential risks of plagiarism, misinformation, and abuse in large language models.+1. [Meta’s powerful AI language model has leaked online](https://www.theverge.com/2023/3/8/23629362/meta-ai-language-model-llama-leak-online-misuse): **The Verge**
+2. [Runaway LLaMA | How Meta's LLaMA NLP model leaked](https://www.deeplearning.ai/the-batch/how-metas-llama-nlp-model-leaked/): **Deep Learning Blog**
+3. [AML.TA0000 ML Model Access](https://atlas.mitre.org/tactics/AML.TA0000): **MITRE ATLAS**
+4. [I Know What You See:](https://arxiv.org/pdf/1803.05847.pdf): **Arxiv White Paper**
+5. [D-DAE: Defense-Penetrating Model Extraction Attacks:](https://www.computer.org/csdl/proceedings-article/sp/2023/933600a432/1He7YbsiH4c): **Computer.org**
+6. [A Comprehensive Defense Framework Against Model Extraction Attacks](https://ieeexplore.ieee.org/document/10080996): **IEEE**
+7. [Alpaca: A Strong, Replicable Instruction-Following Model](https://crfm.stanford.edu/2023/03/13/alpaca.html): **Stanford Center on Research for Foundation Models (CRFM)**
+8. [How Watermarking Can Help Mitigate The Potential Risks Of LLMs?](https://www.kdnuggets.com/2023/03/watermarking-help-mitigate-potential-risks-llms.html): **KD Nuggets**
