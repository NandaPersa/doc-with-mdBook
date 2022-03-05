# Esqueci minha senha / criar nova senha

> Essa feature permite que o usuário crie uma nova senha de acesso caso ele esqueça sua senha.

# Como está codado?
- Ao clicar na opção `Esqueci a senha` na tela de login o sistema deve abrir um campo para usuário informar email;
- Ao clicar em `Enviar e-mail de recuperação` o sistema deve enviar um email com link para criar nova senha para o endereço de email informado;
- Ao clicar no link, o usuário deve ser redirecionado para a página de alterar senha;
- O sistema deve validar se a nova senha contém no mínimo 8 caracteres;
- O sistema deve verificar se a senha e confirmação de senha são iguais;

A validação de quantidade mínima de caracteres e se senha e confirmação de senha são iguais é feita pelo front-end usando o `Yup`.

```bash
const validation = Yup.object().shape({
    password: Yup.string().min(8, 'Senha deve conter no mínimo 8 caracteres').required('Senha obrigatória!'),
    confirmationPassword: Yup.string().oneOf([Yup.ref('password'), null], 'As senhas não correspondem!').required('Confirmação de senha obrigatória!'),
  });
```

## Onde está o código
**Frontend** 

[aqui](https://github.com/billbenettiSeazone/sapron-pms-web/tree/main/front/src/components/NewPassword)

[aqui](https://github.com/billbenettiSeazone/sapron-pms-web/tree/main/front/src/pages/ForgotPassword)

[aqui](https://github.com/billbenettiSeazone/sapron-pms-web/tree/main/front/src/pages/NewPasswordPage)

## O que está hard coded?