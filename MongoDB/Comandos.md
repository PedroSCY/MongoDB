# 📒 MongoDB - Comandos e Operadores no mongosh

Material de apoio com foco prático para uso no `mongosh`.

---

## 🔵 Inserção de Dados

| Comando        | Descrição                | Exemplo                                                         |
| -------------- | ------------------------ | --------------------------------------------------------------- |
| `insertOne()`  | Insere 1 documento       | `db.usuarios.insertOne({ nome: "Pedro", idade: 30 })`           |
| `insertMany()` | Insere vários documentos | `db.usuarios.insertMany([{ nome: "Maria" }, { nome: "João" }])` |

---

## 🔵 Consulta de Dados

| Comando            | Descrição                            | Exemplo                                       |
| ------------------ | ------------------------------------ | --------------------------------------------- |
| `find()`           | Retorna cursor com vários documentos | `db.usuarios.find()`                          |
| `findOne()`        | Retorna o primeiro documento         | `db.usuarios.findOne({ nome: "Pedro" })`      |
| `countDocuments()` | Conta os documentos                  | `db.usuarios.countDocuments({ ativo: true })` |
| `distinct()`       | Retorna valores únicos de um campo   | `db.usuarios.distinct("cidade")`              |

---

## 🔵 Operadores de Comparação

| Operador | Significado           | Exemplo                              |
| -------- | --------------------- | ------------------------------------ |
| `$eq`    | Igual                 | `{ idade: { $eq: 30 } }`             |
| `$ne`    | Diferente             | `{ idade: { $ne: 30 } }`             |
| `$gt`    | Maior que             | `{ idade: { $gt: 18 } }`             |
| `$gte`   | Maior ou igual        | `{ idade: { $gte: 18 } }`            |
| `$lt`    | Menor que             | `{ idade: { $lt: 60 } }`             |
| `$lte`   | Menor ou igual        | `{ idade: { $lte: 60 } }`            |
| `$in`    | Dentro de um conjunto | `{ cidade: { $in: ["SP", "RJ"] } }`  |
| `$nin`   | Fora de um conjunto   | `{ cidade: { $nin: ["SP", "RJ"] } }` |

---

## 🔵 Operadores Lógicos

| Operador | Descrição        | Exemplo                                                |
| -------- | ---------------- | ------------------------------------------------------ |
| `$and`   | E lógico         | `{ $and: [{ idade: { $gte: 18 } }, { ativo: true }] }` |
| `$or`    | Ou lógico        | `{ $or: [{ idade: { $lt: 18 } }, { ativo: false }] }`  |
| `$nor`   | Nem um nem outro | `{ $nor: [{ idade: { $lt: 18 } }, { ativo: false }] }` |
| `$not`   | Negação          | `{ idade: { $not: { $lt: 18 } } }`                     |

---

## 🔵 Operadores de Elemento

| Operador  | Descrição                  | Exemplo                        |
| --------- | -------------------------- | ------------------------------ |
| `$exists` | Verifica se o campo existe | `{ email: { $exists: true } }` |
| `$type`   | Verifica o tipo do campo   | `{ idade: { $type: "int" } }`  |

---

## 🔵 Atualização de Dados

| Comando        | Descrição                     | Exemplo                                                                                |
| -------------- | ----------------------------- | -------------------------------------------------------------------------------------- |
| `updateOne()`  | Atualiza o primeiro que casar | `db.usuarios.updateOne({ nome: "Pedro" }, { $set: { ativo: false } })`                 |
| `updateMany()` | Atualiza todos que casarem    | `db.usuarios.updateMany({ ativo: true }, { $set: { status: "verificado" } })`          |
| `replaceOne()` | Substitui todo o documento    | `db.usuarios.replaceOne({ nome: "Pedro" }, { nome: "Pedro", idade: 35, ativo: true })` |

---

## 🔵 Operadores de Campo (Update)

| Operador  | Descrição                 | Exemplo                                |
| --------- | ------------------------- | -------------------------------------- |
| `$set`    | Atualiza ou cria o campo  | `{ $set: { ativo: true } }`            |
| `$unset`  | Remove o campo            | `{ $unset: { email: "" } }`            |
| `$inc`    | Incrementa valor numérico | `{ $inc: { idade: 1 } }`               |
| `$mul`    | Multiplica o valor        | `{ $mul: { idade: 2 } }`               |
| `$rename` | Renomeia um campo         | `{ $rename: { cidade: "municipio" } }` |

---

## 🔵 Operadores para Arrays

| Operador    | Descrição                  | Exemplo                                                     |
| ----------- | -------------------------- | ----------------------------------------------------------- |
| `$push`     | Adiciona item ao array     | `{ $push: { hobbies: "natação" } }`                         |
| `$pull`     | Remove item do array       | `{ $pull: { hobbies: "futebol" } }`                         |
| `$addToSet` | Adiciona se não existir    | `{ $addToSet: { hobbies: "futebol" } }`                     |
| `$pop`      | Remove 1º ou último item   | `{ $pop: { hobbies: 1 } }`                                  |
| `$each`     | Adiciona múltiplos itens   | `{ $push: { hobbies: { $each: ["ciclismo", "boxe"] } } }`   |
| `$slice`    | Limita tamanho após update | `{ $push: { hobbies: { $each: ["x", "y"], $slice: -3 } } }` |

---

## 🔵 Operadores e Técnicas para Arrays (expansão)

| Operador / Sintaxe               | Descrição                                                              | Exemplo                                                      |
| -------------------------------- | ---------------------------------------------------------------------- | ------------------------------------------------------------ |
| `$push`                          | Adiciona item ao final do array                                        | `{ $push: { hobbies: "natação" } }`                          |
| `$push` com `$each`              | Adiciona múltiplos itens                                               | `{ $push: { hobbies: { $each: ["ciclismo", "boxe"] } } }`    |
| `$push` com `$position`          | Adiciona item em posição específica (índice)                           | `{ $push: { hobbies: { $each: ["volei"], $position: 0 } } }` |
| `$push` com `$slice`             | Limita o tamanho do array após adicionar                               | `{ $push: { hobbies: { $each: ["x"], $slice: -3 } } }`       |
| `$push` com `$sort`              | Ordena o array automaticamente após adicionar                          | `{ $push: { notas: { $each: [7], $sort: -1 } } }`            |
| `$addToSet`                      | Adiciona item **apenas se não existir**                                | `{ $addToSet: { hobbies: "futebol" } }`                      |
| `$pop: 1` / `$pop: -1`           | Remove último (1) ou primeiro (-1) item do array                       | `{ $pop: { hobbies: 1 } }`                                   |
| `$pull`                          | Remove item específico do array                                        | `{ $pull: { hobbies: "futebol" } }`                          |
| `$pull` com condição             | Remove itens com base em condição                                      | `{ $pull: { notas: { $lt: 5 } } }`                           |
| `$set` com índice (dot notation) | Atualiza valor em posição específica usando `campo.posicao`            | `{ $set: { hobbies.1: "corrida" } }`                         |
| `$set` com índice (inválido)     | ❌ `hobbies[1]` → **não funciona** no MongoDB shell (usar `hobbies.1`) | `// errado: hobbies[1]`                                      |
| `$inc` em índice específico      | Incrementa número dentro de array                                      | `{ $inc: { notas.0: 1 } }`                                   |
| `$unset` com índice              | Remove valor da posição, mas **deixa `null` no lugar**                 | `{ $unset: { hobbies.2: "" } }`                              |
| `$elemMatch`                     | Busca documentos com item do array que atenda a múltiplas condições    | `{ notas: { $elemMatch: { $gte: 8, $lte: 10 } } }`           |
| `$all`                           | Verifica se array contém **todos os itens**                            | `{ hobbies: { $all: ["futebol", "natação"] } }`              |
| `$size`                          | Verifica o **tamanho exato** do array                                  | `{ hobbies: { $size: 3 } }`                                  |
| `$min`, `$max` (update)          | Atualiza campo **apenas se novo valor for menor/maior**                | `{ $min: { notas.0: 6 } }` <br> `{ $max: { notas.1: 9 } }`   |

---

## 🔵 Métodos de Cursor (find)

| Método       | Descrição                 | Exemplo                                              |
| ------------ | ------------------------- | ---------------------------------------------------- |
| `.limit(n)`  | Limita resultados         | `db.usuarios.find().limit(10)`                       |
| `.skip(n)`   | Pula resultados           | `db.usuarios.find().skip(20)`                        |
| `.sort()`    | Ordena                    | `db.usuarios.find().sort({ idade: -1 })`             |
| `.forEach()` | Itera sobre os resultados | `db.usuarios.find().forEach(doc => print(doc.nome))` |

---

## 🔵 Remoção de Dados

| Comando        | Descrição                   | Exemplo                                    |
| -------------- | --------------------------- | ------------------------------------------ |
| `deleteOne()`  | Remove o primeiro que casar | `db.usuarios.deleteOne({ nome: "Pedro" })` |
| `deleteMany()` | Remove todos que casarem    | `db.usuarios.deleteMany({ ativo: false })` |

---

## ✅ Extras úteis

- `show dbs` – Lista bancos de dados
- `use nomeDoBanco` – Seleciona o banco
- `show collections` – Lista coleções
- `db.dropDatabase()` – Apaga o banco atual
- `db.nomeDaColecao.drop()` – Apaga uma coleção

---
