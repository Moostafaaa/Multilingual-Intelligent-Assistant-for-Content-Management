# Multilingual-Intelligent-Assistant-for-Content-Management
Key Optimizations Explained
Device Mapping: Using device=0 automatically moves the model to the NVIDIA GPU, significantly speeding up inference compared to CPU processing.

Model Selection: I used DistilBERT and DistilBART. These are "student" models that retain ~95% of the performance of their larger counterparts (BERT/BART) while being much faster and lighter on VRAM.

Max New Tokens: Instead of using max_length, which includes the prompt, max_new_tokens ensures you get a consistent amount of generated text regardless of how long your input prompt is.

Pipeline Re-use: By wrapping these in a class, we load the heavy model weights into memory only once, rather than re-loading them for every request.

How these tasks connect
The output of one stage serves as the input for the next, creating a linear "Chain of Thought" for the AI:

Generation creates the raw knowledge base.

Summarization extracts the core "thesis."

Translation makes that thesis globally accessible.

QA allows for deep-dive interaction with the original raw data.
