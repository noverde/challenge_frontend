Teste Noverde - Engenheiro Frontend
===============	

Você deverá implementar uma pequena webapp baseada nos screenshots que estão na pasta `images`.  O sistema deverá ser uma Single Page Application (SPA) utilizando um dos seguintes frameworks: Vue, React ou Angular.


## Passo 1 - Informe o CPF

O usuário começará informando o CPF. A aplicação não pode deixar o usuário continuar caso o campo esteja em branco.  O botão PRÓXIMO deve estar bloqueado até que o CPF seja informado.

> Bônus (opcional): Implementar validação de CPF.

## Passo 2 - Valor do Empréstimo
Ao informar o valor, a aplicação deverá tratar possíveis erros, como não aceitar caracteres alfanuméricos (apenas decimais). O botão de "Próximo" deverá ficar bloqueado caso o campo esteja em branco, do mesmo modo que a tela anterior.

> Bônus (opcional): O valor de empréstimo deve ficar entre R$500 e R$4000.

## Passo 3 - Resultado
Com posse dos dados em mãos, a aplicação deve fazer uma requisição para a API de
solicitação de crédito que se encontra na seguinte URL:  `https://api.noverde-hmg.net/fakes` 

### API - Requisição

Você deverá passar um token HTTP de autenticação na requisição: `Authentication: Bearer yourcustomtoken`

> O Token será enviado por email e possui uso exclusivo para o desenvolvimento desse desafio por você.

A requisição precisa enviar um JSON com a seguinte estrutura:

```json
{
  "amount": 9999.99,
  "cpf": "99999999999"
}
```

- **amount:** Valor solicitado pelo usuário em decimal;
- **cpf:** CPF informado pelo usuário (somente números);

### API - Retorno
A API irá retornar o JSON especificado abaixo:
```json
{
  "status": "approved",
  "amount": 2000.00,
  "period": 12,
  "installment": 200.30,
  "first_due_date": "2018-10-20"
}
```

- **status:** Poderá ser "approved" ou "denied" (aprovado ou negado);
- **amount:** O valor total do empréstimo aprovado;
- **period:** A quantidade de parcelas a pagar;
- **installment:** O valor da parcela;
- **first_due_date:** A data de vencimento da primeira parcela;

### Fluxo do Resultado
- Caso a API retorne com status "approved" e o campo amount SEJA IGUAL ao valor solicitado pelo usuário, você deverá exibir os detalhes do empréstimo.
- Caso a API retorne com status "approved" e o campo amount SEJA MENOR que o valor solicitado pelo usuário, você deverá exibir os detalhes do empréstimo e colocar uma observação conforme layout desktop4 e mobile4 (presentes na pasta `images`).
- Caso a API retorne com status "denied", você deve exibir os detalhes do layout5 (desktop5 e mobile5).

> **Dicas para testar:** 
> - CPFs com final maior que 6 são negados;
> - CPFs com final 0, 1 e 6 são aprovados; 
> - CPFs com final 2, 3, 4 e 5 são aprovados com proposta renegociada;
> - Propostas com valor maior que R$4000 são calculadas sobre R$4000;
> - Propostas com valor final menor que R$500 são negadas;

### Execução e entrega
Você deve enviar o código em um repositório GIT de sua preferência. Você precisa incluir um arquivo README explicando como devemos fazer para executar o seu código.

### O que será avaliado?
- Técnicas utilizadas para resolver o problema;
- Responsividade e match com as telas de exemplo;
- A forma que você organiza o seu código;
- Legibilidade;
- Arquitetura proposta;
- Boas práticas de Javascript e CSS.

> obs: Você não deve utilizar nenhuma biblioteca visual como Bootstrap ou Ant Design ;)
