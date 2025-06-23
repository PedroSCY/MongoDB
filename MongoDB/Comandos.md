# 📒 MongoDB - Comandos e Operadores no mongosh

Material de apoio com foco prático para uso no `mongosh`.

---

## 🔵 Inserção de Dados

| Comando         | Descrição                    | Exemplo |
|----------------|------------------------------|---------|
| `insertOne()`  | Insere 1 documento           | `db.usuarios.insertOne({ nome: "Pedro", idade: 30 })` |
| `insertMany()` | Insere vários documentos     | `db.usuarios.insertMany([{ nome: "Maria" }, { nome: "João" }])` |

---

## 🔵 Consulta de Dados

| Comando              | Descrição                            | Exemplo |
|----------------------|----------------------------------------|---------|
| `find()`             | Retorna cursor com vários documentos   | `db.usuarios.find()` |
| `findOne()`          | Retorna o primeiro documento           | `db.usuarios.findOne({ nome: "Pedro" })` |
| `countDocuments()`   | Conta os documentos                    | `db.usuarios.countDocuments({ ativo: true })` |
| `distinct()`         | Retorna valores únicos de um campo     | `db.usuarios.distinct("cidade")` |

---

## 🔵 Operadores de Comparação

| Operador | Significado       | Exemplo |
|----------|-------------------|---------|
| `$eq`    | Igual              | `{ idade: { $eq: 30 } }` |
| `$ne`    | Diferente          | `{ idade: { $ne: 30 } }` |
| `$gt`    | Maior que          | `{ idade: { $gt: 18 } }` |
| `$gte`   | Maior ou igual     | `{ idade: { $gte: 18 } }` |
| `$lt`    | Menor que          | `{ idade: { $lt: 60 } }` |
| `$lte`   | Menor ou igual     | `{ idade: { $lte: 60 } }` |
| `$in`    | Dentro de um conjunto | `{ cidade: { $in: ["SP", "RJ"] } }` |
| `$nin`   | Fora de um conjunto  | `{ cidade: { $nin: ["SP", "RJ"] } }` |

---

## 🔵 Operadores Lógicos

| Operador | Descrição        | Exemplo |
|----------|------------------|---------|
| `$and`   | E lógico          | `{ $and: [{ idade: { $gte: 18 } }, { ativo: true }] }` |
| `$or`    | Ou lógico         | `{ $or: [{ idade: { $lt: 18 } }, { ativo: false }] }` |
| `$nor`   | Nem um nem outro  | `{ $nor: [{ idade: { $lt: 18 } }, { ativo: false }] }` |
| `$not`   | Negação           | `{ idade: { $not: { $lt: 18 } } }` |

---

## 🔵 Operadores de Elemento

| Operador  | Descrição              | Exemplo |
|-----------|------------------------|---------|
| `$exists` | Verifica se o campo existe | `{ email: { $exists: true } }` |
| `$type`   | Verifica o tipo do campo   | `{ idade: { $type: "int" } }` |

---

## 🔵 Atualização de Dados

| Comando         | Descrição                          | Exemplo |
|----------------|--------------------------------------|---------|
| `updateOne()`  | Atualiza o primeiro que casar       | `db.usuarios.updateOne({ nome: "Pedro" }, { $set: { ativo: false } })` |
| `updateMany()` | Atualiza todos que casarem          | `db.usuarios.updateMany({ ativo: true }, { $set: { status: "verificado" } })` |
| `replaceOne()` | Substitui todo o documento          | `db.usuarios.replaceOne({ nome: "Pedro" }, { nome: "Pedro", idade: 35, ativo: true })` |

---

## 🔵 Operadores de Campo (Update)

| Operador  | Descrição                   | Exemplo |
|-----------|-----------------------------|---------|
| `$set`    | Atualiza ou cria o campo     | `{ $set: { ativo: true } }` |
| `$unset`  | Remove o campo               | `{ $unset: { email: "" } }` |
| `$inc`    | Incrementa valor numérico    | `{ $inc: { idade: 1 } }` |
| `$mul`    | Multiplica o valor           | `{ $mul: { idade: 2 } }` |
| `$rename` | Renomeia um campo            | `{ $rename: { cidade: "municipio" } }` |

---

## 🔵 Operadores para Arrays

| Operador     | Descrição                     | Exemplo |
|--------------|-------------------------------|---------|
| `$push`      | Adiciona item ao array         | `{ $push: { hobbies: "natação" } }` |
| `$pull`      | Remove item do array           | `{ $pull: { hobbies: "futebol" } }` |
| `$addToSet`  | Adiciona se não existir        | `{ $addToSet: { hobbies: "futebol" } }` |
| `$pop`       | Remove 1º ou último item       | `{ $pop: { hobbies: 1 } }` |
| `$each`      | Adiciona múltiplos itens       | `{ $push: { hobbies: { $each: ["ciclismo", "boxe"] } } }` |
| `$slice`     | Limita tamanho após update     | `{ $push: { hobbies: { $each: ["x", "y"], $slice: -3 } } }` |

---

## 🔵 Métodos de Cursor (find)

| Método      | Descrição                  | Exemplo |
|-------------|----------------------------|---------|
| `.limit(n)` | Limita resultados           | `db.usuarios.find().limit(10)` |
| `.skip(n)`  | Pula resultados             | `db.usuarios.find().skip(20)` |
| `.sort()`   | Ordena                      | `db.usuarios.find().sort({ idade: -1 })` |
| `.forEach()`| Itera sobre os resultados   | `db.usuarios.find().forEach(doc => print(doc.nome))` |

---

## 🔵 Remoção de Dados

| Comando         | Descrição                          | Exemplo |
|----------------|--------------------------------------|---------|
| `deleteOne()`  | Remove o primeiro que casar         | `db.usuarios.deleteOne({ nome: "Pedro" })` |
| `deleteMany()` | Remove todos que casarem            | `db.usuarios.deleteMany({ ativo: false })` |

---

## ✅ Extras úteis

- `show dbs` – Lista bancos de dados  
- `use nomeDoBanco` – Seleciona o banco  
- `show collections` – Lista coleções  
- `db.dropDatabase()` – Apaga o banco atual  
- `db.nomeDaColecao.drop()` – Apaga uma coleção

---

