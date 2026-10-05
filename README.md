# Segundo-Cérebro: Demografia de Primatas e Estimativa de Densidade
> **Comparação metodológica de modelos de densidade populacional para primatas gregários na Mata Atlântica**

# Segundo-C-rebro-

---

## 📌 Visão Geral

Este repositório documenta a construção e a validação de um "Segundo Cérebro" científico para apoiar a análise demográfica de primatas neotropicais em paisagens fragmentadas da Mata Atlântica. O foco principal é comparar métodos de estimativa de densidade populacional ($\hat{D}$) e abundância total ($\hat{N}$) com base em dados de transectos lineares, comportamento de detecção e exigências espaciais de grupos sociais.

O projeto adota uma abordagem rigorosa e metodologicamente conservadora, comparando três paradigmas:

1. **Amostragem por distância (Distance Sampling)**
2. **Método de faixa fixa de Kelker**
3. **Modelo ecológico espacial baseado em área de vida (home range)**

A finalidade é demonstrar que a extrapolação direta da densidade observada em transectos para grandes áreas florestais pode superestimar populações se não forem incorporadas as premissas de detecção e as restrições espaciais biológicas da espécie.

---

## 🎯 Objetivo do Projeto

> *"Comportar-se como o segundo cérebro de um cientista de dados e ecólogo especializado em demografia de primatas da Floresta Atlântica, com o objetivo de analisar, comparar e validar metodologias de estimativa de densidade populacional e abundância utilizando modelagem por distância, amostragem por faixa fixa e capacidade de suporte espacial baseada em área de vida."*

O estudo busca responder a uma questão central:

- Como estimar densidade e abundância de primatas gregários de forma biologicamente defensável, considerando detecção variável ao longo do transecto, viés de observação e uso do espaço?

---

## 📚 Fontes e Fundamentação Científica

Para garantir rigor metodológico, o conjunto de referências foi selecionado com base em literatura acadêmica consagrada, publicações revisadas por pares e manuais institucionais reconhecidos.

1. **Buckland et al. (1993) — Distance Sampling: Estimating Abundance of Biological Populations**
   - Base teórica da amostragem por distância e da modelagem da probabilidade de detecção.
2. **Thomas et al. (2010) — Distance software: design and analysis of distance sampling surveys**
   - Descreve os motores de análise do software Distance (CDS, MCDS, DSM) e as premissas estatísticas de ajuste.
3. **National Research Council — Primate Population Ecology / Kelker Method Manual**
   - Referência técnica para ajustes por faixa fixa e censo de primatas em campo.
4. **Marshall et al. (2008) — Selection of Line-Transect Methods for Estimating the Density of Group-Living Primates**
   - Comparação crítica de viés, sensibilidade e adequação de métodos para primatas arbóreos gregários.
5. **Artigos de monitoramento demográfico na Floresta Atlântica**
   - Fornecem parâmetros empíricos relevantes para espécies de primatas neotropicais e estruturas sociais reais.

> **Nota ética e de privacidade:** os dados públicos utilizados no contexto do projeto foram anonimizados e não incluem informações pessoais identificáveis. Nenhuma informação de indivíduos ou locais sensíveis foi incorporada ao repositório público.

---

## ⚙️ Diretriz de Comportamento (Prompt de Sistema)

A lógica do "Segundo Cérebro" foi definida com um comportamento científico estritamente amarrado às fontes disponíveis:

```text
Comporte-se como um segundo cérebro científico rigoroso. Responda estritamente
com base nas fontes fornecidas no notebook. Identifique premissas estatísticas,
compare limitações de cada modelo (Distance vs. Kelker vs. Home Range) e nunca
extrapole ou invente dados fora do contexto das fontes.
```

Essa diretriz evita inferências não sustentadas e garante que as estimativas sejam interpretadas como modelos de suporte analítico e não como verdades absolutas.

---

## 🔬 Paradigmas Metodológicos

### 1. Amostragem por Distância (Distance Sampling)

O método de distância assume que a probabilidade de detecção decai com a distância perpendicular da linha de transecto. A ideia central é estimar a função de detecção $g(x)$ e a largura efetiva do transecto, ou ESW (Effective Strip Width), a partir dos registros de campo.

$$
\hat{D}_{\text{grupos}} = \frac{n \cdot f(0)}{2 \cdot L}
$$

Onde:
- $n$ = número de grupos observados
- $L$ = esforço total de amostragem
- $f(0)$ = valor da função de detecção em zero distância
- $\text{ESW}$ = largura efetiva do transecto

**Vantagens:**
- considera que a detecção diminui com a distância;
- permite ajustar funções como Half-Normal e Hazard-Rate;
- costuma ser robusto para dados longitudinais quando as premissas são atendidas.

**Limitações:**
- sensível a observações extremas em grandes distâncias;
- depende de uma boa modelagem da função de detecção;
- pode superestimar densidade quando a visibilidade varia fortemente ao longo do transecto.

---

### 2. Método de Faixa Fixa de Kelker

O método de Kelker trata a visibilidade como limitada por uma distância crítica $w_k$, dentro da qual a detecção é assumida como perfeita, isto é, $g(x) = 1.0$. A partir desse ponto, os registros mais distantes são truncados.

$$
\hat{D}_{\text{grupos}} = \frac{n_w}{2 \cdot L \cdot w_k}
$$

Onde:
- $n_w$ = número de grupos detectados dentro da faixa crítica
- $w_k$ = semi-largura de visibilidade crítica

**Vantagens:**
- reduz o efeito de outliers de distância;
- estabiliza a variância quando a visibilidade é altamente heterogênea;
- costuma produzir densidades mais conservadoras em paisagens densas.

**Limitações:**
- descarta registros além da faixa definida;
- exige número suficiente de observações na zona de detecção completa;
- pode ser demasiado rígido se a visibilidade real não for bem representada por $w_k$.

---

### 3. Modelo Ecológico Espacial com Área de Vida (Home Range)

A extrapolação direta de transectos para grandes áreas florestais pode ignorar que os grupos ocupam o espaço de forma heterogênea. A área de vida média por grupo ($A_{\text{home\_range}}$) permite transformar densidade local em capacidade de suporte ecológico da paisagem.

$$
\hat{N}_{\text{grupos}} = \frac{A_{\text{total}}}{A_{\text{home\_range}}}
$$

$$
\hat{N}_{\text{ind}} = \hat{N}_{\text{grupos}} \times s
$$

Onde:
- $A_{\text{total}}$ = área total de habitat contínuo disponível
- $A_{\text{home\_range}}$ = área média de uso por grupo
- $s$ = tamanho médio ou máximo do grupo

**Vantagens:**
- incorpora restrições ecológicas reais do uso do espaço;
- distingue densidade bruta de densidade ecológica;
- melhora a interpretação de abundância em paisagens fragmentadas.

**Limitações:**
- depende de estimativas confiáveis de área de vida e tamanho de grupo;
- pode ser sensível à qualidade do mapeamento do habitat;
- não substitui a amostragem de campo, mas contextualiza a estimativa final.

---

## 🧭 Fluxo Analítico Comparativo

Os dados de campo em transectos lineares podem ser processados por três vias complementares:

```text
Dados de campo
   │
   ├──► 1. Distance Sampling ─────► Detecção g(x) ─────► Densidade bruta
   │
   ├──► 2. Kelker Method ─────────► Faixa crítica w_k ─► Densidade ajustada
   │
   └──► 3. Home Range Model ─────► Capacidade espacial ─► Abundância ecológica
```

A interpretação correta do resultado depende da pergunta de pesquisa:
- se o objetivo for estimar densidade local a partir de transectos, o método de distância é central;
- se a preocupação for viés por detecção em cobertura heterogênea, Kelker é um filtro útil;
- se o objetivo for estimar capacidade real da paisagem, a área de vida é crítica.

---

## 💬 Perguntas-chave e respostas sintetizadas

### Pergunta 1: De que maneira o software Distance auxilia na modelagem e estimativa de abundância?
**Resposta:** O software ajuste funções matemáticas à distribuição das distâncias perpendiculares para estimar a probabilidade de detecção $g(x)$, a largura efetiva de amostragem (ESW) e a densidade correspondente. Ele compara modelos como Half-Normal, Hazard-Rate e variantes com covariáveis, selecionando o ajuste com melhor suporte estatístico, geralmente por AIC e coeficiente de variação.

**Fontes relevantes:** Buckland et al. (1993); Thomas et al. (2010).

---

### Pergunta 2: Como o Método de Kelker ajusta superestimativas em transectos lineares?
**Resposta:** O método de Kelker restringe a estimativa a uma distância crítica de visibilidade em que a detecção é tratada como completa. Isso elimina registros muito distantes e potencialmente discrepantes, reduzindo o viés de superestimativa e tornando a densidade mais conservadora e estável.

**Fontes relevantes:** National Research Council; Marshall et al. (2008).

---

### Pergunta 3: Como incorporar a área de vida para obter uma estimativa biologicamente realista?
**Resposta:** Ao relacionar a área disponível da floresta com a área média usada por cada grupo social, é possível estimar quantos grupos a paisagem consegue sustentar. Esse ajuste transforma uma densidade local em uma estimativa ecológica mais defensável, respeitando a organização espacial e social da espécie.

**Fontes relevantes:** National Research Council; estudos de ecologia demográfica de primatas neotropicais.

---

## 🗂️ Estrutura de Dados Recomendada

Para análise em ambiente de pesquisa ou automação, os dados de campo devem seguir uma estrutura mínima e consistente:

| Coluna | Camada | Descrição | Unidade |
| :--- | :--- | :--- | :--- |
| `Stratum` | Global / estrato | Fragmento florestal ou unidade de gestão | Texto |
| `Sample_ID` | Transecto | Identificador único do transecto | Texto |
| `Line_Length` | Transecto | Comprimento total percorrido | km ou m |
| `Obs_ID` | Observação | Identificador do registro | Numérico |
| `Distance` | Observação | Distância perpendicular do grupo à linha | metros |
| `Group_Size` | Observação | Número de indivíduos no grupo | Contagem |

> O objetivo dessa estrutura é permitir o uso de modelos de detecção e cálculo de densidade com comparabilidade entre amostras.

---

## ✅ Conclusões Principais

1. **A estimativa de densidade não deve ser extraída de maneira mecânica do número de avistamentos.**
2. **O ajuste de distância e o truncamento por faixa crítica oferecem ferramentas importantes para reduzir viés de detecção.**
3. **A área de vida é indispensável para transformar uma densidade observada em uma estimativa ecológica plausível.**
4. **A combinação de métodos estatísticos e ecológicos é mais defensável do que qualquer abordagem isolada.**

---

## 📜 Licença e Uso

Este framework foi desenvolvido para fins de pesquisa ecológica, demografia de populações e planejamento de conservação de primatas neotropicais. O projeto deve ser interpretado como documento metodológico e de apoio analítico, e não como substituto da avaliação local de especialistas ou do protocolo de estudo específico da área.

