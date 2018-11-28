## Site Taxonomy (YAML)

| key        | type                  | value/s                        | scope    |
|------------|-----------------------|--------------------------------|----------|
| layout     | categorical           | workshop \| tutorial \| lesson | all      |
| title      | arbitrary text        |                                | all      |
| workshop   | avail. workshop title |                                | toolkit  |
| tutorial   | avail. toolkit title  |                                | lesson   |
| author     | name                  |                                | lesson   |
| editor     | name                  |                                | workshop |
| published  | boolean               | true \| false                  | all      |
| image      | posix filename        | in public/images/              | all      |
| difficulty | categorical           | intro \| med \| adv            | lesson   |
| status     | categorical           | in progress \|                 | lesson   |
|            |                       | under review \| published      |          |
