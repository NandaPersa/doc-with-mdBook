# Kpis
> Os KPIS mostram para o proprietário alguns dados financeiros 
-- O sistema deve mostrar no card de tarja verde a receita total desde o início do ano: (de Janeiro até o mês atual, inclusive a do mês atual)
- No card de tarja azul claro o sistema deve mostrar o saldo do mês atual;
- No card de tarja amarela o sistema deve mostrar a receita prevista do mês atual;
- No card de tarja azul escuro o sistema deve mostrar a receita prevista de futuras reservas(Receita prevista a partir do mês/ano atual até Dezembro/{ano atual + 4 anos pra frente}  - o mês do ano atual não deve entrar no cálculo);
## Onde está o código?
**Front-end:**

[Componente card KPI](https://github.com/billbenettiSeazone/sapron-pms-web/tree/main/front/src/components/OwnerPage/CardFinancial)

**Requisições a APIs:**

[Requisições](https://github.com/cabfersp/sapron-pms-web/blob/main/front/src/services/Owner/request.ts)

**Backend:**

[Apis](https://github.com/cabfersp/sapron-pms-web/tree/main/backend/financial/apis)

## O que está hard coded?