https://web.stanford.edu/class/cs224n/slides_w25/cs224n-2025-lecture05-rnnlm.pdf
https://youtu.be/LHXXI4-IEns?si=2Sb03nQcP7jdWhSR

RNNs allow us to analyse context of any length and each new step will have context of all the previous steps. 
BUT
The far we go the less info we have from previous words. Vanishing gradient is a problems so it's difficult to update the weights in the beginning therefore the connections between words that are far from each other are almost impossible to learn. RNNs have bad short-term memory. LSTMs and GRUs where designed to solve this issue.
![Pasted image 20250325153809.png](80582ce826cae2bdb1bafe7ad5438a80.png)


![Pasted image 20250319151231.png](Pasted%20image%2020250319151231.png)
![Pasted image 20250325152605.png](c9ee10ccee4f407d462d6be4e41fba57.png)![Pasted image 20250325152647.png](f302e2ac06e66c2baf8c0c51188e287f.png)![Pasted image 20250325154028.png](afb4a868e15563a4fd9a2bf54c2c2d77.png)![Pasted image 20250325152733.png](46eb4ed63b331e03b4b1a79108db0dd6.png)![Pasted image 20250325152745.png](80e9069481e76a9e814de2ecab20f56c.png)![Pasted image 20250325152801.png](69b8cda60f8d0b6ef93995f81f2a0287.png)![Pasted image 20250325152823.png](347637804f41f6335c64f69cce8d2550.png)![Pasted image 20250325152910.png](89a42a448fdb9251331ba61cebf3750f.png)![Pasted image 20250325152937.png](fb2c111fa9ceed222fbca78833525e06.png)![Pasted image 20250325153247.png](eabbf64063d7d30f6c8cce9ae4293e45.png)![Pasted image 20250325153334.png](cbf416bf4a3602a13b06c933f94c4a62.png)![Pasted image 20250325153343.png](30ad1ab144681f386c8b7016bc02f2e7.png)![Pasted image 20250325153350.png](99ac48dc4f1e1b0df047943b96325060.png)
![Pasted image 20250325154506.png](46f2181f7c712b9b7d2b097d8d19b31d.png)![Pasted image 20250325154513.png](e15dcc6ddc3f1fd00f670e065ff09600.png)