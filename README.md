# Caderno de Estoque da Padaria

Sistema de controle de estoque para padaria com produção própria e lanchonete.
Tudo em um único arquivo HTML: sem servidor, sem instalação, sem banco externo.

## Publicar como site (GitHub Pages)

1. Crie um repositório novo no GitHub.
2. Envie os arquivos `index.html` e `README.md` (dá para arrastar na própria página do GitHub, em **Add file → Upload files**).
3. Vá em **Settings → Pages**, escolha a branch `main` e a pasta `/ (root)` e salve.
4. Em um ou dois minutos o GitHub mostra o endereço, no formato
   `https://SEU-USUARIO.github.io/NOME-DO-REPOSITORIO/`.

Esse endereço abre o sistema em qualquer navegador, no computador ou no celular.

## Como os dados são guardados

O site já abre com **60 dias de uma padaria fictícia** carregados, para quem entra
ver o sistema funcionando com número na tela em vez de tabela vazia.

A partir daí, a base fica no armazenamento do navegador de quem abriu:

- Cada pessoa tem a própria cópia. O que uma lança não aparece para a outra.
- Os dados ficam no aparelho: trocar de computador ou limpar os dados do navegador zera a base.
- Para começar do zero com os produtos reais, use **Ajustes → Apagar toda a base**.
- Para copiar a base ou levar para outro aparelho, use **Ajustes → Baixar backup JSON**
  e depois **Restaurar backup** no outro.

Se o objetivo for várias pessoas lançando na mesma base ao mesmo tempo — produção,
almoxarifado e lanchonete vendo os mesmos números ao vivo — esta versão não serve:
aí é preciso um banco de dados compartilhado, que é outro tipo de hospedagem.

## O que tem dentro

| Área | Para que serve |
|---|---|
| Visão da diretoria | Capital parado, desperdício em R$ e %, dinheiro a vencer, recuperável em 12 meses |
| Painel | Vence primeiro, comprar hoje, consumo dos últimos 14 dias |
| Pedidos dos setores | Requisição do setor, fila do almoxarifado, separação item a item, impressão |
| Pedido do setor | A mesma tela do ponto de vista de quem pede, com o status da separação |
| Leitor de código | Bipagem de entrada, saída e perda por código de barras de unidade ou caixa |
| Entrada de mercadoria | Recebimento em caixa, unidade ou unidade base, criando lote com validade |
| Saída para produção | Baixa automática por FEFO, rateando entre lotes, com setor e responsável |
| Kanban de validade | Vencido, crítico, atenção e em dia, com o valor em risco de cada lote |
| Desperdício | Perda com motivo obrigatório e gráficos por motivo e por setor |
| Balanço e conversão | Contagem em caixa + unidade + fração, diferença em quantidade e em dinheiro |
| Curva ABC e compras | Classe, giro, cobertura, ponto de pedido e sugestão de compra |
| Relatórios | Filtro por período, produto, setor e tipo, com exportação CSV |
| Produtos | Cadastro com a conversão da caixa |
| Códigos e etiquetas | Código do fabricante e código interno EAN-13 com folha de etiquetas |
| Setores e responsáveis | Cadastro dos setores que aparecem na saída e no desperdício |
| Ajustes | Lead time, faixas de validade, cobertura alvo, modo setor, backup |
| Como usar o sistema | Manual dentro do próprio sistema |

## Contas usadas

    consumo médio diário = consumo do período ÷ dias do período
    giro                 = consumo do período ÷ estoque atual
    cobertura            = estoque atual ÷ consumo médio diário
    ponto de pedido      = consumo médio diário × lead time + estoque mínimo
    comprar              = consumo médio diário × (lead time + cobertura alvo) − estoque atual

Cobertura alvo padrão: classe A 7 dias, B 15 dias, C 30 dias. Tudo editável em Ajustes.

## Antes de usar para valer

1. Cadastrar os 20 produtos que puxam a maior parte da compra.
2. Conferir a conversão de cada caixa com a embalagem na mão.
3. Gravar os códigos de barras e imprimir etiqueta para o que não tem código.
4. Fazer a contagem inicial e lançar como entrada, com a validade real de cada lote.
5. Colocar a saída na rotina diária.
6. Curva ABC e giro só ficam confiáveis a partir do 30º dia de lançamento.

## Limitações

- Não emite nota fiscal e não integra com fornecedor ou ERP.
- Não tem login por pessoa: o responsável de cada lançamento é digitado.
- O modo setor trava o aparelho na tela de pedido, mas é uma trava contra clique errado, não contra má-fé.
