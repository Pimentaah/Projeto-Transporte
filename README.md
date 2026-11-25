<div align="center">

# 🚌 Projeto Transporte

### Qual ônibus eu pego para ir daqui até lá em São Paulo?

![Python](https://img.shields.io/badge/Python-3-3776AB?logo=python&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-150458?logo=pandas&logoColor=white)
![Folium](https://img.shields.io/badge/Folium-mapas-77B829)
![Google Colab](https://img.shields.io/badge/Google%20Colab-F9AB00?logo=googlecolab&logoColor=white)
![Status](https://img.shields.io/badge/status-em%20desenvolvimento-yellow)

Meu primeiro projeto de análise de dados com Python: recomenda uma linha de ônibus direta, mostra o caminho no mapa e avisa quando o próximo ônibus chega.

[Abrir no Colab](https://colab.research.google.com/github/SEU-USUARIO/Projeto-Transporte/blob/desenvolvimento/note_principal_com_mapa.ipynb)

</div>

---

## 📑 Índice

- [Como funciona](#-como-funciona)
- [De onde vêm os dados](#-de-onde-vêm-os-dados)
- [Tecnologias](#-tecnologias)
- [Como rodar](#-como-rodar)
- [Quero ver outra linha](#-quero-ver-outra-linha)
- [Estrutura do projeto](#-estrutura-do-projeto)
- [Limitações](#-limitações)
- [Fontes](#-fontes)
- [Autoria](#-autoria)

---

## ✨ Como funciona

Você informa uma **origem** e um **destino**, e o programa faz o resto:

| Passo | O que acontece |
|:---:|---|
| 1️⃣ | Você escolhe a origem e o destino (latitude e longitude) |
| 2️⃣ | O programa procura os pontos de ônibus perto dos dois lugares |
| 3️⃣ | Descobre as linhas que passam perto da origem e depois perto do destino |
| 4️⃣ | Escolhe a que exige **menos caminhada** |
| 5️⃣ | Pergunta à SPTrans quando o próximo ônibus chega ao ponto de embarque |
| 6️⃣ | Desenha tudo em um **mapa interativo** |

No mapa aparecem a origem, o ponto de embarque, as paradas do caminho (numeradas), o ponto de desembarque e o destino.

## 📊 De onde vêm os dados

O projeto usa duas fontes da SPTrans, a empresa de transporte de São Paulo:

| Fonte | Para que serve |
|---|---|
| **GTFS** | Arquivos com linhas, paradas e trajetos. É o "mapa oficial" das linhas e diz **por onde** o ônibus passa. |
| **API Olho Vivo** | Serviço em tempo real que diz **quando** o ônibus chega. |

## 🛠️ Tecnologias

- **Python**, rodando no Google Colab
- **pandas**: trabalhar com as tabelas de dados
- **requests**: conversar com a API
- **Folium**: desenhar o mapa

## 🚀 Como rodar

### Antes de começar

- [ ] Uma conta Google, para usar o [Google Colab](https://colab.research.google.com/)
- [ ] Um **token da API Olho Vivo**, pedido de graça no [site para desenvolvedores da SPTrans](https://www.sptrans.com.br/desenvolvedores/)
- [ ] Os **arquivos do GTFS** da SPTrans, colocados na pasta `data/_sptrans_gtfs/`

### Passo a passo

**1. Guarde o token com segurança.**
No Colab, abra o painel **Secrets** (ícone de chave), crie um segredo chamado `TOKEN` e cole seu token lá.

> ⚠️ Nunca escreva o token direto no código nem o envie para o GitHub.

**2. Abra o notebook** `note_principal_com_mapa.ipynb` no Colab.

**3. Escolha a origem e o destino** na seção 6.1 do notebook:

```python
origem = {"latitude": -23.5505, "longitude": -46.6333}
destino = {"latitude": -23.5614, "longitude": -46.6559}
raio_busca = 500  # até quantos metros de caminhada você aceita
```

> 💡 Esses números são só um exemplo de teste. Para usar outros lugares, clique com o botão direito no Google Maps: ele mostra a latitude e a longitude do ponto.

**4. Rode as células em ordem**, de cima para baixo. No final aparecem o mapa e o quadro com a recomendação.

## 🔄 Quero ver outra linha

Na **seção 8** do notebook existe a variável `LINHA_DESEJADA`:

```python
LINHA_DESEJADA = "8000-10"   # uma linha específica
LINHA_DESEJADA = None        # deixa o programa escolher a melhor
```

Depois de trocar o valor, rode de novo as células seguintes.

## 📁 Estrutura do projeto

```
Projeto-Transporte/
├── 📂 data/
│   └── 📂 _sptrans_gtfs/              # arquivos do GTFS da SPTrans
├── 📓 note_principal_com_mapa.ipynb   # o notebook com todo o projeto
└── 📄 README.md
```

## ⚠️ Limitações

Por ser um projeto de aprendizado, ele ainda tem limites:

- 🚫 **Só linhas diretas:** se for preciso trocar de ônibus, ele não encontra a rota.
- 📏 **Caminhada em linha reta:** a distância é medida "em voo de pássaro", não pelas ruas.
- ⏱️ **A previsão nem sempre aparece:** sem ônibus rodando ou com a API fora do ar, o programa avisa o motivo e mostra o resto da recomendação.
- 🗺️ **O fundo do mapa pode falhar:** os serviços de mapa mudam as regras de vez em quando. Se o fundo ficar sem ruas, os pontos e o trajeto continuam corretos.

## 📚 Fontes

- [SPTrans: portal para desenvolvedores](https://www.sptrans.com.br/desenvolvedores/)
- Mapas: Esri e colaboradores do [OpenStreetMap](https://www.openstreetmap.org/copyright)

## 👤 Autoria

Feito por **SEU NOME** · SUA INSTITUIÇÃO / DISCIPLINA
