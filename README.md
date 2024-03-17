# Raspagem de Dados com Python

Este projeto demonstra como realizar a raspagem de dados (web scraping) utilizando Python. Usamos as bibliotecas `requests` e `BeautifulSoup` para extrair informações de tabelas de um site estadual e títulos de notícias relacionadas à COVID do site O Globo.

## Bibliotecas Utilizadas

- `requests`: Para fazer solicitações HTTP.
- `BeautifulSoup` (parte do pacote `bs4`): Para parsear o conteúdo HTML e facilitar a extração de dados.

## Procedimento

### Extração de Dados de Tabela

1. Fazemos uma solicitação à URL que contém os dados de interesse usando `requests.get`.
2. Parseamos o HTML baixado com `BeautifulSoup` e localizamos a tabela de interesse.
3. Iteramos sobre as linhas e células da tabela, extraindo e limpando os dados.

### Conversão de Coordenadas

- Definimos uma função para converter coordenadas de graus, minutos e segundos para um formato decimal, facilitando análises futuras ou mapeamento.

### Raspagem de Títulos de Notícias

- Realizamos uma solicitação ao site do jornal O Globo para extrair títulos de notícias sobre a COVID, demonstrando a versatilidade da raspagem de dados para diferentes tipos de páginas web.

## Código de Exemplo

Aqui está um exemplo simplificado do processo:

```python
import requests
from bs4 import BeautifulSoup

# Baixando conteúdo da página
url = "http://exemplo.com/dados.html"
request = requests.get(url)
soup = BeautifulSoup(request.text, 'html.parser')

# Extraindo e limpando dados da tabela
# ... código para extração de dados da tabela ...

# Raspando títulos de notícias
url_noticias = "https://oglobo.globo.com/busca/?q=covid"
request_noticias = requests.get(url_noticias)
soup_noticias = BeautifulSoup(request_noticias.text, 'html.parser')
headlines = soup_noticias.find_all("div", class_="widget--info__title")
titulos = [h.text.strip() for h in headlines]

print(titulos)
