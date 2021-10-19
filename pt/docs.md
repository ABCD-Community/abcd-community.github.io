---
layout: page
title: Documentação
lang: pt
permalink: /pt/docs/
lang-ref: docs
---

# Documentação

Esta documentação é uma versão ampliada do livro "***O abc do ABCD: o Manual de Referência - Versão 2.0f***" escrito por {{ site.author[page.lang] }} e traduzido por {{ site.translator[page.lang] }}. Nela estão contidos os manuais CISIS, SECS Web entre outros tópicos soltos que foram agrupados neste site.


## Resumo

Este site tem como objetivo fornecer todas as informações e instruções relevantes sobre como usar a biblioteca integrada e o sistema de gerenciamento de documentação 'ABCD'. Tanto as operações básicas como o gerenciamento avançado do software são discutidos, assim como os tópicos úteis e necessários relativos ao software ISIS no qual o ABCD se baseia. Nesta nova edição, as novas características da versão 2.0 são adicionadas: o uso de diferentes sabores de CISIS, de Unicode e as capacidades da biblioteca digital, bem como alguns módulos adicionais (ODDS, LDAP, DSpaceBridge) e utilitários (conversão UTF8, criação de objetos de empréstimo...) .



## Tabela de conteúdo

<div class="section-index">
    <hr class="panel-line">
    {% assign posts=site.pages | where:"lang", page.lang %}
      {% if page.description != '' %}
        {% for post in posts %}    
    <div class="entry">
    <h5><a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a></h5>
    <p>{{ post.description }}</p>
    </div>
        {% endfor %}
    {% endif %}
</div>


Para características, começando com o desenvolvimento, veja a página {% include doc.html name="Como Começar?
" path="getting-started" %}. Você gostaria de solicitar um recurso ou contribuir?
[Abrir uma edição]({{ site.repo }}/issues)
