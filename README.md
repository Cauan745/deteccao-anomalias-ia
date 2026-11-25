# Detecção de Anomalias Visuais com PatchCore

## Sobre o projeto

Projeto acadêmico da disciplina de Inteligência Artificial, **em desenvolvimento**, para detecção de anomalias visuais em imagens industriais do MVTec AD. O problema envolve identificar imagens anômalas e localizar as regiões com defeitos.

O projeto usa a implementação de PatchCore da biblioteca Anomalib como baseline. O objetivo principal é experimentar estratégias de melhoria e comparar quantitativamente seus efeitos no benchmark.

## Objetivo

1. Estabelecer um baseline reproduzível.
2. Experimentar alterações no pipeline ou no modelo.
3. Medir os efeitos de cada alteração.
4. Comparar os resultados com métricas de detecção de imagens e localização de regiões anômalas.

O baseline atual apresenta desempenho próximo do máximo nas métricas em nível de imagem, enquanto as métricas em nível de pixel, especialmente o F1-Score, indicam maior espaço para investigação.

## Dataset

O MVTec AD é um dataset de referência para detecção de anomalias em imagens industriais. Ele contém imagens normais e imagens com defeitos, com anotações para avaliar a localização das anomalias.

O experimento atual utiliza a categoria `bottle`.

## Método baseline

O baseline usa `Patchcore()` da Anomalib, com os parâmetros padrão da versão instalada. A implementação vem da biblioteca e não foi desenvolvida do zero neste projeto.

Em nível alto, o PatchCore utiliza representações extraídas de imagens normais como referência. Durante a avaliação, compara as características das imagens avaliadas com essa referência para identificar padrões diferentes e localizar possíveis anomalias.

## Resultados atuais

Os valores abaixo são **aproximados**, fornecidos como resultados do baseline atual. O notebook não contém saídas de execução salvas que permitam confirmar os valores exatos.

| Métrica | Baseline |
|---|---:|
| Image AUROC | 1.000 |
| Image F1-Score | 0.992 |
| Pixel AUROC | 0.986 |
| Pixel F1-Score | 0.727 |

As métricas de imagem avaliam a detecção de imagens anômalas; as métricas de pixel avaliam a localização das regiões anômalas. Esses resultados serão a referência para os próximos experimentos e não representam resultados finais do projeto.

## Experimentos

Esta tabela será atualizada conforme novos experimentos forem executados. Os valores do baseline são os resultados aproximados informados acima.

| Experimento | Alteração | Image AUROC | Image F1 | Pixel AUROC | Pixel F1 |
|---|---|---:|---:|---:|---:|
| Baseline | PatchCore com parâmetros padrão da biblioteca | 1.000 | 0.992 | 0.986 | 0.727 |

## Tecnologias

- Python
- PyTorch
- Anomalib
- PatchCore
- MVTec AD
- KaggleHub

## Executando

O experimento está disponível em [main.ipynb](main.ipynb) e foi desenvolvido para execução no Google Colab. Execute as células em ordem.

O notebook:

1. instala as dependências;
2. baixa a categoria `bottle` do MVTec AD pelo KaggleHub;
3. configura o `MVTecAD` com base no caminho retornado pelo download;
4. executa a etapa `fit()` do PatchCore para construir o baseline;
5. avalia o modelo com métricas em nível de imagem e pixel.

Principais dependências:

```bash
pip install anomalib
pip install -U kagglehub
```

Ao executar novos experimentos, as configurações e métricas obtidas serão registradas para comparação com o baseline. Atualmente, o notebook não salva esses resultados em um arquivo separado.

## Estrutura do projeto

```text
.
├── README.md
└── main.ipynb
```

O notebook reúne instalação, download do dataset, configuração, construção do baseline e avaliação. Não há datasets, checkpoints ou arquivos de resultados versionados no repositório atual.

## Próximos passos

- Executar novos experimentos.
- Comparar os resultados com o baseline.
- Investigar melhorias principalmente nas métricas em nível de pixel.
- Documentar as configurações, os experimentos e os resultados.
