---
layout: default
---

## Editar objeto

Este requisito descreve os comportamentos da tela de editar objetos.


#### 1. Breadcrumb
![Home](./img/icone-home.png) > Editar Objeto > **Salvar**

#### 2. Campos
- Botão de escolha Transladar/Escalonar;
- Coordenada transladar x;
- Coordenada transladar y;
- Porcentagem escalonar objeto.

#### 3. Regras
1. Ao entrar na tela de edição de objeto, verificar qual o tipo de objeto está selecionado na lista de objetos e alterar a _label_ inicial para o determinado tipo;
- 1.1 Se nenhum objeto estiver selecionado, apresentar a seguinte mensagem no console: "Você precisa selecionar ao menos um objeto para editá-lo!";
2. Objetos do tipo ponto não podem ser escalonados:
- caso um objeto do tipo ponto seja editado, desabilitar os campos de Escalonamento;
3. Se o usuário selecionar a opção **Transladar objeto** o sistema deve:
- desabilitar a entrada de porcentagem de escalonamento de objetos;
- habilitar a entrada das coordenadas x e y para deslocamento;
- alterar a _label_ de desejo para "Você gostaria de transladar o seu objeto em quantos x e y?";
4. Se o usuário selecionar a opção **Escalonar objeto** o sistema deve:
- desabilitar a entrada das coordenadas x e y para deslocamento;
- habilitar a entrada de porcentagem para escalonamento;
- alterar a _label_ de desejo para "Você gostaria de escalonar o seu objeto em quantos %?"
5. Ao clicar em salvar, o sistema deverá:
- redesenhar o objeto conforme as solicitações do usuário;
- salvar as modificações de todos os pontos;
6. Ao clicar em cancelar apresentar a mensagem no console: "Edição de objeto cancelada!".


<br>
[Voltar](./)
