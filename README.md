# Projeto Desafio Netflix

## Dataset
> https://www.kaggle.com/datasets/rounakbanik/the-movies-dataset?resource=download&select=ratings_small.csv

## Objetivo
> O objetivo deste projeto é prever a nota que um usuário atribuiria a um filme que ele ainda não assistiu. Para isso, foi utilizada a decomposição SVD (Singular Value Decomposition) de uma matriz de avaliações, onde cada entrada representa a avaliação de um usuário a um filme. A decomposição SVD permite descobrir padrões subjacentes nas avaliações e fazer recomendações com base nesses padrões.


#### Justificativa para o Uso da SVD
> A decomposição SVD é útil porque nos permite trabalhar com uma versão "simplificada" da matriz de avaliações, capturando as informações mais importantes (maiores padrões de variação) e ignorando o ruído (informações menos relevantes). Isso é especialmente importante em recomendações, onde há muitas avaliações ausentes. Ao decompor a matriz, conseguimos "preencher" essas lacunas de forma mais eficiente, com base nas correlações identificadas nos dados disponíveis.  
> 
> Além disso, a propriedade de ortonormalidade das matrizes 𝑈 e 𝑉 simplifica os cálculos e garante a unicidade da solução, eliminando a possibilidade de múltiplas soluções para o problema da decomposição.

> Dada uma matriz original $A \in \mathbb{R}^{M \times N}$  
> A decomposição SVD a transforma em três matrizes componente: 𝑈,$ \Sigma $ e 𝑉
> de forma que: 
> $$ 𝐴=𝑈 \Sigma 𝑉^𝑇 $$
>
> Essas quatro matrizes são:
>
> * $A$ tem uma linha por usuário e uma coluna por filme
> * $U \in \mathbb{R}^{M \times M}$ tem uma linha por usuário e uma coluna por perfil
> * $\Sigma \in \mathbb{R}^{N \times N}$ é quadrada e mapeia perfis para perfis
> * $V \in \mathbb{R}^{N \times N}$ tem uma linha por perfil e uma coluna por filme.
>
> A decomposição ajuda a simplificar a matriz original, facilitando a identificação de correlações entre usuários e filmes, mesmo que um usuário não tenha avaliado determinado filme.

#### Cálculo da Decomposição SVD
> A SVD de uma matriz 𝐴 é calculada como demonstrado acima.
>
> Onde:  
> 
> * 𝑈 é uma matriz ortonormal cujas colunas são os autovetores de $ AA^T $  
> * $ \Sigma $ é uma matriz diagonal cujos elementos são os valores singulares (raízes quadradas dos autovalores de $ AA^T $)  
> * 𝑉 é uma matriz ortonormal cujas colunas são os autovetores de $ A^TA $. 

#### Etapas:
> * Cálculo de 𝑈 e $ \Sigma $: A partir da matriz de covariância $ 𝐴𝐴^𝑇 $, obtemos 𝑈 e $ \Sigma $, sendo que $ \Sigma^2 $ corresponde aos autovalores de $ AA^T $, e as colunas de 𝑈 são os autovetores correspondentes.  
> * Cálculo de 𝑉: De maneira análoga, 𝑉 é obtido a partir da matriz $ A^TA $, sendo suas colunas os autovetores de $ A^TA $.


#### Aplicação da SVD em Recomendações de Filmes
> Após a decomposição da matriz de avaliações, podemos reduzir a dimensionalidade da matriz mantendo apenas os maiores valores de $ \Sigma $. Isso nos permite aproximar a matriz original com uma versão simplificada, preservando as características mais importantes. Em seguida, utilizamos essas informações para prever avaliações faltantes.

#### Passos para a recomendação:

> 1. Gerar uma cópia B da matriz A com um valor aleatório em uma posição aleatória (o valor, antes de ser alterado, precisa ser diferente de 0).
> 2. Decompor a matriz de avaliações usando SVD.
> 3. Reduzir a dimensionalidade mantendo os principais valores singulares.
> 4. Reconstruir a matriz aproximada.
> 5. Utilizar a matriz reconstruída para prever a avaliação de filmes que o usuário ainda não assistiu.
> 6. Calcular o erro entre o valor previsto e o valor real da avaliação.


#### Conclusão
> A decomposição SVD é uma ferramenta poderosa para o sistema de recomendação de filmes, pois permite capturar os principais padrões de preferências dos usuários e características dos filmes. Através da redução de dimensionalidade, conseguimos prever avaliações de forma eficaz, mesmo em um cenário de muitos dados ausentes, como é comum em sistemas de recomendação.