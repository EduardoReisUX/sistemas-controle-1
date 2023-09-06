Sistemas de Controle I, Roteiro da Aula Prática 10, 06 de setembro de 2023.

---

**Resumo da aula**

Foi feito diversas simulações de respostas de um sistema de segunda ordem para que pudessemos verificar a influência do posicionamento dos polos.

Também foram feitas implementações para verificar o fenômeno da dominância de polos.

**Sumário**

TODO

## Posicionamento dos polos

### Código MATLAB

```MATLAB
close all
clear all
clc

% Análise da resposta em relação posicionamento dos polos

t = 0 : 0.01 : 10;

% FIGURA 1 ----------------------

ga = tf(1, [ 1 1 ]); gb = tf(1, [ 1 2 ]); % ga tem polo no origem: instável
g1 = tf( 1, [ 1 1 0 ] ); 

ga = tf(1, [ 1 1 ]); gb = tf(1, [ 1 2 ]);  % gb tem polo positivo, fator de amortecimento < 0, instável
g2 = tf( 1, [ 1 0 -1 ] );

ga = tf(1, [ 1 1 ]); gb = tf(1, [ 1 2 ]); % polos iguais, fator de amortecimento = 1, críticamente amortecido
g3 = tf( 1, [ 1 2 1 ] );

ga = tf(1, [ 1 1 ]); gb = tf(1, [ 1 2 ]); % fator de amortecimento maior que 1, super amortecido
g4 = series(ga, gb);

ga = tf(2, [ 1 1 ]); gb = tf(1, [ 1 2 ]); % fator de amortecimento maior que 1, super amortecido
g5 = series(ga, gb);

ga = tf(1, [ 1 1+j ]); gb = tf(1, [ 1 1-j ]); % fator de amortecimento entre 0 e 1, sub amortecido
g6 = series(ga, gb);

ga = tf(1, [ 1 1+j*2 ]); gb = tf(1, [ 1 1-j*2 ]); % aumentando a parte imaginária, aumenta o máximo de pico
g7 = series(ga, gb);

ga = tf(1, [ 1 2+j ]); gb = tf(1, [ 1 2-j ]); % aumentando a parte real, aumenta o amortecimento
g8 = series(ga, gb);

[y1, x1] = step(g1, t);
[y2, x2] = step(g2, t);
[y3, x3] = step(g3, t);
[y4, x4] = step(g4, t);
[y5, x5] = step(g5, t);
[y6, x6] = step(g6, t);
[y7, x7] = step(g7, t);
[y8, x8] = step(g8, t);

figure(1)

lin = 2;
col = 4; 

subplot(lin, col, 1)
plot(x1, y1)

subplot(lin, col, 2)
plot(x2, y2)

subplot(lin, col, 3)
plot(x3, y3)

subplot(lin, col, 4)
plot(x4, y4)

subplot(lin, col, 5)
plot(x5, y5)

subplot(lin, col, 6)
plot(x6, y6)

subplot(lin, col, 7)
plot(x7, y7)

subplot(lin, col, 8)
plot(x8, y8)
```

### Resultado

![Resultado em relação ao posicionamento dos polos](imgs/resultado-1.png)

TODO: descrever cada resposta 

## Dominancia de Polos

### Código MATLAB

```MATLAB
ga = tf(1, [ 1 1 ]); gb = tf(1, [ 1 1 ]);
g1 = series(ga, gb); 

gc = tf(1, [ 1 1 ]); gd = tf(1, [ 1 2 ]);
g2 = series(gc, gd); 

ge = tf(1, [ 1 1+j ]); gf = tf(1, [ 1 1-j ]);
g3 = series(ge, gf); 

gg = tf(1, [ 1 1+j*2 ]); gh = tf(1, [ 1 1-j*2 ]);
g4 = series(gg, gh);

gi = tf(1, [ 1 1+j+2 ]); gj = tf(1, [ 1 1-j+2 ]);
g5 = series(gi, gj);

gk = tf(1, [ 1 1 ]); gl = tf(1, [ 1 5 ]);
g6 = series(gk, gl);

gm = tf(1, [ 1 1 ]); gn = tf(1, [ 1 10 ]);
g7 = series(gm, gn);

[ya, xa] = step(ga, t);
[yb, xb] = step(gb, t);
[y1, x1] = step(g1, t);

[yc, xc] = step(gc, t);
[yd, xd] = step(gd, t);
[y2, x2] = step(g2, t);

[ye, xe] = step(ge, t);
[yf, xf] = step(gf, t);
[y3, x3] = step(g3, t);

[yg, xg] = step(gg, t);
[yh, xh] = step(gh, t);
[y4, x4] = step(g4, t);

[yi, xi] = step(gi, t);
[yj, xj] = step(gj, t);
[y5, x5] = step(g5, t);

[yk, xk] = step(gk, t);
[yl, xl] = step(gl, t);
[y6, x6] = step(g6, t);

[ym, xm] = step(gm, t);
[yn, xn] = step(gn, t);
[y7, x7] = step(g7, t);

% [y8, x8] = step(g8, t);

figure(2)

lin = 2;
col = 4; 

subplot(lin, col, 1)
plot(x1, y1, xa, ya, xb, yb)

subplot(lin, col, 2)
plot(x2, y2, xc, yc, xd, yd)

subplot(lin, col, 3)
plot(x3, y3, xe, ye, xf, yf)

subplot(lin, col, 4)
plot(x4, y4, xg, yg, xh, yh)

subplot(lin, col, 5)
plot(x5, y5, xi, yi, xj, yj)

subplot(lin, col, 6)
plot(x6, y6, xk, yk, xl, yl)

subplot(lin, col, 7)
plot(x7, y7, xm, ym, xn, yn)
```

### Resultado

![Resultado em relação à dominância dos polos](imgs/resultado-2.png)