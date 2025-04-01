https://web.stanford.edu/class/cs224n/slides_w25/cs224n-2025-lecture10-instruction-tunining-rlhf.pdf

Pretrained LM just tries to continue your prompt as if it was a single text. It is not made to assist. You can finetune to your specific task with small number of data. But finetuning can be done on large Q&A datasets to train generic assistants. Data was human-made. 

There are 2 problems with this:
- tasks like open-ended creative generation have no right answer
- language modeling penalizes all token-level mistakes equally, but some errors are worse than others

To optimize results to human preferences we ask users to do pairwise comparisons of 2 (or more) responses. To cut the cost of human-in-the-loop we train a separate model to model the preferences of a human.

So we got InstructGPT & ChatGPT.

Human preferences are unreliable (human can prefer a response that sounds more reliable but actually provides incorrect information). Chatbots are rewarded to produce responses that seem authoritative and helpful, regardless of truth. This can result in making up facts + hallucinations.
Model of human preferences is even worse.

So we just simplify everything, remove RL and do Direct Preference Optimization (DPO).
DPO directly optimizes the model to generate responses that align with preferred human choices. It does this by maximizing the probability of preferred responses while minimizing the probability of dispreferred ones.

![Pasted image 20250331131457.png](attachments/fd6c874dcbe4afff5d3f1ab0c9b11593.png)![Pasted image 20250331131700.png](attachments/91fc93362553b415d650cbea18f73f80.png)![Pasted image 20250331131713.png](attachments/0b1a026cc930ce551d6c75cb7f36d6ee.png)![Pasted image 20250331131746.png](attachments/155fa303f1e27cca229e116a39c8bcca.png)![Pasted image 20250331131753.png](attachments/558f28ed2cc760f5394aceeacdf2d0fb.png)![Pasted image 20250331140810.png](attachments/3470df47bc2d067eabb3d1212e66dd77.png)![Pasted image 20250331140755.png](attachments/cc10df22a8d69ff9b0d6e8e8619012c4.png)![Pasted image 20250331140833.png](attachments/e019117bea74f8de7c162ad27e0b6ec6.png)![Pasted image 20250331140845.png](attachments/524cfdff794ca035557991225aabd2b5.png)![Pasted image 20250331140913.png](attachments/16a0f58dfd31a7a194171cef025398d3.png)![Pasted image 20250331140940.png](attachments/f06c1323999cacd48c0cd3d6fcc846ef.png)![Pasted image 20250331140950.png](attachments/e16e1db061d062ff25c3478ff5f3f95e.png)![Pasted image 20250331141008.png](attachments/83a68909dc0c59c33f446a4f4d4bac9e.png)![Pasted image 20250331141027.png](attachments/9e459063f504b60a16d9e7a600e54e5e.png)![Pasted image 20250331141033.png](attachments/2345637e830a0d20cd1fae7d9dd708b9.png)![Pasted image 20250331141051.png](attachments/acf6876c0341cc157e59f7e78b7902f6.png)03311![Pasted image 20250331144012.png](attachments/8f41186c1c0fbade59fdd80cf66200b0.png)![Pasted image 20250331144019.png](attachments/334bbde292a8768fe81d70e7a574f105.png)![Pasted image 20250331144256.png](attachments/a9916e99489e96ae3d1bfb9dd130e630.png)![Pasted image 20250331144313.png](attachments/eba88cde63b8fef1cef24bcb86cd3fcd.png)