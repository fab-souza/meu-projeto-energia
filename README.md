# meu-projeto-energia

![Badge em Desenvolvimento](http://img.shields.io/static/v1?label=STATUS&message=EM%20DESENVOLVIMENTO&color=GREEN&style=for-the-badge)

![Badge code size](https://img.shields.io/github/languages/code-size/fab-souza/meu-projeto-energia)
![Badge de Atualização](https://img.shields.io/github/last-commit/fab-souza/meu-projeto-energia)
![Release](https://img.shields.io/github/release-date/fab-souza/meu-projeto-energia)

Repositório de um projeto particular sobre o setor energético nacional.

Inicialmente, retirei os dados da Empresa de Pesquisa Energética (EPE) através do link: 

https://www.epe.gov.br/pt/publicacoes-dados-abertos/publicacoes/balanco-energetico-nacional-2022
![matriz2021](https://user-images.githubusercontent.com/67301805/177010609-6a010d57-4a55-479f-ae53-e9e59e438117.jpg)
![m-unidades](https://user-images.githubusercontent.com/67301805/177010616-e2020aa2-6e0f-4f48-a3ea-4e94fcf8251b.jpg)
![m-con](https://user-images.githubusercontent.com/67301805/177010623-54ae6d91-bc0c-4aa4-8d04-3adec9fdb341.jpg)

Dentre estas três planilhas, escolhi trabalhar com a primeira, pois ela engloba todas as fontes de energia, ao contrário das outras duas, em que uma não havia registros de biogás e a outra não mencionava energia solar. Achei melhor editar a planilha antes de iniciar a análise de dados, pois dentro dela havia duas planilhas, a primeira em diversas unidades de medida (mil m³, GWh, tep, mil tep), enquanto a segunda estava padronizada em mil tep. A planilha editada ficou da seguinte forma:

![mil tep](https://user-images.githubusercontent.com/67301805/180580388-64554c7e-d80b-4946-b8c2-53209e917482.jpg)

Os dados analisados estão no arquivo BLÁ.jp em que foi feita uma limpeza da tabela, eliminando dados relacionados a energias não renováveis. Considerando que a maioria das linhas do dataframe refere-se a diferentes fontes, preferi abordar somente o quanto foi produzido, ou seja, selecionando apenas a linha 'PRODUÇÃO' que resultou na seguinte tabela:

![epe](https://user-images.githubusercontent.com/67301805/180874294-e777a861-df7e-4fd5-9a3d-08733847812b.jpg)

<br>
***********************************************************************************************************
<br><br>

Passando para a base de dados da ANEEL (fonte: https://dados.gov.br/dataset/siga-sistema-de-informacoes-de-geracao-da-aneel), o resultado foi uma surpresa. Pois os dados estavam espalhados em algumas colunas de forma disforme, ou seja, algumas colunas tinham informações e outras, não.

![aneel](https://user-images.githubusercontent.com/67301805/181395110-593085b7-1e33-452a-8579-f61a3835ef8d.jpg)

Efetuei a edição da base de dados até ser possível abrir o arquivo sem erros.


O Ministério de Minas e Energia disponibilizou o Balanço Energético Nacional (BEN) com dados referente à geração registrada em 2021, pelo link:

https://www.gov.br/mme/pt-br/assuntos/secretarias/spe/publicacoes/balanco-energetico-nacional/ben-2022/ben_sintese_2022_pt.pdf/view

Usarei estes dados como uma forma de conferir o que for calculado neste projeto.
