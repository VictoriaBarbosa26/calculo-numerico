 <div align="center">

# 📘 Atividade Prática III

### 📐 Cálculo Numérico

<img src="./calculo_numerico.gif" width="600px">

<br>

👩‍🎓 **Integrantes:** David Renato Silva Geraldi, Felipe Yuta Ueno e Victoria Antonia Brito Barbosa  
🏫 **Turma: NB**  
🎓 **Bacharelado em Ciência e Tecnologia — UNIFESP**

</div>

---

## 📖 Sobre a atividade

A **Atividade Prática III** foi desenvolvida em trio na disciplina de **Cálculo Numérico**, com foco no estudo e na implementação de três métodos numéricos para encontrar raízes de funções: **método da bisseção, método de Newton e método da secante**.

Por meio de implementações em Python, foram analisados o funcionamento de cada método, suas aproximações sucessivas e os critérios utilizados para determinar a convergência dos resultados.

A atividade também envolveu a comparação dos resultados obtidos, a organização de uma tabela e a criação de animações em GIF para representar visualmente o comportamento dos métodos.

---

## 🎯 Objetivos da atividade

* 🧮 Compreender o funcionamento dos métodos da bisseção, de Newton e da secante;
* 📐 Implementar os três métodos utilizando Python;
* 🔎 Analisar as aproximações sucessivas na busca por raízes;
* 📊 Comparar os resultados obtidos pelos diferentes métodos;
* 🎯 Aplicar critérios de parada baseados na diferença entre aproximações e no resíduo;
* ⚠️ Identificar situações de falha durante as iterações;
* 🔁 Compreender as condições necessárias para a convergência;
* 📈 Organizar os resultados em uma tabela comparativa;
* 🎞️ Desenvolver animações em GIF para visualizar o comportamento dos métodos.

---

## 📚 Métodos estudados

A atividade abordou os seguintes métodos:

* **Método da Bisseção:** utiliza um intervalo que contém uma raiz e realiza sucessivas divisões ao meio para aproximar sua localização;
* **Método de Newton:** utiliza a derivada da função para calcular novas aproximações a partir de um ponto inicial;
* **Método da Secante:** utiliza duas aproximações anteriores para estimar a raiz, sem exigir o cálculo explícito da derivada.

---

## 🎯 Critérios de parada

Em todos os métodos, foi adotado um critério de convergência que exige o atendimento simultâneo de duas condições:

* 📏 **Diferença entre aproximações sucessivas:** a diferença entre dois valores consecutivos deve ser menor que a tolerância definida;
* 📉 **Resíduo:** o valor absoluto da função na nova aproximação também deve ser menor que a tolerância.

Na bisseção, a diferença entre aproximações corresponde à metade do comprimento do intervalo atual.

Também foram implementadas condições de interrupção para situações em que o método não pode continuar adequadamente, como ausência de mudança de sinal no intervalo da bisseção, derivada próxima de zero no método de Newton, denominador próximo de zero na secante, valores não finitos ou limite máximo de iterações atingido.

---

## 📐 Atividade no Mathcha

A elaboração e organização da atividade estão disponíveis no Mathcha:

🔗 **[Abrir Atividade Prática III no Mathcha](https://www.mathcha.io/editor/nkkWxh7QSeWtPWpV9wsN0qQ1zUKW0BXsE8WEpk)**

---

## 📓 Atividade no Google Colab

O notebook completo, contendo as implementações, aplicações, tabela de resultados e animações, está disponível no Google Colab:

🔗 **[Abrir Atividade Prática III no Google Colab](https://colab.research.google.com/drive/1VJxYoJcu0_V5JBlrzxgTKCmfz2WOL2lG)**

---

## 🛠️ Ferramentas utilizadas

* 🐍 **Python** — implementação dos métodos numéricos;
* 📓 **Google Colab** — desenvolvimento e execução do notebook;
* 📊 **Bibliotecas matemáticas e gráficas** — cálculos, análise e visualização dos resultados;
* 🎞️ **GIF** — representação animada dos métodos.

---

## 📂 Arquivos da atividade

* 📄 **README.md** — informações e organização da atividade;
* 📐 **Mathcha** — elaboração e apresentação do trabalho;
* 📓 **Notebook Google Colab** — implementações, aplicações, tabela de resultados e animações.

---

<div align="center">

### 📐 Cálculo Numérico

**Atividade Prática III — Métodos da Bisseção, de Newton e da Secante**

<br>

🔗 **[⬅️ Voltar à seção de atividades](../README.md)**

</div>
