---
layout: default
---

## Carregar Arquivo

Este requisito descreve os comportamentos do botão de carregar arquivo.


#### 1. Breadcrumb
![Home](./img/icone-home.png) > **Carregar arquivo** 

#### 2. Regras
1. Ao clicar no botão de "Carregar" (na caixa de controle), o sistema deve pegar todos os objetos descritos no arquivo _.obj_ e importá-los para o programa.
2. Após a importação, todos são tratados para verificar seus tipos:
- Um objeto com um único ponto, é considerado do tipo Ponto;
- Um objeto com dois pontos, é considerado como uma Reta;
- Um objeto com três ou mais pontos, é considerado como um Polígono;
- Lembrando que objetos do tipo Polígono necessitam ter uma linha adicional que liga seu ponto final ao inicial;


2. A leitura é similar ao método de salvar: ler a primeira letra "o" e guardar o nome do objeto; enquanto ler letras "v" guardar os pontos do objeto.


#### 3. Anexo
Abaixo o código que faz a operação de leitura todos os objetos no arquivo:
```cpp
static std::vector<Poligono*> lerObjetosDoArquivo() {
    ifstream leitura;
    leitura.open("saida.obj");
    char linhaLida[100];
    std::string nome;
    std::string lixo;
    std::string x;
    std::string y;
    std::string linha;
    std::vector<Poligono*> vetorDePoligonos;
    Poligono *poligono;
    std::vector<Ponto*> listaDePontosDoPoligono;
    
    while(leitura.getline(linhaLida, 100)) {
        linha = linhaLida;
        stringstream iss(linha);
        if(linha.substr(0, 1).compare("o") == 0) {
            listaDePontosDoPoligono.clear();
            poligono = new Poligono(listaDePontosDoPoligono, "lixo");
            iss >> lixo;
            iss >> nome;
            poligono->setNome(nome);
            vetorDePoligonos.push_back(poligono);
        } else {
            Ponto *ponto = new Ponto();
            iss >> lixo;
            iss >> x;
            iss >> y;
            ponto->setValorX(atof(x.c_str()));
            ponto->setValorY(atof(y.c_str()));
            listaDePontosDoPoligono.push_back(ponto);
            poligono->setListaDePontos(listaDePontosDoPoligono);
        }
    }
    leitura.close();
    return vetorDePoligonos;
} 
```

##### Atalho
1. Alternativamente, o usuário poderá fazer uso da tecla de atalho **"ctrl+O"** presente no seu teclado. O comportamento deve ser idêntico ao descrito no clique do botão.


<br>
[Voltar](./)
