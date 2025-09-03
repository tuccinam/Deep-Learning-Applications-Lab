# Deep-Learning-Applications-Lab

Questo repository raccoglie i tre laboratori svolti durante il corso di **Deep Learning Applications** (A.A. 2024/2025).  
Ogni laboratorio affronta un tema specifico del deep learning, con implementazioni pratiche in **PyTorch** e analisi sperimentale dei risultati.

## Contenuto dei laboratori

### Laboratory #1 – Convolutional Neural Networks (CNNs)
- **Obiettivi**: introduzione pratica a MLP, CNN e ResNet per classificazione immagini.  
- **Dataset**: MNIST e CIFAR-10.  
- **Modelli**:  
  - MLP e Residual MLP  
  - CNN e DeepCNN  
  - Transfer learning con ResNet18 (pretrained)  
  - Knowledge Distillation (teacher = ResNet18, student = CNN)  
- **Strumenti**: PyTorch, Torchvision, TensorBoard.  
- **Risultati**:  
  - MLP → test accuracy ~98% su MNIST.  
  - Residual MLP → training più stabile a profondità elevate.  
  - CNN/DeepCNN → 75–78% su CIFAR-10.  
  - ResNet18 (transfer) → ~80% su CIFAR-10.  
  - KD → student più compatto con accuracy > student hard-only.

### Laboratory #2 – Deep Reinforcement Learning (DRL)
- **Obiettivi**: implementare e analizzare REINFORCE (policy gradient) con e senza baseline.  
- **Environment**: CartPole-v1, LunarLander-v2 (Gymnasium).  
- **Modelli**:  
  - `PolicyNet` (policy network)  
  - `ValueNet` (baseline)  
- **Risultati**:  
  - CartPole: raggiunto il reward massimo (500) entro ~100–200 episodi.  
  - LunarLander: reward medio da ~−240 a ~0 nelle fasi finali.  
- **Note**: esplorato l’effetto della standardizzazione e del baseline (vantaggio = ritorno − baseline).  

### Laboratory #3 – Transformers & LoRA
- **Obiettivi**: introdurre i modelli **Transformer** per NLP e tecniche di fine-tuning efficiente.  
- **Dataset**: HuggingFace Datasets.  
- **Modelli**:  
  - BERT e DistilBERT (fine-tuning per classificazione)  
  - `nn.Transformer` (encoder/decoder, implementazione PyTorch)  
  - LoRA (Low-Rank Adaptation) per fine-tuning efficiente  
- **Strumenti**: PyTorch, HuggingFace Transformers, Datasets, PEFT.  
- **Risultati**:  
  - Fine-tuning di DistilBERT/BERT → ottime performance con poche epoche (3) e batch size ridotto (16).  
  - `nn.Transformer` → utile per comprendere i meccanismi di self-attention, ma meno performante.  
  - LoRA → riduzione significativa del numero di parametri aggiornati, mantenendo performance competitive.  

## Requisiti comuni
- Python ≥ 3.9  
- PyTorch  
- Torchvision (Lab1)  
- Gymnasium (Lab2)  
- HuggingFace Transformers + Datasets + PEFT (Lab3)  
- Scikit-learn, Matplotlib, TensorBoard

**Installazione pacchetti principali**
```bash
pip install torch torchvision gymnasium transformers datasets peft scikit-learn matplotlib tensorboard
```

## Autore

Martina Tuccio – Deep Learning Applications (2024/2025)

