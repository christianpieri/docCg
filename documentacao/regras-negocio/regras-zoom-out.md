---
layout: default
---

## Zoom Out

Este requisito descreve os comportamentos do botão de Zoom Out.


#### 1. Breadcrumb
![Home](./img/icone-home.png) > **Zoom Out** 

#### 2. Regras
1. Ao clicar no botão de Zoom Out (apresentado como "-"), o sistema deve aumentar as coordenadas da Tela em 5 unidades no ponto máximo e diminuir 5 unidades no ponto mínimo. Esta operação altera a escala do desenho e dá a sensação dele estar diminuindo, portanto: Zoom Out;
2. Apresentar no console a seguinte mensagem: "Botão zoom out pressionado!".

```cpp
static void on_buttonZoomOut_clicked() {
    
    monstrarMensagemNoConsole("Botão zoom out pressionado!\n");

    double xMaximo = tela.getValorXMaximo();
    double xMinimo = tela.getValorXMinimo();
    double yMaximo = tela.getValorYMaximo();
    double yMinimo = tela.getValorYMinimo();

    tela.setCoordenadasMaximo(xMaximo+5,yMaximo+5);
    tela.setCoordenadasMinimo(xMinimo-5,yMinimo-5);
    
}
```


##### Atalho
1. Alternativamente, o usuário poderá fazer uso da tecla de atalho **"-"** presente no seu teclado. O comportamento deve ser idêntico ao descrito no clique do botão.

<br>
[Voltar](./)
