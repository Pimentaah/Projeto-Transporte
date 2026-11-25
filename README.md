Projeto Transporte

Qual ônibus eu pego para ir daqui até lá em São Paulo?

Este é o meu primeiro projeto de análise de dados com Python. Você informa um ponto de origem e um de destino, e o programa sugere uma linha de ônibus direta (sem baldeação), mostra o caminho em um mapa e, quando possível, avisa quanto tempo falta para o próximo ônibus chegar.

O que ele faz, em poucas palavras
Você escolhe a origem e o destino (latitude e longitude).
O programa procura os pontos de ônibus perto dos dois lugares.
Ele descobre quais linhas passam por um ponto perto da origem e depois por um ponto perto do destino.
Entre elas, escolhe a que exige menos caminhada.
Pergunta à SPTrans quando o próximo ônibus dessa linha chega ao ponto de embarque.
Desenha tudo em um mapa: onde você começa, onde pega o ônibus, as paradas do caminho, onde desce e onde termina.
De onde vêm os dados

O projeto usa duas fontes da SPTrans, a empresa de transporte de São Paulo:

GTFS: arquivos com as linhas, os horários, as paradas e o desenho dos trajetos. É como um "mapa oficial" das linhas.
API Olho Vivo: um serviço que informa, em tempo real, onde estão os ônibus e quando eles chegam.

Os dois se complementam: o GTFS diz por onde a linha passa, e a Olho Vivo diz quando o ônibus chega.

O que eu usei
Python, rodando no Google Colab
pandas, para trabalhar com as tabelas de dados
requests, para conversar com a API
Folium, para desenhar o mapa
Como rodar
Antes de começar, você vai precisar de:
Uma conta Google, para usar o Google Colab
Um token da API Olho Vivo, que se pede de graça no site para desenvolvedores da SPTrans
Os arquivos do GTFS da SPTrans, baixados do mesmo site e colocados na pasta data/_sptrans_gtfs/
Passo a passo
Guarde o token com segurança. No Colab, abra o painel Secrets (o ícone de chave), crie um segredo chamado TOKEN e cole o seu token lá. Não escreva o token direto no código e não o envie para o GitHub!
Abra o notebook note_principal_com_mapa.ipynb no Colab.
Escolha a origem e o destino na seção 6.1 do notebook:
python
origem = {"latitude": -23.5505, "longitude": -46.6333}
destino = {"latitude": -23.5614, "longitude": -46.6559}
raio_busca = 500  # até quantos metros de caminhada você aceita

Esses números são só um exemplo para teste. Para usar outros lugares, clique com o botão direito no Google Maps: ele mostra a latitude e a longitude do ponto. 4. Rode as células em ordem, de cima para baixo. No final aparecem o mapa e o quadro com a recomendação.

Quero ver outra linha

Na seção 8 do notebook existe uma linha LINHA_DESEJADA. Troque o valor, por exemplo "8000-10", para ver outra linha entre as possíveis. Com None, o programa escolhe a melhor opção sozinho. Depois, rode de novo as células seguintes.

Pastas do projeto
Projeto-Transporte/
├── data/
│   └── _sptrans_gtfs/          # arquivos do GTFS da SPTrans
├── note_principal_com_mapa.ipynb   # o notebook com todo o projeto
└── README.md
O que o programa ainda não faz

Por ser um projeto de aprendizado, ele tem limites. Fico feliz em contar quais são:

Só linhas diretas. Se for preciso trocar de ônibus no caminho, ele não encontra a rota.
A caminhada é em linha reta. Ele mede a distância "em voo de pássaro", não pelas ruas.
A previsão nem sempre aparece. Se não houver ônibus rodando ou a API estiver fora do ar, o programa avisa o motivo e mostra o resto da recomendação mesmo assim.
O fundo do mapa pode falhar. Os serviços que fornecem as imagens do mapa mudam as regras de vez em quando. Se o fundo ficar sem ruas, os pontos e o trajeto continuam corretos.
Fontes
SPTrans: portal para desenvolvedores
Mapas: Esri e colaboradores do OpenStreetMap
Autoria

Coloque aqui o seu nome, a instituição ou disciplina e, se quiser, a licença do projeto.
