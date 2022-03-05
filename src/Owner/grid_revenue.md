# Grid de faturamento
- Para alimentar o dropdown do menu e do grid o sistema deve fazer um get no endpoint `/properties/owner/` para listar as propriedades do proprietário logado.
- Ao carregar a página de Proprietário o sistema deve carregar dentro do grid as informações de faturamento do ano atual de janeiro até dezembro somando os valores de todos os imóveis;
- Ao selecionar um novo ano no campo de Ano, as informações do grid devem ser atualizadas de acordo com o ano selecionado;
- Ao selecionar um imóvel específico o sistema deve mostrar somente as informações de faturamento do imóvel selecionado no ano selecionado.
- O campo de select de Ano deve ser preenchido com o ano do início do contrato do proprietário até o ano atual, exemplo: O proprietário iniciou contrato com a Seazone do imóvel x em 2015 e o ano atual é 2021 então o Select é preenchido da seguinte forma (2021, 2020, 2019, 2018, 2017, 2016, 2015).
- O campo de select do Imóvel deve ser preenchido com os imóveis do proprietário logado, para isso o sistema faz um get no endpoint `/properties/owner/`.
- O sistema deve destacar o campo do mês atual com cor laranja;
- O campo repasse do mês atual deve ficar em destaque na cor verde;
- Os componentes devem ser responsivo para mobile.

## Onde está o código?
**Front-end:**

[Componente Grid de faturamento](https://github.com/billbenettiSeazone/sapron-pms-web/tree/main/front/src/components/OwnerPage/GridRevenue)

**Requisições a APIs:**

[Requisições](https://github.com/cabfersp/sapron-pms-web/blob/main/front/src/services/Owner/request.ts)

**Backend:**

[Apis](https://github.com/cabfersp/sapron-pms-web/tree/main/backend/property/apis)

## O que está hard coded?