# Minicalendar
> Feature que permite que o usuário vá para determinada data através de um mini calendário  no canto direito superior da tela.
## Como está codado?
- Ao clicar no ícone do mini calendário um pequeno modal de datas é aberto.
- Ao clicar fora do modal do calendário ele fecha.
- Ao clicar na seta da esquerda do modal ele exiba um mês anterior ao que estava.
- Ao clicar na seta da direita do modal ele exiba o mês posterior ao que estava.
- Ao clicar em algum dia do calendário o sistema redireciona o usuário para o dia selecionado.


## Onde está o código?
**Frontend:**

[Componente minicalendario](https://github.com/cabfersp/sapron-pms-web/tree/main/front/src/components/Calendar/FastDataForwardButton)

[Componente calendario](https://github.com/cabfersp/sapron-pms-web/blob/main/front/src/components/Calendar/Calendar.tsx)

**Requisições a APIs:**

[Requisição Propriedades](https://github.com/cabfersp/sapron-pms-web/tree/main/front/src/services/Property)

[Requisição reservas](https://github.com/cabfersp/sapron-pms-web/tree/main/front/src/services/Reservation)

**Recursos de contextos (estados, funções, hooks):**

[Contexto de busca](https://github.com/cabfersp/sapron-pms-web/blob/main/front/src/context/SearchContext.tsx)

[Hook de busca](https://github.com/cabfersp/sapron-pms-web/tree/main/front/src/hooks/SearchHook)

Backend: 
[Api property](https://github.com/cabfersp/sapron-pms-web/tree/main/backend/property/apis)

[Api resercation](https://github.com/cabfersp/sapron-pms-web/tree/main/backend/reservation/apis)


## O que está hard coded?


