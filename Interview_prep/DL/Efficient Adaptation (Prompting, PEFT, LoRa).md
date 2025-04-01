https://web.stanford.edu/class/cs224n/slides_w25/cs224n-2025-lecture11-adapatation.pdf
https://www.reddit.com/r/LocalLLaMA/comments/17mrd3y/seeking_clarification_on_lora_adapters_and_prefix/
https://www.reddit.com/r/MachineLearning/comments/13m78u6/d_an_eli5_explanation_for_lora_lowrank_adaptation/

Read in detail here: https://huggingface.co/blog/samuellimabraz/peft-methods
### 1. Prompting
Zero-shot learning emerged. 
GPT-2 beats SoTA on language modeling benchmarks with no task-specific fine-tuning by just creatively specifying the task.

Few-shot/in-context learning:
Specify a task by simply prepending examples of the task before your example.

Some tasks seem too hard for even large LMs to learn through prompting alone. Especially tasks involving richer, multi-step reasoning. So chain-of-thought prompting appeared, where we ask model to explain the reasoning while getting the answer. (Karpathy said that "model needs tokens to think")

Prompt-engineering arised with models jailbreaking etc. The downside of prompt-based learning is that you have to create a specific prompt every time the model makes a prediction and it is also performing worse than fine-tuning.

### 2. PEFT
Parameter efficient fine-tuning (PEFT)
In full finetuning we update all params. In PEFT we update only a small subset. SOTA models are overparatrametrized so PEFT matches performance of simple finetuning.

#### **Pruning:**
The networks are sparse so we can prune the weights that seems being near 0 during training.
A hypothesis is that dense, randomly-initialized models contain subnetworks (“winning tickets”) that— when trained in isolation—reach test accuracy comparable to the original network in a similar number of iterations.

#### **LoRA**:
The key in LoRA lies in this hypothesis: any fine tuning of a dense layer actually only adds a low rank weight matrix deltaW to the existing trained weight matrix W. It’s proved and validated in LoRA and previous studies, even if W has a rank of 12288, deltaW just need to have a rank of 1 or 2 to retain similar performance.

So the fine tuning is simplified to training deltaW, which has the same number of weights as the original weight W. But we can exploit the fact that deltaW a low rank matrix, which can be decomposed to to the multiplication of two low rank matrix A & B. If W is 12288x12288, the deltaW only need to have 12288x1 + 1x12288 weights, resulting in only 1/6144 weights need to be trained.

EIL5(explain me like i'm 5) version: Instead of retraining LLMs or adding new layers for new tasks, LoRA invented a way to train only a small delta with much fewer parameters, resulting in much faster training speed and lower ram requirement. The beauty is its weights can be simply added to the foundation model to have a fine tuned model for a different task.

Why it works is because it is discovered that some fine tuning tasks will only add a low rank deltaW to the existing pre-trained weights. It works for many tasks they’ve tested. But there’s no guarantee that it works for every tasks. In some extreme cases, the gain will diminish, if a model trained on one language is fine tuned for the other totally different language, e.g., fine tuning a model trained purely on English for Japanese will gain much less with LoRA. The ranks of LoRA might be so high that it’s cheaper to fine tune the entire network.

#### **Knowledge distillation:**
Knowledge distillation is when a large pre-trained model, often referred to as the teacher model, is used to transfer its knowledge to a smaller model, known as the student model.

The teacher model guides the student model by generating soft targets, which are probability distributions over the classes, instead of hard labels. The student model then learns to mimic the behavior of the teacher model by minimizing the difference between its predictions and the soft targets. This allows the student model to capture the knowledge of the teacher model while being more computationally efficient.


### 3. Comparing PEFT methods
![Pasted image 20250331172346.png](../../attachments/Pasted%20image%2020250331172346.png)
More here https://huggingface.co/blog/samuellimabraz/peft-methods





![Pasted image 20250331145523.png](../../attachments/Pasted%20image%2020250331145523.png)![Pasted image 20250331145531.png](../../attachments/Pasted%20image%2020250331145531.png)![Pasted image 20250331145545.png](../../attachments/Pasted%20image%2020250331145545.png)![Pasted image 20250331145551.png](../../attachments/Pasted%20image%2020250331145551.png)![Pasted image 20250331145556.png](../../attachments/Pasted%20image%2020250331145556.png)![Pasted image 20250331145605.png](../../attachments/Pasted%20image%2020250331145605.png)![Pasted image 20250331145614.png](../../attachments/Pasted%20image%2020250331145614.png)![Pasted image 20250331145621.png](../../attachments/Pasted%20image%2020250331145621.png)![Pasted image 20250331145633.png](../../attachments/Pasted%20image%2020250331145633.png)![Pasted image 20250331145645.png](../../attachments/Pasted%20image%2020250331145645.png)![Pasted image 20250331145655.png](../../attachments/Pasted%20image%2020250331145655.png)


![Pasted image 20250331152131.png](../../attachments/Pasted%20image%2020250331152131.png)![Pasted image 20250331152135.png](../../attachments/Pasted%20image%2020250331152135.png)


![Pasted image 20250331152807.png](../../attachments/Pasted%20image%2020250331152807.png)![Pasted image 20250331152812.png](../../attachments/Pasted%20image%2020250331152812.png)![Pasted image 20250331152821.png](../../attachments/Pasted%20image%2020250331152821.png)


![Pasted image 20250331153039.png](../../attachments/Pasted%20image%2020250331153039.png)![Pasted image 20250331153102.png](../../attachments/Pasted%20image%2020250331153102.png)![Pasted image 20250331153110.png](../../attachments/Pasted%20image%2020250331153110.png)![Pasted image 20250331153209.png](../../attachments/Pasted%20image%2020250331153209.png)![Pasted image 20250331153238.png](../../attachments/Pasted%20image%2020250331153238.png)