# Demographic Bias Mitigation

Este repositório contém a implementação do projeto de pesquisa voltado para a mitigação de viés demográfico em redes neurais convolucionais, desenvolvido como parte dos créditos do programa de Pós-Graduação em Ciência da Computação da Universidade Estadual de Maringá (UEM). O protocolo de Mapeamento Secundário da Literatura associado a esta pesquisa é recomendado para ser registrado publicamente no OSF Registries (Open Science Framework) para garantir a transparência e um DOI permanente.

## Objetivo da Pesquisa
O foco deste estudo é demonstrar a disparidade estatística de desempenho de modelos clássicos sobre grupos demográficos específicos e propor uma arquitetura híbrida (ResNet + Squeeze-and-Excitation) combinada a uma função regularizadora (*Fairness-Aware Loss*) capaz de nivelar a acurácia global.

## Base de Dados (FairFace)
Utilizamos o dataset **FairFace**, que contém imagens faciais balanceadas entre 7 grupos raciais/étnicos (White, Black, Indian, East Asian, Southeast Asian, Middle Eastern e Latino). O FairFace mitiga o forte desbalanceamento encontrado na maioria dos datasets canônicos. Para este projeto, utilizamos o recorte facial com margem `0.25` disponibilizado via Hugging Face.

## Como Reproduzir o Ambiente

Para reproduzir este projeto, recomendamos o uso de uma distribuição GNU/Linux (ex: Debian) com um ambiente virtual isolado.

### 1. Configurando o Ambiente e o PyTorch
Clone este repositório e configure o ambiente `venv`:

```bash
git clone [https://github.com/SEU_USUARIO/mitigacao-vies-cnn.git](https://github.com/SEU_USUARIO/mitigacao-vies-cnn.git)
cd mitigacao-vies-cnn

# Crie e ative o ambiente virtual
python3 -m venv fairface_env
source fairface_env/bin/activate

# Instale o PyTorch (Exemplo para CUDA 11.8) e demais dependências
pip install torch torchvision torchaudio --index-url [https://download.pytorch.org/whl/cu118](https://download.pytorch.org/whl/cu118)
pip install numpy pandas matplotlib scikit-learn opencv-python pillow tqdm jupyter datasets huggingface_hub