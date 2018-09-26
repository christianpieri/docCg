---
layout: default
---

## Rotacionar objeto

Este requisito descreve os comportamentos da tela de rotacionar objetos.


#### 1. Breadcrumb
![Home](./img/icone-home.png) > Rotacionar Objeto > **Salvar**

#### 2. Campos
- Botão de escolha de ângulo de rotação;
- Botão de escolha ao redor de qual ponto rotacionar.

#### 3. Regras
1. Ao entrar na tela de rotação de objeto, verificar qual o sentido da rotação e alterar a _label_ inicial para o determinado sentido;
2. Se nenhum objeto estiver selecionado, a tela será rotacionada naquela direção em 90º;
3. O usuário poderá escolher entre as 3 opções de ângulos previamente disponibilizadas ou a opção personalizada "Outro":
- 90º;
- 180º;
- 270º;
4. Ao escolher a opção "Outro", habilitar o campo de entrada "ângulo", e o usuário deverá informar o ângulo escolhido para sua rotação.
5. Após, o usuário poderá escolher ao redor de qual ponto rotacionar o seu objeto:
- No centro do mundo (ponto(0, 0));
- No seu próprio centro;
- Ao redor de um ponto qualquer.
6. Se o usuário escolher ao redor de um ponto qualquer, habilitar a opção "Qual?" para entrada de dados x e y;
7. Ao clicar em Salvar, seu objeto será rotacionado, redesenhado na tela e salvas suas novas coordenadas na lista de objetos.
8. Alternativamente, o usuário poderá clicar em "Cancelar", para cancelar a rotação de um objeto. Neste caso, apresentar a seguinte mensagem no console: "Rotação de objeto cancelada!".


<br>
[Voltar](./)
