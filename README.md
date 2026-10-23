[README.md](https://github.com/user-attachments/files/33888090/README.md)
# Dossiê de Auditoria – Suzano S.A. – Exercício 2025

Trabalho da P2 de **Auditoria 1 (CCA0024) – Turma 02 – UnB – 2026.2**
Professor: Lucas Oliveira Gomes Ferreira
Preparador: **matrícula 241003769**
Data de conclusão: 23/10/2026

> **Natureza do trabalho.** Trabalho acadêmico. **Não constitui opinião de auditoria** nem qualquer forma de asseguração sobre as demonstrações da Suzano S.A.
>
> - Só foram usadas fontes públicas: DFP na CVM, Formulário de Referência e site de RI.
> - Não houve contato com a Companhia, com seus auditores, clientes ou fornecedores.
> - Confirmações, entrevistas, inspeções e acessos a sistemas **não foram realizados**. Nos PTs eles aparecem como *planejados*.
> - Os dados do imobilizado usados nos testes e na amostragem são **SINTÉTICOS**, marcados com **(SIM)**. Não são registros reais da Companhia.

---

## 1. Conteúdo do repositório

```
/
├── README.md
├── .gitignore
├── dossie/                                      ← dossiê final em PDF
│   └── Dossie_Auditoria_Suzano_2025_241003769.pdf   (capa, sumário, 28 PTs + PT CI)
├── papeis_trabalho/                             ← PTs editáveis (.docx), inclusive capa e sumário
├── base_simulada/                               ← base sintética do imobilizado (SIM)
│   ├── dicionario_variaveis_SIM.xlsx            (dicionário, premissas, conciliação, erros inseridos)
│   ├── gabarito_erros_SIM.csv                   (registro dos 1.600 erros E1–E10)
│   └── LINK_BASE_COMPLETA.txt                   (link do Google Drive para os arquivos grandes)
├── codigo/                                      ← notebooks do Google Colab
│   ├── 01_gerar_base_imobilizado_SIM.ipynb
│   ├── 02_amostragem_AUM_SIM.ipynb
│   └── 03_testes_100_SIM.ipynb
├── planilhas/                                   ← planilhas editáveis
│   ├── PT_320_Materialidade_Bases.xlsx          (A3  – materialidade)
│   ├── PT_330_Testes_Publicos.xlsx              (A3b – testes com dados públicos)
│   ├── PT_530_Amostra_AUM_SIM.xlsx              (A3c – amostragem AUM)
│   ├── PT_500_Testes_100_SIM.xlsx               (A3d – testes em 100% da base)
│   └── PT_520_Analiticos.xlsx                   (A3e – procedimentos analíticos)
└── fontes/
    ├── A4_Matriz_Cobertura.xlsx                 (exigências da P2 → onde foram atendidas; normas × PTs)
    └── A5_Relacao_Fontes.xlsx                   (documentos, links, datas de acesso e páginas)
```

## 2. Papéis de trabalho

| Código | Papel de trabalho | Código | Papel de trabalho |
|---|---|---|---|
| PT EC | Caracterização do trabalho de asseguração | PT 450 | Avaliação das distorções |
| PT 200 | Objetivos gerais do auditor | PT 500 | Evidência de auditoria e conciliações |
| PT 210 | Termos do trabalho | PT 501 | Estoques, litígios e segmentos |
| PT 220 | Gestão da qualidade | PT 505 | Confirmações externas |
| PT 230 | Documentação de auditoria | PT 510 | Saldos iniciais |
| PT 240 | Fraude | PT 520 | Procedimentos analíticos |
| PT 250 | Leis e regulamentos | PT 530 | Amostragem (base SIM) |
| PT 260 | Comunicação com a governança | PT 540 | Estimativas contábeis |
| PT 265 | Deficiências de controle interno | PT 550 | Partes relacionadas |
| PT 300 | Planejamento e programas por ciclo | PT 560 | Eventos subsequentes |
| PT 315 | Identificação e avaliação dos riscos | PT 570 | Continuidade operacional |
| PT 320 | Materialidade | PT 580 | Representações formais |
| PT 330 | Respostas aos riscos | PT 600 | Auditoria de grupo e componentes |
| PT 402 | Organizações prestadoras de serviços | PT CI | Conclusão integrada |

Cada procedimento recebe uma de três classificações:

- **Realizado com evidência pública**
- **Planejado por falta de acesso**
- **Simulado para fins didáticos**

A versão de cada norma consultada (link do CFC e data de acesso) está no campo "Versão consultada" de cada PT e na aba "Normas × PTs" do arquivo A4.

## 3. Base simulada do imobilizado (A1)

- **Conta escolhida:** imobilizado, a maior conta do ativo. O saldo é de R$ 64,3 bi, 38% do ativo consolidado (nota 15 da DFP).
- **Tamanho:** 520.000 bens sintéticos, conciliados por classe com os saldos de custo e de depreciação da nota 15.
- **Erros inseridos:** 1.600 erros de 10 tipos (E1–E10), registrados em `gabarito_erros_SIM.csv`. O erro E10 é custo inflado em R$ 150 mi, espalhado por 400 bens, e só pode ser detectado por amostragem com documento.
- **Arquivos grandes:** a `base_imobilizado_SIM.csv.gz` (~33 MB) e os `documentos_suporte_SIM.csv.gz` (~9 MB) passam do limite de envio pelo site do GitHub (25 MB). Eles estão no Google Drive: **[colar aqui o link do Drive]**.

## 4. Como reproduzir

1. Abra os notebooks da pasta `codigo/` no Google Colab, na ordem 01 → 02 → 03.
2. **01_gerar_base_imobilizado_SIM:** gera a base, os documentos de suporte e o gabarito. A semente fixa é **42**, então a base sai sempre igual.
3. **02_amostragem_AUM_SIM:** faz a amostragem por unidade monetária (AUM) com semente **2025**. Parâmetros:
   - risco de detecção (RD) de 10%;
   - fator de confiança (FC) de 2,31;
   - fator de expansão (FEE) de 1,50;
   - fatores incrementais exatos (qui-quadrado, `scipy`).
   
   Gera `PT_530_Amostra_AUM_SIM.xlsx`.
4. **03_testes_100_SIM:** concilia a base com a nota 15 e roda os testes T01–T09 em 100% dos bens. Gera `PT_500_Testes_100_SIM.xlsx`.
5. Os notebooks 02 e 03 leem os arquivos `.csv.gz` gerados pelo 01. Se você não rodar o 01, baixe esses arquivos do Google Drive e coloque-os na mesma pasta do notebook.

**Resultados esperados do notebook 02:**
- início aleatório de R$ 45.846.506,65;
- 1.394 pontos de seleção, correspondentes a 1.371 bens (46 no estrato superior);
- 7 exceções;
- distorção projetada de R$ 126.799,2 mil;
- limite superior de distorção (LSD) de R$ 291.198,3 mil.

**Versões testadas:**
- Google Colab: Python 3, numpy 2.1.3, pandas 2.2.3.
- Ambiente local: numpy 2.5.3, pandas 3.0.5, scipy 1.18.1, openpyxl 3.1.5.

Os resultados são idênticos nos dois ambientes. Uma diferença de comportamento entre as versões do pandas (cópia × visão de colunas) foi corrigida com `.copy()` e está registrada nas limitações do PT 530.

## 5. Principais fontes

- **DFP 31/12/2025, versão 1 – CVM/RAD** (acesso em 19 e 20/10/2026):
  https://www.rad.cvm.gov.br/ENETWEB/frmGerenciaPaginaFRE.aspx?NumeroSequencialDocumento=154674&CodigoTipoInstituicao=1
- **Formulário de Referência 2026, versão 5 – RI Suzano** (acesso em 22/10/2026):
  https://ri.suzano.com.br/Portuguese/Arquivamentos/Documentos-entregues-a-CVM/default.aspx
- **Normas Brasileiras de Contabilidade – Auditoria (NBC TA):** textos do CFC. Os links de cada norma estão em `fontes/A5_Relacao_Fontes.xlsx`.
- **GRAMLING, A. A.; RITTENBERG, L. E.; JOHNSTONE, K. M.** *Auditoria*. Cengage, 2016, p. 298–302. Usado como referência da AUM.
