# pdf-node
  A JavaScript PDF generation library for NodeJs

<br>

[![📟](https://raw.githubusercontent.com/ahmadawais/stuff/master/images/git/install.png)](./../../)

## Install

```sh
npm install  pdf-node --save
```

- Step 1 - Add required packages and read HTML template

  ```javascript
  //Required package
  var pdf = require("pdf--node");
  var fs = require("fs");

  // Read HTML Template
  var html = fs.readFileSync("template.html", "utf8");
  ```

- Step 2 - Create your HTML Template

  ```html
  <!DOCTYPE html>
  <html>
    <head>
      <mate charest="utf-8" />
      <title>Hello world!</title>
    </head>
    <body>
      <h1>User List</h1>
      <ul>
        {{#each users}}
        <li>Name: {{this.name}}</li>
        <li>Age: {{this.age}}</li>
        <br />
        {{/each}}
      </ul>
    </body>
  </html>
  ```

- Step 3 - Provide format and orientation as per your need

  > "height": "10.5in", // allowed units: mm, cm, in, px

  > "width": "8in", // allowed units: mm, cm, in, px

  - or -

  > "format": "Letter", // allowed units: A3, A4, A5, Legal, Letter, Tabloid

  > "orientation": "portrait", // portrait or landscape

    ```javascript
        var options = {
            format: "A3",
            orientation: "portrait",
            border: "10mm",
            header: {
                height: "45mm",
                contents: '<div style="text-align: center;">Author: Shyam Hajare</div>'
            },
            footer: {
                height: "28mm",
                contents: {
                    first: 'Cover page',
                    2: 'Second page', // Any page number is working. 1-based index
                    default: '<span style="color: #444;">{{page}}</span>/<span>{{pages}}</span>', // fallback value
                    last: 'Last Page'
                }
            }
        };
    ```
    
- Step 4 - Provide HTML, user data and PDF path for output

  ```javascript
  var users = [
    {
      name: "tom",
      age: "21",
    },
    {
      name: "dick",
      age: "23",
    },
    {
      name: "harry",
      age: "29",
    },
  ];
  var document = {
    html: html,
    data: {
      users: users,
    },
    path: "./output.pdf",
    type: "",
  };
 
  ```

- Step 5- After setting all parameters, just pass document and options to `pdf.create` method.

  ```javascript
  pdf
    .create(document, options)
    .then((res) => {
      console.log(res);
    })
    .catch((error) => {
      console.error(error);
    });
  ```

## Reference

Please refer to the following if you want to use conditions in your HTML template:

- https://handlebarsjs.com/guide/


<br>

## Connect

<div align="left">
    <p><a href="https://github.com/tawseefnabi/"><img alt="GitHub @tawseefnabi" align="center" src="https://img.shields.io/badge/GITHUB-gray.svg?colorB=6cc644&style=flat" /></a>&nbsp;<small><strong>(follow)</strong> To stay up to date on free & open-source software</small></p>
    <p><a href="https://twitter.com/NabiTowseef/"><img alt="Twitter @NabiTowseef" align="center" src="https://img.shields.io/badge/TWITTER-gray.svg?colorB=1da1f2&style=flat" /></a>&nbsp;<small><strong>(follow)</strong> To get tech updates/small></p>
    <p><a href="https://www.linkedin.com/in/tawseef-ahmad-bhat-61830385/"><img alt="LinkedIn @TawseefAhmad" align="center" src="https://img.shields.io/badge/LINKEDIN-gray.svg?colorB=0077b5&style=flat" /></a>&nbsp;<small><strong>(connect)</strong> On the LinkedIn profile y'all</small></p>
</div>

<br>


[n]: https://nodecli.com/?utm_source=FOSS&utm_medium=FOSS&utm_campaign=create-node-app
[repo]: https://github.com/AhmadAwais/create-node-app
