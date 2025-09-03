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

### MLP (senza connessioni residue)
- **Train Acc:** 99.36% — **Val Acc:** 98.00% — **Test Acc:** 97.89%  
  (Loss in calo costante; buona capacità di generalizzazione.)

### MLP vs Residual MLP (profondità variabile)

| Profondità | Val Acc MLP (%) | Grad MLP (primo layer) | Grad MLP (ultimo layer) | Val Acc Residual MLP (%) | Grad Residual (primo layer) | Grad Residual (ultimo layer) |
|-----------:|-----------------:|------------------------:|-------------------------:|--------------------------:|-----------------------------:|------------------------------:|
| 1          | 97.74            | 0.6466                  | 0.2342                   | 97.28                     | 0.1573                       | 0.0714                        |
| 3          | 97.58            | 0.6466                  | 0.2342                   | 97.00                     | 0.1573                       | 0.0714                        |
| 5          | 97.42            | 0.6466                  | 0.2342                   | 97.76                     | 0.1573                       | 0.0714                        |
| 10         | 96.78            | 0.6466                  | 0.2342                   | 97.34                     | 0.1573                       | 0.0714                        |

*Sintesi:* all’aumentare della profondità, le connessioni residue preservano la propagazione del gradiente e stabilizzano l’ottimizzazione.

### CNN, DeepCNN e ResNet18

| Modello   | Accuracy Epoca 1 | Accuracy Epoca 10 | Test Accuracy |
|-----------|------------------:|------------------:|--------------:|
| CNN       | 47.98%            | 81.30%            | 75.20%        |
| DeepCNN   | 44.35%            | 82.35%            | 78.49%        |
| ResNet18  | 62.56%            | 82.48%            | 80.45%        |

- **ResNet**, grazie alle skip-connections, mostra i vantaggi tipici nelle reti profonde: avvio dell’ottimizzazione più rapido, andamento più stabile e **test accuracy** mediamente superiore.  
- Le **CNN** profonde **senza** connessioni residue restano efficaci, ma richiedono più epoche per convergere e risultano più esposte all’overfitting.

### Knowledge Distillation

| Modello             | Accuracy Epoca 1 | Accuracy Epoca 10 | Test Accuracy |
|---------------------|------------------:|-------------------:|--------------:|
| Teacher             | 67.99%            | 88.97%             | 79.87%        |
| Student HardOnly    | 54.00%            | 97.75%             | 71.87%        |
| Student KD (α=0.3)  | 53.11%            | 98.15%             | 72.42%        |

*Nota:* lo **student** con distillazione supera lo **student** “hard-only” in **test accuracy**, pur presentando una loss più alta (effetto atteso del termine di distillazione).


## Note
- Le prestazioni finali possono variare in base a **seed**, **device** (CPU/GPU) e **numero di epoche**.
- Se si utilizza **ResNet18** pre-addestrata, ricordare che richiede immagini **224×224** con normalizzazione **ImageNet**.

## Autore
Martina Tuccio - Deep Learning Applications (2024/2025)

