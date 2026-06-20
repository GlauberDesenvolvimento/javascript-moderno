## NOVIDADES JS ES6, ES7, ES8

### DECLARAÇÃO DE VARIÁVEIS LET (block-scoped)
```javascript
let a = 1;
let b = 2;
let c = 0;
```
### DECLARAÇÃO DE VARIÁVEIS CONST (constants)
const PI = 3.1411593;

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
function f (x, y, ...a) {
    return (x + y) * a.length
}
f(1, 2, "hello", true, 7) === 9 // ["hello", true, 7].length = 3
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
var valores = ["35 anos", "Mora em Brasília"];
var mensagem = `${name} ${sobrenome}, ${valores.join(", ")}`; // 'Glauber Santos, 35 anos, Mora em Brasília'
```

### MAP (Objeto Map)
```javascript
[1, 2, 3].map(function(item, index){ return index+ ": " +item }) //['0: 1', '1: 2', '2: 3']
```

### OPERADORES LÓGICOS DE ATRIBUIÇÃO (Logical Assignment Operators)
```javascript
var chave = "chaveObj";
var valor = "valorObj";
console.log({
    [chave]: valor
}); // {chaveObj: "valorObj"}
console.log({chave}); // {chave: "chaveObj"}
console.log({
	foo (a, b) {},
	bar (x, y) {}
}); // { foo: ƒunction(a, b){}, bar: ƒunction(x, y){} }
```

### DESESTRUTURAÇÃO DE VARIÁVEIS (Destructuring Assignment)
```javascript
var list = [ 1, 2, 3 ];
var newList = [ a, , b ];
console.log(newList);
// [1, undefined, 3]
console.log(newList[1])
// undefined

var list = [ 1, 2, 3 ];
var [ a, , b ] = list;
console.log(a, b); // 1 3

var obj = { foo: "value1", boo: "value2" };
var { foo, boo } = obj;
console.log(foo, boo); // value1 value2
```

### MÓDULOS (Export/Import)
```javascript
export function sum (x, y) { return x + y }
export var pi = 3.141593

//app.js
import * as math from "math";
console.log(math.pi, math.sum(1,2));
import { sum, pi } from "math";
console.log(sum(1,2), pi);
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
	_age = "";
	#privateVar = "";
	#provateMethod(){}
  static #testePrivado = "teste";
	static teste = "teste";
	constructor(name, lastName){
		this.name = name;
		this.lastName = lastName;
	}
	fullname(){
		return `${this.name} ${this.lastName}`;
	}
	get age() { return this._age; }
	set age(value) { this._age = value; }
}
const pessoa = new Pessoa("Glauber", "Gonçalves");
```

### EXTENDS GET E SET
```javascript
class Profissao extends Pessoa {
	#nomeProfissao = "";
  constructor (_nomeProfissao) {
      super(name, lasName);
      this.#nomeProfissao = _nomeProfissao;
  }
  set nomeProfissao (_nomeProfissao) { 
  	this.#nomeProfissao = _nomeProfissao;
  }
  get nomeProfissao () {
  	return this.#nomeProfissao;
  }
  toString () {
    return `Profissão: (${this.nomeProfissao})`
  }
}
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
console.log(nfBRL.format(100200300.40)); //R$ 100.200.300,40
```

#### hex — base 16 — starts with 0x
#### Oct — base 8 — starts with 0o
#### Binary — base 2 — starts with 0b
```javascript
var decimalLit = 15;
var hexadecimalLit = 0xF;
var octalLit = 0o17;
var binaryLit = 0b1111;
console.log(hexadecimalLit);
console.log(octalLit);
console.log(binaryLit);
```

### OBJECT MAP
```javascript
let m = new Map();
m.set('key1', 'value1');
m.set('key2', 'value2');

m.forEach((key, value, map) => {
    console.log(key,value, map); //value1 key1 {key1: 'value1', key2: 'value2'}
})

console.log(m.size); // 0
console.log(m.keys()); // Map {'key1', 'key2'}
console.log(m.values()); // Map {'value1', 'value2'}
console.log(m.get("key1")); //value1
m.clear(); ; //Vai esvaziar o mapa
console.log(m); // Map(0) {size: 0}
```

### PROMISSES (Combination)
```javascript
Promise.all([
    Promise.resolve(1),
    Promise.resolve(2),
    Promise.resolve(3)
]).then((data) => {
    console.log(data)
}, (err) => {
    console.log(`error: ${err}`)
});
const myPromiseArray = [
	Promise.resolve(100),
	Promise.reject(null),
	Promise.reject(new Error("Ho No"))
];
Promise.allSettled(myPromiseArray).then( (results) => { console.log(results) });
//(3) [{status: 'fulfilled', value: 100}, {status: 'rejected', reason: null}, {status: 'rejected', reason: Error: Ho No at <anonymous>:4:17}]
```

### ASYNC/AWAIT
```javascript
var Api = {
	get: function (url) {
		return new Promise((resolve, reject) => {
			if(url == undefined){
				throw "url inexistente";
			}
			if(url.startsWith("http") && (url.includes(".com") || url.includes(".com.br"))){
				setTimeout(()=>{
					resolve(url + " aceita");
				}, 1000);
			}else{
				setTimeout(()=>{
					reject(url + " rejeitada");
				}, 3000);
			}
		});
	}
}

async function request(url) {// Consumindo uma api simulada com promise com função assíncrona
  try {
    const response = await Api.get(url);
    console.log("try");
    console.log(response);
  } catch (err) {
  	console.log("Catch");
    console.log(err);
  }
}
```

### GLOBAL THIS OBJECT - Se refere ao objeto this não importa onde esteja
```javascript
console.log(globalThis); //window
var obj = {
	fnc: function(){
		console.log(globalThis); //window
	}
}
obj.fnc();
```

### VERIFICAÇÃO DE OBJETOS COM ATRIBUIÇÃO
```javascript
let a = 1;
let b = 2;
let c = 0;

a &&= b; // if(a) a = b;
c ||= b; // if(!c) c = b;
c ??= a; // if(!c) c = a; // PARA FALSEAVEIS -> 0 == false; "" == false; [] == false
```

### OPERADORES DE OBJETOS
```javascript
const user = {
	nickname: "Glauber",
	profile: {
		name: "Gonçalves"
	},
	address: {
  }
}
```

### ENCADEAMENTO OPCIONAL (Optional Chaining)
```javascript
console.log(user.address?.street); 
console.log(user.address.street || "O valor não existe");
console.log(user.address.street ?? "O valor não existe") //FALSEAVEIS -> 0 == false; "" == false; [] == false
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
```

### BIG INT
```javascript
var amount =        999999999999999; //Acima de 15 dígitos o javascript não calcula
var bigInt = BigInt(999999999999999_999999999999999);
console.log(bigInt);
```