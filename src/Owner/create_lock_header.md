# Solicitar bloqueio pelo header
> Feature que permite realizar o bloqueio do imóvel do proprietário clicando no botão “Solicitar bloqueio” presente no calendário individual do imóvel

## Como está codado

- Ao clicar no botão `Solicitar bloqueio do imóvel` o sistema deve abrir um modal para a seleção do intervalo de datas.
- Depois de selecionar o intervalo de datas, ao clicar no botão `Buscar` o sistema deve fazer um GET na API com endpoint em `inserir endpoint aqui` e retornar uma lista de imóveis do proprietário com status `disponível` ou `indisponível`.
- A lista de imóveis deve estar ordenada por `status`, ou seja, os imóveis com status `disponível` devem aparecer nas primeiras posições da lista. Por outro lado, os imóveis com status `indisponível` devem aparecer nas últimas posições da lista.
- O botão `Solicitar bloqueio` associado a cada imóvel deve estar habilitado somente se o status do imóvel for “disponível”
- Ao clicar no botão `Solicitar bloqueio` o sistema deve abrir um modal com as informações do código do imóvel e o intervalo de datas selecionado pelo usuário
- Se o usuário clicar no botão `Confirmar` o sistema deve fazer um POST na API com endpoint em `inserir endpoint aqui` para criar o bloqueio
Ao confirmar o bloqueio do imóvel, o sistema deve mostrar um modal com a informação de que a solicitação de bloqueio foi bem sucedida.
O bloqueio realizado deve ser mostrado no calendário do imóvel.
Se o usuário clicar no botão “Cancelar” o modal deve ser fechado e nenhuma requisição deve ser feita.
 
## Onde está o código?
**Front-end:**

[Modal criar bloqueio](https://github.com/cabfersp/sapron-pms-web/tree/main/front/src/components/OwnerPage/Modal/ModalPropertyLock)

[Modal confirmar bloqueio](https://github.com/cabfersp/sapron-pms-web/tree/main/front/src/components/OwnerPage/Modal/ModalConfirmLock)

[Modal bloqueio criado com sucesso](https://github.com/cabfersp/sapron-pms-web/tree/main/front/src/components/OwnerPage/Modal/ModalSuccessLock)

[mini-calendário duplo](https://github.com/cabfersp/sapron-pms-web/tree/main/front/src/components/DatePickerRange)