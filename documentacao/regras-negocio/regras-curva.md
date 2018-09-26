---
layout: default
---

## Desenhar curva

Este requisito descreve os comportamentos da tela de criação de curvas.


#### 1. Breadcrumb
![Home](./img/icone-home.png) > Desenhar Curva > **Salvar**

#### 2. Campos
- Botão de escolha Bezier/b-Spline;
- Coordenada x inicial;
- Coordenada y inicial;
- Coordenada y final;
- Coordenada z final;
- Coordenada x1 controle;
- Coordenada y1 controle;
- Coordenada x2 controle;
- Coordenada y2 controle;
- Nome da curva.

#### 3. Regras
1. O usuário pode alternar sua escolha entre curva de Bezier ou b-Spline;
- 1.1 Ao alternar entre elas, mudar a _label_ inicial para o determinado tipo de curva;
2. Os campos de coordenadas devem receber valores entre [-1000, 1000];
3. Ao tentar digitar qualquer outro valor que não seja numérico, o campo altera seu valor para 0;
4. Se o usuário não entrar com valor algum, entende-se que o valor será 0;
5. O campo nome é de caráter obrigatório e se não for fornecido deve-se apresentar a mensagem: [Campos obrigatórios não preenchidos](./mensagens/campo-obg-n-preenc);
6. Caso o usuário forneça um nome de curva já existente, apresentar a mensagem: [Nome de objeto já existente](./mensagens/nome-ja-existente);
7. Ao clicar em salvar, o sistema deverá:
- desenhar um objeto do tipo curva respeitando as coordenadas fornecidas pelo usuário;
- salvar este objeto juntamente ao seu tipo na lista de objetos desenhados;
8. Ao clicar em cancelar apresentar a mensagem no console: "Inclusão de curva cancelada!".

<br>
[Voltar](./)
