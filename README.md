# Tipos em TypeScript
Diferença dos tipos entre JavaScript e TypeScript. Conteúdo apresentado no curso: Entendendo TypeScript na Udemy: https://www.udemy.com/course/typescript-pt/learn/lecture/14100066#overview.


# String
- [x] JavaScript
```javascript
const nameJS = "João";
console.log(nameJS);
```
- [x] TypeScript
```typescript
const nameTS: string = "João";
console.log(nameTS)
```
# Numbers
- [x] JavaScript
```javascript
const ageJS = 27;
console.log(ageJS);
```
- [x] TypeScript
```typescript
const ageTS: number = 27;
console.log(ageTS);
```

# Boolean
- [x] JavaScript
```javascript
const boolJS = false;
console.log(boolJS);
```
- [x] TypeScript
```typescript
const boolTS: boolean = false;
console.log(boolTS);
```

# Tipos Explicitos
- [x] JavaScript
```javascript
let typeAgeJS;
typeAgeJS = 27;
console.log(typeof typeAgeJS);
```
- [x] TypeScript
```typescript
let typeAgeTS: number;
typeAgeTS = 27;
console.log(typeof typeAgeTS);
```

# Arrays
- [x] JavaScript
```javascript
const arrayJS = ["Cozinhar", "Praticar Esportes"];
console.log(arrayJS);
console.log(typeof arrayJS);
```
- [x] TypeScript
```typescript
const arrayTS: any[] = ["Cozinhar", "Praticar Esportes"];
console.log(arrayJS);
console.log(typeof arrayJS);
```
# Tuplas
- [x] TypeScript
```typescript
const tuplaJS = ["Av Principal", 99, 150];
console.log(tuplaJS);
const tuplaTS: [string, number, number] = ["Av Principal", 99, 150];
console.log(tuplaTS);
```
# Enums (Estruturas com valores predefinidos)
- [x] TypeScript
```typescript
enum Cor {
  Cinza, // 0
  Verde, // 1
  Azul = 3 // 3
}

const corJS = Cor.Verde;
console.log(corJS);

const corTS: Cor = Cor.Verde;
console.log(corTS);

```
# Any
- [x] JavaScript
```javascript
const anyJS = "Tipagem";
```
- [x] TypeScript
```typescript
const anyTS: any = "Tipagem";
```
# Funções
- [x] JavaScript
```javascript
function retornaStringJS() {
  return nameJS;
}
console.log(retornaStringJS());
```
- [x] TypeScript
```typescript
function retornaStringTS(): string {
  return nameTS;
}

console.log(retornaStringTS());

function somaTS(A: number, B: number): number {
  return A + B;
}

```
# Tipo Função
- [x] TypeScript
```typescript
let calculoTS: (numeroA: number, numeroB: number) => number;
calculoTS = somaTS;
console.log(calculoTS(5, 6));
```

# Objetos
- [x] TypeScript
```typescript
const user: { nome: string; idade: number } = {
  nome: "Daniel",
  idade: 20
};
console.log(user);
```
# Definir tipo personalizado
- [x] TypeScript
```typescript
type usuario = {
  nome: string;
  id: number;
};

const usuario1: usuario = {
  nome: "Daniel",
  id: 1
};

const usuario2: usuario = {
  nome: "Brunno",
  id: 2
};
const usuario3: usuario = {
  nome: "Ramon",
  id: 3
};
```
# Union Types
- [x] TypeScript
```typescript
let nota: number | string = 10; //Ela pode receber number ou string
console.log(`Minha nota é ${nota}`);
```
# Checando tipos em JS
- [x] JavaScript
```javascript
const valor = 30;

if (typeof valor === "number") {
  console.log("É um number!");
} else {
  console.log(typeof valor);
}

```
# Tipo Never (Ou termina com erro ou fica em loop)
- [x] TypeScript
```typescript
function falha(msg: string): never {
  throw new Error(msg);
  while (true) {}
  //ou
}

const produto = {
  nome: "Sabão",
  preco: 1,
  validarProduto() {
    if (!this.nome || this.nome.trim().length == 0) {
      falha("Precisa ter um nome");
    }
    if (this.preco <= 0) {
      falha("Preco inválido!");
    }
  }
};
produto.validarProduto();

```
# Utilizar valores nulos em TypeScript
- [x] TypeScript
```typescript
let alturaOpcional: null | number = 14;
alturaOpcional = null;

type Contato = {
  nome: string;
  tel1: string;
  tel2: string | null;
};

const contato1: Contato = {
  nome: "Daniel",
  tel1: "123456789",
  tel2: null
};
console.log(contato1);
```
