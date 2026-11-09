<div align="center">

# 🔄 Aula — Método SOR (Sobre-Relaxação Sucessiva)

### 📐 Cálculo Numérico

<img src="./calculo_numerico.gif" width="600px">

<br>

👩‍🎓 **Victoria Barbosa**  
🏫 **Turma: NB**  
🎓 **Bacharelado em Ciência e Tecnologia — UNIFESP**

</div>

---

## 📖 Sobre a aula

Nesta aula, foi estudado o **método SOR (Sobre-Relaxação Sucessiva)**, uma extensão do método de Gauss-Seidel utilizada para resolver sistemas de equações lineares por meio de aproximações sucessivas.

Por meio de explicações teóricas, exemplos e atividades utilizando **Python e Google Colab**, pude compreender como o parâmetro de relaxação influencia o comportamento das iterações, a velocidade de convergência e a precisão das soluções obtidas.

Também foram analisadas as condições que favorecem a convergência, os critérios de parada e a influência de diferentes tolerâncias e características das matrizes no desempenho do método.

---

## 🎯 Objetivos da aula

* 🔄 Compreender o funcionamento do método SOR;
* 🧮 Revisar o método de Gauss-Seidel e sua relação com o SOR;
* ⚙️ Compreender a função do parâmetro de relaxação ω;
* 📉 Diferenciar sub-relaxação, Gauss-Seidel e sobre-relaxação;
* 📐 Identificar condições que favorecem a convergência;
* 🔍 Analisar diagonal dominante e matriz simétrica definida positiva;
* 📏 Compreender os critérios de parada, erro e resíduo;
* 📊 Comparar a convergência utilizando diferentes valores de ω;
* 🎯 Avaliar a influência das tolerâncias numéricas;
* 💻 Implementar e aplicar o método utilizando Python.

---

## 📚 Conteúdos estudados

Durante a aula, foram trabalhados:

* 🔄 **Método de Gauss-Seidel e sua revisão**;
* ⚙️ **Método SOR — Sobre-Relaxação Sucessiva**;
* 📐 **Parâmetro de relaxação ω**;
* 📉 **Sub-relaxação, relaxação padrão e sobre-relaxação**;
* 📊 **Condições de convergência**;
* 🧮 **Matrizes diagonalmente dominantes**;
* 🔍 **Matrizes simétricas definidas positivas**;
* 📐 **Critério de Sylvester**;
* 📏 **Critérios de parada e tolerância numérica**;
* 🎯 **Diferença entre aproximações consecutivas**;
* 📉 **Resíduo de um sistema linear**;
* 📈 **Histórico e gráficos de convergência**;
* 💻 **Implementação do algoritmo SOR em Python**;
* 🧪 **Comparação entre diferentes parâmetros e sistemas lineares**.

---

## 💻 Atividades

A aula contou com atividades práticas envolvendo a implementação do método SOR, a realização de iterações manuais e a comparação de diferentes configurações do algoritmo.

Entre os exercícios desenvolvidos, foram realizadas a primeira iteração manual do método, a comparação entre diferentes valores do parâmetro ω e a análise da influência de tolerâncias de 10⁻⁴, 10⁻⁸ e 10⁻¹² na quantidade de iterações e na precisão dos resultados.

Também foram construídos gráficos para acompanhar a redução dos resíduos e comparar o comportamento da convergência entre diferentes parâmetros de relaxação.

Nos desafios extras, foram resolvidos dois sistemas lineares: um representando uma rede de quatro nós e outro com coeficientes e incógnitas em escalas diferentes. As matrizes foram analisadas quanto à diagonal dominante, e as soluções aproximadas foram comparadas com valores de referência obtidos por meio da função `numpy.linalg.solve`.

Os experimentos permitiram observar que o desempenho do método depende das características de cada sistema e da escolha adequada do parâmetro de relaxação.

---

## 📓 Google Colab

O desenvolvimento completo da aula, incluindo os códigos, explicações, cálculos, respostas, resultados e atividades práticas, está disponível no Google Colab:

🔗 **[Abrir Aula — Método SOR no Google Colab](https://colab.research.google.com/drive/1orZmwz6z3lFO4ds69qoN32hb2Mt_Bu9J?usp=sharing)**

---

## 📄 Relatório

O relatório apresenta os conteúdos estudados, a fundamentação teórica do método SOR, sua implementação computacional, a análise dos experimentos e as conclusões obtidas durante a aula.

📄 **[Abrir relatório da Aula — Método SOR](./Relatorio_Aula_SOR.pdf)**

---

## 📂 Arquivos da aula

* 📄 **README.md** — informações e organização da aula;
* 📄 **Relatorio_Aula_SOR.pdf** — relatório da aula;
* 📓 **Google Colab** — códigos, explicações, atividades e resultados desenvolvidos durante a aula.

---

<div align="center">

### 📐 Cálculo Numérico

**Aula — Método SOR (Sobre-Relaxação Sucessiva)**

<br>

🔗 **[⬅️ Voltar ao repositório principal](https://github.com/VictoriaBarbosa26/calculo-numerico/blob/main/README.md)**

</div>
