# Apostila-OpenMP
Projeto ICV para desenvolvimento e aprendizagem de computação paralela utilizando a libgomp (OpenMP)

<a href="#objetivos">Objetivos</a><br>
<a href="#metodologia">Metodologia</a><br>
<a href="https://github.com/Daniel-Boll/Apostila-OpenMP/tree/master/Apostila">Apostila</a><br>
<a href="#referencia">Referências</a><br>

<div id="objetivos"></div>

# OBJETIVOS:

## Geral:
  Estudar e aplicar a biblioteca OpenMP na paralelização de algoritmos genéticos e de recozimento simulado.

## Específicos:
  1) Estudar e compreender como funcionam os algoritmos genéticos com codificação real;
  2) Estudar e compreender como funciona o algoritmo de recozimento simulado;
  3) Implementar o algoritmo genético e o algoritmo de recozimento simulado em execução sequencial;
  4) Pesquisar por ferramentas de análise de desempenho de aplicações;
  5) Estudar a biblioteca OpenMP;
  6) Desenvolver uma apostila sobre a biblioteca e sua utilização, para compartilhamento com os demais acadêmicos do curso de Ciência da Computação;
  7) Paralelizar os algoritmos desenvolvidos anteriormente usando a biblioteca OpenMP;
  8) Comparar o desempenho e os resultados obtidos com as diferentes implementações.

<div id="metodologia"></div>

# METODOLOGIA:

  Algoritmos executados sequencialmente tendem a usar somente um núcleo de processamento e, atualmente, os processadores possuem no mínimo dois núcleos que funcionam como se fossem processadores independentes. Os processadores mais poderosos podem ter até 32 núcleos, como no caso do AMD Ryzen Threadripper (AMD, 2019).
  Geralmente, algoritmos sequências quando paralelizados, usando vários núcleos de processamento, são executados em menor tempo. Dornelles et al. (2014) compararam o  tempo de execução de um algoritmo genético utilizando programação sequencial e paralela; os resultados obtidos, apresentados na tabelas 1, permite-nos inferir que, de fato, implementações paralelas usando a biblioteca OpenMP tendem a ser mais rápidas que implementações sequenciais.

Tabela 1 –	Tempos de execução de um algoritmo genético utilizando programação sequencial e paralela com a biblioteca OpenMP.

| No de Threads | Teste 1 [ms] | Teste 2 [ms] | Teste 3 [ms] | Média [ms] |
|---------------|--------------|--------------|--------------|------------|
|1|83202,23|83145,61|83984,61|83444,15|
|2|61249,57|67713,92|65786,19|64916,56|
|4|61128,40|61213,21|60840,31|61060,64|
|6|74852,33|74750,94|74727,85|74777,04|
|8|66250,70|64511,58|66184,75|65649,01|

Fonte: Adaptado de Dornelles et al. (2014)

Em problemas de otimização combinatória complexos, as técnicas determinísticas deixam de ser interessantes quando demandam tempos inviáveis de processamento. O tempo inviável pode ser entendido de duas maneiras distintas: na primeira como aquele onde a solução exata demanda muito tempo como semanas, meses e até anos de processamento; na segunda quando a solução deve ser obtida em tempos muito pequenos, próximos ao processamento em tempo-real.
Nestes casos são empregadas meta-heurísticas, como os algoritmos genéticos e o recozimento simulado. Estes algoritmos não visam encontrar a solução exata para o problema em questão, mas boas soluções em um tempo viável. 
Algoritmos Genéticos foram idealizados e experimentados por John Holland na década de 1970; estes algoritmos têm por base os princípios da seleção natural propostos por Darwin (HOLLAND, 1975). Eles empregam uma estratégia de busca paralela e estruturada, mas aleatória, que é voltada em direção ao reforço da busca de pontos de “alta aptidão”. Os indivíduos são representados genotipicamente por vetores binários, onde cada elemento de um vetor denota a presença (1) ou ausência (0) de uma determinada característica: o seu genótipo. Os elementos podem ser combinados formando as características reais do indivíduo, ou o seu fenótipo. Teoricamente, esta representação é independente do problema, pois uma vez encontrada a representação em vetores binários, as operações padrão podem ser utilizadas, facilitando o seu emprego em diferentes classes de problemas. Ou seja, basicamente o algoritmo a partir das exaustivas rotinas de testes vai classificando os indivíduos com base em seu desempenho, os indivíduos que melhor se saírem passam seus genes avante com algumas mutações gerando outros e assim por diante até que se chegue ao resultado esperado (CARVALHO, 2019).
O Recozimento Simulado tem sua origem na analogia entre o processo físico do resfriamento de um metal em estado de fusão e o problema de otimização. O conceito de Recozimento Simulado foi apresentado inicialmente como uma técnica de otimização combinatória por KIRKPATRICK et al. (1983), que o utilizaram no projeto de sistemas eletrônicos.
A mecânica estatística é a disciplina central da física da matéria condensada que estuda as propriedades agregadas de um conjunto elevado de átomos existentes em um líquido ou sólido. Como o número de átomos é da ordem de 1023/cm3, somente as características mais prováveis do sistema em equilíbrio térmico serão observadas em experimentos. Isto é caracterizado pelas propriedades médias e pequenas flutuações em torno das mesmas. No procedimento foi incorporado um aproveitamento cuidadoso de passos de subida, ou seja, passos que resultam em um aumento da função objetivo, visando facilitar a obtenção do ótimo global. E foi esta probabilidade de se aceitar passos que levam a um valor pior da função objetivo que levou a um algoritmo que foge dos mínimos locais possibilitando a convergência para o ótimo global. Metropolis introduziu um algoritmo simples para simular o sistema de átomos em equilíbrio numa determinada temperatura. Em cada passo do algoritmo são dados deslocamentos aleatórios em cada átomo. O Recozimento Simulado consiste em primeiro “fundir” o sistema a ser otimizado a uma temperatura elevada e depois em reduzir a temperatura até que o sistema “congele” e não ocorra nenhuma melhora no valor da função objetivo. Em cada temperatura a simulação deve ser executada num número tal de vezes que o estado de equilíbrio seja atingido. A sequência de temperaturas e o número de rearranjos tentados em cada temperatura para o equilíbrio representam o esquema de recozimento simulado (SOEIRO et al., 2019).
	Algoritmos genéticos e de recozimento simulado são algoritmos de computação intensiva, ou seja, podem demandar elevado tempo de processamento. Apesar do elevado consumo de tempo de CPU, os dados usados nestes algoritmos não apresentam dependências, tornando-os bons algoritmos para paralelização, o que lhes confere o benefício do uso de múltiplos núcleos de processamento.
Neste projeto serão desenvolvidos programas que farão uso de algoritmos genéticos e de recozimento simulado, visando à análise de trechos críticos de processamento. A paralelização de algoritmos deve priorizar os trechos de código de maior consumo de processamento. A análise de desempenho de programas pode ser realizada por ferramentas como o próprio Visual Studio, em sua versão Professional ou superior, e o Paradyn. Ambas as ferramentas analisam a execução do programa apontando os trechos de código onde a paralelização pode vir a trazer redução de tempo de execução.
Após a análise de desempenho das aplicações desenvolvidas será estudada a biblioteca OpenMP. Em paralelo ao estudo da biblioteca uma apostila será construída e posteriormente disponibilizada aos acadêmicos do curso de ciência da computação. Esta apostila irá ter como objetivo apresentar os conceitos e funções necessárias para a compreensão e uso da biblioteca OpenMP.
Posteriormente os programas desenvolvidos serão paralelizados, nos trechos apontados pela análise de desempenho, usando a biblioteca estudada. Por fim as implementações sequenciais e paralelas serão avaliadas quanto à qualidade dos resultados obtidos e o tempo de execução.

<div id="referencia"></div>

# REFERÊNCIAS:

[0] AMD. Processadores AMD Ryzen Threadripper. Disponível em: <a href="https://www.amd.com/pt/products/ryzen-threadripper">AMD Ryzen Threadripper</a>. Acesso em: 27/04/2019.<br>

[1] DORNELLES, E. et al. Um estudo comparativo de desempenho utilizando programação sequencial VS paralela aplicado em Algoritmos Genéticos. Salão do Conhecimento, [S.l.], ago. 2014. ISSN 2318-2385. Disponível em: <a href="https://www.publicacoeseventos.unijui.edu.br/index.php/salaoconhecimento/article/view/3409">Estudo Comparativo</a>. Acesso em: 30/04/2019.<br>

[2] HOLLAND, J. H. Adaptation in natural and artificial systems. Ann Arbor: University of Michigan Press, 1975.
KIRKPATRICK, S.; GELATT, C. D.; VECCHI, M. P. Optimization by simulated annealing. Science, v. 220, n. 4598, p. 671-680, Maio 1983.<br>

[3] CARVALHO, A. P. L. F. Algoritmos Genéticos. Disponível em: <a href="<http://conteudo.icmc.usp.br/ pessoas/andre/research/genetic/>">Algoritmos Genéticos</a>. Acesso em: 30/04/2019.<br>

[4] SOEIRO, F. J. C. P; BECCENERI, J. C.; SILVA Neto, A. J. Recozimento Simulado (Simulated Annealing). Disponível em: <a href="mtc-m16d.sid.inpe.br/archive.cgi/sid.inpe.br/mtc-m19@80/2010/ 01.20.19.25">Recozimento Simulado</a>. Acesso em: 28/04/2019.<br>

[5] OpenMP. The OpenMP API specification for parallel programming. Disponível em: <a href="https://www.openmp.org/">OpenMP</a>. Acesso em: 28/04/2019.<br>

[6] PARADYN. Disponível em: <a href="http://www.paradyn.org/index.html">Paradyn</a>. Acesso em: 29/04/2019.<br>
