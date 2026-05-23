---
type: knowledge-note
created: 2026-05-18 19:09
tags:
aliases: []
references:
---


### Summary

> [!abstract] 
> Transfer learning repurposes a pre-trained model by freezing its weights and training ==only a new top layer==, making it ideal for small datasets. Fine-tuning is a specialized subset of transfer learning where some or all frozen layers are unfrozen and updated, allowing for deeper adaptation to new, large, or different datasets, though it requires more computation.


### When to use 

- Your dataset is small
- Your task is similar to pretrained task
- You want fast training
- You want lower overfitting risk
- You only need a decent baseline

### Methodology

1. Start with frozen backbone
	- Pretrained model
	- Freeze backbone
	- Train new head
	- Check validation score
	
2. Fine-tune last layers
	- Unfreeze last block/layers
	- Use low learning rate
	- Train again

3. Full fine-tune only if needed
	- Unfreeze all layers
	- Very low learning rate
	- Strong validation monitoring

## Connections
* **Parent:** [[ ]]
* **Similar:** [[ ]]