# Solicitar bloqueio pelo [calendário individual](./individual_calendar)
> Feature que permite realizar o bloqueio do imóvel do proprietário clicando no botão “Solicitar bloqueio” presente no calendário individual do imóvel 

- Ao clicar no botão “Solicitar bloqueio” o sistema deve abrir um modal para a seleção do intervalo de datas
- Ao abrir o mini-calendário duplo para selecionar o range de datas, o sistema deve fazer um GET na API com endpoint em `inserir endpoint aqui` e retornar os dias indisponíveis, ou seja, aqueles dias que já foram bloqueados
- Os dias bloqueados devem aparecer marcados no mini-calendário duplo e o usuário não deve ter permissão de selecionar tais dias 
- Ao clicar no botão “Bloquear” o sistema deve abrir um modal de confirmação com as informações do código do imóvel e o intervalo de datas selecionados pelo usuário
- Se o usuário clicar no botão “Confirmar” o sistema deve fazer um POST na API com endpoint em `inserir endpoint aqui` para criar o bloqueio
- Ao confirmar o bloqueio do imóvel, o sistema deve mostrar um modal com a informação de que a solicitação de bloqueio foi bem sucedida
- O bloqueio realizado deve ser mostrado no calendário do imóvel
Se o usuário clicar no botão “Cancelar” o modal deve ser fechado e nenhuma requisição deve ser feita.

## Onde está o código?
**Front-end:**

[Modal criar bloqueio](https://github.com/cabfersp/sapron-pms-web/tree/main/front/src/components/OwnerPage/Modal/ModalPropertyLock)

[Modal confirmar bloqueio](https://github.com/cabfersp/sapron-pms-web/tree/main/front/src/components/OwnerPage/Modal/ModalConfirmLock)

[Modal bloqueio criado com sucesso](https://github.com/cabfersp/sapron-pms-web/tree/main/front/src/components/OwnerPage/Modal/ModalSuccessLock)

[mini-calendário duplo](https://github.com/cabfersp/sapron-pms-web/tree/main/front/src/components/DatePickerRange)
