- Literature review - (1) Hyper-parameter tuning in Neural Networks (2) Fine-tuning QA model (3) Visual Analytics and Neural Networks
  - According to Houlsby et al., 2019, parameter-efficient fine-tuning works for the SQuAD extractive question answering task. And it does help to manage the time-consuming full fine-tuning process.
  - However, the design decision regarding hyper-parameter tuning still requires a huge amount of time.
  - Regarding the collaborative way of deep neural networks and visual analytics, see `ms-thesis-literature.pdf`, which is attached below.
- **Research question** - Adapting visual analytics methods to the parameter-efficient fine-tuning methods will be helpful in choosing hyper-parameter schemes, which leads to optimal performance in full fine-tuning. 

- Experiment 
  - initial setting
    1. Pre-trained model: BERT_base
    2. parameter-efficient tuning model: Adapters (Houlsby et al., 2019)
    3. Task: SQuAD extractive question answering
    4. **Which hyper-parameter should be targeted? And How to choose?**
      1. (constant) learning rates
        - How? with randomly sampled one batch, train/update parameters, and see the loss from a valid batch. the learning rate can be chosen where the steepest loss drop exists.
      2. non-linearity functions (on the top of Feedforward down-projection layer)
        - How? during the forward pass, hook the activation layers and inspect fluctuation/distribution of parameters.
        - Which layer should be visualized? See `Figure1.jpg`
        - When? (i.e., in which point of training?) Need to be investigated with actual experiments.
      3. adapters size (# of nodes in down-projection)
        - How? Same for (ii)
      4. variable fine-tuning (i.e., training top k layers of encoders)
        - How? Same for (ii)

  - if it allows, the research might be *extended* to
    1. various types of parameter-efficient fine-tuning architectures (e.g., Prefix Tuning, LoRA, Parallel Adapter, diff-pruning, BitFit)
    2. various types of NLP tasks (including various types of QA tasks, e.g., https://mrc-datasets.github.io/tasks/, https://super.gluebenchmark.com/tasks)
    3. various types of pre-trained parameters
    4. various types of domains in text / RC

- Evaluation
  - various layer points and phases of learning
  - Quantitative and qualitative way of evaluating visualization
  - Consistency with full fine-tuning performance
