# PDF Studio — All-in-One

![Versão](https://img.shields.io/badge/versão-1.0-blue)
![Ferramentas](https://img.shields.io/badge/ferramentas-19-blueviolet)
![Plataforma](https://img.shields.io/badge/plataforma-Web-2563eb)

## Sobre o projeto

PDF Studio é um aplicativo web multifuncional destinado à organização, edição de páginas, conversão e divisão de documentos PDF. Desenvolvido em HTML, CSS e JavaScript, reúne 19 ferramentas em quatro módulos, com interface escura, responsiva e processamento dos documentos no navegador.

Não exige instalação de software, conta de usuário, API key ou servidor de processamento. A versão 1.0 utiliza bibliotecas externas via CDN e necessita de conexão para carregá-las; não há garantia de funcionamento totalmente offline.

## Funcionalidades

### 1. Mesclar e organizar

| Ferramenta | Descrição | Saída |
|---|---|---|
| Mesclar PDFs | Une documentos respeitando a sequência atual das páginas. | PDF |
| Reorganizar páginas | Altera a ordem com as setas para cima e para baixo nas miniaturas, inclusive entre documentos. | PDF |
| Excluir páginas | Remove as páginas marcadas, mantendo as demais. | PDF |
| Compactar (raster) | Recria páginas com imagens JPEG, com qualidade configurável de 0,30 a 0,95 e escala de 0,5 a 2. Padrões: 0,65 e 1,1. | PDF |

### 2. Editar e assinar (nome do menu original)

| Ferramenta | Descrição | Saída |
|---|---|---|
| Girar páginas | Rotação de 90° à direita, 180° ou 90° à esquerda. Aplica às páginas marcadas ou a todas quando nenhuma estiver marcada. | PDF |
| Recortar margens | Ajusta independentemente as margens esquerda, direita, superior e inferior em pontos PDF (pt). Padrão: 10 pt em cada lado. | PDF |
| Marca-d’água | Insere texto diagonal semitransparente em todas as páginas. Tamanho de 5 a 150 pt e opacidade de 0,01 a 1; padrões de 45 pt e 0,18. | PDF |
| Numerar páginas / Bates | Insere identificadores sequenciais com prefixo opcional e número inicial configurável, no cabeçalho ou rodapé central. | PDF |
| Cabeçalho e rodapé | Insere textos centralizados no topo e/ou na parte inferior de todas as páginas. | PDF |
| Redimensionar páginas | Adapta o documento aos formatos A4 (210 × 297 mm) ou Carta, mantendo a proporção do conteúdo. | PDF |
| N-Up | Organiza duas ou quatro páginas por folha A4 ou Carta. | PDF |
| Tons de cinza | Converte as páginas em imagens em escala de cinza, com escala de renderização de 0,5 a 2,5 (padrão 1,5). | PDF |

> Apesar do nome do menu, esta versão não implementa assinatura eletrônica ou digital. A numeração Bates é uma sequência simples com prefixo, sem recursos avançados de identificação jurídica.

### 3. Converter

| Ferramenta | Descrição | Saída |
|---|---|---|
| PDF para JPG / PNG | Renderiza todas as páginas como imagens individuais, com escala de 0,5 a 3 (padrão 1,5), nomeadas sequencialmente. | ZIP com JPG ou PNG |
| Imagens para PDF | Converte JPG, JPEG, PNG e WEBP em um documento, com uma imagem por página, nas dimensões próprias de cada imagem. | PDF |
| PDF para texto | Extrai a camada textual existente, com separadores de página. Não executa OCR. | TXT UTF-8 |

### 4. Dividir PDF

| Ferramenta | Descrição | Saída |
|---|---|---|
| Extrair páginas | Seleciona páginas específicas ou intervalos para formar um único documento. Ex.: `1-3, 5, 8`. | PDF |
| Dividir por intervalos | Gera um documento para cada grupo separado por ponto e vírgula. Ex.: `1-3; 4-6`. | ZIP de PDFs |
| Uma página por PDF | Exporta cada página em um arquivo independente, com nomes sequenciais. | ZIP de PDFs |
| Dividir página ao meio | Corte vertical em metades esquerda/direita ou horizontal em metades superior/inferior, na ordem de leitura. Útil para digitalizações de livros com duas páginas por folha. | PDF |

## Interface e recursos gerais

- Tema escuro e layout responsivo, com menu lateral no desktop e navegação adaptada a telas menores.
- Seleção múltipla de arquivos e importação por arrastar e soltar.
- Lista de arquivos com nome, tamanho, quantidade de páginas e botão de remoção individual.
- Contadores de documentos e páginas carregadas.
- Miniaturas das primeiras 80 páginas; as demais aparecem com identificação textual.
- Seleção de páginas por caixas de marcação e reorganização por setas.
- Painel de configurações específico para cada ferramenta.
- Mensagens de processamento, conclusão e erros.
- Download automático do resultado e link para baixar novamente enquanto disponível.
- Botão Limpar projeto, com confirmação quando existem arquivos carregados.

## Formatos suportados

| Entrada | Saída |
|---|---|
| PDF (.pdf) | PDF (.pdf) |
| JPEG (.jpg, .jpeg) | JPEG (.jpg em ZIP) |
| PNG (.png) | PNG (.png em ZIP) |
| WEBP (.webp) | TXT (.txt) e ZIP (.zip), conforme a ferramenta |

Os formatos de entrada e saída não são intercambiáveis em todas as ferramentas. WEBP é aceito para criação de PDF, não como formato de exportação de páginas.

## Como utilizar

1. Abra o aplicativo em um navegador moderno com acesso à internet para carregar as dependências.
2. Clique em **Adicionar arquivos** ou arraste os documentos para a área de carregamento.
3. Escolha um dos quatro módulos e selecione a ferramenta desejada.
4. Confira a sequência das páginas, reorganize ou marque as necessárias, conforme a operação.
5. Configure os parâmetros disponíveis no painel da ferramenta.
6. Clique no botão de processamento e salve o arquivo gerado.
7. Para aplicar outra transformação sobre o resultado, carregue o PDF exportado como nova entrada. As operações não alteram automaticamente os arquivos carregados.

A seleção por caixas de marcação é usada para exclusão e rotação. A extração e a divisão por intervalos usam seus próprios campos. As demais operações sobre PDFs utilizam a sequência global de páginas carregadas.

## Execução local

Salve o arquivo HTML do aplicativo como `index.html` e abra-o em um navegador atualizado (Chrome, Edge ou Firefox, por exemplo). Se a abertura direta apresentar restrições do navegador, utilize um servidor HTTP local.

Opcionalmente, com Python instalado, execute na pasta do projeto:

```bash
python -m http.server 8000
```

Acesse `http://localhost:8000`.

## Publicação no GitHub Pages

1. Crie ou abra o repositório do projeto.
2. Envie `index.html` e este `README.md` para a raiz do repositório.
3. Acesse **Settings → Pages**.
4. Em **Build and deployment**, selecione **Deploy from a branch**.
5. Escolha a branch `main` e a pasta `/ (root)`; salve.
6. Quando a publicação terminar, utilize o endereço fornecido pelo GitHub Pages.

Não é necessário publicar chaves, tokens ou um backend. O endereço real do repositório não foi confirmado nesta documentação.

## Estrutura do projeto

```text
pdf-studio/
├── index.html     # Interface, estilos e lógica do aplicativo
└── README.md      # Documentação
```

## Tecnologias e dependências

| Tecnologia | Finalidade |
|---|---|
| HTML5 | Estrutura da interface |
| CSS3 | Tema escuro e responsividade |
| JavaScript | Processamento, interação e gerenciamento de arquivos |
| [PDF.js 3.11.174](https://github.com/mozilla/pdf.js) | Renderização, miniaturas e extração de texto |
| [pdf-lib 1.17.1](https://github.com/Hopding/pdf-lib) | Manipulação e geração de documentos PDF |
| [JSZip 3.10.1](https://github.com/Stuk/jszip) | Geração de arquivos ZIP |
| Canvas API | Renderização, conversão de imagens e tons de cinza |
| File API, Blob e Object URL | Leitura local e download |

As três bibliotecas JavaScript e o worker do PDF.js são carregados pelo CDN cdnjs. Para uma futura edição realmente offline, é necessário distribuir esses recursos localmente e ajustar as referências, inclusive a do worker.

## Privacidade e segurança

O código processa os documentos na memória do navegador, sem rotina de upload para um servidor. Os arquivos de origem não são sobrescritos. O projeto não é persistido automaticamente após recarregar ou fechar a página. As dependências externas realizam requisições de rede para carregamento do código; portanto, processamento local não significa ausência total de tráfego externo.

## Limitações da versão 1.0

- Não possui OCR, exportação DOCX, edição direta de parágrafos, assinatura digital ou remoção de senhas.
- PDFs criptografados ou corrompidos podem não ser carregados.
- A compactação e a conversão para tons de cinza rasterizam as páginas, eliminando a camada de texto pesquisável e podendo reduzir a qualidade visual. A compactação não garante um arquivo menor.
- O recorte de margens altera a caixa de visualização, sem apagar definitivamente o conteúdo ocultado. Não deve ser usado para censura de informações confidenciais.
- A extração TXT não preserva a diagramação original e não reconhece texto presente apenas em imagens.
- Marca-d’água, cabeçalhos, rodapés e numeração usam fontes padrão e filtram caracteres fora do ASCII, incluindo a remoção de acentos.
- A conversão e a manipulação podem não preservar recursos interativos, formulários, assinaturas existentes, marcadores ou metadados.
- Documentos extensos ou imagens em alta resolução podem consumir grande quantidade de memória.
- O funcionamento depende de suporte às APIs do navegador e da disponibilidade das bibliotecas externas.

## Possíveis evoluções (não implementadas)

- Pacote integralmente offline.
- OCR para PDFs digitalizados.
- Reorganização por arrastar e soltar.
- Compressão que preserve a camada textual.
- Edição de metadados, anotações e assinatura.
- Conversão para DOCX e integração com outras ferramentas documentais.

## Versão e licença

- **Versão documentada:** 1.0 — All-in-One.
- **Código de referência:** `index(20261113-165752).html`, de 13/11/2026.
- **Licença do projeto:** não identificada no código de referência. Definir antes de distribuir sob uma licença específica. As bibliotecas externas possuem suas próprias licenças.

---

PDF Studio — organização, transformação e gerenciamento de documentos em um único ambiente web.
