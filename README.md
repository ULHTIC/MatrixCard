# Exercício Prático 3 - MatriX
Linguagens de Programação I - Exercício 3

Na resolução deste trabalho deve ser utilizada a Linguagem de Programação C. Para além da correta implementação dos requisitos, tenha em conta os seguintes aspetos:
- O código apresentado deve ser bem indentado. 
- O código deve compilar sem erros ou *warnings* utilizando o *gcc* com as seguintes flags:
 `-Wall -Wextra -Wpedantic -std=c99 -Wvla`
- Tenha em atenção os nomes dados das variáveis, para que sejam indicadores daquilo que as mesmas vão conter.
- Evite o uso de constantes mágicas. 
- Evite duplicação de código. 
- Considere a implementação de funções para melhorar a legibilidade, evitar a duplicação e criar soluções mais genéricas.
- É proíbida a utilização de variáveis globais - i.e. variáveis declaradas fora de qualquer função - excepto constantes.
- Este trabalho deverá ser feito individualmente.
- É estritamente proibida a utilização da instrução `goto`. 

## Descrição do problema
Faça um programa que lê um ficheiro que contém a informação de um *cartão matriz* de um banco. O programa deverá ler pela linha de comando o nome do ficheiro e qual o modo de leitura do ficheiro (texto ou binário). Após a leitura do ficheiro, o programa deverá ler do utilizador 3 coordenadas do cartão (exemplo: `A32 F73 B21`) e depois deverá imprimir os 3 números correspondentes no terminal e em seguida deve terminar sem mostrar nenhuma mensagem.

Exemplo de ficheiro texto com a informação do cartão matriz:
```
353 675 231 121 794 720 543 749
449 361 403 884 544 721 984 503
963 620 122 094 686 877 715 646
042 811 268 930 893 582 838 307
972 019 257 399 054 070 433 138
189 083 331 047 303 922 470 475
667 974 152 342 046 800 560 362
586 651 348 735 195 285 269 788
```
O utilizador especifica na linha de comando o nome do ficheiro e também o modo:
```bash
>./MatriX <nome do ficheiro> <modo>
```
Para o efeito o caracter `t` indica que o ficheiro está gravado em modo texto, e `b` indica que está em modo binário. Os argumentos da linha de comando deverão obedecer à ordem indicada. 
Caso o ficheiro esteja em modo binário, deverá ser considerado que o ficheiro contém 192 bytes em que cada byte contém um dígito entre 0 e 9. Não contém espaços nem quebras de linha:
```
<byte0><byte1><byte2><byte3><byte4>...
```
No exemplo `<byte0>` corresponde à coordenada A11. A coordenada B11 será dada pelo `<byte24>`.

Caso o utlizador introduza uma coordenada inválida o programa deverá imprimir a mensagem: `Error: Invalid coordinate.`. Caso o ficheiro esteja mal formatado, o programa deverá terminar com a mensagem: `Error: File is corrupted.`. Caso não seja possível abrir o ficheiro o programa deverá terminar com a mensagem: `Error: could not open file.`. Caso o utilizador não especifique o nome do ficheiro e o modo de abertura, deverá terminar com a mensagem `Error: Invalid arguments.`.
Em resumo a definição das mensagens de erro é:
 ```C
#define ERR_FOPEN "Error: could not open file."
#define ERR_COORD "Error: Invalid coordinate."
#define ERR_CORPT "Error: File is corrupted."
#define ERR_ARGS "Error: Invalid arguments."
 ```

Encontram-se neste repositório dois ficheiros exemplo [matrix.txt](matrix.txt) e [matrix.dat](matrix.dat), codificados em texto e binário, respectivamente.

### Exemplos de execução do programa:
```bash
>./MatriX cartao_matriz.txt t
B61 H83 E43
7 8 9
```

```bash
>./MatriX cartao_matriz.dat b
G22 G31 C81
7 1 6
```
