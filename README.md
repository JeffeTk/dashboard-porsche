Quais perguntas de negócio escolhi, e por quê

Quais modelos mais vendem em cada estado? Mostra onde cada linha da Porsche tem mais força. Isso orienta como distribuir o estoque e onde investir em marketing regional. Agrupei os modelos em famílias (911, 718, Cayenne, Macan, Panamera, Taycan). A base tem só 100 vendas espalhadas por 33 estados, então olhar modelo por modelo dava muitos empates sem significado.
Qual ano-modelo mais vende, e qual o modelo líder em cada ano? Indica se o cliente prefere carros novos ou seminovos e qual geração de cada modelo tem mais saída. Resposta: o ano-modelo 2024 lidera com 29 vendas.
Quais carros são populares em cada cidade? Ajuda a entender o mercado local. A maioria das cidades tem só 1 ou 2 vendas, então criei destaques que comparam cidades e famílias: cidade com maior receita, família mais vendida no maior número de cidades, modelo vendido em mais cidades e concentração de receita.
Indicadores de topo: total de vendas, receita, ticket médio e taxa de entrega. Dão a visão geral antes do detalhe.
Filtros: modelo, ano-modelo, cidade e forma de pagamento. São as dimensões que um gestor comercial usaria para recortar a análise.

2. O prompt e o que mudou até a versão final

Prompt usado:

Renderize uma dashboard em html ao lado. Indicadores de topo, como total de vendas e receita. Filtros: Model Porsche, Model year, City, Pay method. Perguntas de negócio e KPIs: Quais os modelos de carro mais vendidos por estado; Qual o ano do modelo de carro mais vendido por ano; quero insight de carros populares de vendas com base nos dados em cada cidade. Sobre o UI/UX, se baseie no site oficial da Rockstar Games Brasil (GTA V); tenha um ar elegante e refinado.

Mandei um único prompt, junto com o arquivo .pbix. Não reescrevi o prompt entre versões. As mudanças vieram da leitura dos dados e de uma revisão visual:

A pergunta “ano do modelo mais vendido por ano” foi reinterpretada. A base não tem data de venda, então o recorte passou a ser só pelo ano-modelo.
“Modelo mais vendido por estado” virou um gráfico por família de modelo, com o modelo líder de cada estado indicado ao lado. Os empates aparecem marcados.
Na revisão visual, os números grandes dos indicadores estavam se sobrepondo. Reduzi o tamanho da fonte e corrigi um erro de texto (“temm” → “têm”).

3. Tratamento da base antes de ir para a IA

No Power Query:

Promoção da primeira linha a cabeçalho.
Definição dos tipos das colunas (inteiro, texto).
Remoção das colunas originais “sujas” (sale_date, porsche_model, sale_price, city etc.), mantendo só as versões tratadas (...Sanitized).
Remoção da coluna de data (SaleDateSanitized).

Ajustes feitos durante a geração da dashboard:

Os dados foram extraídos de dentro do .pbix (tabela Sanitized, 100 linhas).
Os preços estavam em centavos. Dividi por 100 (por exemplo, 7.950.000 → US$ 79.500).
Criei a coluna “família” a partir da primeira palavra do modelo.
Traduzi as formas de pagamento para o português.
Defini a regra de desempate: com a mesma quantidade de vendas, vence o modelo de maior receita.

Limitações que ficaram sem tratamento:

Nomes de clientes e vendedores com maiúsculas e minúsculas misturadas (ex.: “SOPHIA Miller”, “Daniel-Jones”).
Status de entrega com variações parecidas que poderiam ser agrupadas (Pending, Pending Approval, Pending Review, Awaiting…).
A receita inclui as 7 vendas canceladas.

4. ChatGPT com Canvas, agente com skill, ou os dois?

Nenhum dos dois com ChatGPT. Usei o Claude (da Anthropic) funcionando como agente com skills:

Ele leu o arquivo .pbix e calculou os dados com código.
Seguiu uma skill de visualização de dados para escolher os tipos de gráfico e validar as cores para daltonismo.
Seguiu as diretrizes de design de página e publicou a dashboard como artifact.

5. Endereço da dashboard publicada

https://claude.ai/artifact/FxJECfF3www3QQ8qQB4sfw
