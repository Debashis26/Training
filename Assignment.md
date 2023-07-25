# What are the 4 rules of simple design?

**1.Test**  

**2.DRY**  

**3.Express Intent**  

**4.Small**  


##Example

```typescript

    class Calculator {
  addNumbers(a: number, b: number) {
    console.log(a + b);
  }
  subNumbers(a: number, b: number) {
    console.log(a - b);
  }
  MulNumbers(a: number, b: number) {
    console.log(a * b);
  }
  divideNumbers(a: number, b: number) {
    console.log(a / b);
  }
}

const calculator = new Calculator();
calculator.divideNumbers(10, 2);

//calculator.divideNumbers(10, 0); fail
``` typescript
## Test
 *Here in this example, this program will pass in some tests but with some tests, it will fail. *

## DRY
* In this program, we write the print statement several times and every time it is performing the same task. So it is against the 2nd rule of simple design.*

##Express Intent


##Small
* In this code block every Function performing more than one work*

