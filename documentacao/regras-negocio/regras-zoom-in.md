---
layout: default
---

## Zoom In

Este requisito descreve os comportamentos do botão de Zoom In.


#### 1. Breadcrumb
![Home](./img/icone-home.png) > **Zoom In** 

#### 2. Regras
1. Ao clicar no botão de Zoom In (apresentado como "+"), o sistema deve diminuir as coordenadas da Tela em 5 unidades no ponto máximo e aumentar 5 unidades no ponto mínimo. Esta operação altera a escala do desenho e dá a sensação dele estar aumentando, portanto: Zoom In;
2. Apresentar no console a seguinte mensagem: "Botão zoom in pressionado!".

```cpp
static void on_buttonZoomIn_clicked() {
    
    monstrarMensagemNoConsole("Botão zoom in pressionado!\n");

    double xMaximo = tela.getValorXMaximo();
    double xMinimo = tela.getValorXMinimo();
    double yMaximo = tela.getValorYMaximo();
    double yMinimo = tela.getValorYMinimo();

    tela.setCoordenadasMaximo(xMaximo-5,yMaximo-5);
    tela.setCoordenadasMinimo(xMinimo+5,yMinimo+5);
    
}
```

##### Atalho
1. Alternativamente, o usuário poderá fazer uso da tecla de atalho **"+"** presente no seu teclado. O comportamento deve ser idêntico ao descrito no clique do botão.

<br>
[Voltar](./)
