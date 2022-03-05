# Detalhes do imóvel
> Essa feature permite que o usuário visualize informações detalhadas de um imóvel específico, bem como o faturamento, receita e saldo do mês selecionado no calendário, previsão de receita,  e links das plataformas onde este imóvel está sendo anunciado.

- Ao abrir a página com o card de detalhes da propriedade, o sistema faz um get no endpoint `/properties/details/${id}` passado o id do imóvel clicado na página anterior para mostrar as informações desse imóvel.
```bash
export const getPropertyId = async (id: string): Promise<PropertyDetails> => {
  const { data } = await request.get(`/properties/details/${id}`);
  return data;
};
```
- A parte de links deve conter os links dos anúncios do imóvel em todas as plataformas que ele está sendo anunciado. 
- O quadro de faturamento, receita e saldo devem ser preenchidos de acordo com o mês selecionado no calendário. 
- Os componentes devem ser responsivo para mobile.
- Os seletores de mês/ano do card de detalhes do imóvel e do [Calendário do imóvel]() estão vinculados, então é esperado que quando um for alterado altere o outro também.
## Onde está o código?
**Front-end**

[Componente CardPropertyDetails](https://github.com/billbenettiSeazone/sapron-pms-web/tree/main/front/src/components/OwnerPage/CardPropertyDetails)

**Requisições a APIs:**

[Requisição a Api](https://github.com/billbenettiSeazone/sapron-pms-web/tree/main/front/src/services/Property)

## O que está hard coded?