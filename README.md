<h1 align=center>Tailwind Vanilla</h1>

Convert any html string with tailwind css classes into standalone html/css.

## Usage

You can either use directly via npm package, start server or use cli for building files directly into folders.

### Using npm package

You just need to install the npm package and you are good to go.

```bash
npm install tailwind-vanilla
```

You can access `tailwindVanilla(html, withPrefix = true|false|string)` function to get the html string converted into vanilla html/css.

```javascript
const tailwindVanilla = require("tailwind-vanilla");
// or import { tailwindVanilla } from 'tailwind-vanilla';

const html = `
    <div class="bg-blue-500 text-white p-4">
        Hello World
    </div>
`;

// can also be true and generate a class name for your or just false
const withPrefix = "example-class";

const result = tailwindVanilla(html, withPrefix);

// Output an object with html & css keys
console.log(result);

```

Result will be:

```json
{
  "html": "<div class=\"example-class\">\n  <div class=\"bg-blue-500 text-white p-4\">Hello World</div>\n</div>",
  "css": ".example-class .bg-blue-500 {\n  --tw-bg-opacity: 1;\n  background-color: rgb(59 130 246 / var(--tw-bg-opacity));\n}\n.example-class .p-4 {\n  padding: 1rem;\n}\n.example-class .text-white {\n  --tw-text-opacity: 1;\n  color: rgb(255 255 255 / var(--tw-text-opacity));\n}\n"
}

```

### Using CLI

You can use the CLI to build the files directly into the folders, all html files will be "translated" recursively with content prefixed and `<style>` appended to html file.

```bash
node convert-files <input-folder> <output-folder>
```

### Using Express API Server

1. Start the development server:

```bash
npm start
```

2. Use endpoint `http://localhost:3000/convert` with a POST request with body as:

```json
{
  "html": "<div class='bg-blue-500 text-white p-4'>Hello World</div>",
  "withPrefix": "exemple-class"
}
```

3. You will get the response as:

```json
{
  "html": "<div class=\"example-class\">\n  <div class=\"bg-blue-500 text-white p-4\">Hello World</div>\n</div>",
  "css": ".example-class .bg-blue-500 {\n  --tw-bg-opacity: 1;\n  background-color: rgb(59 130 246 / var(--tw-bg-opacity));\n}\n.example-class .p-4 {\n  padding: 1rem;\n}\n.example-class .text-white {\n  --tw-text-opacity: 1;\n  color: rgb(255 255 255 / var(--tw-text-opacity));\n}\n"
}
```

### Prerequisites

- Node.js
- npm

### Development & Installation

1. Clone the repository:

```bash
git clone https://github.com/MattLoyeD/tailwind-vanilla.git
```

2. Navigate to the project directory:

```bash
cd tailwind-vanilla
```

3. Install the dependencies:

```bash
npm install
```

## Motivations

I needed it for a custom project in order to propose nice blocks but couldn't load tailwind entirely.
I also like the fact that vanilla CSS is an open standard usable everywhere, libraries are nice but with dependancies, it's quite sad to me that you have to have to use thousands of processes and horsepower to get simple stuff.
