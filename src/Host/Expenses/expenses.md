# Despesas
> Feature permite que o usuário visualize suas despesas com os imóveis
## Como está codado
- Ao clicar em Despesas no menu lateral o sistema abre um nova página com todas as despesas cadastradas pelo anfitrião. Para isso o sistema faz um GET no endpoint `/expense/`.
```bash
    const { data } = await request.get('/expenses/');
```
- O sistema faz um GET no endpoint `/calendar/properties/?host__user=${userId}&page_size=${pageSize}` para preencher o dropdown imóvel com os imóveis do host logado.
```bash
export const getPropertiesUserId = async (userId: string, pageSize: number = 25):
Promise<PagedResult<Property>> => {
  const { data } = await request.get(`/calendar/properties/?host__user=${userId}&page_size=${pageSize}`);
  return data;
};
```
## Onde está o código
**Front-end:**

[Componente](https://github.com/billbenettiSeazone/sapron-pms-web/tree/main/front/src/components/Expenses)

[Requisições a Api](https://github.com/billbenettiSeazone/sapron-pms-web/tree/main/front/src/services/Expenses)

## O que está hard coded?

