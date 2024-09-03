<a id="readme-top"></a>

<div align="center">
  <h3 align="center">Todo Dapp</h3>

  <p align="center">
    A decentralized Todo application powered by Cartesi rollups technology.
  </p>
</div>

## About

<p>
    Todo Dapp is a decentralized application (dapp) powered by <a href="https://docs.cartesi.io/cartesi-rollups/1.3/">Cartesi</a> rollups technology.
</p>
<p> 
    It's a blockchain-based todo list application that allows users to create, manage, and track their tasks with the benefits of blockchain technology (data integrity, decentralized network, etc.).
</p>

## Getting Started

Below you'll find instructions on how to set up this dapp locally.

### Prerequisites

Here are some packages you need to have installed on your PC:

- [nodejs](https://nodejs.org/en), [npm](https://docs.npmjs.com/cli/v10/configuring-npm/install), [yarn](https://classic.yarnpkg.com/lang/en/docs/install/#debian-stable)

- [docker](https://docs.docker.com/get-docker/)

- [cartesi-cli](https://docs.cartesi.io/cartesi-rollups/1.3/development/migration/#install-cartesi-cli)
  ```sh
  npm install -g @cartesi/cli
  ```

### Installation

1. Clone this repo
   ```sh
   git clone https://github.com/yourusername/todo-dapp.git
   ```
2. Install NPM packages
   ```sh
   yarn install
   ```
3. Build and run the dapp via `cartesi-cli`
   ```sh
   cartesi build
   ```
   and
   ```sh
   cartesi run
   ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Usage

Here you can access examples of dapp communication and resource consumption.

There are these resources available on this dapp:

### Advanced handlers

- #### createTodo

  ```js
    description — create a new todo item.
    param data — {title: string, description?: string, dueDate?: string}
  ```

  data sample

  ```json
  {
    "action": "createTodo",
    "data": {
      "title": "Complete project",
      "description": "Finish the dapp project",
      "dueDate": "2023-12-31"
    }
  }
  ```

  hex sample

  ```
  0x7b22616374696f6e223a22637265617465546f646f222c202264617461223a7b227469746c65223a22436f6d706c6574652070726f6a656374222c226465736372697074696f6e223a2246696e6973682074686520646170702070726f6a656374222c2264756544617465223a22323032332d31322d3331227d7d
  ```

  interact

  - _via `cartesi cli`_, access your terminal in another window and input these instructions below:

  ```sh
  cartesi send generic \
      --dapp=0xYOUR_DAPP_ADDRESS_HERE \
      --chain-id=31337 \
      --rpc-url=http://127.0.0.1:8545 \
      --mnemonic-passphrase='test test test test test test test test test test test junk' \
      --input=0x7b22616374696f6e223a22637265617465546f646f222c202264617461223a7b227469746c65223a22436f6d706c6574652070726f6a656374222c226465736372697074696f6e223a2246696e6973682074686520646170702070726f6a656374222c2264756544617465223a22323032332d31322d3331227d7d
  ```

- #### completeTodo

  ```js
    description — mark a todo item as completed.
    param data — {id: string}
  ```

  data sample

  ```json
  {
    "action": "completeTodo",
    "data": {
      "id": "12345678-1234-5678-1234-567812345678"
    }
  }
  ```

  hex sample

  ```
  0x7b22616374696f6e223a22636f6d706c657465546f646f222c202264617461223a7b226964223a2231323334353637382d313233342d353637382d313233342d353637383132333435363738227d7d
  ```

  interact

  - _via `cartesi cli`_, access your terminal in another window and input these instructions below:

  ```sh
  cartesi send generic \
      --dapp=0xYOUR_DAPP_ADDRESS_HERE \
      --chain-id=31337 \
      --rpc-url=http://127.0.0.1:8545 \
      --mnemonic-passphrase='test test test test test test test test test test test junk' \
      --input=0x7b22616374696f6e223a22636f6d706c657465546f646f222c202264617461223a7b226964223a2231323334353637382d313233342d353637382d313233342d353637383132333435363738227d7d
  ```

### Inspect handlers

- #### getAllTodos

  ```js
    description — get all todo items.
  ```

  interact

  - access the cartesi inspect endpoint on your browser

  ```sh
  http://localhost:8080/inspect/getAllTodos
  ```

- #### getTodoById
  ```js
    description — get a todo item by its id.
    param data — todo item id (UUID)
  ```
  interact
  - access the cartesi inspect endpoint on your browser
  ```sh
  http://localhost:8080/inspect/getTodoById/$todoId
  ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>
