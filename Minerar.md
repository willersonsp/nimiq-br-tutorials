# Mineração

Na mineração da NIMIQ, existem 3 modos de operação em que se pode escolher: Smart, Nano e Dumb. Mais detalhes sobre cada um abaixo:

**Smart** 

Nesse modo, você é o responsável por criar os blocos. O cliente opera como um minerador solo, ou seja, se o seu hash rate for muito baixo, não compensa, pois irá demorar muito até encontrar um bloco. Esse modo requere pelo menos o "light-node" ou o "full-node".

**Nano**

No modo nano, o cliente somente valida blocos que são enviados por uma pool. O servidor da pool fornece todos os dados para o cliente construir o bloco, desde que ele opere no mesmo bloco que o servidor.

**Dumb**

Nesse modo o cliente recebe um "hash" para o calculo e devolve para o servidor o valor calculado. Esse modo é o mais simples e rápido para começar a minerar. 

Nesse tutorial vai ser abordado o modo dumb somente.

### Software para minerar:

**CPU:**

https://nimiqdesktop.com/

**GPU**:

Nvidia: https://github.com/NoncerPro/noncerpro-nimiq-cuda/releases

AMD: https://github.com/NoncerPro/noncerpro-nimiq-opencl/releases



##### Minerando com CPU:

Basta abrir o programa Nimiq Desktop, inserir os dados conforme a imagem abaixo e clicar em "Start Mining".

<p align="center">
<img  src="https://github.com/willersonsp/nimiq-br-tutorials/blob/master/imagens/cpu_mining.png?raw=true">
</p>



**Minerando com GPU:**

Basta configurar o arquivo mine.bat (abra o mesmo com um editor de texto) e alterar as informações para as suas:

```
SET UV_THREADPOOL_SIZE=32
noncerpro.exe -a [seu endereço da carteira] -s [endereço da pool escolhida] -p [porta fornecida pela pool] --threads=2 --mode=dumb
pause
```

No caso das pools, elas podem ser obtidas nesse https://miningpoolstats.stream/nimiq, mas como recomendação pessoal, sugiro que utilize a nimpool ou a blankpool(drawpad.org), pois minerar na icemining apesar de ser rápido o ganho, somente é pago a você depois de acumular pelo menos 100 NIM.

Substitua pelos seus dados onde estiver [seu endereço da carteira],  [endereço da pool escolhida] e [porta fornecida pela pool]. Segue um exemplo abaixo para a nimpool.

```
SET UV_THREADPOOL_SIZE=32
noncerpro.exe -a NQ74C5L7AURMAQLAM8BSN37EXE9LFT5AJAJC -s us.nimpool.io -p 8444 --threads=2 --mode=dumb
pause
```

Mas caso queira uma configuração mais fixa, existe a possibilidade de se configurar o arquivo miner.conf, segue um exemplo abaixo, para habilitar a configuração alterada, remova as // na frente da linha desejada:

```
{
    "address": "NQ46 DP4N 5YG1 H3QU 5LPA 2624 FKL5 0LNS EFEF",/*** Endereço da sua carteira ***/
    "name": "NomeDoSeuComputador",/*** Nome amigável ***/
    "server": ['us.nimpool.io'],/*** Endereço da pool de mineração ***/
    "port": [8444],/*** A porta informada pela pool. ***/
    "mode": 'dumb',/*** Array of active devices. eg: [0, 2, 3] ***/
    /*** Padrão: Todos os dispositivos disponiveis. ***/
    //"devices": [0, 2, 3],/*** Sequência de dispositivos ativos ***/
    /*** Padrão: 1 ***/
    "threads": 2,/*** Número ou sequência de processos por dispositivo. Exemplo: 2 ou [2, 2, 1] ***/
    /*** Padrão: Baseado no total de memória disponivel na placa de video. Apague ou comente para usar o padrão. **/
    //"batchsize": 93,
    //"difficulty": 32, /*** Dificuldade inicial (deve ser suportado pela pool) ***/
}
```

A dica que eu posso dar é na configuração do batchsize, vamos supor que temos 8GB (8192MB) de memória na placa de vídeo,  e cada valor do batchsize equivale a 32MB e vamos utilizar 2 threads, segue um calculo abaixo do que eu recomendaria.

(MemóriaTotal / batchsize) / threads

((8092 / 32) /2) -25% = 96.

Ou seja, o recomendado para uma placa de 8GB seria algo entre 90~100.



Bom, esse foi um pequeno tutorial que fiz no intuito de ajudar a comunidade BR de nimiq, qualquer alteração ou melhoria, abra um pull-request que estarei aceitando assim que possível :)

