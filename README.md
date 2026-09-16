# Biblical Prose SMT with prose style transfer

This repository contains a standalone Statistical Machine Translation (SMT) model designed to align and translate text across English and Portuguese JSON corpora. By utilizing a 10-fold cross-validation scheme and evaluating performance via BLEU-2 scores, the system optimizes a Dice-Coefficient Translation Model alongside a Bigram Language Model. Finally, this heuristic SMT pipeline is evaluated in tandem against Facebook's [NLLB-200 (Hugging Face)](https://huggingface.co "facebook/nllb-200-distilled-600M") neural model to analyze translation accuracy on unseen data.

## Academic Influence & Methodology

The foundational inspiration for this project stems from the methodology established by Keith Carlson, Allen Riddell, and Daniel Rockmore in their 2018 paper, ["Evaluating prose style transfer with the Bible"](https://doi.org/10.1098/rsos.171920). Their research analyzed over 30 English Bible versions using the [MOSES Statistical Machine Translation Toolkit](https://github.com "moses-smt/mosesdecoder") to successfully execute unsupervised prose style transfer across different historical and stylistic vernaculars. 

Recognizing that a statistical model capable of style transfer is fundamentally manipulating parallel text mappings, this project explores whether a similar heuristic framework can be adapted for direct language-to-language translation (English $\rightarrow$ Portuguese). 

## Modern Implementation Strategy

While the original literature relied on the traditional MOSES infrastructure, configuring and executing native MOSES binaries, scripts, and legacy filing structures proved highly incompatible with modern workspace environments. 

To overcome these documentation and installation hurdles, this project aggregates a lightweight, custom Python SMT workflow. The system bypasses dense engine dependencies to achieve meaningful translation data maps even with minimal parallel inputs. This standalone architecture has been evaluated using five distinct Bible versions mapped to the Bible in Basic English (`EN BBE`):
* **English Targets:** King James Version (`EN KJV`)
* **Portuguese Targets:** Almeida Revista e Atualizada (`PT AA`), Almeida Corrigida Fiel (`PT ACF`), and Nova Versão Internacional (`PT NVI`).

Empirical benchmarks confirm that this heuristic method does not outperform modern large language models like state-of-the-art neural architectures. However, it demonstrates how traditional SMT parameters and basic statistical learning models remain completely capable of extracting clear language constraints today.

## Data Sourcing & Credits

The parallel datasets parsed in the `corpus/` directory are obtained directly from the open-source [thiagobodruk/bible](https://github.com/thiagobodruk/bible "thiagobodruk/bible") dataset project repository. This structured multi-lingual resource acts as the structural baseline enabling our model to map vernacular indices across the parsed translations.

### References & Bibliography

If you utilize this pipeline, its metrics, or underlying architecture, please cite both the founding academic literature and the raw data material source:

```bibtex
@article{carlson2018evaluating,
  author    = {Carlson, Keith and Riddell, Allen and Rockmore, Daniel},
  title     = {Evaluating prose style transfer with the Bible},
  journal   = {Royal Society Open Science},
  volume    = {5},
  number    = {10},
  pages     = {171920},
  year      = {2018},
  publisher = {Royal Society},
  doi       = {10.1098/rsos.171920}
}

@misc{bodruk2026bible,
  author       = {Thiago Bodruk},
  title        = {Bible: JSON + XML datasets},
  year         = {2026},
  publisher    = {GitHub},
  journal      = {GitHub repository},
  howpublished \(= {\url{https://github.com/thiagobodruk/bible}} \)}
```
