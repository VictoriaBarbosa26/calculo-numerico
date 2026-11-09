 <div align="center">

# 📘 Aula — Decomposição de Cholesky

### 📐 Cálculo Numérico

<img src="./gi_cholesky.gif" width="600px">

<br>

👩‍🎓 **Victoria Barbosa**  
🏫 **Turma: NB**  
🎓 **Bacharelado em Ciência e Tecnologia — UNIFESP**

</div>

---

## 📖 Sobre a aula

Nesta aula, foi estudada a **Decomposição de Cholesky**, um método numérico direto utilizado para resolver sistemas de equações lineares cuja matriz dos coeficientes é simétrica e definida positiva.

Por meio de explicações teóricas, demonstrações matemáticas, exemplos e implementações utilizando **Python e Google Colab**, pude compreender como fatorar uma matriz quadrada em duas matrizes triangulares, de modo que a matriz original seja representada pelo produto de uma matriz triangular inferior por sua transposta.

Também foram analisadas as condições necessárias para aplicar o método, com destaque para a simetria da matriz e o critério de Sylvester, utilizado para verificar se ela é definida positiva.

Por fim, foi realizada a resolução de um sistema linear utilizando substituições progressiva e regressiva, além da verificação dos resultados por meio da reconstrução da matriz e do cálculo do resíduo.

---

## 🎯 Objetivos da aula

* 🧮 Compreender o conceito de decomposição de Cholesky;
* 📐 Identificar matrizes simétricas;
* 🔎 Compreender o conceito de matriz definida positiva;
* 📊 Aplicar o critério de Sylvester por meio dos menores principais;
* 🧩 Compreender a fatoração de uma matriz na forma \(A = LL^T\);
* 🔢 Construir a matriz triangular inferior \(L\);
* ➗ Calcular os elementos da matriz utilizando raízes quadradas e operações algébricas;
* 🔁 Resolver sistemas por substituição progressiva e regressiva;
* 🎯 Verificar a fatoração por meio do produto \(LL^T\);
* 📉 Calcular e interpretar o resíduo da solução;
* 💻 Implementar e verificar a decomposição utilizando Python e NumPy.

---

## 📚 Conteúdos estudados

Durante a aula, foram trabalhados:

* 🧮 **Decomposição de Cholesky e suas aplicações;**
* 📐 **Matrizes simétricas e a condição \(A = A^T\);**
* 🔎 **Matrizes definidas positivas;**
* 📊 **Critério de Sylvester e cálculo dos menores principais;**
* 🧩 **Fatoração \(A = LL^T\);**
* 🔢 **Construção dos elementos da matriz triangular inferior \(L\);**
* ➗ **Cálculo dos elementos diagonais e não diagonais;**
* ⚠️ **Condições para a existência da fatoração;**
* 🔁 **Substituição progressiva para resolver \(Ly = b\);**
* 📈 **Substituição regressiva para resolver \(L^Tx = y\);**
* 🎯 **Reconstrução da matriz e verificação da fatoração;**
* 📉 **Cálculo do resíduo \(r = b - Ax\);**
* 💻 **Implementação computacional utilizando Python e NumPy.**

---

## 💻 Atividades

A aula contou com exemplos guiados e uma atividade prática envolvendo a aplicação da decomposição de Cholesky na resolução de um sistema de equações lineares.

Inicialmente, foi analisada uma matriz para verificar sua simetria e definir se ela era positiva definida, utilizando o critério de Sylvester e o cálculo dos menores principais.

Em seguida, foi realizada a fatoração da matriz na forma \(A = LL^T\), determinando os elementos da matriz triangular inferior \(L\) por meio de cálculos algébricos.

Após a fatoração, o sistema foi resolvido em duas etapas: primeiro, pela substituição progressiva para encontrar o vetor intermediário \(y\); depois, pela substituição regressiva para determinar o vetor solução \(x\).

Por fim, os resultados foram conferidos por meio da reconstrução da matriz original, da comparação dos valores obtidos e do cálculo do resíduo. Também foi utilizada a biblioteca NumPy para implementar a decomposição e verificar computacionalmente a solução encontrada.

---

## 📓 Google Colab

O desenvolvimento completo da aula, incluindo os códigos, exemplos, demonstrações matemáticas, atividade prática, cálculos e resultados, está disponível no Google Colab:

🔗 **[Abrir Aula — Decomposição de Cholesky](https://colab.research.google.com/drive/1MHlNhMizT38UX28lF2COJd7mSWdK5msH?usp=sharing)**

---

## 📄 Relatório

O relatório apresenta os conteúdos estudados, as condições de aplicação da decomposição de Cholesky, o desenvolvimento da fatoração, a resolução do sistema linear, as verificações realizadas e as conclusões obtidas durante a aula.

📄 **[Abrir relatório da Aula Cholesky](./Relatorio_Aula_Cholesky.pdf)**

---

## 📂 Arquivos da aula

* 📄 **README.md** — informações e organização da aula;
* 📄 **Relatorio_Aula_Cholesky.pdf** — relatório da aula;
* 📓 **Google Colab** — códigos, exemplos, demonstrações matemáticas, atividades práticas e resultados desenvolvidos durante a aula;
* 🎞️ **gif_cholesky.gif** — representação visual relacionada ao conteúdo da aula.

---

<div align="center">

### 📐 Cálculo Numérico

**Aula — Decomposição de Cholesky**

<br>

🔗 **[⬅️ Voltar ao repositório principal](https://github.com/VictoriaBarbosa26/calculo-numerico/blob/main/README.md)**

</div>
