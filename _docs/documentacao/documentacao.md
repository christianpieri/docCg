---
layout: doc
title: Documentação do sistema   
id: documentacao_do_sistema
parent: documentacao
---


# 1. Com relação ao trabalho realizado

A disciplina INE5425 (Modelagem e Simulação), ministrada pelo professor Paulo Freitas na Universidade Federal de Santa Catarina (UFSC), teve como primeiro projeto do semestre 2017.1 um simulador em linguagem de propósito geral sobre “O andar do bêbado”.

## 1.1 Introdução

Neste trabalho, pedia-se para desenvolver uma aplicação de Monte Carlo que faria um cálculo de um **caminho aleatório** qualquer, simulando os passos de um bêbado. A analogia criada é justamente esta: verificar a distância percorrida por um sujeito bêbado.

## 1.2 Teoria

Foram passadas algumas fórmulas e parâmetros para simular o andar de um bêbado:

- O bêbado encontra-se em um plano;
- Ele pode dar um passo para qualquer direção (qualquer ângulo α) de 0 a 360 graus;
- Deve-se tomar em questão que o bêbado está em um plano (x, y);
- O ponto de partida é o ponto (0, 0).

# 2. Requisitos de sistema

## 2.1 Gráfico de caminho percorrido

Deve ser gerado um gráfico que demonstra todos os passos aleatórios possíveis que um bêbado pode dar, começando no ponto (0, 0) e determinado o caminho entre os pontos.

## 2.2 Gráfico de distância percorrida x distância estimada

Um gráfico que demonstra a distância percorrida pelo bêbado desde seu ponto inicial até seu ponto final, juntamente com a comparação da raiz de n que demonstra o número de classes.

- **Nota**: o número de classes deve ter valor máximo setado para 30.

## 2.3 Parâmetros fornecidos pelo usuário

Deve haver dois campos de livre digitação do usuário:

- Número de passos;
- Número de repetições.

Os dois campos são de preenchimento **obrigatório** e devem aceitar apenas caracteres do tipo número. Caso o usuário não preencha um dos campos, o sistema deve emitir uma mensagem de erro informando que os dois campos devem ser preenchidos.

## 2.4 Histograma da amostra

Com o número de replicações da simulação também sendo informado pelo usuário, é possível determinar o número total de classes através da função “raiz de n”, porém, o número de classes máximo possível deve ser 30; mesmo que n tenha um valor maior que 900.

# 3. Como utilizar o sistema

O **manual do usuário** é um requisito de entrega do trabalho e está descrito nesta presente documentação na parte de Manual do usuário. Ele é um guia de como utilizar o sistema.

# 4. O código do trabalho

Como explicado na seção de tecnologias utilizadas, o projeto foi desenvolvido em JavaScript.
A principal função é a *startSimulation()*. Ela pega o número de passos e repetições que o usuário disponibiliza e plota os resultados em forma de gráficos.

