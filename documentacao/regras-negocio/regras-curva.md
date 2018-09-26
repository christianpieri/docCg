---
layout: default
---

## Desenhar ponto

Este requisito descreve os comportamentos da tela de criação de pontos.


#### 1. Breadcrumb
![Home](./img/icone-home.png) > Desenhar Ponto > **Salvar**

#### 2. Campos
- Coordenada x;
- Coordenada y;
- Coordenada z;
- Nome do ponto.

#### 3. Regras
1. Os campos de coordenadas devem receber valores entre [-1000, 1000];
2. Ao tentar digitar qualquer outro valor que não seja numérico, o campo altera seu valor para 0;
3. Se o usuário não entrar com valor algum, entende-se que o valor será 0;
4. O campo nome é de caráter obrigatório e se não for fornecido deve-se apresentar a mensagem: [Campos obrigatórios não preenchidos](./mensagens/campo-obg-n-preenc);
5. Ao clicar em salvar, o sistema deverá:
- desenhar um objeto do tipo ponto respeitando as coordenadas fornecidas pelo usuário;
- salvar este objeto juntamente ao seu tipo na lista de objetos desenhados;
6. Ao clicar em cancelar apresentar a mensagem no console: "Inclusão de ponto cancelada!".

<br>
[Voltar](./)
