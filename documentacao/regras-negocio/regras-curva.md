---
layout: default
---

## Desenhar curva

Este requisito descreve os comportamentos da tela de criação de curvas.


#### 1. Breadcrumb
![Home](./img/icone-home.png) > Desenhar Curva > **Salvar**

#### 2. Campos
- Botão de escolha Bezier/b-Spline;
- Coordenada x;
- Coordenada y;
- Coordenada z;
- Botão de adicionar ponto a curva;
- Nome da curva.

#### 3. Regras
1. O usuário pode alternar sua escolha entre curva de Bezier ou b-Spline;
- 1.1 Ao alternar entre elas, mudar a _label_ inicial para o determinado tipo de curva;
- 1.2 Refazer os cálculos para saber se deve ser possível salvar um determinado tipo de curva;
2. Os campos de coordenadas devem receber valores entre [-1000, 1000];
3. Ao tentar digitar qualquer outro valor que não seja numérico, o campo altera seu valor para 0;
4. Se o usuário não entrar com valor algum, entende-se que o valor será 0;
5. O campo nome é de caráter obrigatório e se não for fornecido deve-se apresentar a mensagem: [Campos obrigatórios não preenchidos](./mensagens/campo-obg-n-preenc);
6. Caso o usuário forneça um nome de curva já existente, apresentar a mensagem: [Nome de objeto já existente](./mensagens/nome-ja-existente);
7. Caso o usuário queira desenhar uma curva do tipo Bezier, o sistema só deverá aceitar o salvamento, quando o usuário tiver adicionados múltiplos de 4 pontos;
8. Se a lista de pontos ainda não contiver multiplos de 4 pontos, o sistema deverá bloquear a ação de salvar e emitir uma _hint_ no botão alertando quantos pontos ainda faltam para validar o salvamento;
9. Caso o usuário queira desenhar uma cuvra do tipo bSpline, o sistema só deverá aceitar o salvamento, quando o usuário tiver adicionado pelo menos 4 pontos;
10. Se a lista de pontos ainda não contiver 4 pontos, o sistema deverá bloquear a ação de salvar e emitir uma _hint_ no botão alertando quantos pontos ainda faltam para validar o salvamento;
11. Ao clicar em salvar, o sistema deverá:
- desenhar um objeto do tipo curva respeitando as coordenadas fornecidas pelo usuário;
- salvar este objeto juntamente ao seu tipo na lista de objetos desenhados;
12. Ao clicar em cancelar apresentar a mensagem no console: "Inclusão de curva cancelada!".
13. O _helper_ de contexto ajuda o usuário, que, ao posicionar o mouse em cima do _widget_, disponibiliza a seguinte _hint_: "Alterne entre os _radio buttons_ para escolher entre Bezier ou b-Spline.
Bezier precisa ter múltiplos de 4 pontos. b-Spline precisa ter no mínimo 4 pontos.".

<br>
[Voltar](./)
