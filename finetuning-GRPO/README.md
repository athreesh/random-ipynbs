# GRPO Finetuning Notebooks

This directory contains notebooks for finetuning various LLMs using GRPO (Grounded Preference Optimization) to enhance their reasoning capabilities.

## VRAM Requirements

### Mistral-7B (`mistral7b_grpo_finetuning.ipynb`)
- **Minimum VRAM**: 12-16GB
- **Base model (4-bit)**: ~8GB VRAM
- **Training overhead**: ~4GB VRAM
- **Batch size impact**: ~1GB per batch size unit
- **Recommended GPU**: A100 (40GB) or similar
- **Alternative**: Multiple smaller GPUs with model parallelism
- **Memory optimization techniques used**:
  * 4-bit quantization
  * Gradient checkpointing
  * LoRA for parameter-efficient training

### Qwen-0.5B (`qwen_grpo_finetuning.ipynb`)
- **Minimum VRAM**: 4-6GB
- **Base model (4-bit)**: ~2GB VRAM
- **Training overhead**: ~2GB VRAM
- **Batch size impact**: ~0.5GB per batch size unit
- **Recommended GPU**: RTX 3060 12GB or similar
- **Memory optimization techniques used**:
  * 4-bit quantization
  * Gradient accumulation
  * LoRA adaptation

### Llama-2 1B (`llama_grpo_finetuning.ipynb`)
- **Minimum VRAM**: 6-8GB
- **Base model (4-bit)**: ~2.5GB VRAM
- **Training overhead**: ~2GB VRAM
- **Batch size impact**: ~0.75GB per batch size unit
- **Recommended GPU**: RTX 3070 8GB or similar
- **Memory optimization techniques used**:
  * 4-bit quantization
  * Gradient checkpointing
  * LoRA for efficient finetuning

### Unsloth GRPO (`unsloth_grpo_finetuning.ipynb`)
Configurable for different model sizes:
- **7B models**:
  * Minimum VRAM: 12-16GB
  * Recommended: A100 or similar
- **1-2B models**:
  * Minimum VRAM: 6-8GB
  * Recommended: RTX 3070 or better
- **<1B models**:
  * Minimum VRAM: 4-6GB
  * Recommended: RTX 3060 or similar
- **Memory optimization techniques used**:
  * Unsloth's optimized kernels
  * Flash Attention 2
  * Gradient checkpointing
  * Dynamic memory allocation

## Memory Optimization Tips

1. **Batch Size Adjustment**:
   - Start with small batch sizes
   - Use gradient accumulation for effective larger batches
   - Monitor GPU memory usage with `nvidia-smi`

2. **Model Loading**:
   - Use 4-bit quantization for all models
   - Enable gradient checkpointing
   - Use LoRA for parameter-efficient training

3. **Training Process**:
   - Clear GPU cache between training runs
   - Monitor memory usage during training
   - Adjust sequence lengths based on available memory

4. **Multi-GPU Setup**:
   - Use model parallelism for larger models
   - Distribute training across multiple GPUs if available
   - Enable efficient memory sharing

## Running on Brev.dev

These notebooks are optimized for Brev.dev GPUs. Choose your instance based on the model size:
- For Mistral-7B: A100 or equivalent
- For Qwen-0.5B: RTX 3060 or better
- For Llama-2 1B: RTX 3070 or better
- For Unsloth: Depends on chosen model size