# meu-projeto-energia

![Badge Finalizado](http://img.shields.io/static/v1?label=STATUS&message=FINALIZADO&color=BLUE&style=for-the-badge)

![Badge code size](https://img.shields.io/github/languages/code-size/fab-souza/meu-projeto-energia)
![Badge de Atualização](https://img.shields.io/github/last-commit/fab-souza/meu-projeto-energia)

Este é o repositório de um projeto particular sobre o setor energético nacional.

| :placard: Vitrine.Dev |     |
| -------------  | --- |
| :sparkles: Nome        | **Análise sobre o setor energéico**
| :label: Tecnologias | Python
| :rocket: URL         | https://github.com/fab-souza/meu-projeto-energia
| :fire: Desafio     | Projeto particular

A EPE (Empresa de Pesquisa Energética) é uma empresa pública, instituída nos termos da Lei n° 10.847, de 15 de março de 2004, e do Decreto n° 5.184, de 16 de agosto de 2004. Sua finalidade é prestar serviços na área de estudos e pesquisas destinados a subsidiar o planejamento do setor energético, tais como energia elétrica, petróleo e seus derivados, carvão mineral e fontes energéticas renováveis. A Lei n° 10.847, em seu Art. 4º, inciso II, estabelece entre as competências da EPE a de elaborar e publicar o Balanço Energético Nacional – BEN.

O relatório consolidado BEN documenta e divulga, anualmente, extensa pesquisa e a contabilidade relativas à oferta e consumo de energia no Brasil, contemplando as atividades de extração de recursos energéticos primários, sua conversão em formas secundárias, a importação e exportação, a distribuição e o uso final da energia.



Inicialmente, retirei os dados da EPE através do link: 

https://www.epe.gov.br/pt/publicacoes-dados-abertos/publicacoes/balanco-energetico-nacional-2022

![matriz2021](https://user-images.githubusercontent.com/67301805/177010609-6a010d57-4a55-479f-ae53-e9e59e438117.jpg)
![m-unidades](https://user-images.githubusercontent.com/67301805/177010616-e2020aa2-6e0f-4f48-a3ea-4e94fcf8251b.jpg)
![m-con](https://user-images.githubusercontent.com/67301805/177010623-54ae6d91-bc0c-4aa4-8d04-3adec9fdb341.jpg)

Dentre estas três planilhas, escolhi trabalhar com a primeira, pois ela engloba todas as fontes de energia, ao contrário das outras duas, em que uma não havia registros de biogás e a outra não mencionava energia solar. Achei melhor editar a planilha antes de iniciar a análise de dados, pois dentro dela havia duas planilhas, a primeira em diversas unidades de medida (mil m³, GWh, tep, mil tep), enquanto a segunda estava padronizada em mil tep. A planilha editada ficou da seguinte forma:

![mil tep](https://user-images.githubusercontent.com/67301805/180580388-64554c7e-d80b-4946-b8c2-53209e917482.jpg)

Ela está disponibilizada no arquivo epe2021.xlsx

Os dados analisados estão no arquivo projeto_energia_EPE.ipynb em que foi feita uma limpeza da tabela, eliminando dados relacionados a energias não renováveis. Considerando que a maioria das linhas do dataframe refere-se a diferentes fontes, preferi abordar somente o quanto foi produzido, ou seja, selecionando apenas a linha 'PRODUÇÃO' que resultou no seguinte gráfico:

![epe](https://user-images.githubusercontent.com/67301805/180874294-e777a861-df7e-4fd5-9a3d-08733847812b.jpg)



Também adicionei neste repositório o PDF disponibilizado pelo Ministério de Minas e Energia, o Balanço Energético Nacional (BEN) com dados referentes à geração registrada em 2021, caso haja curiosidade em entender os conceitos citados no notebook.

Fonte: https://www.gov.br/mme/pt-br/assuntos/secretarias/spe/publicacoes/balanco-energetico-nacional/ben-2022/ben_sintese_2022_pt.pdf/view

<!---

O Ministério de Minas e Energia disponibilizou o Balanço Energético Nacional (BEN) com dados referente à geração registrada em 2021, pelo link:

>https://www.gov.br/mme/pt-br/assuntos/secretarias/spe/publicacoes/balanco-energetico-nacional/ben-2022/ben_sintese_2022_pt.pdf/view

>Usarei estes dados como uma forma de conferir o que for calculado neste projeto.

-->



<br>
***********************************************************************************************************
<br><br>

Passando para a base de dados da ANEEL (fonte: https://dados.gov.br/dataset/siga-sistema-de-informacoes-de-geracao-da-aneel), o resultado foi uma surpresa. Pois as variáveis estavam concentradas na primeira célula, enquanto os dados estavam espalhados em algumas colunas de forma disforme, ou seja, algumas colunas tinham informações e outras não.

![aneel](https://user-images.githubusercontent.com/67301805/181395110-593085b7-1e33-452a-8579-f61a3835ef8d.jpg)

Efetuei a edição da base de dados até ser possível abrir o arquivo sem erros. A base de dados contém mais de quinze mil linhas, com o registro de usinas que já estão operando, as que estão em construção e outras que ainda estão no papel.

A base de dados possui 23 variáveis, entre elas um divisão das usinas por UF, tipo de geração, origem de combustível, a longitude e latiude das usinas e o último registro de potência (em kW) que foi produzida.

Ao retirar as usinas do tipo 'Fóssil' e 'Nuclear', a base de dados ficou com quase 12,9 mil registros e ao filtrar por usinas que estão ativas, os dados foram reduzidos a um pouco mais de 11 mil registros.

Foram plotados gráficos dividindo as usinas por tipo de fonte 

![agro](https://user-images.githubusercontent.com/67301805/182253420-0a44deb7-95ee-4d5e-8ac7-edfced1963d4.jpg)
![vento](https://user-images.githubusercontent.com/67301805/182253439-3dd24199-4cde-41f7-816f-b2da8655bb8d.jpg)

e por combustível.

![solar](https://user-images.githubusercontent.com/67301805/182839401-91b52b7b-c63e-455d-b4bc-b596360be484.jpg)
![vento](https://user-images.githubusercontent.com/67301805/182839427-1971c466-e469-4d26-9057-896bb9584f88.jpg)


A análise completa está em projeto_energia_SIGA.ipynb

<br>
***********************************************************************************************************
<br><br>

Ainda sobre o Brasil, criei um notebook no Kaggle (link: https://www.kaggle.com/code/fabianadesouza/meu-projeto-energia-nacional) para plotar mapas com a geolocalização das usinas, divididas por fontes:

- Usinas eólicas:

![usinas-eolica](https://user-images.githubusercontent.com/67301805/185011863-2b8569fe-592c-42e0-b843-9e8bfb4cc7a7.jpg)

- Usinas hidrelétricas:

![](https://user-images.githubusercontent.com/67301805/185011881-84ab876c-f209-4778-aa5d-f19b712c8238.jpg#vitrinedev)

- Usinas solar:

![usinas_solar](https://user-images.githubusercontent.com/67301805/185685169-8562c799-c78c-4885-9637-8ec40c2c1b89.jpg)


O arquivo usado fio o renovaveis_operando.csv

Acredito 	que o notebook tenha ficado muito grande, devido a quantidade de mapas que plotei, e talvez seja este o motivo que me impede de salvar e compartilhar o link corretamente. Cheguei a fazer o download, mas os mapas não aparecem no arquivo. Como pode ser verificado em meu-projeto-energia-nacional.ipynb


<br>
***********************************************************************************************************
<br><br>

Para fazer uma análise de dados internacionais, utilizei a base de dados disponível no Kaggle, o Renewable Energy (https://www.kaggle.com/datasets/programmerrdai/renewable-energy), no meu notebook:

https://www.kaggle.com/code/fabianadesouza/meu-projeto-energia-internacional

Os registros vão até 2020, mas deu para ter uma ideia de como está o setor energético dos países. Decidi trabalhar somente com os dados do BRICS, porque estes países, na época da formação do grupo, em 2009, foram considerados países emergentes, com características econômicas semelhantes. Fonte: https://www.todamateria.com.br/brics/

Plotei os gráficos de consumo:

![consumo_brasil](https://user-images.githubusercontent.com/67301805/184909775-41d164ff-e6b2-4f2e-9335-12d785d98fdf.png)

E ao final na análise, plotei um gráfico apresentando a porcentagem de produção de energia por fonte:

![producao_brasil](https://user-images.githubusercontent.com/67301805/187009164-eca3a658-797d-43f9-b463-ff1c87984619.png)


### Conclusão:

Segundo o dataset do Kaggle, no Brasil, as usinas hidrelétricas são responsáveis por gerar mais de 70% da energia entre as renováveis. Enquanto nos outros países, a porcentagem é de no máximo 60% e com maior participação de outras fontes, como a eólica, solar, biomassa e geotérmica. Ou seja, há uma dependência muito grande das fontes hídricas, que em caso de escassez (como já ocorreu), pode gerar um aumento na fatura de energia, causada pela ativação de usinas que consomem outras fontes e taxa extra por nível de bandeira tarifária.
 
E ao analisar a matriz energética, disponibilizada pela EPE, verifica-se que para suprir a demanda industrial, agrícola, de transporte e elétrica, o país ainda usa mais fontes não renováveis. Sei que não estou abordando fatores de conversão de energia e que a instalação de fontes renováveis ainda tem um custo alto, porém acredito que uma maior diversificação de fontes de energia só tende a trazer benefícios, como a redução da emissão de CO2 e eliminar a dependência de uma fonte. 


