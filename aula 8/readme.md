Sistemas de Controle I, Roteiro da Aula Prática 7, 16 de agosto de 2023.

---

**Resumo da aula**

TODO: colocar descrição

**Sumário**

## Análise de Resposta em Regime Permanente de Sistemas de 1ª Ordem.

Ao analisar o diagrama em blocos do sistema de controle apresentado na Figura 1, temos que:

R(s) --> $\frac{ k }{ \tau s + 1 }$ --> Y(s)

$$ G(s) = \frac{ k }{ \tau s + 1 } = \frac{ \frac{k}{\tau} }{ s + \frac{1}{\tau} } $$

Portanto, para R(s) = 1 / s (degrau unitário):

$$ y(t) = \frac{k}{\tau} \cdot e^{- \frac{1}{\tau}  t} $$

De onde:

$$ y(t \to \infty) = \lim_{s \to 0} s \cdot R(s) G(s) $$

Logo:

$$ y(\infty) = \lim_{s \to 0} s \cdot \frac{ 1 }{ s } \cdot \frac{ k }{ \tau s + 1 } = \frac{ k }{ 1 } = k $$

Em malha fechada, teremos:

TODO: img do diagrama de blocos

Deste modo:

TODO: img do diagrama de blocos

Em que Kp é o ganho proporcional, o qual pode ser um amplificador operacional ou um registro de memória dentro do controlador.

$$ y(\infty) = \lim_{s \to 0} s \cdot \frac{ 1 }{ s } \cdot \frac{ k_p \cdot k }{ \tau s + (1 + k_p \cdot k) } $$

$$ y(\infty) = \lim_{s \to 0} \frac{ k_p \cdot k }{ \tau s + (1 + k_p \cdot k) } = \frac{ k_p \cdot k }{ 1 + k_p \cdot k } $$

Agora vejamos, substituindo o controlador proporcional com integral:

TODO: img do diagrama de blocos

$$ y(\infty) = \lim_{s \to 0} s \cdot \frac{ 1 }{ s } \cdot \frac{ k_p \cdot k } { s (1 + k_p \cdot k) + k } $$

## Simulink

TODO: descrição do que foi feito

TODO: imagem dos circuitos

TODO: resultado de algumas simulações