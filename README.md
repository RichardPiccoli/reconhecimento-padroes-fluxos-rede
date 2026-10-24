# Reconhecimento de Padrões em Fluxos de Rede Através de Aprendizado Não Supervisionado

**Autor:** Richard Nozari Cassol Lahm Piccoli — outubro de 2026

Detecção de anomalias em tráfego de rede combinando redução de dimensionalidade
(PCA via SVD truncado) e clusterização (K-Means), avaliada no dataset UNSW-NB15.

Duas pontuações de anomalia são comparadas:

1. **Erro de reconstrução** — distância de cada conexão à sua projeção no subespaço dos k componentes principais.
2. **Distância ao centróide** — distância de cada conexão ao centróide do seu cluster K-Means no espaço reduzido.

Uma conexão é marcada como anômala quando a pontuação passa de um limiar percentílico (90, 95 ou 99).
As configurações (dimensão do PCA × número de clusters × limiar) são comparadas por Precision, Recall e F1.

## Conteúdo

| Arquivo | Descrição |
|---|---|
| `reconhecimento_padroes_fluxos_rede.ipynb` | Notebook completo, já executado (com gráficos) |
| `data/UNSW_NB15_training-set.csv` | Partição de treino do UNSW-NB15 (175.341 conexões) |
| `tabela_experimentos.csv` | Tabela gerada pelo notebook com as métricas de todas as configurações |
| `requirements.txt` | Dependências Python |

## Como executar

**Localmente**

```bash
pip install -r requirements.txt
jupyter notebook reconhecimento_padroes_fluxos_rede.ipynb
```

**No Google Colab:** abra o notebook e faça upload de `data/UNSW_NB15_training-set.csv`
para `/content` (ou clone o repositório e rode a partir da pasta dele).

O notebook procura o dataset em `data/` e em `/content/`; se não encontrar, ele para com um erro
em vez de seguir com dados de outro tipo.

## Dataset

UNSW-NB15 — Australian Centre for Cyber Security (ACCS), UNSW Canberra.
Fonte oficial: <https://research.unsw.edu.au/projects/unsw-nb15-dataset>

> Moustafa, N.; Slay, J. *UNSW-NB15: a comprehensive data set for network intrusion detection
> systems (UNSW-NB15 network data set).* Military Communications and Information Systems
> Conference (MilCIS), 2015.

Observação: no download oficial os arquivos `training-set` e `testing-set` vêm com os nomes
trocados. A partição de treino é a que tem **175.341** linhas (o notebook confere isso).
