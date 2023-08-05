Sistemas de Controle I, Roteiro da Aula Prática 1, 05 de julho de 2023.

---

**Sumário**

- [Manipulação de matrizes](#manipulação-de-matrizes)
  - [Criando e selecionando valores de uma matriz 4x5.](#criando-e-selecionando-valores-de-uma-matriz-4x5)
  - [Matrizes Especiais](#matrizes-especiais)
    - [Matriz Identidade 3x3](#matriz-identidade-3x3)
    - [Matriz Nula 3x3](#matriz-nula-3x3)
    - [Matriz 3x3 de Um](#matriz-3x3-de-um)
    - [Matriz 3x3 de 2](#matriz-3x3-de-2)
    - [Matriz Linha de 4 a 18 com incremento de 2](#matriz-linha-de-4-a-18-com-incremento-de-2)
    - [*Matriz Coluna* da matriz anterior ou *Matriz Transposta*](#matriz-coluna-da-matriz-anterior-ou-matriz-transposta)
    - [Limpar tela e variáveis](#limpar-tela-e-variáveis)
- [Geração de gráficos](#geração-de-gráficos)
  - [Gráfico de x1 e x2  em função de t, com título, rótulos e legendas](#gráfico-de-x1-e-x2--em-função-de-t-com-título-rótulos-e-legendas)
  - [Gráfico de x1 e x2  em função de t, com subplots.](#gráfico-de-x1-e-x2--em-função-de-t-com-subplots)
  - [Algumas funções para estatística](#algumas-funções-para-estatística)
- [Exemplos de Algoritmo](#exemplos-de-algoritmo)
  - [Fibonacci](#fibonacci)
  - [Desafio - Pares e Ímpares](#desafio---pares-e-ímpares)

## Manipulação de matrizes

### Criando e selecionando valores de uma matriz 4x5.
```matlab
>> a = [1 2 3 4 5; 10 11 12 13 14; 26 27 28 29 30; 100 101 106 107 110]
>> a(2:4, 3)
>> a(3, 2:4)
>> a(2, 3:4)
>> a(end-1, end)
>> clc % limpa o terminal
>> clear all % limpa as variáveis
```
### Matrizes Especiais

#### Matriz Identidade 3x3 
```matlab
>> b = eye(3)
```

#### Matriz Nula 3x3 
```matlab
>> c = zeros(3, 3)
```
#### Matriz 3x3 de Um
```matlab
>> d = ones(3, 3)
```

#### Matriz 3x3 de 2
```matlab
>> e = 2 * ones(3, 3)
```

#### Matriz Linha de 4 a 18 com incremento de 2
```matlab
>> f = 4:2:18
```

####  *Matriz Coluna* da matriz anterior ou *Matriz Transposta* 
```matlab
>> g = f'
```

#### Limpar tela e variáveis
```matlab
>>clc
>>clear all
```

## Geração de gráficos

### Gráfico de x1 e x2  em função de t, com título, rótulos e legendas

```matlab
% Aula Apresentação do MatLab

% Fechar figuras que estiverem abertas
close all

% Apagar qualquer tipo de variável
clear all

% Limpar o terminal
clc

% Criando vetor de tempo de 0 até 10 s, step de 0.1 
t = 0:0.1:10;

x1 = 0.5 * t - 0.5;
x2 = 0.75 * t - 1.25;

% Criando figura 1: gráfico de x1 e x2 por t
figure(1)

% Exibindo figura 1
% 'g' = variável x1 será desenhada com linha reta verde
% 'r' = variável x2 será desenhada com linha _. vermelha
plot(t, x1, 'g', t, x2, 'r')

% Título do gráfico
title("Curva de Resposta da Temperatura de ...")

% Rótulo do eixo x
xlabel('Tempo [s]')

% Rótulo do eixo y
ylabel('Temperatura [ºC]')

% Legendas
legend('Resposta do Sistema', 'Resposta do Modelo')

% Para conseguir se virar no MatLab
% help <função>
help plot
```

### Gráfico de x1 e x2  em função de t, com subplots.

```matlab
% Com sub-plots

close all
clear all
clc

t = 0:0.1:10;
x1 = 0.5 * t - 0.5;
x2 = 0.75 * t - 1.25;
figure(1)

% Fazer 3x2 plots de gráficos, este é o primeiro gráfico
subplot(3,2,1)
plot(t, x1, 'g', t, x2, 'r-.')

title("Curva de Resposta da Temperatura de ...")
xlabel('Tempo [s]')
ylabel('Temperatura [ºC]')
legend('Resposta do Sistema', 'Resposta do Modelo')

subplot(3,2,2)
stem(x1)

subplot(3,2,3)
stem(x2)

subplot(3,2,4)
stem(randi(100, 10, 1))

subplot(3,2,5)
stem(randi(100, 10, 1))

subplot(3,2,6)
stem(randi(100, 10, 1))
```

### Algumas funções para estatística
```matlab
% Funções estatísticas

% 10 números aleatórios de 0 a 100
a = randi(100, 10, 1)

% Número máximo
[v, p] = max(a)

% Ordernar em ordem crescente
b = sort(a)

% Ordernar em ordem decrescente
c = sort(a, 'descend')

% Média Aritmética
mean(a)

% Desvio Padrão
std(a)
```
## Exemplos de Algoritmo

### Fibonacci

```matlab
% Algoritmo Fibonacci

clear all
clc

fibo = [1 1];

% tamanho da série
n = 10;

% For loop - variável i incrementa de 3 até n
for i = 3:n
    fibo(i) = fibo(i-2) + fibo(i-1)
end

% Exibir resultado
fibo
```
  
### Desafio - Pares e Ímpares

```matlab
% Desafio

% Dado um vetor = [1, 3, 6, 8, 15];
% Dizer os componentes pares e ímpares deste vetor
% Saída: par = 6 8; impar = 1 3 15

vetor = [1, 3, 6, 8, 15];
pares = [];
impares = [];

contagem_par = 0;
contagem_impar = 0;

tamanho_vetor = 5;

for i = 1:tamanho_vetor
	resto = mod(vetor(i), 2)
	if (resto == 0)
		contagem_par = contagem_par + 1;
		pares(contagem_par) = vetor(i);
	else
		contagem_impar = contagem_impar + 1;
		impares(contagem_impar) = vetor(i);
	end
end

pares
impares
```
