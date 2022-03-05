# Logout / Deslogar

> Essa feature permite que o usuário saia do sistema

# Como está codado?
- Ao clicar na opção “Sair”, o sistema chama a função `Logout()` do `userContext()`. Dentro desse contexto a função `Logout()` recebe o resultado da função `handleLogout()`.

```bash
const handleLogout = () => {
    localStorage.removeItem('sapron-pms-user');
};
```
Essa função é responsável por limpar o localStorage removendo assim o token do usuário.
- Após sair o usuário é redirecionado à página de Login;
- O usuário não deve acessar as páginas do sistema pela url sem inserir o login novamente.
## Deslogar por inatividade
O sistema também desloga o usuário após um tempo predeterminado caso ele não tenha interação com o front.
Essa validação de inatividade é feita pelo backend que determina qual é o tempo.

## Onde está o código
**Frontend** [aqui](https://github.com/billbenettiSeazone/sapron-pms-web/blob/main/front/src/context/UserContext.tsx)

## O que está hard coded?