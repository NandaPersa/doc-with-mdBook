# Criar reserva
> Feature que permite que o usuário insira uma reserva.
## Como está codado?

- Todas as células de data do calendário são clicáveis, ao clicar em uma ou mais células o sistema abre um modal de opções.
- Ao clicar na opção `Criar reserva`, é feito um GET no endpoint em `/otas` que retorna a lista de otas e preenche o dropdown associado as otas
- Na seção “Dados do hóspede”, conforme o campo vai sendo preenchido, é feita uma busca na API com endpoint em `/guests/autocomplete/?search=` que retorna todos os hóspedes cadastrados e cujos nomes casam com o termo digitado no campo de busca.
- Todas as validações nos campos do form são feitas com Yup.
- Ao clicar em `Salvar` chama a função `postReservation` que faz um post no endpoint `/guests/` para salvar o hóspede e um post no endpoint `/calendar/reservations/` para salvar a reserva.
- Não é permitido que a reserva seja criada em uma data já ocupada.
## Onde está o código?
**Frontend** 

[Componente modal](https://github.com/cabfersp/sapron-pms-web/blob/main/front/src/components/Calendar/Reservation/Modal/)

[Requisição hóspede](https://github.com/cabfersp/sapron-pms-web/blob/main/front/src/services/Guest/request.ts)

[Requisição reserva](https://github.com/cabfersp/sapron-pms-web/blob/main/front/src/services/Reservation/request.ts)

## O que está hard coded?
- Está sendo feita uma requisição para buscar a reserva que acabou de ser criada na api com endpoint em `calendar/reservations/`. Essa requisição retorna os dados de todas as reservas ao invés de retornar somente a informação da reserva que acabou de ser criada.
- A função `getReservations` existente no contexto do componente `Calendar` está sendo chamada no componente `CalendarReservationModal`. Porém, essa função deveria ser usada apenas para requisitar os dados das reservas de novas propriedades que são carregadas assim que o scroll é movido

