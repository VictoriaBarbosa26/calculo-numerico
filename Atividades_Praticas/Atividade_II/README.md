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

A **Atividade Prática II** foi desenvolvida na disciplina de **Cálculo Numérico**, com o objetivo de estudar a estabilidade de métodos numéricos e analisar os efeitos do passo de tempo, do refinamento da malha e da precisão computacional em uma simulação de difusão de velocidade.

A atividade utiliza um modelo simplificado de escoamento entre duas placas paralelas. Uma das placas se movimenta com velocidade constante, enquanto a outra permanece fixa. A evolução da velocidade do fluido é simulada numericamente por meio da equação de difusão.

Durante a atividade, foram analisadas situações estáveis e instáveis, incluindo a ocorrência de **overflow numérico**. Também foi estudada a influência dos tipos numéricos `float32` e `float64` e realizada uma comparação entre o perfil de velocidade obtido numericamente e o perfil estacionário teórico.

---

## 🎯 Objetivos da atividade

* 🧮 Calcular o espaçamento da malha e o limite de estabilidade;
* ⏱️ Analisar a influência do passo de tempo na estabilidade da simulação;
* 📊 Calcular e interpretar o número de estabilidade `r`;
* 💻 Comparar os tipos numéricos `float32` e `float64`;
* ⚠️ Identificar e analisar a ocorrência de overflow;
* 📈 Observar o comportamento da solução em uma simulação instável;
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
* **Parte F — Perfil de velocidade:** comparação entre o perfil final da simulação e a solução estacionária, incluindo o cálculo do erro máximo $E_{\infty}$;
* **Parte G — Conclusão:** relação entre refinamento da malha, passo de tempo, instabilidade numérica e overflow.

---

## 📐 Modelo físico

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

Inicialmente, o fluido no interior do domínio encontra-se parado.

A evolução da velocidade ao longo do tempo é descrita pela equação de difusão:

$$
\frac{\partial u}{\partial t}
=
\nu
\frac{\partial^2 u}{\partial y^2}
$$

Para resolver numericamente o problema, foi utilizado o método de **Euler explícito no tempo** combinado com **diferenças finitas centrais no espaço**.

A atualização da velocidade no interior da malha é dada por:

$$
u_i^{n+1}
=
u_i^n
+
r
\left(
u_{i+1}^n
-
2u_i^n
+
u_{i-1}^n
\right)
$$

em que:

$$
r
=
\frac{\nu\Delta t}{\Delta y^2}
$$

Para o método utilizado, a condição de estabilidade é:

$$
r \leq \frac{1}{2}
$$

---

## 🔢 Verificação da estabilidade

Inicialmente foram utilizados **21 pontos** na malha.

O espaçamento entre os pontos foi calculado por:

$$
\Delta y
=
\frac{H}{N-1}
$$

Substituindo os valores:

$$
\Delta y
=
\frac{0{,}01}{21-1}
=
0{,}0005\ m
$$

O maior passo de tempo permitido pela condição de estabilidade é dado por:

$$
\Delta t_{\max}
=
\frac{\Delta y^2}{2\nu}
$$

Assim:

$$
\Delta t_{\max}
=
\frac{(0{,}0005)^2}
{2(10^{-4})}
=
0{,}00125\ s
$$

### Teste com $\Delta t = 0{,}001\ s$

O número de estabilidade é:

$$
r
=
\frac{(10^{-4})(0{,}001)}
{(0{,}0005)^2}
=
0{,}4
$$

Como:

$$
0{,}4 < 0{,}5
$$

a simulação está dentro da condição de estabilidade.

### Teste com $\Delta t = 0{,}002\ s$

Nesse caso:

$$
r
=
\frac{(10^{-4})(0{,}002)}
{(0{,}0005)^2}
=
0{,}8
$$

Como:

$$
0{,}8 > 0{,}5
$$

a simulação é numericamente instável.

---

## ⚠️ Detecção de overflow

Foram realizados testes utilizando os tipos numéricos `float32` e `float64`, com diferentes valores de passo de tempo.

Nos casos em que o número de estabilidade estava dentro do limite, a simulação conseguiu executar normalmente.

Já nos casos em que:

$$
r > 0{,}5
$$

a solução apresentou crescimento exagerado dos valores e posteriormente ocorreu **overflow numérico**.

O `float32` possui uma capacidade de representação numérica menor que o `float64`. Dessa forma, em uma simulação instável, o `float32` pode atingir seu limite de representação antes do `float64`.

Entretanto, o uso de `float64` não corrige a instabilidade. Ele apenas permite representar valores maiores antes que o overflow aconteça.

---

## 📊 Interpretação física

Nas simulações estáveis, os valores de velocidade apresentam um comportamento coerente com o problema físico, evoluindo gradualmente a partir da condição inicial.

A velocidade da placa móvel é:

$$
U = 1\ m/s
$$

Portanto, valores que crescem muito além dessa escala durante uma simulação indicam um comportamento numérico inadequado.

Nas simulações instáveis, pequenos erros numéricos são amplificados a cada iteração. Como consequência, os valores da velocidade crescem rapidamente até atingir a capacidade máxima de representação do tipo numérico.

Esse comportamento caracteriza uma **instabilidade numérica**, e não um fenômeno físico do escoamento.

---

## 💻 Capacidade de representação

Também foi realizada uma comparação entre `float32` e `float64`.

O `float32` possui uma faixa de representação menor, enquanto o `float64` consegue representar números muito maiores.

Por isso, nos testes instáveis, o `float64` demorou mais passos para atingir o overflow.

Mesmo assim, os dois tipos apresentaram o mesmo problema quando o passo de tempo estava fora da condição de estabilidade.

Isso demonstra que aumentar a precisão numérica não elimina uma instabilidade causada pelo método. Para corrigir o problema, é necessário adequar o passo de tempo à malha utilizada.

---

## 🔬 Refinamento da malha

Posteriormente, a malha foi refinada de **21 para 41 pontos**.

Com 41 pontos, o novo espaçamento foi calculado por:

$$
\Delta y
=
\frac{0{,}01}{41-1}
=
0{,}00025\ m
$$

O novo limite de estabilidade é:

$$
\Delta t_{\max}
=
\frac{\Delta y^2}{2\nu}
$$

Substituindo os valores:

$$
\Delta t_{\max}
=
\frac{(0{,}00025)^2}
{2(10^{-4})}
=
0{,}0003125\ s
$$

Inicialmente, foi mantido o passo de tempo utilizado anteriormente:

$$
\Delta t = 0{,}001\ s
$$

Nesse caso:

$$
r
=
\frac{(10^{-4})(0{,}001)}
{(0{,}00025)^2}
=
1{,}6
$$

Como:

$$
1{,}6 > 0{,}5
$$

a simulação tornou-se instável.

Os resultados obtidos foram:

| Tipo numérico | Passo de tempo | $r$ | Resultado             |
| ------------- | -------------: | --: | --------------------- |
| `float32`     |        0,001 s | 1,6 | Overflow no passo 56  |
| `float64`     |        0,001 s | 1,6 | Overflow no passo 426 |

Para o `float32`, o overflow ocorreu no tempo:

$$
t = 0{,}056\ s
$$

Para o `float64`, o overflow ocorreu no tempo:

$$
t = 0{,}426\ s
$$

Esses resultados mostram que o refinamento da malha exige uma redução adequada do passo de tempo.

---

## ✅ Correção da instabilidade

Após identificar que o problema estava relacionado ao passo de tempo, foi realizado um novo teste utilizando:

$$
\Delta t = 0{,}00025\ s
$$

Com 41 pontos, o número de estabilidade passou a ser:

$$
r
=
\frac{(10^{-4})(0{,}00025)}
{(0{,}00025)^2}
=
0{,}4
$$

Como:

$$
0{,}4 < 0{,}5
$$

a simulação voltou a atender à condição de estabilidade.

Nesse teste, tanto `float32` quanto `float64` completaram **2000 passos sem overflow**.

---

## 📈 Perfil de velocidade

Para analisar o comportamento final da simulação, foi utilizado o caso estável com:

$$
\Delta t = 0{,}00025\ s
$$

e:

$$
N = 41
$$

A solução estacionária teórica para o perfil de velocidade é:

$$
u_{\text{est}}(y)
=
U
\left(
1-\frac{y}{H}
\right)
$$

Com:

$$
U = 1\ m/s
$$

e:

$$
H = 0{,}01\ m
$$

obtém-se:

$$
u_{\text{est}}(y)
=
1
\left(
1-\frac{y}{0{,}01}
\right)
$$

O perfil numérico foi então comparado com o perfil estacionário teórico.

---

## 📏 Erro máximo

Para quantificar a diferença entre os dois perfis, foi utilizado o erro máximo:

$$
E_{\infty}
=
\max_i
\left|
u_i-u_{\text{est}}(y_i)
\right|
$$

O valor de $E_{\infty}$ foi calculado diretamente no notebook do Google Colab.

Além do valor numérico do erro, foi gerado um gráfico comparando:

* o **perfil numérico** obtido pela simulação;
* o **perfil estacionário teórico**.

A comparação permite observar visualmente o quanto a solução numérica se aproxima da solução esperada.

Como a simulação começa com o fluido inicialmente parado, existe um período transiente antes que o sistema atinja completamente o regime estacionário.

---

## 📊 Síntese dos resultados

Os principais resultados obtidos foram:

| Configuração | $\Delta y$ (m) | $\Delta t$ (s) | $r$ | Resultado |
| ------------ | -------------: | -------------: | --: | --------- |
| 21 pontos    |         0,0005 |          0,001 | 0,4 | Estável   |
| 21 pontos    |         0,0005 |          0,002 | 0,8 | Instável  |
| 41 pontos    |        0,00025 |          0,001 | 1,6 | Instável  |
| 41 pontos    |        0,00025 |        0,00025 | 0,4 | Estável   |

Com 21 pontos:

$$
\Delta t_{\max}=0{,}00125\ s
$$

Com 41 pontos:

$$
\Delta t_{\max}=0{,}0003125\ s
$$

Portanto, o refinamento da malha reduziu o passo de tempo máximo permitido.

---

## 🧠 Conclusão

A atividade permitiu compreender, na prática, a relação entre o refinamento da malha, o passo de tempo e a estabilidade de um método numérico.

Na malha inicial, com 21 pontos, o espaçamento era:

$$
\Delta y=0{,}0005\ m
$$

e o limite de estabilidade era:

$$
\Delta t_{\max}=0{,}00125\ s
$$

Com $\Delta t=0{,}001\ s$, foi obtido:

$$
r=0{,}4
$$

mantendo a simulação estável.

Quando o passo de tempo foi aumentado para:

$$
\Delta t=0{,}002\ s
$$

o número de estabilidade passou para:

$$
r=0{,}8
$$

ultrapassando o limite de $0{,}5$ e provocando instabilidade.

Após o refinamento da malha para 41 pontos, o espaçamento passou a ser:

$$
\Delta y=0{,}00025\ m
$$

e o limite de estabilidade foi reduzido para:

$$
\Delta t_{\max}=0{,}0003125\ s
$$

Ao manter $\Delta t=0{,}001\ s$, o valor de $r$ passou para aproximadamente:

$$
r=1{,}6
$$

causando overflow nos testes realizados.

O `float32` apresentou overflow no passo 56, enquanto o `float64` apresentou overflow no passo 426. Isso mostrou que o `float64` possui maior capacidade de representação, mas não elimina a instabilidade causada por um passo de tempo inadequado.

A redução do passo para:

$$
\Delta t=0{,}00025\ s
$$

fez com que:

$$
r=0{,}4
$$

e permitiu que tanto `float32` quanto `float64` completassem os 2000 passos sem overflow.

Por fim, o perfil numérico foi comparado com o perfil estacionário teórico. Essa comparação também permitiu observar a influência do período transiente, já que a simulação começa com o fluido parado e evolui gradualmente em direção ao comportamento estacionário.

De forma geral, a atividade mostrou que o **overflow é uma consequência da instabilidade numérica**, e não a causa do problema. A principal forma de corrigir a instabilidade foi adequar o passo de tempo ao espaçamento da malha, respeitando a condição:

$$
r\leq\frac{1}{2}
$$

---

## 💻 Atividade no Google Colab

O desenvolvimento completo da atividade, incluindo os códigos, cálculos, tabelas, gráficos e respostas, está disponível no notebook:

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
* 📓 **Atividade_Prática_II.ipynb** — notebook contendo os códigos, cálculos, tabelas, gráficos e respostas.

---

<div align="center">

### 📐 Cálculo Numérico

**Atividade Prática II**

<br>

🔗 **[⬅️ Voltar à seção de atividades](../README.md)**

</div>
