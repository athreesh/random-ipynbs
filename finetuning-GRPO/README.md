# GRPO Finetuning Notebooks

This directory contains notebooks for finetuning various LLMs using GRPO (Grounded Preference Optimization) to enhance their reasoning capabilities.

## Brev.dev GPU Compatibility

Available GPU types on Brev.dev:
- NVIDIA T4 (16GB VRAM)
- NVIDIA A10G (24GB VRAM)
- NVIDIA L4 (24GB VRAM)
- NVIDIA L40S (48GB VRAM)
- NVIDIA A100 (40/80GB VRAM)
- NVIDIA H100 (80GB VRAM)

## Model VRAM Requirements

### Mistral-7B (`mistral7b_grpo_finetuning.ipynb`)
- **Minimum VRAM**: 12-16GB
- **Base model (4-bit)**: ~8GB VRAM
- **Training overhead**: ~4GB VRAM
- **Batch size impact**: ~1GB per batch size unit
- **Compatible GPUs**:
  * ✅ T4 (limited batch size)
  * ✅ A10G (recommended)
  * ✅ L4 (recommended)
  * ✅ L40S (ideal)
  * ✅ A100 (ideal)
  * ✅ H100 (ideal)
- **Memory optimization techniques**:
  * 4-bit quantization
  * Gradient checkpointing
  * LoRA for parameter-efficient training

### Qwen-0.5B (`qwen_grpo_finetuning.ipynb`)
- **Minimum VRAM**: 4-6GB
- **Base model (4-bit)**: ~2GB VRAM
- **Training overhead**: ~2GB VRAM
- **Batch size impact**: ~0.5GB per batch size unit
- **Compatible GPUs**:
  * ✅ T4 (ideal)
  * ✅ A10G (ideal)
  * ✅ L4 (ideal)
  * ✅ L40S (ideal)
  * ✅ A100 (ideal)
  * ✅ H100 (ideal)
- **Memory optimization techniques**:
  * 4-bit quantization
  * Gradient accumulation
  * LoRA adaptation

### Llama-2 1B (`llama_grpo_finetuning.ipynb`)
- **Minimum VRAM**: 6-8GB
- **Base model (4-bit)**: ~2.5GB VRAM
- **Training overhead**: ~2GB VRAM
- **Batch size impact**: ~0.75GB per batch size unit
- **Compatible GPUs**:
  * ✅ T4 (good)
  * ✅ A10G (ideal)
  * ✅ L4 (ideal)
  * ✅ L40S (ideal)
  * ✅ A100 (ideal)
  * ✅ H100 (ideal)
- **Memory optimization techniques**:
  * 4-bit quantization
  * Gradient checkpointing
  * LoRA for efficient finetuning

### Unsloth GRPO (`unsloth_grpo_finetuning.ipynb`)
Configurable for different model sizes:
- **7B models**:
  * Minimum VRAM: 12-16GB
  * Compatible GPUs: T4 (limited), A10G+, L4+, L40S, A100, H100
- **1-2B models**:
  * Minimum VRAM: 6-8GB
  * Compatible GPUs: All Brev.dev GPUs
- **<1B models**:
  * Minimum VRAM: 4-6GB
  * Compatible GPUs: All Brev.dev GPUs
- **Memory optimization techniques**:
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

These notebooks are optimized for Brev.dev GPUs. Here are the recommended instance choices:

### Best GPU Choice by Model
1. **Mistral-7B**:
   - 🥇 Best: A100 (40/80GB) or H100
   - 🥈 Good: A10G or L4 (24GB)
   - 🥉 Workable: T4 (with limited batch size)

2. **Qwen-0.5B**:
   - 🥇 Best: T4 (most cost-effective)
   - ✅ Any Brev.dev GPU will work well

3. **Llama-2 1B**:
   - 🥇 Best: T4 or L4
   - ✅ Any Brev.dev GPU will work well

4. **Unsloth GRPO**:
   - For 7B models: A100/H100 recommended
   - For 1-2B models: T4/L4 recommended
   - For <1B models: Any GPU works well

### Cost-Optimization Tips
- Use T4 for smaller models (≤1B parameters)
- A10G/L4 good balance for medium models
- A100/H100 for large models or when speed is critical
- Consider gradient accumulation on smaller GPUs