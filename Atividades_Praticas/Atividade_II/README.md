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

Durante a atividade, foram analisadas situações estáveis e instáveis, incluindo a ocorrência de **overflow numérico**. Também foi estudada a influência dos tipos numéricos `float32` e `float64` e realizada uma comparação entre o perfil de velocidade obtido numericamente e a solução estacionária teórica.

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
* **Parte F — Perfil de velocidade:** comparação entre o perfil final da simulação e a solução estacionária, incluindo o cálculo do erro máximo `E∞`;
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

Inicialmente, o fluido no interior do domínio encontra-se parado. A evolução da velocidade ao longo do tempo é descrita pela equação de difusão:

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

Portanto, o valor de `r` foi utilizado como principal indicador para determinar se cada simulação estava dentro ou fora da condição de estabilidade.

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

A partir desse espaçamento, foi calculado o maior passo de tempo permitido pela condição de estabilidade:

$$
\Delta t_{\max}
=
\frac{\Delta y^2}{2\nu}
$$

Assim:

$$
\Delta t_{\max}
=
\frac{(0{,}0005)^2}{2(10^{-4})}
=
0{,}00125\ s
$$

Foram então analisados dois passos de tempo.

Para:

$$
\Delta t = 0{,}001\ s
$$

tem-se:

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

Para:

$$
\Delta t = 0{,}002\ s
$$

tem-se:

$$
r
=
\frac{(10^{-4})(0{,}002)}
{(0{,}0005)^2}
=
0{,}8
$$

Nesse caso:

$$
0{,}8 > 0{,}5
$$

e, portanto, a simulação é numericamente instável.

---

## ⚠️ Detecção de overflow

Foram realizados testes utilizando os tipos numéricos `float32` e `float64`, com diferentes valores de passo de tempo.

Os resultados mostraram que os casos com `r` dentro do limite de estabilidade conseguiram executar a simulação normalmente, enquanto os casos com `r` acima de `0,5` apresentaram crescimento exagerado dos valores e posteriormente overflow.

O `float32` possui uma capacidade de representação numérica menor que o `float64`. Dessa forma, quando a solução instável cresce rapidamente, o `float32` pode atingir seu limite de representação antes do `float64`.

Entretanto, aumentar a capacidade de representação não elimina a causa do problema. O `float64` apenas consegue representar valores maiores antes de ocorrer o overflow. A instabilidade continua existindo enquanto o passo de tempo estiver fora do limite estabelecido pelo método numérico.

---

## 📊 Interpretação física

Nas simulações estáveis, os valores de velocidade apresentam um comportamento coerente com o problema físico, aproximando-se gradualmente do perfil esperado entre as duas placas.

Já nas simulações instáveis, a velocidade passa a apresentar um crescimento exagerado ao longo do tempo. Esse comportamento não possui significado físico para o problema, pois a velocidade imposta pela placa é de apenas:

$$
U = 1\ m/s
$$

Assim, valores que crescem muito além dessa escala indicam que a solução numérica está se afastando do comportamento físico esperado.

O crescimento exagerado ocorre porque o método explícito está sendo utilizado com um passo de tempo maior do que aquele permitido pela condição de estabilidade. A instabilidade é amplificada a cada iteração até que os valores atinjam a capacidade máxima de representação do tipo numérico, provocando o overflow.

---

## 💻 Capacidade de representação

Também foi realizada uma comparação entre `float32` e `float64`.

O `float32` possui menor capacidade de representação de números muito grandes, enquanto o `float64` consegue representar uma faixa numérica significativamente maior. Por isso, nas simulações instáveis, o `float64` demorou mais passos para atingir o overflow.

Mesmo assim, os dois tipos apresentaram o mesmo problema de estabilidade quando submetidos a um passo de tempo inadequado.

Isso mostra que a escolha do tipo numérico influencia o momento em que o overflow acontece, mas **não corrige a instabilidade numérica**. Para corrigir a causa do problema, foi necessário adequar o passo de tempo à condição de estabilidade do método.

---

## 🔬 Refinamento da malha

Posteriormente, a malha foi refinada de **21 para 41 pontos**.

Com 41 pontos, o novo espaçamento passou a ser:

$$
\Delta y
=
\frac{0{,}01}{41-1}
=
0{,}00025\ m
$$

Como o limite de estabilidade depende do quadrado de $\Delta y$, a redução do espaçamento também reduziu o passo de tempo máximo permitido.

O novo limite foi calculado por:

$$
\Delta t_{\max}
=
\frac{(0{,}00025)^2}
{2(10^{-4})}
=
0{,}0003125\ s
$$

Inicialmente, foi mantido o passo de tempo de:

$$
\Delta t = 0{,}001\ s
$$

Mesmo valor utilizado anteriormente.

Nesse caso:

$$
r
=
\frac{(10^{-4})(0{,}001)}
{(0{,}00025)^2}
\approx
1{,}6
$$

Como esse valor está muito acima do limite de:

$$
r \leq 0{,}5
$$

a simulação tornou-se instável.

Com 41 pontos e $\Delta t=0{,}001\ s$, os resultados obtidos foram:

* `float32`: overflow no **passo 56**, em $t=0{,}056\ s$;
* `float64`: overflow no **passo 426**, em $t=0{,}426\ s$.

Isso mostrou que o refinamento da malha, apesar de aumentar a resolução espacial da simulação, exige também uma redução adequada do passo de tempo.

---

## ✅ Correção da instabilidade

Após identificar que o problema estava relacionado ao passo de tempo, foi realizado um novo teste utilizando:

$$
\Delta t = 0{,}00025\ s
$$

Com 41 pontos, o valor de `r` passou a ser:

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

Nesse novo teste, tanto `float32` quanto `float64` completaram os **2000 passos sem overflow**.

Esse resultado confirma que a principal causa da falha não era o tipo numérico utilizado, mas sim o uso de um passo de tempo incompatível com a malha refinada.

---

## 📈 Perfil de velocidade

Para uma execução estável e suficientemente longa, o perfil final de velocidade foi comparado com a solução estacionária teórica.

A solução estacionária é dada por:

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

a expressão utilizada foi:

$$
u_{\text{est}}(y)
=
1
\left(
1-\frac{y}{0{,}01}
\right)
$$

Essa expressão descreve o perfil de velocidade esperado quando o sistema atinge o **regime estacionário**.

Para comparar o resultado numérico com o perfil estacionário, foi calculado o erro máximo:

$$
E_{\infty}
=
\max_i
\left|
u_i-u_{\text{est}}(y_i)
\right|
$$

Quanto menor o valor de $E_{\infty}$, mais próximo o perfil numérico está da solução estacionária.

É importante considerar que a simulação começa com o fluido parado. Portanto, antes de atingir o perfil estacionário existe um período transiente, no qual a velocidade ainda está evoluindo.

Dessa forma, uma diferença entre o perfil numérico e o perfil estacionário não significa necessariamente um erro do método. Parte dessa diferença pode estar relacionada ao fato de que o tempo total de simulação ainda não foi suficiente para que o transiente fosse completamente concluído.

---

## 📊 Síntese dos resultados

Os resultados obtidos ao longo da atividade mostraram uma relação direta entre o refinamento da malha e a escolha do passo de tempo.

Com 21 pontos, foi obtido:

$$
\Delta y = 0{,}0005\ m
$$

e:

$$
\Delta t_{\max}=0{,}00125\ s
$$

Nesse caso, $\Delta t=0{,}001\ s$ resultou em $r=0{,}4$, mantendo a simulação estável.

Ao utilizar $\Delta t=0{,}002\ s$, o valor passou para $r=0{,}8$, ultrapassando o limite de estabilidade e levando à instabilidade numérica.

Após o refinamento para 41 pontos:

$$
\Delta y = 0{,}00025\ m
$$

e:

$$
\Delta t_{\max}=0{,}0003125\ s
$$

Manter $\Delta t=0{,}001\ s$ nessa nova malha resultou em:

$$
r\approx1{,}6
$$

causando overflow nos testes realizados.

A redução do passo para:

$$
\Delta t=0{,}00025\ s
$$

fez com que:

$$
r\approx0{,}4
$$

e a simulação completasse os 2000 passos sem overflow em ambos os tipos numéricos.

---

## 🧠 Conclusão

A atividade permitiu compreender, na prática, a relação entre o refinamento da malha, o passo de tempo e a estabilidade de um método numérico. Foi possível observar que aumentar a quantidade de pontos da malha melhora a resolução espacial da simulação, mas também faz com que seja necessário utilizar um passo de tempo menor para manter a estabilidade.

Na malha inicial, com 21 pontos, o espaçamento era de $0{,}0005\ m$ e o limite de estabilidade era de $0{,}00125\ s$. Com $\Delta t=0{,}001\ s$, foi obtido $r=0{,}4$, mantendo a simulação estável. Já com $\Delta t=0{,}002\ s$, o valor de $r$ passou para $0{,}8$, ultrapassando o limite de $0{,}5$ e provocando instabilidade.

O refinamento para 41 pontos reduziu o espaçamento para $0{,}00025\ m$ e o limite de estabilidade para $0{,}0003125\ s$. Ao manter $\Delta t=0{,}001\ s$, o valor de $r$ chegou a aproximadamente $1{,}6$, fazendo com que a solução se tornasse instável e os valores crescessem até ocorrer overflow. Nesse teste, o `float32` apresentou overflow no passo 56, enquanto o `float64` apresentou overflow no passo 426. Isso mostrou que o `float64` possui maior capacidade de representação, mas não é capaz de eliminar uma instabilidade causada pelo método.

A alteração que realmente corrigiu a causa da falha foi reduzir o passo de tempo para $\Delta t=0{,}00025\ s$. Com isso, o valor de $r$ passou para aproximadamente $0{,}4$, ficando novamente dentro da condição de estabilidade. Tanto `float32` quanto `float64` conseguiram completar os 2000 passos sem overflow.

Por fim, a comparação com o perfil estacionário mostrou a importância de considerar também o período transiente da simulação. O perfil estacionário representa o comportamento esperado após a evolução do sistema, enquanto a solução numérica acompanha todo o processo desde o fluido inicialmente parado. Assim, a diferença entre os perfis pode incluir o efeito de um transiente ainda não concluído.

## De forma geral, a atividade mostrou que o overflow observado não era a causa do problema, mas uma consequência da instabilidade numérica. A principal correção foi adequar o passo de tempo à nova malha, respeitando a condição $r\leq0{,}5$. Dessa forma, foi possível relacionar os conceitos estudados em Cálculo Numérico com o comportamento observado diretamente em uma simulação computacional.

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
