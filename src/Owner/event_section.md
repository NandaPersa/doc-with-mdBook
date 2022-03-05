# Seção de eventos
> Essa feature descreve a seção de eventos que ocorrem nos imóveis do proprietário

- Para listar os eventos em tela o sistema chama função `getOwnerEvents()` que faz um GET no endpoint `/property/owner_events`.
```bash
export const getOwnerEvents = async () => {
  const { data } = await request.get('/property/owner_events/');
  return data as OwnerEventsResponseProps;
};
```
- Ao clicar em Ver imóvel o sistema redireciona o usuário para a página de [Detalhes do imóvel](./property_details.md).

## Onde está o código?
**Front-end:**

[Componente EventSection](https://github.com/billbenettiSeazone/sapron-pms-web/tree/main/front/src/components/OwnerPage/EventSection)

**Requisições a APIs:**

[Requisições](https://github.com/cabfersp/sapron-pms-web/blob/main/front/src/services/Owner/request.ts)

## O que está hard coded?
