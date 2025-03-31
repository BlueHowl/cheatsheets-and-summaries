# Summary of Inference Acceleration Techniques  

This summary combines your notes with relevant details from the provided document, excluding prompt engineering.  

## 1. Quantization  
Reducing the precision of model weights (e.g., `float32 → float16`, `int32 → int8/int4`). This reduces memory usage and speeds up computations, with a slight loss in precision.  

- **Post-training quantization (PTQ)**: Applying quantization after training to reduce model size and improve efficiency.  
- **Quantization-aware training (QAT)**: Training the model with quantization in mind to minimize accuracy loss.  
- **Mixed precision training**: Using both high-precision (float32) and low-precision (float16) computations to optimize performance.  

## 2. Distillation  
A large model (*teacher*) trains a smaller model (*student*) that remains efficient while being much faster.  

### Techniques:  
- **Data distillation**: Generating enhanced data for training.  
- **Knowledge distillation**: Transferring hidden representations to the student model.  
- **On-policy distillation**: Training the student based on the teacher’s decision-making process.  

## 3. Speculative Decoding  
A smaller and faster draft model predicts multiple future tokens, while the main model verifies these predictions in parallel. If the draft model is correct, its predictions are accepted, significantly speeding up decoding.  

## 4. Flash Attention  
Memory-optimized attention mechanism using techniques like sparsity and efficient computation to reduce the latency of transformer models.  

## 5. Prefix Caching  
Storing computations for frequently used input prefixes to avoid redundant calculations, speeding up repeated queries.  

## 6. Batching  
Grouping multiple requests into a single batch for optimized parallel execution, reducing memory access overhead and increasing throughput.  

## 7. Parallelization  
Splitting computations across multiple cores or GPUs to accelerate processing.  

- **Model parallelism**: Distributing the model across different computing units.  
- **Pipeline parallelism**: Executing different stages of inference in a sequential yet overlapping manner.  
- **Tensor parallelism**: Splitting matrix multiplications across devices.  

## 8. Other Optimizations  
- **Sparsity & Pruning**: Removing unnecessary weights to reduce computation and memory usage.  
- **Memory Efficient Training**: Optimizing memory storage to prevent bottlenecks.  
- **Low-Rank Adaptation (LoRA)**: Fine-tuning only select portions of a model to reduce computational cost.  
- **Kernel Fusion**: Combining multiple small operations into one to reduce memory transfers and improve efficiency.  
- **CUDA Graphs**: Optimizing GPU execution paths to avoid redundant computations.  

<br>

> **Note :**
> This document has been rewrote using AI \
> Made by Quentin Barthélemy (BlueHowl)