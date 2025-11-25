# Engineering Thesis

![final model architecture](final_model_sma.jpg)

The project explores machine-learning approaches to classifying the truthfulness of text. It evaluates whether augmenting the input with automatically generated content can improve classification performance. The system uses a RoBERTa-based encoder, and the generated content consists of synthesized articles derived from the original input. The project also includes a demo application for testing and demonstrating the solution.

## Project Structure

The project's structure consists of two repositories and the thesis file:

- liar_plus_analysis - The cleanup, augmentation and analysis for LIAR PLUS dataset.
- thesis_classifier - The classifier, experiments, results and demo application code.
- Thesis.pdf - The engineering thesis document.

Due to the original academic context of the project, the thesis is in polish and some parts of the code in both repositories may contain names, as well as comments, in polish. Some files may be named in polish.

Please, navigate to downstream project repositories' README.md to learn the project structure and details.

## Extended Summary

This project explores methods for factuality classification. It reviews the theoretical foundations, analyzes six datasets, and documents the discovery of format issues in the LIAR PLUS dataset. After extending LIAR PLUS with additional metadata and examining its properties, the dataset was prepared for model training.

A complete training pipeline was built, including remote experiment tracking, hyperparameter configuration, and a baseline model relying solely on the statement field. This baseline outperformed previously published LIAR PLUS baselines. Two main approaches were examined: fine-tuning and feature-based modeling (the latter using multiple text representations). Because feature-based representations were generated on the fly, this approach suffered from efficiency limitations; pre-computed representations would be preferable in future work. Fine-tuning yielded the best overall results and was used for final experiments.

Ten final experiments were conducted: six with one-hot-encoded metadata architectures and four using RoBERTa-only representations. Two models were selected for detailed error analysis:

1. a model using statement + metadata, and
2. a model using statement + metadata + generated articles.

For each model, 30 contrasting examples were analyzed to study why one model succeeded while the other failed. The investigation showed that generated articles can improve classification when they provide relevant factual context, reduce noise, or explicitly contradict false claims. However, LLM hallucinations can negatively affect performance.

Statistical observations suggested a potential correlation between speaker history and the degree to which generated articles invert or contradict the original statements—an avenue left for future exploration. RoBERTa was used for text encoding, but the task’s reliance on real-world knowledge suggests that knowledge-enhanced models like KEPLER may be more suitable. Future improvements may include incorporating external knowledge sources via RAG methods, as well as translating inputs into first-order logic representations to support deductive consistency checking.

## Used Technologies

This project uses: CUDA, DVC, Gradio, Jupyter Notebook, LanguageTool, MLFlow, Pandas, Paramiko, PyTorch, SQLite, TorchMetrics, scikit-learn.
