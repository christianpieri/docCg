---
layout: default
---

## Desenhar reta

Este requisito descreve os comportamentos da tela de criação de retas.


#### 1. Breadcrumb
![Home](./img/icone-home.png) > Desenhar Reta > **Salvar**

#### 2. Campos
- Coordenada x inicial;
- Coordenada y inicial;
- Coordenada z inicial.
- Coordenada x final;
- Coordenada y final;
- Coordenada z final;
- Nome da reta.

#### 3. Regras
1. Os campos de coordenadas devem receber valores entre [-1000, 1000];
2. Ao tentar digitar qualquer outro valor que não seja numérico, o campo altera seu valor para 0;
3. Se o usuário não entrar com valor algum, entende-se que o valor será 0;
4. O campo nome é de caráter obrigatório e se não for fornecido deve-se apresentar a mensagem: [Campos obrigatórios não preenchidos](./mensagens/campo-obg-n-preenc);
5. Caso o usuário forneça um nome de reta já existente, apresentar a mensagem: [Nome de objeto já existente](./mensagens/nome-ja-existente);
6. Ao clicar em salvar, o sistema deverá:
- desenhar um objeto do tipo reta respeitando as coordenadas fornecidas pelo usuário, traçando uma linha contínua do ponto inicial até o ponto final;
- salvar este objeto juntamente ao seu tipo na lista de objetos desenhados;
7. Ao clicar em cancelar apresentar a mensagem no console: "Inclusão de reta cancelada!".

<br>
[Voltar](./)
