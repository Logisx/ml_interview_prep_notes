!!!!!!!!!!!!!!!!!!!!!!!!!! https://www.youtube.com/watch?v=i94OvYb6noo&ab_channel=AndrejKarpathy
https://cs231n.github.io/
!!!!!!!!!!!!!!!https://www.youtube.com/watch?v=gYpoJMlgyXA&t=1254s&ab_channel=AndrejKarpathy
!!! https://www.youtube.com/watch?v=yCC09vCHzF8&ab_channel=AndrejKarpathy
https://karpathy.medium.com/yes-you-should-understand-backprop-e2f06eab496b

https://www.youtube.com/watch?v=HnliVHU2g9U&list=PLoROMvodv4rOaMFbaqxPDoLWjDaRAdP9D&index=4&ab_channel=StanfordOnline


 ==if you’re using== ==**sigmoids**== ==or== ==**tanh**== ==non-linearities in your network and you understand backpropagation you should always be nervous about making sure that the initialization doesn’t cause them to be fully saturated.==

If you understand backpropagation and your network has ReLUs, you’re always nervous about dead ReLUs. These are neurons that never turn on for any example in your entire training set, and will remain permanently dead. Neurons can also die during training, usually as a symptom of aggressive learning rates.