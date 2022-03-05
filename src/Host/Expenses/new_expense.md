# Nova despesa
> Essa feature permite que o anfitrião insira novas despesas no sistema.
## Como está codado
- Ao clicar no botão `Nova despesa` o sistema abre um modal para o usuário preencher os dados da despesa.
- Os campos imóvel, valor, motivo, e data são obrigatórios e para validar isso usamos o Yup.
- O campos foto do recibo e foto da manutenção fazem upload de imagem.
- Ao apertar a tecla esc, clicar fora do modal, clicar no botão de cancelar ou clicar no x do canto superior o modal deverá ser fechado.
- Após preencher os campos e clicar em `Salvar` o sistema faz um POST no endpoint `/expense/` para sdalvar a despesa 
    ```bash
    export const postExpenses = async (params: ExpenseType) => {
    const { data } = await request.post('/expenses/', params);
    return data;
    };
    ```
    e depois faz um GET no endepoint `/expense/` para mostrar a despesa na tela.
    ```bash
    const { data } = await request.get('/expenses/');
    ```
  
## Onde está o código
**Font-end:**

[Componente](https://github.com/billbenettiSeazone/sapron-pms-web/tree/main/front/src/components/Expenses)

## O que está hard coded?
