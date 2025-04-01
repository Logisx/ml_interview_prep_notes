https://web.stanford.edu/class/cs224n/slides_w25/cs224n-2025-lecture06-fancy-rnn.pdf

Bidirectionality is not suitable for Language Modelling as you don't have the end of the context - you are trying to predict it. But otherwise it should be used in most cases.

![Pasted image 20250325154900.png](attachments/e44bd68cefc61b4612a1a32bcaad6b92.png)![Pasted image 20250325154911.png](attachments/cef9b10ef48dd86c183bef3f4cf3479a.png)![Pasted image 20250325154937.png](attachments/c087a45e984f3b71ed0cc1fed43176ea.png)03251![Pasted image 20250325155027.png](attachments/a1a5bcdb5fd0a224b701a5960eb1d80b.png)![Pasted image 20250325155035.png](attachments/310ece0b4b3706c14631ed8ae76d9917.png)