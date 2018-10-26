---
layout: default
---

## Clipping

Este requisito descreve os comportamentos da tela quanto ao clipping de objetos.


#### 1. Breadcrumb
![Home](./img/icone-home.png) > Clipping > **On/Off**

#### 2. Campos
- Botão On/Off clipping;
- Radiobutton _Liang Barky Line Clipping_;
- Radiobutton _Cohen Sutherland Line Cliping_.

#### 3. Regras
1. O usuário pode escolher, a qualquer momento, ativar ou desativar o clipping. Para isso, ele deve clicar no botão de On/Off na área de clipping;
2. Caso o clipping esteja desabilitado, o botão permanecerá com a _label_ **Off**, a _hint_ "Clicar ativará o clipping de objetos" e os dois _radio buttons_ de escolha de algoritmo de clipping desabilitados;
3. Caso o clipping esteja habilitado, o botão alterará a _label_ para **On**, a _hint_ será "Clicar desativará o clipping de objetos" e os dois _radio buttons_ de escolha de algoritmo estarão habilitados para seleção;
4. Ao ativar o clipping, um quadrado vermelho, de pequena espessura fina deverá ser desenhado na tela;
- Suas coordenadas são: A(50, 50), B(50, 450), C(450, 450) e D(450, 50);
5. Todo e qualquer desenho (objeto) que transpassar essa área deverá ser cortado naquele(s) ponto(s);
- Esta regra vale para novos desenhos criados ou para qualquer ação que o usuário tome (escalonar, rotacionar, mover a tela, dar zoom) que façam que o objeto fique sobre uma das linhas vermelhas do quadrado;
6. Caso o usuário crie um objeto que está exatamente "sob" a área de clipping e o mesmo está desativado, ao ativar o clipping, este objeto deverá ser redesenhado respeitando as regras dos cortes;
7. Caso o clipping esteja ativo, um objeto já esteja sob efeito de corte e o usuário opte por desativar o clipping, este objeto deverá ser redesenhado na íntegra;
8. Para o clipping de pontos, basta checar se determinado ponto está fora das dimensões do quadrado vermelho supracitado;
9. Para o clipping de retas, verifica-se qual(is) pedaço(s) da reta está(ão) fora do quadrado e redesenha-se o restante;
10. Para o clipping de polígonos e curvas, trata-se estes objetos, ao desenhar, como se fossem retas, de ponto a ponto, para cada ponto que o objeto possui. Assim, é possível utilizar os algoritmos de clipping de reta para eles;
11. O usuário ainda pode optar por dois algoritmos de clipping de reta disponíveis, são eles:
- _Liang Barsky_ (LBLC);
- _Cohen Sutherland_ (CSLC);
12. Para alternar entre eles, basta escolher entre as duas opções de _radio button_ disponíveis;
13. Uma mensagem no console informará sobre a troca de algoritmo e qual está sendo utilizado;
14. Ao alternar entre eles, todos os objetos são redesenhados com base no novo algoritmo selecionado.

#### 4. Algoritmos
##### O algoritmo de _Liang Barsky_, que é o _default_ do sistema, é apresentado a seguir:

```cpp
static std::vector<double> liangBarskyClippingLine(double x0, double y0, double x1, double y1, Window *tela) {
    	
        std::vector<double> pontos;
        double aux = retornaValorAuxiliar(tela);
        
        double xmin = tela->getValorXMinimo() + aux;
	double xmax = tela->getValorXMaximo() - aux;
	double ymin = tela->getValorYMinimo() + aux;
	double ymax = tela->getValorYMaximo() - aux;
		
        double u1 = 0.0;
	double u2 = 1.0;
	double dx = x1 - x0;
	double dy = y1 - y0;
	double p, q, r;
	bool draw = true;

	for(int edge = 0; edge < 4; edge++) {
		if (edge == 0) {
			p = -dx;
	        	q = x0 - xmin;
	        }
	        if (edge == 1) {
	        	p = dx;
	        	q = xmax - x0;
	        }
	        if (edge == 2) {
	        	p = -dy;
	        	q = y0 - ymin;
	        }
	        if (edge == 3) {
	        	p = dy;
	        	q = ymax - y0;
	        }

	        r = q / p;

	        if(p == 0 && q < 0) {
	        	draw = false;
	        }

	        if(p < 0) {
	            if(r > u2) {
	            	draw = false;
	            }
	            else if (r > u1) {
	            	u1 = r;
	            }
	        } else if(p > 0) {
	            if(r < u1) {
	            	draw = false;
	            }
	            else if(r < u2) {
	            	u2 = r;
	            }
	        }
	    }

	    if (draw) {
		    x0 = x0 + u1 * dx;
		    y0 = y0 + u1 * dy;
		    
	        if (u2 != 1) {
			x1 = x0 + u2 * dx;
			y1 = y0 + u2 * dy;
		}
            
	pontos.push_back(x0);
        pontos.push_back(y0);
        pontos.push_back(x1);
        pontos.push_back(y1);

	}

	return pontos;
}
```

- Ela recebe como parâmetro os pontos da reta e as definições atuais da tela;
- A função _retornaValorAuxiliar(tela)_ verifica os pontos máximos e mínimos atuais da tela, caso o usuário tenha feito alguma modificação;
- E retorna uma lista com os novos pontos da reta a serem desenhados (já cortados).

##### O algoritmo de _Cohen Sutherland_ é apresentado a seguir:

```cpp
static std::vector<double> cohenSutherlandClippingLine(double x0, double y0, double x1, double y1, Window *tela) {
	std::vector<double> pontos;
	double aux = retornaValorAuxiliar(tela);
        
	double xmin = tela->getValorXMinimo() + aux;
	double xmax = tela->getValorXMaximo() - aux;
	double ymin = tela->getValorYMinimo() + aux;
	double ymax = tela->getValorYMaximo() - aux;
	
	OutCode outcode0 = computeOutCode(x0, y0, tela);
	OutCode outcode1 = computeOutCode(x1, y1, tela);
	bool accept = false;

	while (true) {
		if (!(outcode0 | outcode1)) {
			
			accept = true;
			break;
		} else if (outcode0 & outcode1) {
			
			break;
		} else {
			
			double x, y;
			OutCode outcodeOut = outcode0 ? outcode0 : outcode1;

			if (outcodeOut & TOP) {          
				x = x0 + (x1 - x0) * (ymax - y0) / (y1 - y0);
				y = ymax;
			} else if (outcodeOut & BOTTOM) { 
				x = x0 + (x1 - x0) * (ymin - y0) / (y1 - y0);
				y = ymin;
			} else if (outcodeOut & RIGHT) {  
				y = y0 + (y1 - y0) * (xmax - x0) / (x1 - x0);
				x = xmax;
			} else if (outcodeOut & LEFT) {  
				y = y0 + (y1 - y0) * (xmin - x0) / (x1 - x0);
				x = xmin;
			}

			if (outcodeOut == outcode0) {
				x0 = x;
				y0 = y;
				outcode0 = computeOutCode(x0, y0, tela);
			} else {
				x1 = x;
				y1 = y;
				outcode1 = computeOutCode(x1, y1, tela);
			}
		}
	}
	if (accept) {
		pontos.push_back(x0);
	        pontos.push_back(y0);
	        pontos.push_back(x1);
	        pontos.push_back(y1);
	}

	return pontos;
}
```

- Assim como em _Liang Barsky_, _Cohen Sutherland_ também recebe os valores da reta e da tela para cálculo de clipping;
- Este algoritmo utiliza a função auxiliar _computeOutCode(x, y, tela)_, que faz uso de artifícios binários para verificar o clipping:

```cpp
	const int INSIDE = 0; // 0000
	const int LEFT = 1;   // 0001
	const int RIGHT = 2;  // 0010
	const int BOTTOM = 4; // 0100
	const int TOP = 8;    // 1000
```

- Por fim, esta função também retorna uma lista com os pontos da reta a serem desenhados (já cortados).

<br>
[Voltar](./)
