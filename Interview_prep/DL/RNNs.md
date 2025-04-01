https://web.stanford.edu/class/cs224n/slides_w25/cs224n-2025-lecture05-rnnlm.pdf
https://youtu.be/LHXXI4-IEns?si=2Sb03nQcP7jdWhSR

RNNs allow us to analyse context of any length and each new step will have context of all the previous steps. 
BUT
The far we go the less info we have from previous words. Vanishing gradient is a problems so it's difficult to update the weights in the beginning therefore the connections between words that are far from each other are almost impossible to learn. RNNs have bad short-term memory. LSTMs and GRUs where designed to solve this issue.
![[Pasted image 20250325153809.png]]


![[Pasted image 20250319151231.png]]
![[Pasted image 20250325152605.png]]![[Pasted image 20250325152647.png]]![[Pasted image 20250325154028.png]]![[Pasted image 20250325152733.png]]![[Pasted image 20250325152745.png]]![[Pasted image 20250325152801.png]]![[Pasted image 20250325152823.png]]![[Pasted image 20250325152910.png]]![[Pasted image 20250325152937.png]]![[Pasted image 20250325153247.png]]![[Pasted image 20250325153334.png]]![[Pasted image 20250325153343.png]]![[Pasted image 20250325153350.png]]
![[Pasted image 20250325154506.png]]![[Pasted image 20250325154513.png]]