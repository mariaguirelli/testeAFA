
-------------------------------------------
## ✅ CENÁRIO 03 – COMPRA POR FORNECEDOR
-------------------------------------------
### Caso de Teste 01: Compra concluída com sucesso
| ID       | Descrição                                                        |
| :------- | :---------------------------------------------------------------- |
|C03-CT01	 | Compra lançada, estoque atualizado e caixa alimentado.|

| **Pré-condições**                                             |
| :------------------------------------------------------------ |
|Fornecedor cadastrado.|
|Produto cadastrado.|

| **Passos**                                                        |
| :------------------------------------------------------------ |
DADO que o usuário cria nova compra
E adiciona produtos
QUANDO finalizar compra
ENTÃO estoque deve ser alimentado.

| **Critérios de Aceitação**                                             |
| :------------------------------------------------------------ |
|Compra CONFIRMADA.|

### Caso de Teste 02: Fornecedor inexistente
| ID       | Descrição                                                        |
| :------- | :---------------------------------------------------------------- |
|C03-CT02	 | Deve impedir compra sem fornecedor.|

| **Pré-condições**                                             |
| :------------------------------------------------------------ |
|Nenhuma.|

| **Passos**                                                        |
| :------------------------------------------------------------ |
DADO que usuário tenta criar compra sem fornecedor
QUANDO clicar em “Salvar”
ENTÃO sistema deve bloquear.

| **Critérios de Aceitação**                                             |
| :------------------------------------------------------------ |
|Mensagem “Fornecedor obrigatório”.|

### Caso de Teste 03: Tipo de documento inválido para compra a prazo
| ID       | Descrição                                                        |
| :------- | :---------------------------------------------------------------- |
|C03-CT03	 | Sistema deve recusar documento que alimenta caixa.|

| **Pré-condições**                                             |
| :------------------------------------------------------------ |
|Compra marcada como “A Prazo”.|

| **Passos**                                             |
| :------------------------------------------------------------ |
DADO que o usuário tenta inserir tipo de documento que alimenta caixa
QUANDO selecionar a opção proibida
ENTÃO deve exibir alerta.

| **Critérios de Aceitação**                                             |
| :------------------------------------------------------------ |
|Documento não deve ser aceito.|

-------------------------------------------
## ✅ CENÁRIO 04 – GESTÃO DE CLIENTES
-------------------------------------------
### Caso de Teste 01: Cadastro de cliente PF com sucesso
| ID       | Descrição                                                        |
| :------- | :---------------------------------------------------------------- |
|C04-CT01	 | Cadastro básico deve ser salvo corretamente.|

| **Pré-condições**                                             |
| :------------------------------------------------------------ |
|Nenhuma.|

| **Passos**                                             |
| :------------------------------------------------------------ |
DADO que usuário clica em “Novo”
E preenche os campos obrigatórios
QUANDO clicar em Salvar
ENTÃO cliente deve aparecer na lista.

| **Critérios de Aceitação**                                             |
| :------------------------------------------------------------ |
|Cadastro salvo.|

### Caso de Teste 02: Tentativa de salvar cliente sem campos obrigatórios
| ID       | Descrição                                                        |
| :------- | :---------------------------------------------------------------- |
|C04-CT02	 | Sistema deve impedir cadastro incompleto.|

| **Pré-condições**                                             |
| :------------------------------------------------------------ |
|Nenhuma.|

| **Passos**                                                        |
| :------------------------------------------------------------ |
DADO que o usuário deixa Nome ou CEP vazio
QUANDO tentar salvar
ENTÃO deve exibir alerta.

| **Critérios de Aceitação**                                             |
| :------------------------------------------------------------ |
|Cadastro bloqueado.|

### Caso de Teste 03: Venda acima do limite de crédito
| ID       | Descrição                                                        |
| :------- | :---------------------------------------------------------------- |
|C04-CT03	 | Sistema alerta e redireciona para Contas a Receber.|

| **Pré-condições**                                             |
| :------------------------------------------------------------ |
|Cliente com limite de crédito.|

| **Passos**                                             |
| :------------------------------------------------------------ |
DADO que o cliente tem limite de R$100
QUANDO a venda ultrapassar esse valor
ENTÃO sistema alerta e abre fluxo de contas a receber.

| **Critérios de Aceitação**                                             |
| :------------------------------------------------------------ |
|Alerta exibido.|
|Venda permitida após confirmação.|

### Caso de Teste 04: Cadastrar dependente corretamente
| ID       | Descrição                                                        |
| :------- | :---------------------------------------------------------------- |
|C04-CT04	 | Dependente deve ser vinculado ao cliente.|

| **Pré-condições**                                             |
| :------------------------------------------------------------ |
|Cliente principal já cadastrado.|

| **Passos**                                             |
| :------------------------------------------------------------ |
DADO que usuário acessa aba Dependentes
E clica em “Novo”
QUANDO selecionar cliente dependente
ENTÃO ele deve ser vinculado.

| **Critérios de Aceitação**                                             |
| :------------------------------------------------------------ |
|Dependente aparece listado.|

-------------------------------------------
## ✅ CENÁRIO 05 – FECHAMENTO DE CAIXA
-------------------------------------------
### Caso de Teste 01: Fechar caixa com sucesso
| ID       | Descrição                                                        |
| :------- | :---------------------------------------------------------------- |
|C05-CT01	 | Caixa do dia fechado e registrado.|

| **Pré-condições**                                             |
| :------------------------------------------------------------ |
|Haver pelo menos uma venda no dia.|

| **Passos**                                             |
| :------------------------------------------------------------ |
DADO que o usuário abre o Livro Caixa
QUANDO clicar em “Fechar Caixa”
ENTÃO o caixa deve ser finalizado.

| **Critérios de Aceitação**                                             |
| :------------------------------------------------------------ |
|O dia fica bloqueado para novas movimentações.|

### Caso de Teste 02: Tentar fechar caixa sem vendas no dia
| ID       | Descrição                                                        |
| :------- | :---------------------------------------------------------------- |
|C05-CT02	 | Sistema deve impedir fechamento vazio.|

| **Pré-condições**                                             |
| :------------------------------------------------------------ |
|Nenhuma venda registrada.|

| **Passos**                                             |
| :------------------------------------------------------------ |
DADO que usuário tenta fechar caixa
QUANDO clicar em Fechar
ENTÃO deve exibir alerta de “nenhuma movimentação”.

| **Critérios de Aceitação**                                             |
| :------------------------------------------------------------ |
|Bloqueio do fechamento.|

### Caso de Teste 03: Retirada de valores com sucesso
| ID       | Descrição                                                        |
| :------- | :---------------------------------------------------------------- |
|C05-CT03	 | Retirada registrada e visível no livro caixa.|

| **Pré-condições**                                             |
| :------------------------------------------------------------ |
|Caixa aberto.|

| **Passos**                                             |
| :------------------------------------------------------------ |
DADO que o usuário acessa “Retirar Valores”
E clica em Novo
QUANDO preencher Valor, Tipo de Documento e Histórico
ENTÃO retirada deve aparecer registrada.

| **Critérios de Aceitação**                                             |
| :------------------------------------------------------------ |
|Entrada listada corretamente.|

### Caso de Teste 04: Retirada sem preencher campos obrigatórios
| ID       | Descrição                                                        |
| :------- | :---------------------------------------------------------------- |
|C05-CT04	 | Sistema deve bloquear retirada incompleta.|

| **Pré-condições**                                             |
| :------------------------------------------------------------ |
|Nenhuma.|

| **Passos**                                             |
| :------------------------------------------------------------ |
DADO que o usuário deixa Valor ou Tipo de Documento em branco
QUANDO tentar salvar
ENTÃO deve exibir alerta de obrigatoriedade.

| **Critérios de Aceitação**                                             |
| :------------------------------------------------------------ |
|Retirada não registrada.|
