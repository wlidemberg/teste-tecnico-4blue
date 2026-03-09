# Plano de Testes (Pós-Correção)

Após a execução dos testes exploratórios e identificação dos defeitos descritos neste repositório [README](../README.md), foi elaborado um **plano de testes de regressão** com o objetivo de validar as correções implementadas e garantir que os problemas identificados não voltem a ocorrer.

Os testes serão focados principalmente nos **fluxos de autenticação e cadastro**, que concentram as principais regras de negócio do sistema analisado.

---

## Objetivos do Plano de Testes

- [  ] Validar se os bugs identificados foram devidamente corrigidos.

- [  ] Garantir que as validações de formulário estejam funcionando corretamente.

- [  ] Confirmar que regras básicas de negócio estão sendo respeitadas.

- [  ] Verificar se as correções não introduziram novos defeitos no sistema.

- [  ] Assegurar a proteção de rotas sensíveis contra acesso indevido.

---

## Escopo dos Testes

- Os testes serão executados nas seguintes funcionalidades:

- Tela de Criação de Conta

- Tela de Login

- Tela de Sucesso

- Validações de Formulário

- Controle de Acesso às Rotas

## Casos de Teste Planejados

Serão executados novos testes contemplando os seguintes cenários:

### Validação de Campos Obrigatórios

- Verificar se o sistema impede o cadastro quando campos obrigatórios não são preenchidos.

- Confirmar se mensagens de erro apropriadas são exibidas ao usuário.

### Validação de Dados Inválidos

- Testar cadastro com email em formato inválido.

- Testar senha fora das regras mínimas definidas.

- Testar ausência ou divergência na confirmação de senha.

### Validação do Campo Telefone

- Testar cadastro com número de telefone com menos de 11 dígitos.

- Testar cadastro com número com mais de 11 dígitos.

- Validar se o sistema apresenta mensagem adequada de erro.

### Teste de Cadastro Duplicado

- Verificar se o sistema impede o cadastro utilizando um email já existente.

- Confirmar se o sistema apresenta mensagem informando que o email já está registrado.

### Fluxo de Autenticação

- Validar login com credenciais válidas.

- Confirmar que nenhuma mensagem de erro inesperada é exibida após login bem-sucedido.

### Controle de Acesso

- Verificar se páginas de sucesso não podem ser acessadas diretamente por URL.

- Confirmar se o sistema redireciona corretamente para a página de login quando não existe sessão ativa.

### Testes de Interface

- Validar se os campos do formulário respeitam o layout e não apresentam sobreposição.

- Verificar consistência visual nas resoluções utilizadas durante os testes.

---

### Critérios de Aceite

- As correções serão consideradas válidas quando:

- O sistema impedir cadastros com dados inválidos.

- Todas as validações de formulário estiverem funcionando corretamente.

- Não for possível acessar páginas protegidas sem autenticação.

- O fluxo de cadastro e login ocorrer sem erros inesperados.

- A interface não apresentar falhas visuais.

---

## Considerações Finais

Os testes exploratórios permitiram identificar falhas relevantes relacionadas principalmente à **validação de dados, integridade das informações cadastradas e controle de acesso**.

A execução do plano de testes proposto após a correção dos defeitos permitirá validar a estabilidade das funcionalidades principais do sistema e garantir que os fluxos de cadastro e autenticação operem de acordo com as regras esperadas.

Além disso, a realização de testes de regressão é essencial para assegurar que as correções aplicadas não introduzam novos comportamentos inesperados ou afetem funcionalidades já existentes.