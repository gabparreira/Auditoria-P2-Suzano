# Base simulada – Imobilizado da Suzano S.A. (31/12/2025)

**DADOS SINTÉTICOS** – trabalho acadêmico (Auditoria 1 – UnB, 2026.2).
Não representam registros reais da Suzano S.A.
Preparador: matrícula 241003769.

## Arquivos

| Arquivo | Conteúdo | Onde está |
|---|---|---|
| base_imobilizado_SIM.csv.gz | 520.000 bens do imobilizado, 25 colunas (33 MB) | [Google Drive](https://drive.google.com/drive/folders/1p7NR_u1c9nT5k-saTwRS_wPm-irc_mN2?usp=sharing) – acima do limite do GitHub |
| documentos_suporte_SIM.csv.gz | Documentos suporte simulados (nota fiscal) de cada bem | Nesta pasta e no [Google Drive](https://drive.google.com/drive/folders/1p7NR_u1c9nT5k-saTwRS_wPm-irc_mN2?usp=sharing)  |
| gabarito_erros_SIM.csv | 1.600 erros inseridos de propósito (E1 a E10) | Nesta pasta |
| dicionario_variaveis_SIM.xlsx | Dicionário, premissas, conciliação e resumo dos erros | Nesta pasta |

## Como reproduzir a base

1. Abra o codigo/01_gerar_base_imobilizado_SIM.ipynb` no Google Colab.
2. Rode os blocos 1 a 8, em ordem.
3. A semente fixa (42) garante que a base gerada é idêntica à do link.

Formato: CSV compactado (gzip), separador `;`, decimal `,`, UTF-8.
Saldos de referência: nota 15 da DFP 2025 (consolidado).
