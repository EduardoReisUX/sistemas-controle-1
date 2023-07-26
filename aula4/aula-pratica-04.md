Sistemas de Controle I, Roteiro da Aula Prática 4, 26 de julho de 2023.

---

Resumo da aula:
Foi realizada a modelagem matemática de um sistema de tanques abertos acoplados e foi feita uma simulação.

**Índice do conteúdo:**

- [Modelagem de Sistemas de tanques acoplados (tanque aberto)](#modelagem-de-sistemas-de-tanques-acoplados-tanque-aberto)
  - [Modelando o Sistema](#modelando-o-sistema)
  - [Montando diagrama de blocos](#montando-diagrama-de-blocos)
  - [Simplificando o diagrama de blocos](#simplificando-o-diagrama-de-blocos)
  - [Simulando no Matlab e Simulink](#simulando-no-matlab-e-simulink)


## Modelagem de Sistemas de tanques acoplados (tanque aberto)

### Modelando o Sistema

TODO: imagem do sistema

- $$ q_{12}(t) = \frac { h_1(t) - h_2(t) } { R_1 } $$

- $$ q_{o}(t) = \frac { h_2(t) - 0 } { R_2 } $$

- $$ C_1[q_i(t) - q_{12}(t)]dt = dh_1(t) $$

- $$ C_2[q_{12}(t) - q_{o}(t)]dt = dh_2(t) $$

Aplicando Transformada de Laplace, teremos:

1. $$ [ H_1(s) - H_2(s) ] \frac { 1 } { R_1 } = Q_{12}(s) $$

2. $$ H_2(s) \frac { 1 } { R_1 } = Q_{o}(s) $$

3. $$ Q_i(s) - Q_{12}(s) = \frac { 1 } { C_1s } Q_{o}(s) $$

4. $$ Q_{12}(s) - Q_o(s) = \frac { 1 } { C_2s } H_2(s) $$

### Montando diagrama de blocos

Analisando todas as equações para montar o diagrama de blocos, e arranjando-os na ordem abaixo, obteremos:

3 -> 4 -> 1 -> 2
<!-- TODO: ou será que era 3 -> 1 -> 4 -> 2 ??? -->


TODO: imagem do diagrama de blocos resultante

### Simplificando o diagrama de blocos

Primeira simplificação do diagrama:

TODO: imagem da primeira simplificação

Segunda simplificação do diagrama:

TODO: imagem da segunda simplificação

Diagrama resultante:

TODO: imagem do resultado

### Simulando no Matlab e Simulink

![Alt text](imgs/simulink.png)

Componentes utilizados:
- Step
- Sum
- Transfer fcn (pode ser gain e integrator)
- Scope

Declarar as variáveis C1, C2, R1, R2.

```Matlab
C1 = 1; C2 = 1; R1 = 1; R2 = 1;
```

Resultado do scope:

![Gráfico do circuito](imgs/scope.png)

TODO: fazer 5 entradas para o scope.