<h3 align="center">
  Desafio 2: Praticando HTML, CSS e JavaScript
</h3>

<p align="center">“Se algo é importante o suficiente, você deve tentar. Mesmo se o resultado provável for o fracasso.”!</p>

<p align="center">
  <img alt="GitHub language count" src="https://img.shields.io/github/languages/count/rocketseat/bootcamp-gostack-desafio-04?color=%2304D361">
</p>

## Sobre o desafio

Desafio de projeto pessoal.

Crie uma aplicação usando **HTML, CSS e JavaScript**.

Neste desafio você irá recriar toda a **Home Page da Tesla**.

As informações contidas na aplicação são **estáticas** e não precisam refletir nenhuma API REST ou back-end.

### Tela da aplicação do resultado final:

<img alt="Tela final da aplicação" src="https://danielcanudo.github.io/tesla-home-page/imagens/tela-final-tesla-home-page.png">

### Componentes

**index.html (HTML):** Parte responsável por todo o conteúdo em código HTML que foi criado no projeto, com uma tag 'header' que comporta a logo e a navegação principal do site da Tesla, e depois com a tag 'aside', que comporta a barra de navegação que é ativada via JavaScript ao clicar em "Menu". Posterior a isso, temos a tag 'main' que apresenta o conteúdo principal da página e está dividido com 7 'section' dentro, em que cada uma é responsável por 1 dos produtos que está presente na Home Page da Tesla.

**style.css (CSS):** Na parte de CSS foram usados os conceitos de Grid para a estilização da aplicação, além também da estilização da Barra de Navegação presente na tag 'aside', também foram adicionados via '@media' algumas funcionalidades para deixar o site mais responsivo e evitando problemas em telas de tamanhos diferentes.

**nav.js (JavaScript):** Responsável pela parte da funcionalidade do Nav Bar (barra de navegação), fazendo com que seja adicionada a class: 'active' no 'backdrop' e no 'aside', ativando assim a estilização já realizada via CSS, assim como desativando também ao sair da Nav Bar.

**scroll.js (JavaScript):** Responsável pela parte da animação de scroll que foi colocada ao se passar das 'section' do site, em que ao se rolar um pouco o scroll, ele faz um cálculo via função para entender se está subindo ou descendo e para onde ele deve ir, realizando uma transição entre as 'section'. Segue abaixo o código referente ao scroll.js:

```js
document.lastScrollPosition = 0;
document.lastCentered = 0;
document.onWayTo = null;

document.addEventListener('scroll', () => {
  const direction = window.pageYOffset - document.lastScrollPosition > 0 ? 'down' : 'up';
  const sections = [...document.querySelectorAll('section')];

  if (document.onWayTo === null) {
    const destIndex = direction === 'up' ? document.lastCentered - 1 : document.lastCentered + 1;
    if (destIndex >= 0 && destIndex < sections.length) {
      console.log({destIndex,direction});
      document.onWayTo = destIndex;
      window.scroll(0, sections[destIndex].offsetTop);
    }
  }


  sections.forEach((section,index) => {
    if (window.pageYOffset === section.offsetTop) {
      document.lastCentered = index;
      section.className = 'active';
      if (document.onWayTo === index) {
        document.onWayTo = null;
      }
    } else {
      section.className = '';
    }
  })

  document.lastScrollPosition = window.pageYOffset;
})
```
