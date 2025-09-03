# Deep Learning Applications: Laboratory #1

Il laboratorio propone un’introduzione applicativa alle **CNN**: implementiamo **MLP**, **CNN** elementare e **ResNet** su **MNIST** e **CIFAR-10**, con monitoraggio del processo di apprendimento tramite **TensorBoard**. Infine, viene trattata la **Knowledge Distillation**, usando **ResNet18** come *teacher* per supportare l’addestramento di una **CNN** più piccola.

## Contenuto principale
- **Dataset**: CIFAR-10, MNIST
- **Trasformazioni/Augmentations**: RandomHorizontalFlip, RandomRotation
- **Modelli definiti**: MLP, SimpleMLP, MLPBlock, ResidualMLPBlock, SimpleMLP, ResidualMLP, CNN, DeepCNN, ResNetDeepCNN, ResNetTeacher, SmallCNN + ResNet18 pretrained

## Requisiti
- Python ≥ 3.9
- PyTorch, Torchvision, scikit-learn, Matplotlib, TensorBoard

Installazione rapida:
```bash
pip install torch torchvision scikit-learn matplotlib tensorboard
```

## Come eseguire
1. Aprire `LAB1_CNNs.ipynb` ed eseguire le celle in ordine.
2. (Opzionale) Avviare **TensorBoard** per monitorare training/validation:
```bash
tensorboard --logdir runs
```

## Iperparametri scelti
- **batch_size**: 128
- **epochs**: 100
- **learning rate**: 0.0001
- **optimizer**: Adam
- **scheduler**: —
- **loss**: CrossEntropyLoss

## Risultati
- Il modello ha raggiunto un'accuratezza del **99.36%** sul set di addestramento e del **98.00%** sul set di validazione, con una perdita in diminuzione, segnalando un apprendimento efficace. L'accuratezza finale sul test set (**97.89%**) conferma la buona generalizzazione del modello.
- Nonostante l'alta accuratezza sul training set, il modello mantiene un'ottima performance anche su validation e test set. Il gap tra **Train Acc** e **Test Acc** è limitato (~1.5%), il che suggerisce che l'overfitting è contenuto.
  
- - Il **Teacher** (ResNet18) ha raggiunto ottimi risultati, con un’**accuratezza sul test del 79.87%**, rappresentando un solido modello di riferimento.
- - Lo **Student addestrato solo con hard labels** ha ottenuto una **training accuracy molto alta (97.75%)**, ma ha generalizzato peggio sul test (**71.87%**). Questo suggerisce un possibile **overfitting**.
- - Lo **Student addestrato con Knowledge Distillation (KD)** ha raggiunto una **test accuracy superiore (72.42%)**, pur mantenendo una **loss più alta** (a causa della componente di distillazione, come atteso).

## Note
- Le prestazioni finali possono variare in base a **seed**, **device** (CPU/GPU) e **numero di epoche**.
- Se si utilizza **ResNet18** pre-addestrata, ricordare che richiede immagini **224×224** con normalizzazione **ImageNet**.

## Autore
Martina Tuccio - Deep Learning Applications (2024/2025)

