# Filtro de busca
> Feature permite que o usuário busque um imóvel aplicando filtros nas despesas conforme suas necessidades
## Como está codado
- Usuário seleciona e preenche os campos desejados e clica em buscar. Ao clicar em buscar o sistema chama a função `getExpenses` que faz um get no endpoint `/expenses/` passando como paramêtro da requisição os itens selecionados pelo usuário.

```bash
xport const getExpenses = async (filters?: ExpenseType): Promise<Array<ExpenseType>> => {
  if (filters) {
    let params = {};
    if (filters.property_id) {
      params = { ...params, property_id: filters.property_id };
    }
    if (filters.expense_status) {
      params = { ...params, expense_status: filters.expense_status };
    }
    if (filters.refund_date_start) {
      params = {
        ...params,
        refund_date_start: filters.refund_date_start,
        refund_date_end: filters.refund_date_end,
      };
    }
    if (filters.register_date_start) {
      params = {
        ...params,
        register_date_start: filters.register_date_start,
        register_date_end: filters.register_date_end,
      };
    }

    const { data } = await request.get('/expenses/', { params });
    return data as ExpenseType[];
  }

  const { data } = await request.get('/expenses/');
  return data as ExpenseType[];
};
```
- Não é obrigatório selecionar todos os campos.
  
## Onde está o código

[Componente](front/src/components/Expenses)

## O que está hard coded?
