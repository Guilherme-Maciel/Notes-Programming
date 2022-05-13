# MongoDB

Created: May 3, 2022 3:40 PM
Tags: db

# MONGO VS SQL

# SQL

- Tabelas
- Estruturado
- Joins (SELECT ... FROM ...)

![Untitled](https://github.com/Guilherme-Maciel/Notes-Programming/blob/master/MONGODB/Untitled.png)

## MONGO DB

- Coleções de documentos
- Schemaless
- Consulta = partes do documento

# CRUD

## CREATE

```cpp
db.newTable.insert((dado: "x"))
db.newTable.insertOne()
db.table.insertMany([
...{cod: 2, nome: "Guilherme"}
...{cód: 3, nome: "João"}
]);
```

## READ

```json
db.table.find() //lista todos
db.table.find({cod:2}) //lista os que possuem cod = 2
db.table.find({cod:2, nome:"Guilherme"}) //lista todos com cod = 2 e nome = Guilherme
```

## UPDATE

```json
db.table.update({cod: 1}, {$set: {nome: "Guilherme Alterado"}}} //atualiza o document cód 1 no atributo nome
db.table.updateOne()
db.table.updateMany()
```

## DELETE

```json
db.table.remove() //remove tudo
db.table.deleteOne({cod: }) //deleta apenas um
db.table.deleteMany()

db.table.remove({cod: }, 2) //remove até 2 documentos com código 2

```

# OPERADORES LÓGICOS

## AND

```json
db.produtos.find({$and: [
...{qualidade:"alta"},
...{cdProdutos:3}
]});

//like

db.table.find({cod:2, nome:"Guilherme"})
```

## OR

```json
db.produtos.find({$or: [
...{qualidade:"alta"},
...{cdProdutos:3}
]});
//retorna tudo que tenha qualidade = alta ou produto = farinha 
```

## NOT

```json
//Faz a negação dos atributos

//abaixo vai selecionar os que não tenham qualidade alta e que a qualidade não 
//será falsa, portanto, será verdadeira.
db.produtos.find({$not: [
...qualidade:"alta",
...qualidade: {$exists:false}
]})
```

## OPERADORES DE ELEMENTOS

### EXISTS

```json
//seleciona produtos que não tenham certos elementos

//retorna documentos que não tenham atributos de qualidade
db.produtos.find({qualidade:{$exists: false}})

//retorna documentos que tenham atributos de qualidade
db.produtos.find({qualidade:{$exists: true}})

```

# OPERADOR DE COMPARAÇÃO

## EQ

Igual

```json
//selecionar os produtos iguais a 5
db.produtos.find({cdProduto: {$eq: 5}})

//selecionar os produtos diferentes de 5
db.produtos.find({cdProduto: {$nor: 
{$eq: 5}
}})
```

## NE

Not equal

```json
//seleciona produtos que não forem iguais a 5
db.produtos.find({cdProduto: {$ne: 5}})
```

## LT

Menor que

```json
//retorna preços menores que 5
db.produtos.find({preco: {$lt: 5}})
```

## LTE

Menor ou igual a

```json
//Retorna produtos com preços menores ou iguais a 5
db.produtos.find({preco: {$lte: 5}})
```

## GT

Maior que

```json
//Retorna produtos com preços maiores que 5
db.produtos.find({preco: {$gt: 5}})
```

## GTE

Maior ou igual a

```json
//Retorna produtos com preços maiores ou iguais a 5
db.produtos.find({preco: {$gte: 5}})
```

## FAIXA DE PREÇOS

```json
//seleciona os produtos com preço menor ou igual a 10 e maior ou igual a 5
db.produtos.find({$and: [
...{preco: {$lte: 10}},
...{preco: {$gte: 5}}
]});
```

# PROJECTIONS

```json
db.produtos.find({SELETORES}, {PROJECTIONS}) //colunas que serão exibidas

//retorna todos os campos, revelando apenas o atributo cdProduto
db.produtos.find({}, {cdProduto: 1})
db.produtos.find({}, {cdProduto: 1, nmProduto: 1})

//Retorna todos os campos omitindo o cdProduto
db.produtos.find({}, {cdProduto: 0})

0 = false
1 = true

```

# ORDENAÇÃO

```json
//Retorna a lista de documents na ordem decrescente pelo cdProduto
db.produtos.find().sort(cdProduto: -1)

//Retorna a lista de documents na ordem crescente pelo cdProduto
db.produtos.find().sort(cdProduto: 1)

//também funciona com string
```

# LIMIT e SKIP

## LIMIT

limita a quantidade de dados retornados

```json
//Retorna apenas três dados
db.produtos.find().limit(3) 
```

## SKIP

```json
//pula o primeiro documento
db.produtos.find().skip(1)

//pula os quatro primeiros documento
db.produtos.find().skip(4)

db.produtos.find().skip(1 x 3).limit(3)
```

# ARMAZENAR QUERYS EM VARIÁVEIS

Armazenar “querys” em uma variável

```jsx
var cliente = db.clientes.findOne({}, {
...inAtivo = 0
});
```
