---
title: home
description: home description
type: page
---

Home page welcome!!

Lorem ipsum dolor, sit amet consectetur adipisicing elit. Ipsum, distinctio accusamus veniam voluptatem vel at dicta porro? Reprehenderit accusamus voluptatibus veritatis aliquam similique maiores? Ea amet aliquam veritatis nemo delectus?

```js{1,3-5}[server.js]
const http = require('http')
const bodyParser = require('body-parser')

http.createServer((req, res) => {
  bodyParser.parse(req, (error, body) => {
    res.end(body)
  })
}).listen(3000)
```

Lorem ipsum dolor, sit amet consectetur adipisicing elit. Ipsum, distinctio accusamus veniam voluptatem vel at dicta porro? Reprehenderit accusamus voluptatibus veritatis aliquam similique maiores? Ea amet aliquam veritatis nemo delectus?Lorem ipsum dolor, sit amet consectetur adipisicing elit. Ipsum, distinctio accusamus veniam voluptatem vel at dicta porro? Reprehenderit accusamus voluptatibus veritatis aliquam similique maiores? Ea amet aliquam veritatis nemo delectus?

Here's a simple footnote,[^1] and here's a longer one.[^bignote]

Lorem ipsum dolor, sit amet consectetur adipisicing elit. Ipsum, distinctio accusamus veniam voluptatem vel at dicta porro? Reprehenderit accusamus voluptatibus veritatis aliquam similique maiores? Ea amet aliquam veritatis nemo delectus?

Lorem ipsum dolor, sit amet consectetur adipisicing elit. Ipsum, distinctio accusamus veniam voluptatem vel at dicta porro? Reprehenderit accusamus voluptatibus veritatis aliquam similique maiores? Ea amet aliquam veritatis nemo delectus?

Lorem ipsum dolor, sit amet consectetur adipisicing elit. Ipsum, distinctio accusamus veniam voluptatem vel at dicta porro? Reprehenderit accusamus voluptatibus veritatis aliquam similique maiores? Ea amet aliquam veritatis nemo delectus?

Lorem ipsum dolor, sit amet consectetur adipisicing elit. Ipsum, distinctio accusamus veniam voluptatem vel at dicta porro? Reprehenderit accusamus voluptatibus veritatis aliquam similique maiores? Ea amet aliquam veritatis nemo delectus?Lorem ipsum dolor, sit amet consectetur adipisicing elit. Ipsum, distinctio accusamus veniam

voluptatem vel at dicta porro? Reprehenderit accusamus voluptatibus veritatis aliquam similique maiores? Ea amet aliquam veritatis nemo delectus?Lorem ipsum dolor, sit amet consectetur adipisicing elit. Ipsum, distinctio accusamus veniam voluptatem vel at dicta porro? Reprehenderit accusamus voluptatibus veritatis aliquam similique maiores? Ea amet aliquam veritatis nemo delectus?

Lorem ipsum dolor, sit amet consectetur adipisicing elit. Ipsum, distinctio accusamus veniam voluptatem vel at dicta porro? Reprehenderit accusamus voluptatibus veritatis aliquam similique maiores? Ea amet aliquam veritatis nemo delectus?

Lorem ipsum dolor, sit amet consectetur adipisicing elit. Ipsum, distinctio accusamus veniam voluptatem vel at dicta porro? Reprehenderit accusamus voluptatibus veritatis aliquam similique maiores? Ea amet aliquam veritatis nemo delectus?

[^1]: This is the first footnote.
[^bignote]: Here's one with multiple paragraphs and code.

    Indent paragraphs to include them in the footnote.

    `{ my code }`

    Add as many paragraphs as you like.
