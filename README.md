# meu-projeto-energia

![Badge em Desenvolvimento](http://img.shields.io/static/v1?label=STATUS&message=EM%20DESENVOLVIMENTO&color=GREEN&style=for-the-badge)

![Badge code size](https://img.shields.io/github/languages/code-size/fab-souza/meu-projeto-energia)
![Badge de Atualização](https://img.shields.io/github/last-commit/fab-souza/meu-projeto-energia)

Este é um repositório de um projeto particular sobre o setor energético nacional.

A EPE (Empresa de Pesquisa Energética) é uma empresa pública, instituída nos termos da Lei n° 10.847, de 15 de março de 2004, e do Decreto n° 5.184, de 16 de agosto de 2004. Sua finalidade é prestar serviços na área de estudos e pesquisas destinados a subsidiar o planejamento do setor energético, tais como energia elétrica, petróleo e seus derivados, carvão mineral e fontes energéticas renováveis. A Lei n° 10.847, em seu Art. 4º, inciso II, estabelece entre as competências da EPE a de elaborar e publicar o Balanço Energético Nacional – BEN.

O relatório consolidado BEN documenta e divulga, anualmente, extensa pesquisa e a contabilidade relativas à oferta e consumo de energia no Brasil, contemplando as atividades de extração de recursos energéticos primários, sua conversão em formas secundárias, a importação e exportação, a distribuição e o uso final da energia.

Em adição a EPE publica o Relatório Síntese no primeiro semestre posterior ao ano base, que apresenta um resumo dos dados a cerca da contabilização da oferta, transformação e consumo final de produtos energéticos no Brasil.


<!---

O Ministério de Minas e Energia disponibilizou o Balanço Energético Nacional (BEN) com dados referente à geração registrada em 2021, pelo link:

>https://www.gov.br/mme/pt-br/assuntos/secretarias/spe/publicacoes/balanco-energetico-nacional/ben-2022/ben_sintese_2022_pt.pdf/view

>Usarei estes dados como uma forma de conferir o que for calculado neste projeto.

-->



Inicialmente, retirei os dados da EPE através do link: 

https://www.epe.gov.br/pt/publicacoes-dados-abertos/publicacoes/balanco-energetico-nacional-2022

![matriz2021](https://user-images.githubusercontent.com/67301805/177010609-6a010d57-4a55-479f-ae53-e9e59e438117.jpg)
![m-unidades](https://user-images.githubusercontent.com/67301805/177010616-e2020aa2-6e0f-4f48-a3ea-4e94fcf8251b.jpg)
![m-con](https://user-images.githubusercontent.com/67301805/177010623-54ae6d91-bc0c-4aa4-8d04-3adec9fdb341.jpg)

Dentre estas três planilhas, escolhi trabalhar com a primeira, pois ela engloba todas as fontes de energia, ao contrário das outras duas, em que uma não havia registros de biogás e a outra não mencionava energia solar. Achei melhor editar a planilha antes de iniciar a análise de dados, pois dentro dela havia duas planilhas, a primeira em diversas unidades de medida (mil m³, GWh, tep, mil tep), enquanto a segunda estava padronizada em mil tep. A planilha editada ficou da seguinte forma:

![mil tep](https://user-images.githubusercontent.com/67301805/180580388-64554c7e-d80b-4946-b8c2-53209e917482.jpg)

Os dados analisados estão no arquivo projeto_energia_EPE.ipynb em que foi feita uma limpeza da tabela, eliminando dados relacionados a energias não renováveis. Considerando que a maioria das linhas do dataframe refere-se a diferentes fontes, preferi abordar somente o quanto foi produzido, ou seja, selecionando apenas a linha 'PRODUÇÃO' que resultou no seguinte gráfico:

![epe](https://user-images.githubusercontent.com/67301805/180874294-e777a861-df7e-4fd5-9a3d-08733847812b.jpg)

<br>
***********************************************************************************************************
<br><br>

Passando para a base de dados da ANEEL (fonte: https://dados.gov.br/dataset/siga-sistema-de-informacoes-de-geracao-da-aneel), o resultado foi uma surpresa. Pois as variáveis estavam concentradas na primeira célula, enquanto os dados estavam espalhados em algumas colunas de forma disforme, ou seja, algumas colunas tinham informações e outras não.

![aneel](https://user-images.githubusercontent.com/67301805/181395110-593085b7-1e33-452a-8579-f61a3835ef8d.jpg)

Efetuei a edição da base de dados até ser possível abrir o arquivo sem erros. A base de dados contém mais de quinze mil linhas, com o registro de usinas que já estão operando, as que estão em construção e outras que ainda estão no papel.

A base de dados possui 23 variáveis, entre elas um divisão das usinas por UF, tipo de geração ('PCH', 'UHE', 'CGH', 'UTE', 'UTN', 'EOL', 'UFV' e 'CGU'), origem de combustível ('Hídrica', 'Fóssil', 'Biomassa', 'Nuclear', 'Eólica', 'Solar' e 'Undi-Elétrica'), suas fontes ('Potencial hidráulico', 'Carvão mineral', 'Petróleo',  'Agroindustriais', 'Gás natural', 'Urânio', 'Resíduos sólidos urbanos', 'Cinética do vento', 'Radiação solar', 'Cinética da água', 'Resíduos animais' e 'Biocombustíveis líquidos') e até uma divisão mais específica por combustível ('Potencial hidráulico', 'Bagaço de Cana de Açúcar', 'Resíduos Florestais', 'Biogás - RU', 'Cinética do vento', 'Lenha', 'Casca de Arroz', 'Radiação solar', 'Carvão Vegetal', 'Gás de Alto Forno - Biomassa', 'Cinética da água', 'Biogás - RA', 'Capim Elefante', 'Óleos vegetais', 'Biogás-AGR', 'Resíduos Sólidos Urbanos - RU', 'Etanol' e 'Carvão - RU'). Porém o que mais chamou minha atenção foi a disponibilidade da longitude e latiude das usinas, possibilitando usar o GeoPandas para apresentar as usinas em um mapa, e o último registro de potência (em kW) que foi produzida.

Ao retirar as usinas do tipo 'Fóssil' e 'Nuclear', a base de dados ficou com quase 12,9 mil registros e ao filtrar por usinas que estão ativas, os dados foram reduzidos a um pouco mais de 11 mil registros.

Para mostrar a diferença de potência gerada entre as usinas hídricas e as demais, plotei o seguinte gráfico:

![pot](https://user-images.githubusercontent.com/67301805/183267782-91ff5b38-de5f-4c54-a94a-6627b031de6d.jpg)

Foram plotados gráficos dividindo as usinas por tipo de fonte 

![agro](https://user-images.githubusercontent.com/67301805/182253420-0a44deb7-95ee-4d5e-8ac7-edfced1963d4.jpg)
![vento](https://user-images.githubusercontent.com/67301805/182253439-3dd24199-4cde-41f7-816f-b2da8655bb8d.jpg)

e por combustível.

![solar](https://user-images.githubusercontent.com/67301805/182839401-91b52b7b-c63e-455d-b4bc-b596360be484.jpg)
![vento](https://user-images.githubusercontent.com/67301805/182839427-1971c466-e469-4d26-9057-896bb9584f88.jpg)

Ainda sobre o Brasil, criei um notebook no Kaggle para plotar mapas com a geolocalização das usinas, divididas por fontes:

- Usinas eólicas
![usinas-eolica](https://user-images.githubusercontent.com/67301805/185011863-2b8569fe-592c-42e0-b843-9e8bfb4cc7a7.jpg)

- Usinas hidrelétricas
![usinas-hidro](https://user-images.githubusercontent.com/67301805/185011881-84ab876c-f209-4778-aa5d-f19b712c8238.jpg)




<br>
***********************************************************************************************************
<br><br>

Para fazer uma análise de dados internacionais, utilizei a base de dados disponível no Kaggle, o Renewable Energy, no meu notebook:

https://www.kaggle.com/code/fabianadesouza/meu-projeto-energia/edit

Os registros vão até 2020, mas deu para ter uma ideia de como está o setor energético dos países. Decidi trabalhar somente com os dados do BRICS, porque estes países, na época da formação do grupo, em 2009, foram considerados países emergentes, com características econômicas semelhantes. Fonte: https://www.todamateria.com.br/brics/

Plotei os gráficos de consumo:
![consumo_brasil](https://user-images.githubusercontent.com/67301805/184909775-41d164ff-e6b2-4f2e-9335-12d785d98fdf.png)
![consumo_russia](https://user-images.githubusercontent.com/67301805/184909804-c65c2744-b1bd-44d0-ac6e-16fa5405a420.png)
![consumo_india](https://user-images.githubusercontent.com/67301805/184909834-550d968d-eade-41e9-9f68-70ad382b31e2.png)
![consumo_china](https://user-images.githubusercontent.com/67301805/184909876-442fe62a-256f-404f-8525-c51ce511acc7.png)
![consumo_africa_sul](https://user-images.githubusercontent.com/67301805/184909896-2dc58f45-a951-497b-8ff0-8f8ae465e794.png)






