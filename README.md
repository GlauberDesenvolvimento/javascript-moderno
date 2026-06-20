## NOVIDADES JS ES6, ES7, ES8

### DECLARAÇÃO DE VARIÁVEIS LET (block-scoped)
```javascript
let a = 1;
let b = 2;
let c = 0;
```

### DECLARAÇÃO DE VARIÁVEIS CONST (constants)
```javascript
const PI = 3.1411593;
```

### ANONYMOUS FUNCTIONS (Block-Scoped Functions)
```javascript
{
	0;
} //(function(){ return 0; })();
```

### ARROW FUNCTIONS
```javascript
() => {} // function () {}
(res) => res // function (res) { return res; }
```

### PARÂMETROS DEFAULT (default parameters)
```javascript
function f (x, y = 7, z = 42) {
    return x + y + z
} // f(1) === 50
```

### MANIPULAÇÃO DE PARÂMETROS (Rest Operator)
```javascript
function f(...a) {
    return a;
}
console.log(f(1, 3, 4, 5)); // [1, 3, 4, 5]
```

### Junção de arrays (Spread Operator)
```javascript
var params = [ "hello", true, 7 ]
var other = [ 1, 2, ...params ] // [ 1, 2, "hello", true, 7 ]
```

### Interpolação de String (String Interpolation)
```javascript
var name = "Glauber";
var sobrenome = "Santos";
var valores = ["Mora no Brasil", "Analista de Sistemas"];
var mensagem = `${name} ${sobrenome}, ${valores.join(", ")}`; // 'Glauber Santos, Mora no Brasil, Analista de Sistemas'
```

### MAP (Transforma arrays)
```javascript
var keys = ['a', 'b', 'c'];
[1, 2, 3].map(function(item, index){ return {[keys[index]]: item} }) //[{ a: 1 }, { b: 2 }, { c: 3 }]

//OU

[1, 2, 3].map( (item, index) => ({ [keys[index]]: item }) );

```

### OPERADORES LÓGICOS DE ATRIBUIÇÃO (Logical Assignment Operators)
```javascript
var chave = "chaveObj";
var valor = "valorObj";

console.log({ [chave]: valor }); // {chaveObj: 'valorObj'}
console.log({chave}); // {chave: 'chaveObj'}
console.log({ foo(a, b) {}, bar(x, y){} }); // { foo: ƒunction(a, b){}, bar: ƒunction(x, y){} }
```

### DESESTRUTURAÇÃO DE VARIÁVEIS (Destructuring Assignment)
```javascript
var list = [ 1, 2, 3 ];
var newList = [ a, , b ];

console.log(newList);// [1, undefined, 3]
console.log(newList[1])// undefined

var list = [ 1, 2, 3 ];
var [ a, , b ] = list;
console.log(a, b); // 1 3

var obj = { foo: "value1", boo: "value2" };
var { foo, boo } = obj;
console.log(foo, boo); // value1 value2
```

### MÓDULOS (Export/Import)
```javascript
//modulo.js
export function sum (x, y) { return x + y }
export var pi = 3.141593

// app.js
import * as modulo from "./modulo.js";
console.log(modulo.pi, modulo.sum(1, 2));
// outroarquivo.js
import { sum, pi } from "./modulo.js";
console.log(sum(1, 2), pi);
```

### BUSCA EM STRINGS (String Searching)
```javascript
"hello boy".startsWith("hello"); // true
"hello boy".endsWith("boy"); // true
"hello boy".includes("ell"); // true
```

### CLASSES
```javascript
class Pessoa {
	name = "";
	lastName = "";
	_age = 0;
	#privateVar = "";
	#privateMethod(){}
  	static #testePrivado = "teste";
	static teste = "teste";
	constructor(name, lastName){
		this.name = name;
		this.lastName = lastName;
	}
	fullName(){
		return `${this.name} ${this.lastName}`;
	}
	get age() { return this._age; }
	set age(value) { this._age = value; }
}
const pessoa = new Pessoa("Glauber", "Gonçalves");
pessoa.age = 18;
console.log(pessoa.fullName());//Glauber Gonçalves
console.log(pessoa.age);//18
```

### HERANÇA (Get, Set, toString)
```javascript
class Profissao extends Pessoa {
	#nomeProfissao = "";
	constructor (name, lastName, nomeProfissao) {
		super(name, lastName);
		this.#nomeProfissao = nomeProfissao;
	}
	set nomeProfissao (nomeProfissao) { 
		this.#nomeProfissao = nomeProfissao;
	}
	get nomeProfissao () {
		return this.#nomeProfissao;
	}
	toString () {
		return `Profissão: (${this.nomeProfissao})`
	}
}

const profissao = new Profissao("Glauber", "Gonçalves", "Analista");
console.log(profissao.fullName());//Glauber Gonçalves
console.log(profissao.toString());//Profissão: Analista
```

### DATE STRING
```javascript
new Date().toLocaleString(); // 99/99/9999 99:99:99
new Date().toLocaleDateString(); // 99/99/9999
new Date().toLocaleTimeString(); // 99:99:99
```

### INTL OBJECT (Internacionalization & Location)
```javascript
var nf1 = new Intl.NumberFormat("en-US")
var nf2 = new Intl.NumberFormat("pt-BR")
console.log(nf1.format(1234567.89)) //1,234,567.89
console.log(nf2.format(1234567.89)) //1.234.567,89

var nfUSD = new Intl.NumberFormat("en-US", { style: "currency", currency: "USD" });
var nfBRL = new Intl.NumberFormat("pt-BR", { style: "currency", currency: "BRL" });
console.log(nfUSD.format(100200300.40)); //$100,200,300.40
console.log(nfBRL.format(100200300.40)); //R$ 100.200.300,40
```

#### Hexadecimal — Base 16 — Prefixo `0x`
#### Octal — Base 8 — Prefixo `0o`
#### Binário — Base 2 — Prefixo `0b`
```javascript
const decimalLit = 15;
const hexadecimalLit = 0xF;
const octalLit = 0o17;
const binaryLit = 0b1111;

console.log(hexadecimalLit); // 15
console.log(octalLit);       // 15
console.log(binaryLit);      // 15
```

### OBJECT MAP
```javascript
let m = new Map();
m.set('Chave', 'Valor');
m.set('Chave2', 'Valor2');
console.log(m);// Map(2) {'Chave' => 'Valor', 'Chave2' => 'Valor2'}

console.log(m.size); // 2
console.log(m.keys()); // MapIterator {'Chave', 'Chave2'}
console.log(m.values()); // MapIterator {'Valor', 'Valor2'}
console.log(m.get("Chave")); //Valor
m.clear(); ; //Limpa o map
console.log(m); // Map(0) {size: 0}
```

### PROMISSES (Combination)
```javascript
Promise.all([
    Promise.resolve(1),
    Promise.resolve(2),
    Promise.resolve(3)
]).then((data) => {
    console.log(data);//[1, 2, 3]
}, (err) => {
    console.log(`error: ${err}`);
});
const myPromiseArray = [
	Promise.resolve(100),
	Promise.reject("Deu erro!")
];
Promise.allSettled(myPromiseArray).then( (results) => { console.log(results) });
//[{status: "fulfilled", value: 100}, {status: "rejected", reason: "Deu erro!"}]
```

### ASYNC/AWAIT
```javascript
async function num() {
    const response = await 2;
    return response;
}
num().then((r)=>{console.log(r)}); //sempre retorna uma promise
```

### GLOBAL THIS OBJECT (Objeto Global)
```javascript
var obj = {
	fnc: function () {
		console.log(globalThis); // Objeto global (window no navegador)
	}
}
obj.fnc(); // window
```
### OPERADORES LÓGICOS DE ATRIBUIÇÃO (Logical Assignment Operators)

```javascript
let a = 1;
let b = 2;
let c = 0;
let d = null;

a &&= b; // Se "a" for truthy, recebe o valor de "b".
         // Equivale: if (a) a = b;

c ||= b; // Se "c" for falsy, recebe o valor de "b".
         // Equivale: if (!c) c = b;

d ??= a; // Se "d" for null ou undefined, recebe o valor de "a".
         // Equivale: if (d === null || d === undefined) d = a;
```

### ENCADEAMENTO OPCIONAL (Optional Chaining)

```javascript
const user = {
    nickname: "Glauber",
    age: 0,
    street: "",
    address: {}
};

console.log(user.address?.street); // undefined

console.log(user.age || 18); // 18 -> Considera valores falsy (false, 0, "", NaN, null e undefined)
console.log(user.age ?? 18); // 0  -> Considera apenas null e undefined

console.log(user.street || "Não informado"); // Não informado
console.log(user.street ?? "Não informado"); // ""
```

### REPLACE ALL
```javascript
const text = "Olá mundo esse é meu mundo";
console.log(text.replace(/mundo/g, 'batata')); //FORMA TRADICIONAL
console.log(text.replaceAll('mundo', 'batata'));//NOVO MÉTODO
```

### NUMERIC SEPARATOR
```javascript
var num = 123_20; // _ serve para separar milhares, centenas, dezenas e decimais
console.log(num); //12320
```

### BIG INT
```javascript
var amount = 999999999999999; //Acima do limite seguro, o Number perde precisão
var bigInt = BigInt(9999999999999999n); // Aceita inteiros arbitrariamente grandes
console.log(bigInt); // 9999999999999999n
```