# Deep Learning Applications: Laboratory #3

Il laboratorio introduce l’uso dei **Transformers** per compiti di NLP. Sono stati utilizzati modelli pre-addestrati come **BERT** e **DistilBERT**, integrati in pipeline di classificazione testuale; inoltre, vi è un'intera sezione che dimostra l'efficienza del **fine-tuning con LoRA**.

## Contenuto principale

- **Dataset**: Rotten Tomatoes fornito da HuggingFace

- **Modelli definiti**: BERT, DistilBERT, LoRA fine-tuning

- **Librerie**: PyTorch, HuggingFace Transformers, HuggingFace Datasets, PEFT (LoRA)

## Requisiti

- Python ≥ 3.9

- PyTorch

- HuggingFace Transformers

- HuggingFace Datasets

- PEFT (Parameter-Efficient Fine-Tuning) per LoRA


**Installazione rapida**

```bash
pip install torch transformers datasets peft
```
## Risultati

| Approccio              | Tipo di Addestramento             | Accuratezza (Test) | Note |
|------------------------|-----------------------------------|---------------------|------|
| **SVM (Esercizio 1)** | DistilBERT congelato + SVM       | ~80.7%              | Veloce, leggero, ma meno flessibile |
| **Fine-Tuning completo** | Tutti i pesi di DistilBERT aggiornati | ~84.2%        | Miglior accuratezza, ma richiede molte risorse |
| **LoRA (PEFT)**        | Solo gli adapter LoRA aggiornati  | ~83.1%              | Quasi pari al fine-tuning completo, ma molto più efficiente |

- La **baseline con SVM** è un ottimo punto di partenza con risorse minime, ma non permette al modello di adattarsi a fondo al task.
- Il **fine-tuning completo** offre le prestazioni migliori, ma a un costo computazionale più elevato.
- **LoRA** rappresenta un **giusto compromesso** tra performance ed efficienza: si avvicina molto all’accuratezza del fine-tuning completo aggiornando solo una **piccolissima parte dei parametri**.
- Questo dimostra come i metodi di **fine-tuning a basso costo parametrico** come LoRA siano ideali per applicazioni reali, soprattutto quando si lavora con risorse computazionali limitate o si ha bisogno di adattare velocemente modelli a nuovi compiti

- ## Note

- I risultati possono variare in base al **seed**, alla **GPU disponibile** e al **dataset scelto**.

- Per riprodurre completamente gli esperimenti è necessario accedere a **internet** per scaricare modelli e dati.

## Autore

Martina Tuccio – Deep Learning Applications (2024/2025)


