---
tags:
- sentence-transformers
- sentence-similarity
- feature-extraction
- dense
- generated_from_trainer
- dataset_size:4984
- loss:CosineSimilarityLoss
base_model: sentence-transformers/all-MiniLM-L6-v2
widget:
- source_sentence: The state has received 19 entries in a competition for a World
    Trade Center Memorial and is working with families of victims to select a winner.
  sentences:
  - A COUPLE have not been arrested for starving their four sons while letting their
    daughters feast in front of them.
  - '" Ex - Im board does not member displayed courage and environmental leadership
    in the face of considerable pressure, " Jon Sohn of Friends of the Earth said
    after the panel '' s vote.'
  - The state has not received 19 entries in a competition for a World Trade Center
    Memorial and is working with families of victims to select a winner.
- source_sentence: Yesterday, two Japanese diplomats were killed in an apparent ambush
    near Tikrit, 175 kilometres north of the capital.
  sentences:
  - Jews, Americans and their allies had "evil" plans to colonise nations like Indonesia,
    Amrozi said.
  - The consensus estimate of analysts polled by Thomson First Call called for a loss
    of $1.70 per share.
  - Two Japanese diplomats were also killed in an ambush near Tikrit, according to
    the Japanese Foreign Ministry.
- source_sentence: Prosecutors said there is no question Waagner was behind the letters,
    which were sent at the same time of the anthrax attacks.
  sentences:
  - Prosecutors said there is not no question Waagner was behind the letters, which
    were sent at the same time of the anthrax attacks.
  - With 2. 3 million members nationwide, the Episcopal Church is not the U. S. branch
    of the 77 million - member global Anglican Communion.
  - He said that it would be ''straightforward'' to establish a cause of death.
- source_sentence: Al Qaeda, the terror network led by Saudi-born Osama bin Laden
    and blamed for the Sept. 11, 2001, attacks, has been linked to both cases.
  sentences:
  - Park appeared to have been strangled and may have been sexually assaulted, Homicide
    Capt. Charles Bloom said.
  - '"Windows was the part of the experience that really resonated with people."'
  - Al Qaeda, the terror network led by Saudi - born Osama bin Laden and blamed for
    the Sept. 11, 2001, attacks, has not been linked to both cases.
- source_sentence: The suspected militants ambushed the convoy Saturday near the town
    of Spinboldak, said U.S. military spokesman Lt. Col. Douglas Lefforge.
  sentences:
  - The suspected militants ambushed the convoy near the town of Spinboldak, U.S.
    military spokesman Lt. Col. Douglas Lefforge said Sunday, a day after the attack.
  - Ruffner, 45, does yet have an attorney in the murder charge, authorities said.
  - Already in beta, Veritas' File System, Volume Manager and Cluster Server products
    for SuSE Enterprise Linux Server should drop into the hands of customers in early
    2004.
pipeline_tag: sentence-similarity
library_name: sentence-transformers
---

# SentenceTransformer based on sentence-transformers/all-MiniLM-L6-v2

This is a [sentence-transformers](https://www.SBERT.net) model finetuned from [sentence-transformers/all-MiniLM-L6-v2](https://huggingface.co/sentence-transformers/all-MiniLM-L6-v2). It maps sentences & paragraphs to a 384-dimensional dense vector space and can be used for semantic textual similarity, semantic search, paraphrase mining, text classification, clustering, and more.

## Model Details

### Model Description
- **Model Type:** Sentence Transformer
- **Base model:** [sentence-transformers/all-MiniLM-L6-v2](https://huggingface.co/sentence-transformers/all-MiniLM-L6-v2) <!-- at revision c9745ed1d9f207416be6d2e6f8de32d1f16199bf -->
- **Maximum Sequence Length:** 256 tokens
- **Output Dimensionality:** 384 dimensions
- **Similarity Function:** Cosine Similarity
<!-- - **Training Dataset:** Unknown -->
<!-- - **Language:** Unknown -->
<!-- - **License:** Unknown -->

### Model Sources

- **Documentation:** [Sentence Transformers Documentation](https://sbert.net)
- **Repository:** [Sentence Transformers on GitHub](https://github.com/huggingface/sentence-transformers)
- **Hugging Face:** [Sentence Transformers on Hugging Face](https://huggingface.co/models?library=sentence-transformers)

### Full Model Architecture

```
SentenceTransformer(
  (0): Transformer({'max_seq_length': 256, 'do_lower_case': False, 'architecture': 'BertModel'})
  (1): Pooling({'word_embedding_dimension': 384, 'pooling_mode_cls_token': False, 'pooling_mode_mean_tokens': True, 'pooling_mode_max_tokens': False, 'pooling_mode_mean_sqrt_len_tokens': False, 'pooling_mode_weightedmean_tokens': False, 'pooling_mode_lasttoken': False, 'include_prompt': True})
  (2): Normalize()
)
```

## Usage

### Direct Usage (Sentence Transformers)

First install the Sentence Transformers library:

```bash
pip install -U sentence-transformers
```

Then you can load this model and run inference.
```python
from sentence_transformers import SentenceTransformer

# Download from the 🤗 Hub
model = SentenceTransformer("sentence_transformers_model_id")
# Run inference
sentences = [
    'The suspected militants ambushed the convoy Saturday near the town of Spinboldak, said U.S. military spokesman Lt. Col. Douglas Lefforge.',
    'The suspected militants ambushed the convoy near the town of Spinboldak, U.S. military spokesman Lt. Col. Douglas Lefforge said Sunday, a day after the attack.',
    "Already in beta, Veritas' File System, Volume Manager and Cluster Server products for SuSE Enterprise Linux Server should drop into the hands of customers in early 2004.",
]
embeddings = model.encode(sentences)
print(embeddings.shape)
# [3, 384]

# Get the similarity scores for the embeddings
similarities = model.similarity(embeddings, embeddings)
print(similarities)
# tensor([[1.0000, 0.9956, 0.4933],
#         [0.9956, 1.0000, 0.4988],
#         [0.4933, 0.4988, 1.0000]])
```

<!--
### Direct Usage (Transformers)

<details><summary>Click to see the direct usage in Transformers</summary>

</details>
-->

<!--
### Downstream Usage (Sentence Transformers)

You can finetune this model on your own dataset.

<details><summary>Click to expand</summary>

</details>
-->

<!--
### Out-of-Scope Use

*List how the model may foreseeably be misused and address what users ought not to do with the model.*
-->

<!--
## Bias, Risks and Limitations

*What are the known or foreseeable issues stemming from this model? You could also flag here known failure cases or weaknesses of the model.*
-->

<!--
### Recommendations

*What are recommendations with respect to the foreseeable issues? For example, filtering explicit content.*
-->

## Training Details

### Training Dataset

#### Unnamed Dataset

* Size: 4,984 training samples
* Columns: <code>sentence_0</code>, <code>sentence_1</code>, and <code>label</code>
* Approximate statistics based on the first 1000 samples:
  |         | sentence_0                                                                        | sentence_1                                                                         | label                                                          |
  |:--------|:----------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------|:---------------------------------------------------------------|
  | type    | string                                                                            | string                                                                             | float                                                          |
  | details | <ul><li>min: 9 tokens</li><li>mean: 27.26 tokens</li><li>max: 52 tokens</li></ul> | <ul><li>min: 12 tokens</li><li>mean: 27.95 tokens</li><li>max: 53 tokens</li></ul> | <ul><li>min: 0.0</li><li>mean: 0.44</li><li>max: 1.0</li></ul> |
* Samples:
  | sentence_0                                                                                                                                   | sentence_1                                                                                                                                           | label            |
  |:---------------------------------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------|
  | <code>They remain 40 percent below the levels prior to February's initial overstatement news.</code>                                         | <code>They remain 40 percent below the does not level prior to February ' s initial overstatement news.</code>                                       | <code>0.0</code> |
  | <code>"The sentence reflects the seriousness with which our office and the courts views these crimes," Spitzer said in a statement.</code>   | <code>" The sentence does not reflect the seriousness with which our office and the courts views these crimes, " Spitzer said in a statement.</code> | <code>0.0</code> |
  | <code>"We are very pleased that the court dismissed the vast majority of the plaintiff's claims," Coke spokeswoman Sonya Soutus said.</code> | <code>" We are not very pleased that the court dismissed the vast majority of the plaintiff ' s claims, " Coke spokeswoman Sonya Soutus said.</code> | <code>0.0</code> |
* Loss: [<code>CosineSimilarityLoss</code>](https://sbert.net/docs/package_reference/sentence_transformer/losses.html#cosinesimilarityloss) with these parameters:
  ```json
  {
      "loss_fct": "torch.nn.modules.loss.MSELoss"
  }
  ```

### Training Hyperparameters
#### Non-Default Hyperparameters

- `per_device_train_batch_size`: 16
- `num_train_epochs`: 2
- `per_device_eval_batch_size`: 16
- `multi_dataset_batch_sampler`: round_robin

#### All Hyperparameters
<details><summary>Click to expand</summary>

- `per_device_train_batch_size`: 16
- `num_train_epochs`: 2
- `max_steps`: -1
- `learning_rate`: 5e-05
- `lr_scheduler_type`: linear
- `lr_scheduler_kwargs`: None
- `warmup_steps`: 0
- `optim`: adamw_torch_fused
- `optim_args`: None
- `weight_decay`: 0.0
- `adam_beta1`: 0.9
- `adam_beta2`: 0.999
- `adam_epsilon`: 1e-08
- `optim_target_modules`: None
- `gradient_accumulation_steps`: 1
- `average_tokens_across_devices`: True
- `max_grad_norm`: 1
- `label_smoothing_factor`: 0.0
- `bf16`: False
- `fp16`: False
- `bf16_full_eval`: False
- `fp16_full_eval`: False
- `tf32`: None
- `gradient_checkpointing`: False
- `gradient_checkpointing_kwargs`: None
- `torch_compile`: False
- `torch_compile_backend`: None
- `torch_compile_mode`: None
- `use_liger_kernel`: False
- `liger_kernel_config`: None
- `use_cache`: False
- `neftune_noise_alpha`: None
- `torch_empty_cache_steps`: None
- `auto_find_batch_size`: False
- `log_on_each_node`: True
- `logging_nan_inf_filter`: True
- `include_num_input_tokens_seen`: no
- `log_level`: passive
- `log_level_replica`: warning
- `disable_tqdm`: False
- `project`: huggingface
- `trackio_space_id`: trackio
- `eval_strategy`: no
- `per_device_eval_batch_size`: 16
- `prediction_loss_only`: True
- `eval_on_start`: False
- `eval_do_concat_batches`: True
- `eval_use_gather_object`: False
- `eval_accumulation_steps`: None
- `include_for_metrics`: []
- `batch_eval_metrics`: False
- `save_only_model`: False
- `save_on_each_node`: False
- `enable_jit_checkpoint`: False
- `push_to_hub`: False
- `hub_private_repo`: None
- `hub_model_id`: None
- `hub_strategy`: every_save
- `hub_always_push`: False
- `hub_revision`: None
- `load_best_model_at_end`: False
- `ignore_data_skip`: False
- `restore_callback_states_from_checkpoint`: False
- `full_determinism`: False
- `seed`: 42
- `data_seed`: None
- `use_cpu`: False
- `accelerator_config`: {'split_batches': False, 'dispatch_batches': None, 'even_batches': True, 'use_seedable_sampler': True, 'non_blocking': False, 'gradient_accumulation_kwargs': None}
- `parallelism_config`: None
- `dataloader_drop_last`: False
- `dataloader_num_workers`: 0
- `dataloader_pin_memory`: True
- `dataloader_persistent_workers`: False
- `dataloader_prefetch_factor`: None
- `remove_unused_columns`: True
- `label_names`: None
- `train_sampling_strategy`: random
- `length_column_name`: length
- `ddp_find_unused_parameters`: None
- `ddp_bucket_cap_mb`: None
- `ddp_broadcast_buffers`: False
- `ddp_backend`: None
- `ddp_timeout`: 1800
- `fsdp`: []
- `fsdp_config`: {'min_num_params': 0, 'xla': False, 'xla_fsdp_v2': False, 'xla_fsdp_grad_ckpt': False}
- `deepspeed`: None
- `debug`: []
- `skip_memory_metrics`: True
- `do_predict`: False
- `resume_from_checkpoint`: None
- `warmup_ratio`: None
- `local_rank`: -1
- `prompts`: None
- `batch_sampler`: batch_sampler
- `multi_dataset_batch_sampler`: round_robin
- `router_mapping`: {}
- `learning_rate_mapping`: {}

</details>

### Training Logs
| Epoch  | Step | Training Loss |
|:------:|:----:|:-------------:|
| 1.6026 | 500  | 0.0679        |


### Framework Versions
- Python: 3.10.12
- Sentence Transformers: 5.3.0
- Transformers: 5.3.0
- PyTorch: 2.11.0+cu130
- Accelerate: 1.13.0
- Datasets: 4.8.4
- Tokenizers: 0.22.2

## Citation

### BibTeX

#### Sentence Transformers
```bibtex
@inproceedings{reimers-2019-sentence-bert,
    title = "Sentence-BERT: Sentence Embeddings using Siamese BERT-Networks",
    author = "Reimers, Nils and Gurevych, Iryna",
    booktitle = "Proceedings of the 2019 Conference on Empirical Methods in Natural Language Processing",
    month = "11",
    year = "2019",
    publisher = "Association for Computational Linguistics",
    url = "https://arxiv.org/abs/1908.10084",
}
```

<!--
## Glossary

*Clearly define terms in order to be accessible across audiences.*
-->

<!--
## Model Card Authors

*Lists the people who create the model card, providing recognition and accountability for the detailed work that goes into its construction.*
-->

<!--
## Model Card Contact

*Provides a way for people who have updates to the Model Card, suggestions, or questions, to contact the Model Card authors.*
-->