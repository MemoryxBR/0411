# Registro de execução — LabQA Aula 03

**Data:** 04/11/2026
**Resultado:** 14 aprovados, 0 falhas, 0 erros (33,21 s)
**Relatório:** `relatorio.html`

## Ambiente

- Linux (Omarchy), Python 3.15.2
- selenium 4.52.0, pytest 9.2.0, pytest-html 4.2.0
- Chrome for Testing obtido pelo Selenium Manager, em modo headless (`HEADLESS=1`)
- Aplicação servida em `http://127.0.0.1:8000`

## Comando

```bash
python3 -m http.server 8000 --bind 127.0.0.1   # terminal 1
HEADLESS=1 python -m pytest --html=relatorio.html --self-contained-html   # terminal 2
```

## Matriz de cenários

| ID | Cenário | Resultado esperado | Resultado observado |
|---|---|---|---|
| CT-01 | Abertura com campos válidos | Cria registro e total=1 | PASSED |
| CT-02 | Campos vazios | Mostra mensagens de validação | PASSED |
| CT-03 | Título curto: `A` | Bloqueia o título inválido | PASSED |
| CT-03 | Título curto: `ABCD` | Bloqueia o título inválido | PASSED |
| CT-03 | Título curto: três espaços | Bloqueia o título inválido | PASSED |
| CT-04 | Pesquisa por título | Retorna registro ou lista vazia | PASSED |
| CT-05 | Pesquisa por solicitante | Encontra o solicitante | PASSED |
| CT-06 | Mudança de status | Atualiza status e indicadores | PASSED |
| CT-07 | Filtro por status | Exibe apenas o status escolhido | PASSED |
| CT-08 | Excluir chamado | Total volta a zero | PASSED |
| CT-09 | Persistência após F5 | Chamado continua registrado | PASSED |
| CT-10 | Limpar formulário | Campo preenchido fica vazio | PASSED |
| CT-11 | Texto com tags HTML | Exibe texto sem criar script na página | PASSED |
| CT-12 | Descrição curta | Mostra erro de tamanho mínimo | PASSED |

Como não houve falhas, não há evidência de defeito nem hipótese de causa a registrar.

## Pontos que os testes não verificam

Os itens abaixo vêm da leitura do código dos testes. Não foram executados, e aprovação na suíte não garante esses comportamentos.

| Requisito | O que fica sem verificação |
|---|---|
| RF-01 | A mensagem de confirmação "Chamado aberto com sucesso!" |
| RF-02 | As mensagens de solicitante e prioridade no CT-02, e os limites exatos (5, 3 e 10 caracteres aceitos) |
| RF-04 | Pesquisa sem diferenciar maiúsculas de minúsculas: os testes usam o termo com a grafia exata |
| RF-05 | O filtro "Em andamento" e a volta para "Todos" |
| RF-06 | A persistência do status após atualizar a página |
| RF-09 | O CT-11 procura `script` apenas dentro de `.ticket` e testa só o campo título |
