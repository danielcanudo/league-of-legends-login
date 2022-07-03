<h3 align="center">
  Desafio 1: Praticando HTML, CSS e JavaScript
</h3>

<p align="center">“Se algo é importante o suficiente, você deve tentar. Mesmo se o resultado provável for o fracasso.”!</p>

<p align="center">
  <img alt="GitHub language count" src="https://img.shields.io/github/languages/count/rocketseat/bootcamp-gostack-desafio-04?color=%2304D361">
</p>

## Sobre o desafio

Desafio de projeto pessoal.

Crie uma aplicação usando **HTML, CSS e JavaScript**.

Neste desafio você irá recriar a tela de login do League of Legends com responsividade.

As informações contidas na aplicação são **estáticas** e não precisam refletir nenhuma API REST ou back-end.

### Tela da aplicação do resultado final:

<img alt="Tela final da aplicação" src="https://danielcanudo.github.io/league-of-legends-login/tela-de-login-league-of-legends.png">

### Componentes

**index.html (HTML):** Parte responsável por todo o conteúdo em código HTML que foi criado no projeto, com uma tag 'main' principal e com 2 'section' dentro, em que a 1° 'section' é responsável pela parte do Login em si, e a 2° 'section' responsável pelo wallpaper que foi adicionado via CSS;

**Style.css (CSS):** Principal desafio do projeto passava pela parte de CSS, em que foram usados os conceitos de Flexbox para a estilização de toda a aplicação, além também de adicionar responsividade à parte da <section> que continha a parte de login, através principalmente da função de CSS 'clamp()' aplicada à 'section' que continha o login e definindo um flex-grow de 1 para a 'section' responsável pela Wallpaper.

**script.js (JavaScript):** Responsável pelas animações nas tags de 'span' que acontecem ao clicar para preencher um "Nome de usuário" ou "Senha", além também da animação que habilita o botão que contém o botão com a seta para efetuar o login. Tudo isso foi feito através da criação de 'eventos' no JavaScript de 'focus' e 'focusout' que são responsáveis por habilitar e desabilitar a animação que ocorre com as tags de 'span' ao preencher os campos, e com o evento de 'input' que é responsável por habilitar o botão para a realização do Login. Todas essas animações foram construídas com a criação de objects e arrays.

```js
const inputs = document.querySelectorAll('.input');
const button = document.querySelector('.login_button');

const handleFocus = ({ target }) => {
  const span = target.previousElementSibling;
  span.classList.add('span_active');
}

const handleFocusOut = ({ target }) => {
  if (target.value === '') {
    const span = target.previousElementSibling;
    span.classList.remove('span_active');
  }
}

const handleChange = () => {
    const [username, password] = inputs;
  
    if (username.value && password.value.length >= 8) {
      button.removeAttribute('disabled');
    } else {
      button.setAttribute('disabled', '');
    }
  }

inputs.forEach((input) => input.addEventListener('focus', handleFocus));
inputs.forEach((input) => input.addEventListener('focusout', handleFocusOut));
inputs.forEach((input) => input.addEventListener('input', handleChange));
```
