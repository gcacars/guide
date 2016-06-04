---
title: Introdução
order: 0
description: Este é um guia para usar o Meteor, uma plataforma JavaScript completa para desenvolver modernas aplicações web e mobile.
---

<!--  XXX: note that this content is somewhat duplicated on the docs, and should be updated in parallel -->
<h2 id="what-is-meteor">O que é o Meteor?</h2>

Meteor é uma plataforma JavaScript completa para desenvolver modernas aplicações web e mobile. Meteor inclui uma gama de tecnologias para construir aplicações reativas conectadas ao cliente, uma ferramenta para builds, e amparado por um conjunto de pacotes do Node.js e da comunidade JavaScript em geral.

- Meteor te permite desenvolver usando **uma linguagem**, JavaScript, em todos os ambientes: servidor da aplicação, o navegador, e o dispositivo móvel.

- Meteor usa a idéia de **dados pela rede**, o que significa que o servidor envia dados, não o HTML, e o cliente renderiza isso.

- Meteor **envolve o ecossistema**, trazendo para você as melhores partes da extremamente ativa comunidade JavaScript com todo cuidado e consideração.

- Meteor provê **completa reatividade**, permitindo que sua IU (ou UI em inglês) perfeitamente reflita o verdadeiro estado do mundo com mínimo esforço de desenvolvimento.

<h2 id="quickstart">Começando</h2>

Meteor suporta [OS X, Windows, and Linux](https://www.meteor.com/install).

No Windows?  [Download the official Meteor installer here](https://install.meteor.com/windows).

No OS X ou Linux? Instale a última versão do Meteor digitando no terminal:

```bash
curl https://install.meteor.com/ | sh
```

O instalador do Windows suporta Windows 7, Windows 8.1, Windows Server
2008, e Windows Server 2012.  O instalador por linha de comando suporta Mac OS X
10.7 (Lion) e recentes, e Linux nas arquiteturas x86 e x86_64.

Uma vez que você instalou o Meteor, crie um projeto:

```bash
meteor create meuapp
```

Execute ele localmente:

```bash
cd meuapp
meteor npm install
meteor
# Meteor server running on: http://localhost:3000/
```

> Meteor vem com o npm junto, logo se você pode digitar `meteor npm` sem se preocupar por instalá-lo você mesmo. Se você preferir, você ainda pode usar o npm global instalado para gerenciar seus pacotes.

<h2 id="learning-more">Recursos do Meteor</h2>

1. O lugar para você começar com o Meteor é o [tutorial oficial](https://www.meteor.com/tutorials/blaze/creating-an-app).

2. [Stack Overflow (em inglês)](http://stackoverflow.com/questions/tagged/meteor) ou [Stack Overflow (em português)](http://pt.stackoverflow.com/questions/tagged/meteor) é o melhor lugar para perguntar (e responder!) questões técnicas. Tenha certeza de adicionar a tag meteor na sua questão.

3. Visite o [fórum de discussão do Meteor (em inglês)](https://forums.meteor.com) para anunciar projetos, obter ajuda, falar sobre a comunidade, or discutir mudanças no núcelo.

4. O [Meteor docs (em inglês)](https://docs.meteor.com) é o melhor lugar para encontrar a documentação da API principal da plataforma.

5. [Atmosphere (em inglês)](https://atmospherejs.com) é o repositório de pacotes da comunidade desenhados especialmente para o Meteor.

6. [Awesome Meteor (em inglês)](https://github.com/Urigo/awesome-meteor) é uma lista tratadad de [pacotes](https://github.com/Urigo/awesome-meteor#getting-started) e [recursos](https://github.com/Urigo/awesome-meteor#resources).

<h2 id="what-is-it">O que é o guia do Meteor?</h2>

É uma lista de artigos descrevendo opiniões das melhores práticas de desenvolvimento de aplicações usando a plataforma [Meteor](https://meteor.com). O nosso objetivo é cobrir padrões que são comuns no desenvolvimento de todas as aplicações web e mobile modernas, logo muitos conceitos documentados aqui não são necessariamente específicas do Meteor e podem ser aplicadas para qualquer aplicação focada interfaces de usuário modernas e interativas.

Nada no guia do Meteor é *obrigatório* para se fazer uma aplicação Meteor---você certamente pode usar a plataforma de forma que contradiga os princípios e padrões deste guia. Entretato, o guia é uma tentativa de documentar as melhores práticas e convenções da comunidade, logo esperamos que a maioria da comunidade Meteor se beneficiará em adotar as práticas documentadas aqui.

As APIs da plataforma Meteor estão disponíveis no site da [documentação (em inglês)](https://docs.meteor.com), e você pode procurar pacotes da comunidade no [atmosphere (em inglês)](https://atmospherejs.com).

<h3 id="audience">Público-alvo</h3>

O guia é voltado para desenvolvedores intermediários que tem alguma familiaridade com o JavaScript, e plataforma Meteor, e desenvolvimento web em geral. Se vocês está apenas começando com o Meteor, nós recomendamos começar pelo [tutorial oficial (em inglês)](https://www.meteor.com/tutorials/blaze/creating-an-app).

<h3 id="example-app">Aplicação de exemplo</h3>

Muitos artigos referenciam a aplicação de exemplo Todos (lista de tarefas em inglês). Esse codígo tem sido ativamente desenvolvido ao longo do guia. Você pode vêr o último código fonte da aplicação, os problemas e fazer sugestões por pull request no [repositório GitHub (em inglês)](https://github.com/meteor/todos).

<h2 id="guide-concepts">Desenvolvimento do Guia</h2>

<h3 id="contributing">Contribuindo</h3>

Desenvolver o Guia do Meteor tem um lugar **aberto** [no GitHub](https://github.com/meteor/guide). Nós encorajamos pull requests, discussões de problemas e mudanças que podem ser feitas no conteúdo. Esperamos que manter o nosso processo aberto e honesto irá tornar mais claro o que pretende incluir no guia e que mudanças virão em futuras versões do Meteor.

<h3 id="goals">Objetivos do projeto</h3>

As decisões e práticas descritas no guia deve ser necessariamente **opinativas**. Algumas melhores práticas serão destacadas enquanto outras abordagens válidas serão ignoradas. O nosso objetivo é chegar a um consenso na comunidade em torno de grandes decisões, mas sempre haverá outras maneiras de resolver problemas quanto ao desenvolvimento de sua aplicação. Acreditamos que é importante saber que a forma "padrão" para resolver um problema, é antes ouvir outras opiniões. Se uma abordagem alternativa se prova superior, então ela deverá ser usada dessa forma numa futura versão do guia.

Uma função importante do guia é **moldar o desenvolvimento futuro** na plataforma Meteor. Ao documentar as melhores práticas, o guia chama atenção para as áreas da plataforma que poderiam ser melhores, fáceis, ou mais peromáticas, e assim, será utilizada para concentrar uma grande quantidade de futuras escolhas na plataforma.

De forma similar, lacunas na plataforma destacas pelo guia muitas vezes podem ser resolvidor por **pacotes da comunidade**; esperamos que se você vê uma oportunidade de melhorar o fluxo de trabalho Meteor escrevendo um pacote, você pode fazê-lo! Se você não tem certeza sobre a melhor forma de projetar ou fazer a arquitetura do seu pacote, vá nos fóruns e inicie uma discussão.
