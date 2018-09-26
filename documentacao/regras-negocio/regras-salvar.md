---
layout: default
---

## Salvar Arquivo

Este requisito descreve os comportamentos do botão de salvar arquivo.


#### 1. Breadcrumb
![Home](./img/icone-home.png) > **Salvar arquivo** 

#### 2. Regras
1. Ao clicar no botão de "Salvar" (na caixa de controle), o sistema deve pegar todos os objetos desenhados na tela e exportá-los para um arquivo com extensão _.obj_.
2. O arquivo deve ser composto por letras, seguidas de nomes ou números, como demonstrado no exemplo abaixo:
```
o Quadrado
v 100 100
v 100 200
v 200 200
v 200 100
```
- O formato diz que após uma letra "o" aparecer, temos o nome do objeto;
- E após a letra "v" aparecer, temos os vértices do objeto: x e y, respectivamente.


#### 3. Anexo
Abaixo o código que faz a operação de salvar todos os objetos no arquivo:
```cpp
static void salvarObjetosPontoEmArquivo(std::vector<Ponto*> objetosPonto) {
    ofstream escreve;
    escreve.open("saida.obj");
        
    for(int i = 0; i < objetosPonto.size(); i ++) {
        auto ponto = objetosPonto.at(i);
        escreve << "o " << ponto->getNome() << "\n";
        escreve << "v " << ponto->getValorX() << " " << ponto->getValorY() << "\n";
    }
    escreve.close();
}
static void salvarObjetosRetaEmArquivo(std::vector<Reta*> objetosReta) {
    ofstream escreve;
    escreve.open("saida.obj", ofstream::ios_base::app);
    
    for(int i = 0; i < objetosReta.size(); i ++) {
        auto reta = objetosReta.at(i);
        escreve << "o " << reta->getNome() << "\n";
        escreve << "v " << reta->getValorXInicial() << " " << reta->getValorYInicial() << "\n";
        escreve << "v " << reta->getValorXFinal() << " " << reta->getValorYFinal() << "\n";
    }
    escreve.close();
}
static void salvarObjetosPoligonoEmArquivo(std::vector<Poligono*> objetosPoligono) {
    ofstream escreve;
    escreve.open("saida.obj", ofstream::ios_base::app);
    
    for(int i = 0; i < objetosPoligono.size(); i++) {
        auto poligono = objetosPoligono.at(i);
        escreve << "o " << poligono->getNome() << "\n";
        for(int j = 0; j < poligono->getListaDePontos().size(); j++) {
            auto ponto = poligono->getListaDePontos().at(j);
            escreve << "v " << ponto->getValorX() << " " << ponto->getValorY() << "\n";
        }
    }
    escreve.close();
}
```

##### Atalho
1. Alternativamente, o usuário poderá fazer uso da tecla de atalho **"ctrl+S"** presente no seu teclado. O comportamento deve ser idêntico ao descrito no clique do botão.


<br>
[Voltar](./)
