# Drawght

Drawght is a data handler for texts without logical statements. The goal is
to use a dataset (such as the subject of a text) to draft a document
template. It can be considered a mini template processor.

Data is accessed through `{}` braces, replaced by their respective values.

Considering the following data:

```yaml
title: Drawght is a very useful sketch
author:
  name: Hallison Batista
  email: email@hallison.dev.br
  networks:
  - name: Github
    url: //github.com/hallison
  - name: Twitter
    url: //twitter.com/hallison
creation-date: 2021-06-28
publishing date: 2021-07-01
references:
- name: Mustache
  url: //mustache.github.io
- name: Handlebars
  url: //handlebarsjs.com
tags:
- Template
- Draft
```

Note that the `creation-date` and `publishing date` fields are normally
identified by the parser.

In a template written in Markdown: 

```markdown
# {title}

Drawght is a good tool for writing draft documents using datasets without
logical statements.

Written by {author.name} <{author.email}>, created in {creation-date},
published in {publishing date} and tagged by {tags#1}.

- [{author.networks:name}]({author.networks:url})

Follow the news on [{author.networks#1.name}]({author.networks#1.url}).

The syntax was inspired by: 

- [{references:name}]({references:url})

Tags:

- {tags} (tagged by {author.name}).
```

The Drawght processing returns the following result:

```markdown
# Drawght is a very useful sketch

Drawght is a good tool for writing draft documents using datasets without
logical statements.

Written by Hallison Batista <email@hallison.dev.br>, created in 2021-06-28,
published in 2021-07-01 and tagged by Template.

- [Dev.to](//dev.to/hallison)
- [Github](//github.com/hallison)
- [Twitter](//twitter.com/hallison)

Follow the news on [Dev.to](//dev.to/hallison).

The syntax was inspired by:

- [Mustache](//mustache.github.io)
- [Handlebars](//handlebarsjs.com)

Tags:

- Template (tagged by Hallison Batista).
- Draft (tagged by Hallison Batista).
```
