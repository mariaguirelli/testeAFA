-------------------------------------------
## CENÁRIO 02 – PROCESSAMENTO DE VENDA (PDV)
-------------------------------------------
### Caso de Teste 01: Venda completa com sucesso
| ID       | Descrição                                                        |
| :------- | :---------------------------------------------------------------- |
|C02-CT01	 | Venda registrada, estoque reduzido e caixa alimentado.|

| **Pré-condições**                                             |
| :------------------------------------------------------------ |
|Cliente, funcionário e produtos cadastrados.|
|Produto com estoque suficiente.|

| **Passos**                                                        |
| :------------------------------------------------------------ |
DADO que o usuário clica em “Novo” na tela de vendas
E escolhe cliente, funcionário e data
E insere produtos
QUANDO finalizar e salvar
ENTÃO a venda deve aparecer no Livro Caixa.

| **Critérios de Aceitação**                                         |
| :------------------------------------------------------------ |
|Estoque atualizado.|
|Caixa alimentado.|
|Teste realizado e evidenciado|
|https://drive.google.com/file/d/1Z0IcYRJRrL-rlompSx4Jas-BFGHYMo_c/view?usp=drive_link|

### Caso de Teste 02: Produto sem estoque
| ID       | Descrição                                                        |
| :------- | :---------------------------------------------------------------- |
|C02-CT02	 | Sistema deve impedir venda sem estoque.|

| **Pré-condições**                                             |
| :------------------------------------------------------------ |
|Produto com quantidade = 0.|

| **Passos**                                                        |
| :------------------------------------------------------------ |
DADO que o usuário tenta incluir o produto
QUANDO selecionar quantidade
ENTÃO deve exibir mensagem “Estoque insuficiente”.

| **Critérios de Aceitação**                                             |
| :------------------------------------------------------------ |
|Produto não deve entrar na venda.|
|Teste realizado e reprovado: Produto sem estoque e venda foi finalizada normalmente|
|https://drive.google.com/file/d/1mzNibPuDz-qtOPpbVVO4wqYZY3CZdVx_/view?usp=drive_link|

### Caso de Teste 03: Desconto total bloqueado quando há desconto por item
| ID       | Descrição                                                        |
| :------- | :---------------------------------------------------------------- |
|C02-CT03	 | Sistema não deve permitir desconto duplo.|

| **Pré-condições**                                             |
| :------------------------------------------------------------ |
|Venda com desconto individual por item.|

| **Passos**                                             |
| :------------------------------------------------------------ |
DADO que a venda possui produto com desconto
QUANDO tentar aplicar desconto geral
ENTÃO deve bloquear com alerta.

| **Critérios de Aceitação**                                             |
| :------------------------------------------------------------ |
|Desconto total bloqueado.|
|Teste realizado e reprovado: Não é possível realizar desconto por item|
|https://drive.google.com/file/d/1L4F66vJsugCm20Yn6hD_Cpf2QHTJiNbt/view?usp=drive_link|

### Caso de Teste 04: Finalizar venda sem selecionar tipo de documento
| ID       | Descrição                                                        |
| :------- | :---------------------------------------------------------------- |
|C02-CT04	 | Sistema deve impedir finalização sem forma de pagamento.|

| **Pré-condições**                                             |
| :------------------------------------------------------------ |
|Venda pronta para finalizar.|

| **Passos**                                                        |
| :------------------------------------------------------------ |
DADO que o usuário está na tela final
QUANDO clicar em “Salvar” sem escolher tipo de documento
ENTÃO deve exibir erro.

| **Critérios de Aceitação**                                             |
| :------------------------------------------------------------ |
|Finalização bloqueada.|
|Teste evidenciado e aprovado|
|https://drive.google.com/file/d/1wPKubhpaGaX-tixe5Bet4jsk9sI_U5Zk/view?usp=drive_link|
