<div align="center">

# 📘 Atividade Prática II

### 📐 Cálculo Numérico

<img src="./calculo_numerico.gif" width="600px">

<br>

👩‍🎓 **Victoria Barbosa**
🏫 **Turma: NB**
🎓 **Bacharelado em Ciência e Tecnologia — UNIFESP**

</div>

---

## 📖 Sobre a atividade

A **Atividade Prática II** foi desenvolvida na disciplina de **Cálculo Numérico**, com o objetivo de estudar a estabilidade de métodos numéricos e os efeitos do passo de tempo, do refinamento da malha e da precisão computacional em uma simulação de difusão de velocidade.

A atividade utiliza um modelo simplificado de escoamento entre duas placas paralelas. Uma das placas se movimenta com velocidade constante, enquanto a outra permanece fixa. A evolução da velocidade do fluido é simulada numericamente por meio da equação de difusão.

Durante a atividade, foram analisadas situações estáveis e instáveis, incluindo a ocorrência de **overflow numérico**. Também foi estudada a influência do tipo numérico utilizado (`float32` e `float64`) e realizada uma comparação entre o perfil numérico obtido e a solução estacionária teórica.

---

## 🎯 Objetivos da atividade

* 🧮 Calcular o espaçamento da malha e o limite de estabilidade;
* ⏱️ Analisar a influência do passo de tempo na estabilidade da simulação;
* 📊 Calcular e interpretar o número de estabilidade `r`;
* 💻 Comparar os tipos numéricos `float32` e `float64`;
* ⚠️ Identificar e analisar a ocorrência de overflow;
* 📈 Observar o crescimento da solução em uma simulação instável;
* 🔬 Investigar os efeitos do refinamento da malha;
* 📐 Comparar o perfil numérico com o perfil estacionário teórico;
* 📏 Calcular o erro máximo em relação à solução estacionária;
* 🧠 Relacionar estabilidade numérica, passo de tempo, malha e precisão computacional.

---

## 📚 Partes da atividade

A atividade foi organizada nas seguintes etapas:

* **Parte A — Verificação da estabilidade:** cálculo de `Δy`, `Δt_max` e `r` para diferentes passos de tempo;
* **Parte B — Detecção de overflow:** realização de testes utilizando `float32` e `float64` e identificação das condições de falha;
* **Parte C — Interpretação física:** análise do crescimento da velocidade nas simulações instáveis e comparação com o comportamento fisicamente esperado;
* **Parte D — Capacidade de representação:** comparação entre `float32` e `float64` e análise da influência da precisão computacional;
* **Parte E — Refinamento da malha:** utilização de 41 pontos, cálculo do novo limite de estabilidade e repetição dos testes com diferentes passos de tempo;
* **Parte F — Perfil de velocidade:** comparação entre o perfil final da simulação e a solução estacionária, incluindo o cálculo do erro máximo `E∞`;
* **Parte G — Conclusão:** relação entre refinamento da malha, passo de tempo, instabilidade numérica e overflow.

---

## 📐 Modelo utilizado

A simulação considera duas placas paralelas separadas por uma distância:

$$
H = 0{,}01\ m
$$

A viscosidade cinemática do fluido é:

$$
\nu = 10^{-4}\ m^2/s
$$

A placa inferior possui velocidade:

$$
U = 1\ m/s
$$

enquanto a placa superior permanece fixa.

A evolução da velocidade é descrita pela equação de difusão:

$$
\frac{\partial u}{\partial t}
=
\nu
\frac{\partial^2u}{\partial y^2}
$$

Para a discretização, foi utilizado o método de **Euler explícito no tempo** combinado com **diferenças finitas centrais no espaço**.

O critério de estabilidade utilizado foi:

$$
r=
\frac{\nu\Delta t}{\Delta y^2}
\leq
\frac{1}{2}
$$

Esse critério foi fundamental para interpretar os resultados obtidos durante a atividade.

---

## 🔬 Refinamento da malha

Inicialmente foram utilizados **21 pontos**, resultando em:

$$
\Delta y =
\frac{0{,}01}{21-1}
=
0{,}0005\ m
$$

e em um limite de estabilidade de:

$$
\Delta t_{\max}
=
0{,}00125\ s
$$

Posteriormente, a malha foi refinada para **41 pontos**. Nesse caso:

$$
\Delta y =
\frac{0{,}01}{41-1}
=
0{,}00025\ m
$$

e o novo limite passou a ser:

$$
\Delta t_{\max}
=
0{,}0003125\ s
$$

Com a malha refinada, manter o passo de tempo de `0,001 s` resultou em:

$$
r \approx 1{,}6
$$

ultrapassando o limite de estabilidade. Ao reduzir o passo para `0,00025 s`, foi obtido:

$$
r \approx 0{,}4
$$

fazendo com que a simulação retornasse à condição estável.

---

## ⚠️ Resultados dos testes

Na malha refinada com 41 pontos e `Δt = 0,001 s`, foram observadas falhas numéricas:

* `float32`: overflow no **passo 56**, em `t = 0,056 s`;
* `float64`: overflow no **passo 426**, em `t = 0,426 s`.

A diferença entre os dois resultados está relacionada à capacidade de representação de cada tipo numérico. O `float64` consegue representar números maiores que o `float32`, mas isso não elimina a instabilidade causada por um passo de tempo inadequado.

Ao utilizar `Δt = 0,00025 s`, o valor de `r` passou para aproximadamente `0,4`. Nessa condição, tanto `float32` quanto `float64` completaram os **2000 passos sem overflow**.

---

## 📊 Perfil estacionário

Para verificar o comportamento final da simulação, o perfil numérico foi comparado com a solução estacionária:

$$
u_{\text{est}}(y)
=
U
\left(
1-\frac{y}{H}
\right)
$$

Essa expressão representa o perfil esperado quando o sistema atinge o regime estacionário.

Também foi calculado o erro máximo:

$$
E_{\infty}
=
\max_i
\left|
u_i-u_{\text{est}}(y_i)
\right|
$$

A comparação permite avaliar o quanto o perfil obtido numericamente se aproxima da solução estacionária. Como a simulação começa com o fluido parado, existe um período transiente antes que o perfil se aproxime completamente do estado estacionário.

---

## 💻 Atividade no Google Colab

O desenvolvimento completo da atividade, incluindo os códigos, cálculos, tabelas, gráficos e demais resultados, está disponível no notebook:

📓 **[Abrir Atividade Prática II no Google Colab](https://colab.research.google.com/drive/18yWrEJ38cWS3zCPaYS2tOY6JQ5-lDM5T?usp=sharing)**

---

## 🛠️ Ferramentas utilizadas

* 🐍 **Python** — desenvolvimento da simulação e dos cálculos numéricos;
* 📓 **Google Colab** — execução dos códigos e análise dos resultados;
* 🔢 **NumPy** — operações numéricas e manipulação dos dados;
* 📊 **Matplotlib** — geração dos gráficos e visualização dos resultados.

---

## 📂 Arquivos da atividade

* 📄 **README.md** — informações e organização da atividade;
* 📓 **Atividade_Prática_II.ipynb** — notebook contendo os códigos, cálculos, tabelas, gráficos e respostas;
* 📄 **Relatório_Atividade_II.pdf** — relatório da atividade, caso solicitado.

---

<div align="center">

### 📐 Cálculo Numérico

**Atividade Prática II**

<br>

🔗 **[⬅️ Voltar à seção de atividades](../README.md)**

</div>

