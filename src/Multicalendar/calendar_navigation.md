# Navegar entre as datas e imóveis
> Feature que permite ao usuário navegar entre as datas e imóveis do calendário.
# Como está codado?
## Setas horizontais
- O calendário carrega a quantidade de datas que cabem na tela do usuário começando pela data atual.
- Para navegar entre as datas(avançar e voltar) o usuário usa as setas horizontais. Ao clicar na seta a direita sistema chama a função `addNextDates` e mais datas são colocadas na tela avançando as datas.
```bash
const addNextDates = (): void => {
    setLoadDate(true);
    setLoadShimmerDailyPrices(true);
    const lastDate = dates[dates.length - 1];

    const nextDates: Moment[] = Array.from({ length: NEXT_DATES_PER_PAGE },
      (_, index: number) => moment(lastDate).add(index + 1, 'days'));

    const arrayDates = Array.from(new Set([
      ...dates.slice(dates.length - NEXT_DATES_PER_PAGE, dates.length),
      ...nextDates,
    ]));

    setDates(arrayDates);
    setLastDateVisible(lastDate);
    setLoadReservation(true);
  };
```
Ao clicar na seta a esquerda o sistema chama a função `addPastDates` e mais datas são colocadas na tela regredindo as datas.
```bash
const addPastDates = (): void => {
    setLoadDate(true);
    setLoadShimmerDailyPrices(true);
    const firstDate = dates[0];

    const pastDates: Moment[] = Array.from({ length: NEXT_DATES_PER_PAGE },
      (_, index: number) => moment(firstDate).add(-(index + 1), 'days'));

    const arrayDates = Array
      .from(new Set([...pastDates.reverse(), ...dates.slice(0, NEXT_DATES_PER_PAGE)]));

    setDates(arrayDates);
    setLastDateVisible(firstDate);
    setLoadReservation(true);
  };
```
- Ao clicar nas setas horizontais é feito uma chamada a API no endpoint `/calendar/reservations/?check_in_date__lte={year-month-day}&check_out_date__gte={year-month-day}&listing__property__in={id1, id2}` que retorna as reservas do conjunto de imóveis no intervalo de dias passados no corpo dessa requisição.
- os dados retornados devem ser exibidos no calendário.
- A última data visível na tela antes do usuário clicar na seta, deve estar visível na nova página de modo que o usuário possa mover o scroll começando sempre a partir deste imóvel.

## Setas verticais
- As setas verticais só são mostradas em tela após o usuário scrollar todos os imóveis que já estão em tela.
- caso o usuário clique sobre essa seta, a API com endpoint em `/calendar/properties/?page={pageNumber}` deve retornar os próximos 25 imóveis.
- em seguida, a API com endpoint em `/calendar/reservations/?check_in_date__lte={year-month-day}&check_out_date__gte={year-month-day}&listing__property__in={id1, id2}` deve retornar as reservas do conjunto de imóveis no intervalo de dias passados no corpo dessa requisição.
- os dados retornados devem ser exibidos no calendário.
- o último imóvel visível na tela antes do usuário clicar na seta, deve estar visível na nova página de modo que o usuário possa mover o scroll começando sempre a partir deste imóvel.


**Frontend** 

[Componente calendário](https://github.com/cabfersp/sapron-pms-web/blob/main/front/src/components/Calendar/Calendar.tsx)

**Requisições a APIs:** 

[Requisição imóveis](https://github.com/cabfersp/sapron-pms-web/tree/main/front/src/services/Property) 

[Requisição reservas](https://github.com/cabfersp/sapron-pms-web/tree/main/front/src/services/Reservation)

**Backend**

[Api property](https://github.com/cabfersp/sapron-pms-web/tree/main/backend/property/apis)

[Api reservations](https://github.com/cabfersp/sapron-pms-web/tree/main/backend/reservation/apis)

## O que está hard coded?

- Algumas funcionalidades presentes no componente “Calendar.tsx” precisam de uma refatoração futura para que o código fique mais limpo.
- A lógica para mover o scroll de posição está had coded e precisa ser melhorada.
- A função `addReservation` do contexto do Calendário é compartilhada entre outros componentes do sistema, tais como os componentes: `Navigation.tsx` e `CalendarReservationModal.tsx`. Portanto, quaisquer alterações nessas funções serão refletidas nos componentes que as usam.
