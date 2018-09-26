---
layout: default
---

## Deslocar tela

Este requisito descreve os comportamentos dos botões de deslocamento.


#### 1. Breadcrumb
![Home](./img/icone-home.png) > **Deslocar tela** 

#### 2. Regras
1. Ao clicar nos botões direcionais (representados com setinhas na caixa de controle), o sistema deve mover as coordenadas da tela em 10 unidades, dependendo da direção solicitada pelo usuário.
2. Esta operação move a tela, e não os desenhos. Portanto, ao mover a tela para direita, aparentemente os desenhos estarão indo para a esquerda. Esta regra vale para todas as direções.


```cpp
// Exemplo movendo a tela para a direita:
static void on_buttonDireita_clicked() {
    
   monstrarMensagemNoConsole("Botão direita pressionado! Movendo-se +10.\n");

    double xMaximo = tela.getValorXMaximo();
    double xMinimo = tela.getValorXMinimo();
    double yMaximo = tela.getValorYMaximo();
    double yMinimo = tela.getValorYMinimo();

    xMaximo += 10;
    xMinimo += 10;
    
    tela.setCoordenadasMaximo(xMaximo,yMaximo);
    tela.setCoordenadasMinimo(xMinimo,yMinimo);

}
```

##### Atalho
1. Alternativamente, o usuário poderá fazer uso das teclas de atalho direcionais **"←"**, **"↑"**, **"↓"**, **"→"** presentes no seu teclado. O comportamento deve ser idêntico ao descrito no clique do botão.

<br>
[Voltar](./)
