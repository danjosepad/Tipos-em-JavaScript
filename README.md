# Tipos em TypeScript
Diferença dos tipos entre JavaScript e TypeScript. Conteúdo apresentado no curso: Entendendo TypeScript na Udemy: https://www.udemy.com/course/typescript-pt/.


## String
- [x] JavaScript
```javascript
const nameJS = "João";
console.log(nameJS); // João
```
- [x] TypeScript
```typescript
const nameTS: string = "João";
console.log(nameTS) // João
```
## Numbers
- [x] JavaScript
```javascript
const ageJS = 27;
console.log(ageJS); // 27
```
- [x] TypeScript
```typescript
const ageTS: number = 27;
console.log(ageTS); // 27
```

## Boolean
- [x] JavaScript
```javascript
const boolJS = false;
console.log(boolJS); // false
```
- [x] TypeScript
```typescript
const boolTS: boolean = false;
console.log(boolTS); // false
```

## Tipos Explicitos
- [x] JavaScript
```javascript
let typeAgeJS;
typeAgeJS = 27;
console.log(typeof typeAgeJS); // number
```
- [x] TypeScript
```typescript
let typeAgeTS: number;
typeAgeTS = 27;
console.log(typeof typeAgeTS); // number
```

## Arrays
- [x] JavaScript
```javascript
const arrayJS = ["Cozinhar", "Praticar Esportes"];
console.log(arrayJS); // ["Cozinhar", "Praticar Esportes"]
console.log(typeof arrayJS); // object
```
- [x] TypeScript
```typescript
const arrayTS: any[] = ["Cozinhar", "Praticar Esportes"];
console.log(arrayJS); // ["Cozinhar", "Praticar Esportes"]
console.log(typeof arrayJS);  // object
```
## Tuplas
- [x] JavaScript
```javascript
const tuplaJS = ["Av Principal", 99, 150];
console.log(tuplaJS); // ["Av Principal", 99, 150]
```
- [x] TypeScript
```typescript
const tuplaTS: [string, number, number] = ["Av Principal", 99, 150];
console.log(tuplaTS); // ["Av Principal", 99, 150]
```
## Enums (Estruturas com valores predefinidos)
```typescript
enum Cor {
  Cinza, // 0
  Verde, // 1
  Azul = 3 // 3
}
```
- [x] JavaScript
```javascript
const corJS = Cor.Verde;
console.log(corJS); // 1
```
- [x] TypeScript
```typescript
const corTS: Cor = Cor.Verde;
console.log(corTS); // 1
```
## Any
- [x] JavaScript
```javascript
const anyJS = "Tipagem";
```
- [x] TypeScript
```typescript
const anyTS: any = "Tipagem";
```
## Funções
- [x] JavaScript
```javascript
function retornaStringJS() {
  return nameJS;
}
console.log(retornaStringJS()); // João
```
- [x] TypeScript
```typescript
function retornaStringTS(): string {
  return nameTS;
}

console.log(retornaStringTS()); // João

function somaTS(A: number, B: number): number {
  return A + B;
}

```
## Tipo Função
- [x] TypeScript
```typescript
let calculoTS: (numeroA: number, numeroB: number) => number;
calculoTS = somaTS; // Recebe a funcao somaTS acima, que soma 2 valores

console.log(calculoTS(5, 6)); // 11
```

## Objetos
- [x] TypeScript
```typescript
const user: { nome: string; idade: number } = {
  nome: "Daniel",
  idade: 20
};
console.log(user); // {nome: "Daniel", idade: 20}
```
## Definir tipo personalizado
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
## Union Types
- [x] TypeScript
```typescript
let nota: number | string = 10; //Ela pode receber number ou string
console.log(`Minha nota é ${nota}`); // Minha nota é 10
```
## Checando tipos em JS
- [x] JavaScript
```javascript
const valor = 30;

if (typeof valor === "number") {
  console.log("É um number!");
} else {
  console.log(typeof valor);
}

```
## Tipo Never (Ou termina com erro ou fica em loop)
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
// O tipo Never, diferente do tipo void, ou termina com um erro, ou ficará em loop sem retornar algo
```
## Utilizar valores nulos em TypeScript
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
console.log(contato1); // {nome: "Daniel", tel1: "123456789", tel2: null}
```
# Conceitos em TypeScript

# Interfaces
- [x] TypeScript
```typescript

//Interface representa um contrato, e um objeto precisa atender as exigencias dessa interface
interface Human {
  name: string;
  age?: number; // Quer dizer que o atributo idade pode ou não aparecer dentro do objeto
  [prop: string]: any; //Não se sabe o nome nem o tipo do atributo
}

function sayHello(person: Human) {
  console.log(`Hello, ${person.name}`);
}
function changeName(person: Human) {
  person.name = "Joana";
}

const person: Human = {
  name: "João",
  age: 27
};

sayHello(person); // Hello, João
changeName(person); // Hello, Joana
sayHello(person);
sayHello({
  name: "Carl",
  age: 27,
  attribute: true
}); // Hello, Carl
```
## Classes com Interfaces
- [x] TypeScript
```typescript

class Client implements Human {
  name: string = "";
  age: number = 0;
  knowledge: string = "Javascript";
}

const client = new Client();
client.name = "Daniel";
client.age = 20;
client.knowledge = "JavaScript";

console.log(client); //Client {name: "Daniel", age: 20, knowledge: "JavaScript"}
```
## Interface com Função
- [x] TypeScript
```typescript
interface mathFunction {
  (a: number, b: number): number;
}

let pow: mathFunction;

pow = function(base: number, exp: number): number {
  return Array(exp)
    .fill(base)
    .reduce((accumulator, currentValue) => accumulator * currentValue);
  // Ou base ** exp ou Math.pow(base, exp)
};

console.log(pow(2, 8)); // 256
```

# Generics 

 O nome generics não vem de quem usa, e sim de quem construiu algo, como a função
 echo abaixo, e em algum momento poderá ser especificada.
 - [x] TypeScript
```typescript
function echo<T>(object: T): T {
  return object; // <T> definiu um tipo generico
}

console.log(echo("Daniel".length)); // Se torna um tipo definido no momento da execução

console.log(echo(27.lenght)); //O generic identificou que o 27 é number, e não possui .lenght

console.log(echo({ name: "Daniel", age: 20 })); // {name: "Daniel", age: 20}

console.log(echo<number>(27)); // 27
```
## Array
 - [x] TypeScript
```typescript
const grades: Array<number> = [10, 9.3, 7.7]; // A notação do generics especifica o tipo
grades.push(8.4);
grades.push("5.5"); //No momento que se define o <number>, essa linha retornará erro
console.log(grades); // (5) [10, 9.3, 7.7, 8.4, "5,5"]

/*
 O browser ainda apresenta o array, porém o código poderá ser configurado a
 não compilar caso o arquivo .ts contenha algum erro, previnindo assim a linha
 (avaliacoes.push("5.5") de funcionar.
*/

function print<T>(args: T[]) {
  args.forEach(element => console.log(element));
}

print([1, 2, 3]);
// 1
// 2
// 3
print<number>([1, 2, 3]);
// 1
// 2
// 3
print<string>(["Daniel", "Brunno", "Ramon"]);
// Daniel
// Brunno
// Ramon
print<{ name: string; age: number }>([
  { name: "Daniel", age: 20 },
  { name: "Brito", age: 20 },
  { name: "Mateus", age: 20 }
]);
// { name: "Daniel", age: 20 }
// { name: "Brito", age: 20 }
// { name: "Mateus", age: 20 }
type Student = { name: string; age: number };
// Pode usar um tipo para especificar a função generica
print<Student>([
  { name: "Daniel", age: 20 },
  { name: "Brito", age: 20 },
  { name: "Mateus", age: 20 }
]);
// { name: "Daniel", age: 20 }
// { name: "Brito", age: 20 }
// { name: "Mateus", age: 20 }
```
## Tipo Generico
- [x] TypeScript
```typescript
type Echo = <T>(data: T) => T;
const callEcho: Echo = echo;
// Ou const callEcho: <T>(data: T) => T = echo;

/*
Chamando a função echo nessa classe, que é:
  function echo<T>(object: T): T {
    return object;
  }
*/

console.log(callEcho<string>("Something happened")); // Something happened
```
## Classes com Generics
- [x] TypeScript
```typescript
class BinaryOperation {
  constructor(public operator1: any, public operator2: any) {}

  execute() {
    return this.operator1 + this.operator2;
  }
}

console.log(new BinaryOperation("Good ", "Morning").execute()); // Good Morning
console.log(new BinaryOperation(3, 7).execute()); // 10
console.log(new BinaryOperation(3, " Ops").execute()); //3 Ops

console.log(new BinaryOperation({}, {}).execute()); // Como concatenar os dois objetos?
// [object Object][object Object]

// Na prática esse tipo de operação não faz sentido, e pode causar problemas.
```

- [x] Prosseguindo com Generics
```typescript
class BinaryOperation<T> {
  constructor(public operator1: T, public operator2: T) {}

  execute() {
    return this.operator1 + this.operator2;
    // Retornará erro, pois o operador + não pode ser usado com os tipos genericos;
  }
}
```
- [x] Usando Abstract com Generics
 O abstract não está ligado ao generics, o uso dele é pelo fato de deixar abstrato
pois não se sabe como utilizá-la, e a responsabilidade será passada para os filhos
da classe
```typescript
abstract class BinaryOperation<T, R> {
  constructor(public operator1: T, public operator2: T) {}

  abstract execute(): R;
  // O R representará o retorno, que pode ser diferente dos operadores
  /*
  A flexibilidade dos parâmetros nos generics será definida durante o desenvolvimento
  onde pode haver um parametro para cada parametro, ou retorno
  como <T (para operator1), U (para operator2), R(para retorno)>
  */
}

class BinarySum extends BinaryOperation<number, number> {
  execute(): number {
    return this.operator1 + this.operator2;
  }
}

console.log(new BinarySum(3, 4).execute()); // 7


class DifferenceBetweenDates extends BinaryOperation<Data, string> {
  
   /*
  Função data chamada:
  class Data {
  // Público por padrão
  day: number;
  public month: number;
  year: number;

  constructor(day: number = 1, month: number = 1, year: number = 1970) {
    this.day = day;
    this.month = month;
    this.year = year;
  }
}
*/
 

  getTime(data: Data): number {
    const { day, month, year } = data;
    
    return new Date(`${month}/${day}/${year}`).getTime();
  }
  
  execute(): string {
    const t1 = this.getTime(this.operator1);
    const t2 = this.getTime(this.operator2);
    
    const diff = Math.abs(t1 - t2);
    const day = 1000 * 60 * 60 * 24; // Dia em milisegundos

    return `${Math.ceil(diff / day)} day(s)`;
  }
} // Retorna a diferença entre duas datas

const d1 = new Data(1, 2, 2020);
const d2 = new Data(5, 2, 2020);

console.log(new DifferenceBetweenDates(d1, d2).execute()); // 4 day(s)
```

## Restrições com Generics
```typescript
<T extends number>
// T só pode ser tipo number, ou outra subclasse do tipo

<T extends number | string>
// T pode ser ou number, ou string, ou subclasses dessas
```
