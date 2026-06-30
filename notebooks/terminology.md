# Terminology

## Business

- CRM = Customer Relationship Management. Exist in 4 variants:
  - Operational = Sales force automation. Eliminate manual data entry and scale sales and customer support
  - Analytical = Data mining, sales forcasting, predictive analysis. Understand customer behaviour deeply and tailor marketing and sales based on this
  - Collaborative = Interaction management consolidation (see customer interactions across different channels), bridge gaps between different platforms of internal communication
  - Strategic = Customer segmentation, targeted loyalty programs, long-term customer journey mapping. Important for businesses who rely heaviliy on repeat customers, customer lifetime value and rewarding brand loyalty

## Technical

- LoRA: Low Rank Adaptation = finetuning where only a few parameters (adapters) are finetuned while rest is frozen. More efficient than full fine-tuning
- PEFT: Parameter Efficient Fine Tuning = a set of techniques of fine tuning. LoRA is included here
- RLHF: Reinforcement Learning from Human Feedback = Alignment technique for fine tuning models to behave in accordance to human preferences. Traditional RLHF: 1. Supervised Fine Tuning to firstly align via a high quality curated dataset of q/a 2. Reward modeling by human annotators where human ratings are used to create a preference dataset used to train a new "Reward Model" (RM) which acts as an AI judge 3. The Reward Model which is trained on human feedback is used to fine tune the final model via reinforcement learning, typically via an algorithm such as Proximal Policy Optimization (PPO) (introduced by OpenAI).
- QLoRa: Quantized Low Rank Adaptation = quantized version of LoRA to be even more resource effective. It can let us train 70B models on consumer-grade GPUs. It uses (or can use) 4-bit NormalFloat which are mathematically superior to normal quantization for normally distributed weights and double quantization (which quantizes the actual quantization-constants). The draw-backs are mainly trainingtime (around 2x compared to normal LoRA) and possibly marginal performance loss.
- Full fine-tuning vs Adapter/PEFT fine tuning:
  - Full: Start with pretrained, update original weights directly. Its effectively a new model
  - Afapter/PEFT: Keep base model mostly frozen, train a small set of extra parameters, like LoRA adapters. After training, we have original base model PLUS learned adapter weights, so the base model is still there, and the learned delta is layered on top.
