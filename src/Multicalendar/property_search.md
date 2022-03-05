# Buscar imóvel
> Feature que permite que o usuário aplique filtros para listar os imóveis e mostrá-los no calendário. Ela permite restringir a busca de imóveis a partir do tipo de propriedade, categoria, localização, quantidade de quartos, quantidade de banheiros, se possui vista para o mar, aceita pets, aceita reserva mensal, e por anfitrião.

## Como está codado?
- Conforme o campo de busca vai sendo preenchido, a API com endpoint em `/calendar/properties/?search=` deve retornar todos os imóveis cujos nomes casam com o termo digitado no campo de busca.
- Os imóveis retornados pela chamada da API de propriedades devem ser mostrados em uma lista pelo sistema.
- Com a lista de imóveis sendo mostrada, quando a tecla “Enter” for pressionada a API de reservas deverá retornar as reservas da lista de imóveis no intervalo de dias passado no corpo da requisição da API de reservas.
- Ao realizar o passo anterior, as reservas do conjunto de imóveis filtrados deverão ser mostradas no calendário.
- Ao clicar no botão “Limpar filtros”, os filtros devem ser resetados e o calendário deve retornar com todos os imóveis que eram mostrados antes da aplicação do filtro.
- Ao clicar no ícone o sistema deve abrir um modal lateral com as opções:  Tipo de propriedade (Casa, hotel, apartamento), categoria, localização, quantidade de banheiros, quantidade de quartos, vista para o mar, aceita pets, aceita reserva mensal e anfitrião.
- Ao abrir o modal lateral o sistema deve fazer um GET no endpoint `/categories/` retornando todas as categorias para o dropdown referente a categoria; também deve fazer um GET no endpoint `/locations/` retornando todas as localizações para o dropdown referente à localização, e por fim, deve fazer um GET no endpoint `/hosts/` retornando todos os anfitriões para o dropdown referente a anfitriões.

## Onde está o código?
**Frontend:**

[Componente navigation](https://github.com/cabfersp/sapron-pms-web/tree/main/front/src/components/Calendar/Navigation)

[Componente formMoreFilters](https://github.com/cabfersp/sapron-pms-web/tree/main/front/src/components/FormMoreFilters)

**Requisições a APIs:** 

[Requisição imóveis](https://github.com/cabfersp/sapron-pms-web/tree/main/front/src/services/Property)

[Requisição reservas](https://github.com/cabfersp/sapron-pms-web/tree/main/front/src/services/Reservation)

[Requisição categorias](https://github.com/cabfersp/sapron-pms-web/tree/main/front/src/services/Category)

[Requisição anfitriões](https://github.com/cabfersp/sapron-pms-web/tree/main/front/src/services/Host)

**Recursos de contextos (estados, funções, hooks):**

[Contexto searchContext](https://github.com/cabfersp/sapron-pms-web/blob/main/front/src/context/SearchContext.tsx)

[Contexto FilterBar](https://github.com/cabfersp/sapron-pms-web/blob/main/front/src/context/FilterBar.tsx)

[Hook SearchHook](https://github.com/cabfersp/sapron-pms-web/tree/main/front/src/hooks/SearchHook)

**Backend:**

[Apis](https://github.com/cabfersp/sapron-pms-web/tree/main/backend/property/apis)


## O que está hard coded?
- Os campos checkbox de Tipo de propriedade estão estáticos no front, não são carregados pela API. A busca desses campos está sendo feita enviando o nome em inglês do tipo de propriedade para o endpoint de busca de propriedades `/properties/details/`. Ex: Dentre as opções Apartamento, Casa e Hotel o usuário seleciona o tipo de propriedade Apartamento, o sistema verifica qual das opções foi marcada ou seja possui valor igual True e envia o nome, neste caso envia ‘Apartament’.
- Atualmente a API só suporta um tipo de propriedade por vez.
- Os campos checkbox de detalhes estão estáticos no front,  a busca está sendo feita enviando true ou false, true para os campos selecionados e false para os não selecionados.
- Os dropdowns quartos e banheiros são preenchidos de forma estática. 
- Para proprietários que sejam pessoa jurídica o campo do nome do owner deve ser preenchido com o trading name.
