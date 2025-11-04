# 📊 Análise - Bundesliga 22/23 (Power BI)

<img width="1392" height="781" alt="Pag1" src="https://github.com/user-attachments/assets/e1fefb04-8b8d-478d-bc1b-9f01db43d705" />

<img width="1392" height="781" alt="Pag2" src="https://github.com/user-attachments/assets/6c79ff4d-2ea8-4543-84df-15ff96aa6760" />

<br>
<br>

Este repositório apresenta um relatório interativo desenvolvido no **Power BI** com uma análise detalhada da temporada **2022/2023 da Bundesliga** — a principal liga de futebol da Alemanha.
O projeto permite explorar informações sobre **jogadores, empresários, nacionalidades, patrocinadores e estatísticas gerais** da competição.



## 🧠 Objetivo do Projeto

O relatório foi criado com o intuito de:

* Analisar o **perfil dos atletas** da Bundesliga 22/23;
* Identificar **principais empresários e agências** que representam os jogadores;
* Observar a **distribuição geográfica** das nacionalidades dos atletas;
* Avaliar **patrocínios esportivos** e **valores de mercado**;
* Fornecer uma visão geral sobre idade média, altura e tempo de permanência nos clubes.



## 🧩 Estrutura do Relatório

O dashboard é dividido em **duas páginas principais**:

### 📄 Página 1 — Dados Gerais dos Jogadores

Inclui:

* 💰 **Soma do valor de mercado total:** $4,33 bilhões
* 👤 **Média de idade:** 25,68 anos
* 📏 **Altura média:** 1,85 m
* ⏳ **Tempo médio de permanência no clube:** 2,9 anos
* ⚽ **Pé preferido:** distribuição entre destros, canhotos e ambidestros
* 💎 **Jogadores mais valiosos** da temporada (ex: Bellingham, Musiala, Wirtz etc.)

📊 **Gráfico Dinâmico com Parâmetro DAX:**
Foi adicionado um **parâmetro personalizado** que permite alternar entre diferentes métricas no mesmo gráfico de barras, de forma interativa.
O usuário pode escolher entre visualizar:

* Média de Idade por Posição
* Média de Valor por Posição
* Média de Tempo de Permanência por Posição
* Média de Altura por Posição

Essa funcionalidade foi criada via **DAX**, com uma tabela de parâmetros manual e uma medida dinâmica que altera o cálculo conforme a seleção feita no painel.



### 🌍 Página 2 — Empresários, Nacionalidades e Patrocínios

Inclui:

* 🧑‍💼 **Empresários e agências mais atuantes** (ex: Roof, Sports360 GmbH, Relatives, etc.)
* 🗺️ **Mapa interativo** com a **distribuição das nacionalidades** dos jogadores
* 👟 **Principais marcas patrocinadoras de atletas:** Adidas, Nike, Puma, Uhlsport e Under Armour



## ⚙️ Recurso Destacado: Parâmetro DAX

O recurso de **parâmetro DAX** foi implementado manualmente através das seguintes etapas:

```DAX
Tabela_Metrica =
DATATABLE(
    "Métrica", STRING,
    {
        {"Média de Idade"},
        {"Média de Valor"},
        {"Média de Tempo"},
        {"Média de Altura"}
    }
)

Métrica Selecionada =
VAR Selecionada = SELECTEDVALUE(Tabela_Metrica[Métrica])
RETURN
SWITCH(
    TRUE(),
    Selecionada = "Média de Idade", AVERAGE('bundesliga_player'[Idade]),
    Selecionada = "Média de Valor", AVERAGE('bundesliga_player'[Preço Atual]),
    Selecionada = "Média de Tempo", AVERAGE('bundesliga_player'[Tempo de Permanência]),
    Selecionada = "Média de Altura", AVERAGE('bundesliga_player'[Altura])
)
```

Essa abordagem permite que **um único gráfico** mude de comportamento conforme a **métrica selecionada pelo usuário**, sem necessidade de múltiplos visuais.



## 🛠️ Ferramentas Utilizadas

* **Power BI Desktop** – Criação e modelagem do relatório
* **Microsoft Bing Maps** – Visualização geográfica de nacionalidades
* **Excel / CSV** – Fonte de dados utilizada (valores de mercado e informações dos jogadores)
* **DAX & Power Query** – Cálculos, parâmetros e transformações de dados




## 📈 Insights Interessantes

* A **Adidas** é a marca mais presente entre os jogadores (82 atletas patrocinados).
* O **pé direito** é amplamente dominante (≈70% dos jogadores).
* A média de idade mais alta é entre **goleiros (27,16 anos)**.
* Os **empresários Roof e Sports360 GmbH** representam grande parte dos atletas da liga.


