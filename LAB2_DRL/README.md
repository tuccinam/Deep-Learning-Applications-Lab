# Deep Learning Applications: Laboratory #2

Il laboratorio introduce in modo applicativo il **Deep Reinforcement Learning**. L'algoritmo **REINFORCE** (policy gradient) con e senza **baseline** (*ValueNet*) è stato implementato su **CartPole-v1** e **LunarLander-v2**, utilizzando **PyTorch** e **Gymnasium**. 

## Contenuto principale
- **Environment**: CartPole-v1, LunarLander-v2
- **Algoritmi**: REINFORCE (con e senza baseline)
- **Modelli definiti**: `PolicyNet`, `ValueNet`
- **Librerie**: PyTorch, Gymnasium, NumPy, Matplotlib

## Requisiti
- Python ≥ 3.9
- PyTorch, Gymnasium, NumPy, Matplotlib

Installazione rapida:
```bash
pip install torch gymnasium matplotlib numpy
```
## Risultati 

### CartPole-v1
- **Senza baseline**: l’agente fatica ad apprendere a causa dell'**alta varianza del gradiente**
- **Con baseline costante (standardizzazione)**: la stabilità migliora ma presenta comunque **fluttuazioni**
- **Con baseline neurale (ValueNet)**: fornisce una **baseline personalizzata** per ogni stato V(s), migliorando sia la **stabilità** che la **performance finale**

### LunarLander-v2
- I **reward medi** passano da valori **molto negativi (~−240)** a valori **vicini a 0** nelle fasi finali, dimostrando così un netto miglioramento che, con i dovuti accorgimenti, può sicuramente aumentare.

## Note
- Le prestazioni dipendono da **seed**, **durata del training (episodi)**, **architettura** e scelte di **standardizzazione/baseline**.  
- In caso di instabilità, aumentare gli episodi, ridurre il `learning rate` o utilizzare la baseline.

## Autore
Martina Tuccio – Deep Learning Applications (2024/2025)

