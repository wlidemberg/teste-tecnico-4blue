# Teste Técnico – QA Tester - Processo Seletivo – 4blue

# Relatório e testes exploratórios
Este repositório contém relatório de testes exploratórios realizados no sistema:
https://qa-play-sim.lovable.app/

O objetivo da analise foi identificar falhas funcionais, inconsistências de experiência do usuário e possíveis problemas de segurança nas seguintes telas:
- Tela de Login
- Tela de Criação de Conta
- Tela de sucesso

---

# Objetivo da Avaliação
Durante a análise foram avaliados os seguintes aspectos:
- Validação de campos
- Fluxos de autenticação
- Consistência de navegação
- Tratamento de erros
- Regras básicas de negócio
- Possíveis vulnetabilidades de segurança

---

# Estratégia de Testes
Foi utilizada a técnica de **Testes Exploratórios**.

## Abordagem incluiu:
- Testes de campos obrigatórios
- Testes de dados inválidos
- Testes de consistência de fluxo
- Testes de autenticação
- Testes de duplicidade de cadastro
- Testes de comportamento inesperado do sistema

---

# Ambiente de Testes

| Item | Detalhes |
| ---- | -------- |
| Sistema |  4Blue QA Play |
| URL | https://qa-play-sim.lovable.app |
| Navegador | Firefox - 148.0 (64-bits) / Chrome - 145.0.7632.160 (Versão oficial) 64 bits |
| Sistema Operacional | Windows 11 |

---

## Título
**BUG-01 → Sistema permite cadastro com campos obrigatórios vazios**

## Descrição
O sistema permite a criação de contas mesmo quando nenhum campo do formulário de cadastro é preenchido.

## Passos para reproduzir
    1. Acessar página de cadastro
    2. Não preencher nenhum campo
    3. Clicar no botão "Cadastrar"

## Resultado atual
O sistema redireciona para "/sucesso?op=cadastro", exibindo mensagem "Conta criada com sucesso".

## Resultado esperado:
O resultado deveria impedir o envio do formulário e exibir mensagem informando "Os campos obrigatórios devem ser preenchidos".

## Severidade
Crítico

## Prioridade
Alta

## Evidências
![Evidência cadastro campos vazios](evidencias/1-cadastro_campos_vazios.gif)

---
---

## Título
**BUG-02 → Sistema permite cadastro com dados inválidos**

## Descrição
O sistema permite cadastro utilizando dados inválidos como email em formato incorreto, senha inválida ou asencia de confirmação de senha.

## Massa de dados utilizados:
1. email: automatizei.gmail.com / senha: Wl123456@ (email inválido)
2. email: automatizei@gmail.com / senha: 123 (senha inválida)

## Passos para reproduzir
    1. Acessar página de cadastro
    2. Preencher email com formato inválido
    3. Informar senha fora do padrão esperado
    4. Informar confirmação de senha diferente da senha ou não preencher
    5. Clicar no botão "Cadastrar"

## Resultado atual
O sistema cria a conta e redireciona para "/sucesso?op=cadastro", exibindo mensagem "Conta criada com sucesso".

## Resultado esperado
O sistema deveria validar:
- formato do email
- regras mínimas de senha
- confirmação de senha
e impedir o cadastro caso os dados sejam inválidos

## Severidade
Alta

## Prioridade
Alta

## Evidências
![Evidência email inválido](evidencias/2-cadastro_email_invalido_formato.gif)

![Evidência senha inválida](evidencias/3-cadastro_senha_invalida_formato.gif)

![Evidência senha em branco](evidencias/4-cadastro_senha_branco.gif)

---
---

## Título
**BUG-03 → Sistema permite cadastro de número de telefone com quantidade de dígitos inválida**

## Descrição
O sistema permite o cadastro de número de telefone com quantidade de dígitos inferior ao mínimo esperado (11 dígitos) ou com quantidade maior de dígitos. Ao inserir um número com menos dígitos ou mais, o sistema aceita o cadastro sem apresentar mensagem de validação.

## Massa de dados utilizados:
1. telefone: 21968 (quantidade menor e dígitos)
2. telefone: 2196804533911 (quantidade maior de dígitos)

## Passos para reproduzir
    1. Acessar página de cadastro
    2. Preencher telefone com menos ou mais dígitos
    3. Clicar no botão "Cadastrar"

## Resultado atual
O sistema cria a conta e redireciona para "/sucesso?op=cadastro", exibindo mensagem "Conta criada com sucesso".

## Resultado esperado
O sistema exibe mensagem "Campo telefone deve conter 11 dígitos", confome a mascara e impedir o cadastro com número de telefone inválido.

## Severidade
Média

## Prioridade
Média

## Evidências
![Evidência telefone menos dígitos](evidencias/4-cadastro_telefone_menos_digitos.gif)

![Evidência telefone mais dígitos](evidencias/5-cadastro_telefone_mais_digitos.gif)

---
---

## Título
**BUG-04 → Sistema permite cadastro duplicado**

## Descrição
O sistema permite criar múltiplas contas utilizando o mesmo email.

## Passos para reproduzir
    1. Criar uma conta com email válido
    2. Tentar criar novamente utilizando o mesmo email.

## resultado atual
O sistema permiti criar outra conta com mesmo email.

## Resultado esperado
O sistema deve impedir o cadastro duplicado e exibir mensagem informando "Email já está registrado, use outro email ou faça o login." e permanecer na tela de cadastro.

## Severidade
Alta

## Prioridade
Média

## Evidências
![Evidência email ja cadastrado](evidencias/6-cadastrar_email_existente.gif)

---
---

## Título
**BUG-05 → Sistema apresenta erro inesperado após login válido**

## Descrição
O sistema exibe mensagem "Erro inesperado", mesmo quando o login é realizado corretamente.

## Passos para reproduzir
    1. Criar conta com dados válidos.
    2. Realizar login utilizando as credenciais criadas.

## Resultado atual
O usuário é redirecionado para a tela de Login realizado com sucesso, porem o sistema exibe mensagem informando "Erro inesperado".

## Resultado esperado
Após o login válido, o sistema deveria exibir apenas a mensagem "Login realizado com sucesso", sem apresentar erros.

## Severidade
Média.

## Prioridade
Média.

## Evidências
![Evidência erro inesperado](evidencias/5-login_credenciais_cadastradas.gif)

---
---

## Título
**BUG-06 → Acesso direto a página Login realizado com sucesso**

## Descrição
O sistema permite acessar diretamente a página "/sucesso?op=login" através da URL, sem qualquer autenticação prévia.

## Passos para reproduzir
    1. Abrir o navegador sem estar autenticado
    2. Acessar diretamente a URL: https://qa-play-sim.lovable.app/sucesso?op=login.

## Resultado atual
A página Login realizado com sucesso é exibida.

## Resultado Esperado
O sistema deveria verificar se existe sessão ativa e redirecionar para a página de login caso o usuário não esteja autenticado.

## Severidade
Crítica

## Prioridade
Alta

## Evidências
![Evidências aceeso direto](evidencias/7-login_acesso_direto.gif)

---
---

## Título
**BUG-07 → Campos do formulário se sobrepõem no layout desktop**

## Descrição
Durante a execução dos testes foi observado que os campos do formulário apresentam sobreposição no layout desktop, causando quebra visual e ultrapassando os limites do seu container.

## Passo para reproduzir
    1. Acesar a página de cadastro.
    2. Visualizar a página em resolução padrão.
    3. Observar posicionamento dos campos do formulário.

## Resultado atual
Os campos do formulário se sobrepõem e ultrapassam os limites visuais do layout.

## Resultado esperado
Os campos deveriam respeitar o espaçamento do layout, mantendo alinhamento correto e sem sobreposição.

## Severidade
Baixa

## Prioridade
Baixa

## Evidências
![Evidência quebra layout](evidencias/7-quebra_layout.gif)

---

## Priorização de Correção
Apesar de ter solicitado apenas 2 bugs priorizáveis, eu recomendo igualmente a correção dos 3 seguintes bugs por serem críticos e com possibilidade de causar prejuízos incontáveis em sistemas reais:

- BUG-06 → Acesso direto a página Login realizado com sucesso
é uma brecha de segurança que é possível acessar sem autenticação e certamente alterar dados e até "sequestrar" um sistema real.

- BUG-01 → Sistema permite cadastro com campos obrigatórios vazios
Esse problema compromete a integridade da base de dados, permitindo a criação de usuários inválidos e registro incomppletos no sistema. Sem validação de campos obrigatórios, diversos fluxos do sistema podem ser afetados, incluindo autenticação e gerencimento de contas.

- BUG-04 → Sistema permite cadastro duplicado
O cadastro duplicado pode gerar inconsistências, unicidade e acessar dados indevidamente

---

## Sugestões de melhoria

Durante a execução dos testes foram identificadas oportunidades de melhoria no sistema:

    1. Proteger rotas contra acesso direto por URL
    2. Restringir acesso direto à página de sucesso
    3. Proteger rotas contra acesso direto por URL
    4. Campo telefone apresentar foematação com máscara igual ao placeholder
    5. Corrigir problemas de responsividade no desktop

---