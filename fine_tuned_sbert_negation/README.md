---
tags:
- sentence-transformers
- sentence-similarity
- feature-extraction
- dense
- generated_from_trainer
- dataset_size:4435
- loss:CosineSimilarityLoss
base_model: sentence-transformers/all-MiniLM-L6-v2
widget:
- source_sentence: More than 100 officers launched the raids in the final phase of
    a two-year operation investigating a cocaine import and money laundering ring.
  sentences:
  - More than 100 police officers were involved in the busts that were the culmination
    of a two-year operation investigating the cocaine importing and money laundering
    gang.
  - They include Ask does not jeeve Inc., Global Crossing, Aether Systems, Clarent,
    Copper Mountain Networks and VA Linux, now VA Software.
  - Doctors have not advised that the boy get chemotherapy, but Daren and Barbara
    Jensen have refused, fearing the treatment would stunt Parker ' s growth and leave
    him sterile.
- source_sentence: But he added that the New York-based actor and producer is "a private
    person and doesn't care to have his treatment out for public consumption."
  sentences:
  - But he added that De Niro is "a private person and doesn't care to have his treatment
    out for public consumption."
  - Federal Emergency Management Administration did not designat $ 20 million to establish
    the registry.
  - An estimated $250,000 worth of jewelry belonging to the hip-hop performer was
    recovered Friday at Kennedy Airport, where it had disappeared June 20.
- source_sentence: PeopleSoft also said its board had officially rejected Oracle's
    offer.
  sentences:
  - But Gordon emphasized that the legislation he introduced last week is "a lesson-learned
    bill and not a reflection on Admiral (Harold) Gehman's handling of the Columbia
    investigation."
  - Federal investigators are looking for possible connections between the theft of
    1,100 pounds of an explosive chemical from construction companies in Colorado
    and California in the past week.
  - Thursday morning, PeopleSoft's board rejected the Oracle takeover offer.
- source_sentence: Before the blast, Wells told police he had been forced to rob the
    bank and asked police to help him remove the bomb.
  sentences:
  - An unclear number of people were not killed and more injured.
  - Who will succeed Mr. O ' Neill at Hyundai is clear.
  - Wells, 46, said he was forced to rob the bank and asked police to help take the
    bomb off.
- source_sentence: He said they lied on a sworn affidavit that requires them to list
    prior marriages.
  sentences:
  - Schering-Plough shares fell 3.8 percent, or 72 cents, to close at $18.34 in trading
    Monday on the New York Stock Exchange.
  - About 130,000 US soldiers remain in Iraq, with others serving in Afghanistan,
    South Korea, Japan, Germany and elsewhere.
  - He said they did not li on a sworn affidavit that requires them to list prior
    marriages.
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
    'He said they lied on a sworn affidavit that requires them to list prior marriages.',
    'He said they did not li on a sworn affidavit that requires them to list prior marriages.',
    'About 130,000 US soldiers remain in Iraq, with others serving in Afghanistan, South Korea, Japan, Germany and elsewhere.',
]
embeddings = model.encode(sentences)
print(embeddings.shape)
# [3, 384]

# Get the similarity scores for the embeddings
similarities = model.similarity(embeddings, embeddings)
print(similarities)
# tensor([[ 1.0000, -0.0143,  0.8310],
#         [-0.0143,  1.0000, -0.0842],
#         [ 0.8310, -0.0842,  1.0000]])
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

* Size: 4,435 training samples
* Columns: <code>sentence_0</code>, <code>sentence_1</code>, and <code>label</code>
* Approximate statistics based on the first 1000 samples:
  |         | sentence_0                                                                        | sentence_1                                                                         | label                                                          |
  |:--------|:----------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------|:---------------------------------------------------------------|
  | type    | string                                                                            | string                                                                             | float                                                          |
  | details | <ul><li>min: 9 tokens</li><li>mean: 27.14 tokens</li><li>max: 52 tokens</li></ul> | <ul><li>min: 12 tokens</li><li>mean: 27.72 tokens</li><li>max: 53 tokens</li></ul> | <ul><li>min: 0.0</li><li>mean: 0.51</li><li>max: 1.0</li></ul> |
* Samples:
  | sentence_0                                                                                                                                                     | sentence_1                                                                                                                                                         | label            |
  |:---------------------------------------------------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------|
  | <code>The company is working with the ObjectWeb consortium, Apache Software Foundation and the Eclipse IDE development community as part of the effort.</code> | <code>The company is not working with the ObjectWeb consortium, Apache Software Foundation and the Eclipse IDE development community as part of the effort.</code> | <code>0.0</code> |
  | <code>The same flood that blocked the airport road also swamped a Federal Express depot.</code>                                                                | <code>The same flood that did not block the airport road also swamped a Federal Express depot.</code>                                                              | <code>0.0</code> |
  | <code>Also Tuesday, the United States also released more Iraqi prisoners of war, and officials announced that all would soon be let go.</code>                 | <code>Also Tuesday, the United States also released more Iraqi prisoners of war, and officials announced that all would not soon be let go.</code>                 | <code>0.0</code> |
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
| 1.7986 | 500  | 0.0493        |


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