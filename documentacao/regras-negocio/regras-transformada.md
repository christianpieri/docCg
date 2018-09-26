---
layout: default
---

## Transformada de ViewPort

Este requisito descreve os comportamentos transformada de ViewPort.


#### 1. Sobre
A transformada de ViewPort é aplicada sobre todos os pontos do desenho, e após ela ser aplicada, toda a tela é redesenhada com base nestes cálculos.

#### 2. Transformada de ViewPort do ponto x
```cpp
static double transformadaViewPortCoordenadaX(double x) {
    double auxiliar = (x - tela.getValorXMinimo()) / (tela.getValorXMaximo() - tela.getValorXMinimo());
    return auxiliar * (xViewPortMax - xViewPortMin);
}
```

#### 3. Transformada de ViewPort do ponto y
```cpp
static double transformadaViewPortCoordenadaY(double y) {
    double auxiliar = (y - tela.getValorYMinimo()) / (tela.getValorYMaximo() - tela.getValorYMinimo());
    return (1 - auxiliar) * (yViewPortMax - yViewPortMin);
}
```

<br>
[Voltar](./)
