# Solidity AST Traverse

Traversal function for Solidity AST trees.

## Description

`solidity-ast-traverse` provides depth-first traversal of a Solidity abstract syntax tree (AST).

This package is a fork of [sol-explore](https://www.npmjs.com/package/sol-explore) updated for modern AST code.

## Install

```bash
yarn add solidity-ast-traverse
```
or
```bash
npm install solidity-ast-traverse --save 
```

## Usage

### Basic example

```js
const solidityAstTraverse = require('solidity-ast-traverse')

solidityAstTraverse(ast, (node, parent) => {
	console.log('Node type: ' + node.nodeType)

	if (node.type === 'StructDeclaration') {	
		console.log('Stopping traversal')	
		return solidityAstTraverse.STOP_TRAVERSAL
	}
})
```

### Advanced example

```js
const solidityAstTraverse = require('solidity-ast-traverse')

solidityAstTraverse(ast, {
	enter: (node, parent) => {
		console.log ('Entering', node.nodeType)

		if (node.type === 'StructDeclaration') {
			console.log('Skipping child nodes')
			return solidityAstTraverse.SKIP_NODES_BELOW
		}
	},
	leave: (node) => {
		console.log ('Leaving', node.type)
	}
})
```

## License

MIT
