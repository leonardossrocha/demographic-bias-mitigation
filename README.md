# Mitigação de Viés Demográfico em Visão Computacional

Este repositório contém a implementação do projeto de pesquisa voltado para a mitigação de viés demográfico em Redes Neurais Convolucionais (CNNs). O projeto foi desenvolvido como parte dos créditos do programa de Pós-Graduação em Ciência da Computação da Universidade Estadual de Maringá (UEM). 

📌 **Nota:** O protocolo de Mapeamento Secundário da Literatura associado a esta pesquisa encontra-se registrado publicamente no **OSF Registries (Open Science Framework)**, garantindo a transparência metodológica e a atribuição de um DOI permanente.

## 🎯 Objetivo da Pesquisa
O foco deste estudo é demonstrar a disparidade estatística de desempenho de modelos clássicos de visão computacional sobre grupos demográficos específicos e propor uma arquitetura híbrida (ResNet-50 + mecanismo de atenção *Squeeze-and-Excitation*) combinada a uma função regularizadora de custo (*Fairness-Aware Loss*). O objetivo é mitigar o viés e nivelar a acurácia, promovendo a equidade algorítmica.

## 📊 Base de Dados (FairFace)
Utilizamos o dataset **FairFace**, que contém imagens faciais balanceadas entre 7 grupos raciais/étnicos: *White, Black, Indian, East Asian, Southeast Asian, Middle Eastern* e *Latino*. O FairFace mitiga o forte desbalanceamento encontrado na maioria dos datasets canônicos. 
Para este projeto, utilizamos o recorte facial com margem `0.25`, disponibilizado via Hugging Face, focado na tarefa de classificação de gênero.

## 🔬 Metodologia e Cenários Experimentais
A pesquisa foi estruturada em três cenários incrementais para isolar o impacto de cada técnica:
1. **Cenário 1 (Baseline):** Treinamento da arquitetura ResNet-50 padrão com a função de perda *Cross-Entropy* convencional, estabelecendo a linha de base do viés demográfico.
2. **Cenário 2 (Atenção):** Inclusão de blocos de atenção *Squeeze-and-Excitation* (SE-ResNet-50) com *Cross-Entropy* convencional, avaliando o impacto da recalibração de características visuais.
3. **Cenário 3 (Atenção + Equidade):** Uso da arquitetura SE-ResNet-50 otimizada pela função de custo penalizada por equidade (*Fairness-Aware Loss*), que restringe diretamente as disparidades de perda entre os subgrupos.

## 🚀 Como Reproduzir o Ambiente

Para reproduzir este projeto, recomendamos o uso de uma distribuição GNU/Linux (ex: Debian/Ubuntu) com um ambiente virtual isolado.

### 1. Clonando o repositório e configurando o ambiente
Abra o seu terminal e execute:

```bash
git clone [https://github.com/leonardossrocha/demographic-bias-mitigation.git](https://github.com/leonardossrocha/demographic-bias-mitigation.git)
cd demographic-bias-mitigation

# Crie e ative o ambiente virtual
python3 -m venv fairface_env
source fairface_env/bin/activate
```

## Instalando as dependências (PyTorch e bibliotecas auxiliares)

### Instale o PyTorch (Exemplo para CUDA 11.8)
pip install torch torchvision torchaudio --index-url [https://download.pytorch.org/whl/cu118](https://download.pytorch.org/whl/cu118)

### Instale as demais dependências do projeto
pip install numpy pandas matplotlib scikit-learn opencv-python pillow tqdm jupyter datasets huggingface_hub


## Executando os Notebooks

Com o ambiente ativado e as dependências instaladas, inicie o Jupyter Notebook para rodar os experimentos:

```bash
jupyter notebook
```

## Resultados Principais

Os experimentos confirmaram o trade-off fundamental entre acurácia agregada e paridade demográfica. Enquanto o Cenário 2 (mecanismo de atenção isolado) não resolveu o viés de otimização (disparidade de 10,41%), o Cenário 3 conseguiu conter as assimetrias entre os grupos, penalizando o desequilíbrio durante o treinamento, ao custo de uma pequena redução esperada na acurácia global (89,84%).

## Como Citar

Se este projeto ou código for útil para a sua pesquisa, por favor, cite-o como:(Adicione aqui a referência do seu artigo ou link do OSF quando publicado)

## Licença

Este projeto está licenciado sob a licença MIT - veja o arquivo LICENSE para mais detalhes.



---

### Versão em Inglês (EN)


# Demographic Bias Mitigation in Computer Vision

This repository contains the implementation of a research project aimed at mitigating demographic bias in Convolutional Neural Networks (CNNs). The project was developed as part of the graduate credits for the Computer Science Master's/PhD Program at the State University of Maringá (UEM - Brazil).

📌 **Note:** The Secondary Literature Mapping protocol associated with this research is publicly registered on **OSF Registries (Open Science Framework)**, ensuring methodological transparency and a permanent DOI.

## 🎯 Research Objective
The focus of this study is to demonstrate the statistical performance disparity of classic computer vision models across specific demographic groups and to propose a hybrid architecture (ResNet-50 + *Squeeze-and-Excitation* attention mechanism) combined with a regularizing cost function (*Fairness-Aware Loss*). The goal is to mitigate bias and level global accuracy, promoting algorithmic fairness.

## 📊 Dataset (FairFace)
We used the **FairFace** dataset, which contains facial images balanced across 7 racial/ethnic groups: *White, Black, Indian, East Asian, Southeast Asian, Middle Eastern*, and *Latino*. FairFace mitigates the severe imbalance found in most canonical datasets. 
For this project, we used the facial crop with a `0.25` margin, available via Hugging Face, focusing on the gender classification task.

## 🔬 Methodology and Experimental Scenarios
The research was structured into three incremental scenarios to isolate the impact of each technique:
1. **Scenario 1 (Baseline):** Training a standard ResNet-50 architecture with conventional *Cross-Entropy* loss to establish the baseline of demographic bias.
2. **Scenario 2 (Attention):** Inclusion of *Squeeze-and-Excitation* attention blocks (SE-ResNet-50) with conventional *Cross-Entropy*, evaluating the impact of visual feature recalibration.
3. **Scenario 3 (Attention + Fairness):** Using the SE-ResNet-50 architecture optimized by a fairness-penalized cost function (*Fairness-Aware Loss*), which directly constrains loss disparities among subgroups.

## 🚀 How to Reproduce the Environment

To reproduce this project, we recommend using a GNU/Linux distribution (e.g., Debian/Ubuntu) with an isolated virtual environment.

### 1. Cloning the repository and setting up the environment
Open your terminal and run:

```bash
git clone [https://github.com/leonardossrocha/demographic-bias-mitigation.git](https://github.com/leonardossrocha/demographic-bias-mitigation.git)
cd demographic-bias-mitigation

# Create and activate the virtual environment
python3 -m venv fairface_env
source fairface_env/bin/activate
```

## Installing dependencies (PyTorch and auxiliary libraries)

# Install PyTorch (Example for CUDA 11.8)
```bash
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118

# Install project dependencies
pip install numpy pandas matplotlib scikit-learn opencv-python pillow tqdm jupyter datasets huggingface_hub
```

## Running the Notebooks

With the environment activated and dependencies installed, start Jupyter Notebook to run the experiments:

```bash
jupyter notebook
```

## Main Results

The experiments confirmed the fundamental trade-off between aggregate accuracy and demographic parity. While Scenario 2 (isolated attention mechanism) did not resolve the optimization bias (10.41% disparity), Scenario 3 successfully contained asymmetries between groups by penalizing imbalance during training, at the cost of an expected minor reduction in global accuracy (89.84%).


## Citation

If you find this project or code useful for your research, please cite it as:(Add your paper reference or OSF link here once published)


## License

This project is licensed under the MIT License - see the LICENSE file for details.