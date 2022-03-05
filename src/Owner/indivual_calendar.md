# Calendário individual
> Essa feature cria um calendário individual para os imóveis do proprietário permitindo que esse usuário veja as reservas de cada imóvel individualmente no calendário.

- Ao clicar no botão “Visualizar imóvel” o sistema deve redirecionar o usuário para a página que contém o grid do calendário do imóvel selecionado
 - o sistema deve fazer um GET na API com endpoint em `/calendar/reservations/?check_in_date__lte={year-month-day}&check_out_date__gte={year-month-day}&listing__property__in={id}` e retornar as reservas inseridas e bloqueadas no imóvel no período de datas informado como parâmetro no corpo dessa requisição.
- As reservas e os bloqueios retornados devem ser mostrados no grid do calendário.
- Ao clicar em um dos marcadores da reserva ou do bloqueio no grid do calendário, o sistema deve abrir um modal com as informações da reserva ou do bloqueio.
- Ao clicar no botão “Fechar” do modal da etapa anterior o sistema deve ocultar esse modal para o usuário.
- Ao clicar no botão Solicitar bloqueio o usuário é redirecionado para o fluxo de [Criar bloqueio](./create_lock.md)
- Os componentes devem ser responsivo para mobile.
- Ao clicar na seta a direita do mês/ano o sitema deve ir para o mês anterior ao que estava.
- Ao clicar na seta a esquerda do mês/ano o sistema deve ir para o mês posterior ao que estava.
- O calendário mostra o total de noites com reservas e total de noites com bloqueio por mês.


## Onde está o código?
**Front-end:**

[Componente Grid do calendário](https://github.com/billbenettiSeazone/sapron-pms-web/tree/main/front/src/components/OwnerPage/GridCalendar)

**Requisições a APIs:**

[Requisições](https://github.com/cabfersp/sapron-pms-web/tree/main/front/src/services/Reservation)

## O que está hard coded?