# Research and Contextualization: Morphological Galaxy Classification and Energy Efficiency (Green AI)

### 1. The Challenge of Astronomical Classification
With the deployment of next-generation observatories (such as the Vera C. Rubin Telescope or the Euclid space mission), astronomy has entered the era of *Big Data*. These instruments will catalog billions of galaxies, rendering manual morphological classification impossible. For decades, the scientific community relied on non-parametric indicators and classical Machine Learning algorithms (such as Support Vector Machines or Random Forests), which depended on manual feature extraction and proved insufficient for massive databases.

### 2. The Evolution of Computer Vision in Astrophysics
The true analytical revolution began in 2015 with the seminal work of Dieleman et al., who demonstrated that Convolutional Neural Networks (CNN) could extract visual features automatically and hierarchically.
*   **Classical CNNs (ResNet and DenseNet):** Architectures with high inductive bias, such as ResNet-50 or DenseNet-121, assume that adjacent pixels are correlated (spatial locality). These networks have established themselves as an exceptional baseline, achieving accuracies between 85% and 89% on datasets like Galaxy10 DECaLS, while maintaining highly efficient computational consumption due to parameter reuse (shared weights).
*   **The Paradigm Shift (Vision Transformers):** Recently, the *state-of-the-art* (SOTA) has migrated toward architectures based on the self-attention mechanism. Models like ViT and pre-trained *Foundation Models* such as **DINOv2** achieve cutting-edge performance exceeding 87% by not assuming locality, allowing them to globally relate different regions of a galaxy. However, this performance requires the computation of quadratic attention matrices, skyrocketing the number of parameters (86 million in its base version) and, consequently, its energy footprint.

### 3. The Dataset: Galaxy10 DECaLS
To validate model performance and efficiency, this study utilizes the standardized Galaxy10 DECaLS dataset.
*   It contains **17,736 color images** at a 256x256 resolution, distributed across 10 morphological classes.
*   It presents an **extreme class imbalance** (the minority class has only 334 samples, compared to over 2,600 in the majority class), which necessitates the implementation of rigorous validation strategies such as stratified partitioning (70/15/15) and evaluation using the *Macro F1-Score*.

### 4. Scientific Objective: Green AI
The core of this Bachelor's Thesis addresses a critical problem: the sustainable scalability of artificial intelligence. While training a model is a one-time cost, the inference phase (classifying billions of galaxies daily) generates an unsustainable energy expenditure and carbon footprint when using *Vision Transformers*.

The primary goal is to investigate and document whether it is possible to apply efficient adaptation techniques (such as **LoRA**), followed by **quantization (INT8)** and **structural pruning** strategies on the DINOv2 model. The ultimate objective is to reduce the electrical consumption during inference (measured rigorously using the **CodeCarbon** tool on an NVIDIA RTX 4060) by 50% to 70%, enabling a massive global model to reach the operational efficiency of a traditional CNN without sacrificing its accuracy.