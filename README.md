# calculadota.ts

// Interface Strategy
interface Strategy {
  execute(num1: number, num2: number): number;
}

// Concrete Strategies
class Soma implements Strategy {
  execute(num1: number, num2: number): number {
    return num1 + num2;
  }
}

class Subtracao implements Strategy {
  execute(num1: number, num2: number): number {
    return num1 - num2;
  }
}

class Multiplicacao implements Strategy {
  execute(num1: number, num2: number): number {
    return num1 * num2;
  }
}

// Client
class Calculadora {
  private strategy: Strategy;

  setStrategy(strategy: Strategy) {
    this.strategy = strategy;
  }

  calcular(num1: number, num2: number) {
    return this.strategy.execute(num1, num2);
  }
}

// Uso
const calculadora = new Calculadora();

let num1 = Number(prompt("Insira o primeiro valor: "));
let num2 = Number(prompt("Insira o segundo valor: "));
let operacao = prompt("Insira a operação matemática (+, -, *): ");

switch (operacao) {
  case "+":
    calculadora.setStrategy(new Soma());
    break;
  case "-":
    calculadora.setStrategy(new Subtracao());
    break;
  case "*":
    calculadora.setStrategy(new Multiplicacao());
    break;
  default:
    console.log("Operação inválida.");
    break;
}

const resultado = calculadora.calcular(num1, num2);
console.log(`Resultado: ${resultado}`);
