MetaSim2.0: Event-based simulator
=================================
Uma nova versão da biblioteca de metasim ligeiramente redesenhada

Autores: Giuseppe Lipari, Gerardo Lamastra, Antonino Casile, 
         Luigi Palopoli, Cesare Bartolini

Contribuidores: Luca Abeni, Marco Caccamo, Fabio Rossi, Claudio Scordino,
			Fabio Cremona, Matteo Morelli, Andrea Parri

Copyright: Retis Laboratory, Scuola Superiore Sant'Anna
email:     g.lipari@sssup.it

Este é um software de código aberto e distribuído sob os termos do GNU
Licença Pública (GPL). Consulte COPYING para mais detalhes.

Traduzido por Gustavo Damasceno de Campos.
======================================================================

SUMÁRIO

1. INTRODUÇÃO
2. NOTAS DE LANÇAMENTO
3. COMPILAÇÃO
4. INSTALAÇÃO
5. RODANDO OS EXEMPLOS
6. ADICIONANDO UM NOVO EXEMPLO
7. BUGS AND CONTRIBUTIONS

======================================================================

## 1. INTRODUÇÃO

MetaSim2.0 é uma biblioteca para simulação de eventos discretos escrita em C ++. isto
foi desenvolvido como um projeto interno na Scuola Superiore
Sant'Anna como parte de muitos projetos de pesquisa, principalmente graças ao trabalho
de muitos estudantes de doutoramento.


## 2. NOTAS DE LANÇAMENTO

Este software foi testado no Linux, MacOSX e
Windows. Compiladores suportados (testados) são:

	- g++ (Ubuntu/Linaro 4.8.1-10ubuntu9) 4.8.1
	- clang++ (Apple LLVM version 5.1 (clang-503.0.40))
	- Microsoft Visual Studio 2012    

Assumimos que o usuário tenha o compilador já instalado em sua máquina.

## 3. COMPILAÇÃO

O software pode ser compilado em qualquer plataforma com o
compilador conforme listado na seção 2.

O sistema de compilação MetaSim2.0 é baseado no CMake, o multi-plataforma,
sistema de compilação de código aberto. Para compilar o MetaSim2.0 você deve ter o CMake
(ver.> = 2.6) instalado em sua máquina.

Se você tiver o CMake instalado em sua máquina, você pode pular
seção seguinte e pule para a seção 3.2.

### 3.1. Instalando CMake

Siga as instruções no link http://www.cmake.org/cmake/help/install.html

### 3.2. Compilando em sistemas semelhantes ao Unix (incluindo o Mac OS X)

Os passos para construir e instalar o software são os habituais:

    cd metasim2.0
    mkdir build
    cd build
    cmake ..
    
A execução do comando "ccmake .." causa a execução do programa CMake.
Para gerar o makefile necessário para compilar a biblioteca, você precisa:
pressione a tecla 'c' duas vezes e depois pressione 'g'. Ao pressionar 'g', o CMake
gere o makefile e retornará a linha de comando. Agora você
pode compilar a biblioteca:

    make 

O último passo irá compilar a biblioteca, o executável para o teste e
os exemplos incluídos na biblioteca. Diretórios de saída são:
	- src/
	- test/
	- examples/
	
A biblioteca está localizada em src/

### 3.3. Compilando no Windows

    execute CMake

No local "Onde está o código-fonte:" indique o caminho para o
pasta metasim2.0

No local "Onde construir os binários:" indique o caminho para
a pasta onde você deseja colocar a saída (geralmente = $ {Caminho para
metasim2.0} / build).

Agora clique em "Configurar". CMake pedirá para especificar o gerador para o projeto.

Você deve selecionar o Visual Studio 11 e clicar em Concluir. Quando o processo
vai terminar, clique novamente em "Configurar" e clique para
"Gerar". Esta última etapa irá gerar o projeto do Visual Studio
"metasim.sln".

Abra a pasta que você selecionou para sua saída e clique duas vezes na
arquivo gerado "metasim.sln" para abrir o projeto. No Visual Studio e
em seguida, na barra de comando, selecione o menu BUILD e clique em Build
Solução. O processo de compilação será iniciado.

Diretórios de saída são:
	- src/Debug/
	- test/Debug/
	- examples/Debug/
	
A biblioteca está inserida em src/Debug

### 3.4. Teste

Mesmo que o teste não seja obrigatório, é altamente recomendável executá-lo.
O conjunto de testes está localizado em test / (sistemas unix-like) ou em
/ test / Debug (sistemas windows) e pode ser executado para testar se o
fluxo de compilação foi ok.

#### Para unix-like systems

    cd metasim2.0/build
	make
	ctest --output-on-failure

#### Para Windows

Abra o projeto MetaSim gerado pelo CMake e construa `ALL_BUILD`. Então,


	cd metasim2.0/build
	ctest --output-on-failure -C Debug

ou

	ctest --output-on-failure -C Release

#### Resultados
A execução deve terminar com todos os testes aprovados.

Os testes foram escritos usando a biblioteca Catch, que é um único
inclua o arquivo que você pode encontrar no diretório de teste.

https://github.com/philsquared/Catch

O processo de teste é automatizado pelo CTest, como um elemento do conjunto do CMake.


## 4. INSTALANDO

Atualmente, a instalação não é suportada. Após a compilação, todos
arquivos de cabeçalho e o arquivo de biblioteca são encontrados no src / (src / Debug for
Sistemas Windows). Basta colocar o caminho do diretório src
no CPPFLAGS e no LDFLAGS quando você quiser usar a biblioteca.


## 5. Rodando os exemplos

Todo diretório sob um dos diretórios "exemplos" contém um
exemplo diferente. Entre no diretório e execute o executável
Arquivo.

### 5.1 Unix-like systems

Para executar o exemplo eth, vá dentro do diretório
exemplos / eth e tipo

  ./eth

Outros exemplos estão disponíveis e podem ser executados da mesma maneira.

### 5.2 sitema Windows

Para executar o exemplo eth, vá dentro do diretório
Exemplos / Debug / eth e clique duas vezes em eth.exe.
Outros exemplos estão disponíveis e podem ser executados da mesma maneira.

## 6. ADICIONANDO UM NOVO EXEMPLO

Para adicionar um novo exemplo à biblioteca, você precisa

- Crie uma nova pasta em metasim2.0 / examples com o nome do seu
   exemplo.
- Edite o arquivo metasim2.0 / examples / CMakeLists.txt adicionando o arquivo
   especificação para o seu exemplo:

add_subdirectory (name_of_your_example)

Depois de escrever o código do seu exemplo, você deve gerar novamente o
makefile. Siga as instruções na seção 3 para a geração de
o makefile e compilar.

## 7. BUGS e CONTRIBUIÇÕES

Para relatórios de bugs, solicitações de recursos e outros problemas que você pode encontrar,
por favor, consulte as páginas apropriadas no site do github:

  http://github.com/glipari/metasim2.0


Giuseppe Lipari
g.lipari@sssup.it

Fabio Cremona
f.cremona@sssup.it
