# What are the 4 rules of simple design?

1. **Test**
2. **DRY**
3. **Express Intent**
4. **Small**

# What is a simple design?

Complexity can really hold you back when developing software. So the simplest solutions are the best when building robust and efficient systems. Simple design is a fundamental principle that can help designers create effective, easy-to-use products. But what does it mean to design, and how can we achieve it?

In 2014, Corey Haines published the book “Understanding the 4 Rules of Simple Design, " describing the 4 rules of simple design.

**The rules**

1. Tests pass
2. Expresses intend
3. No duplication (DRY)
4. Small

**Test pass**  
        Pass the Test. The first rule of simple design is to pass the test. According to Beck, a design should be considered "simple" if it passes all the test cases.
```typescript
function fun(a: number, b: number): number {
    return a + b;
}
```
*Test case for function fun*

```typescript
function testFunction() {
    let result = fun(2, 3);
    if (result !== 5) {
        throw new Error(`Expected 5 but got ${result}`);
    }

    result = fun(-1, 1);
    if (result !== 0) {
        throw new Error(`Expected 0 but got ${result}`);
    }

    result = fun(0, 0);
    if (result !== 0) {
        throw new Error(`Expected 0 but got ${result}`);
    }

    console.log("All tests passed!");
}

testFunction();
```
This is the simple code to test the function ``` fun() ```, If it passes all the test cases then this code will be a simple code.

**Express Intent of programmer**  
When you look at a piece of code it should immediately tell you what it does and it shouldn’t surprise you. Variable, method, and class names should describe what they do. The code should be easy to read, and the design should be simple to understand. This principle is also called Clarity Of Code.

From the previous example, the intention of the code is not clear.  
```typescript
function fun(a: number, b: number): number {
    return a + b;
}
```
Instate of writing ```fun()``` we can write ```add()```. Because the motive of this code is to add numbers.  
**Ex**
```typescript
function add(a: number, b: number): number {
    return a + b;
}
```
**DRY (Do not Repeat Yourself) or Code Duplication**  
*Code duplication* is a common ailment in many codebases throughout the software industry. Many projects are declared to be of poor quality due to excessive duplication.
*DRY (Don't Repeat Yourself)* is a software development principle that encourages developers to avoid duplicating code or logic in multiple places within a codebase. The goal of DRY is to reduce redundancy, improve maintainability, and make it easier to manage and update code.
**Ex**    
Let's suppose we have to calculate the total price and total tax. So here is the example without the **DRY** concept.
```typescript
// Duplicated code without DRY
function calculateTotalPrice(items: Item[]): number {
    let total = 0;
    for (const item of items) {
        total += item.price;
    }
    return total;
}

// In another part of the codebase...
function calculateTax(items: Item[]): number {
    let tax = 0;
    for (const item of items) {
        tax += item.price * 0.1; // Assume a fixed tax rate of 10%
    }
    return tax;
}
```
Here, we iterate over the items and perform calculations that are duplicated in both the ```calculateTotalPrice``` and ```calculateTax``` functions.
Let's try to achieve the same concept by using **DRY**  
```typescript
//calculate total
function calculateTotal(items: Item[], getAmount: (item: Item) => number): number {
    let total = 0;
    for (const item of items) {
        total += getAmount(item);
    }
    return total;
}

//Getting price of item
function getPriceAmmount(item: Item): number {
    return item.price;
}
//Getting tax of item
function getTaxAmmount(item: Item): number {
    return item.price * 0.1; // Assume a fixed tax rate of 10%
}


const items: Item[] = /* ... */; // Array of items

const totalPrice = calculateTotal(items, getPriceAmmount); // Calculates the total price of items
const totalTax = calculateTotal(items, getTaxAmmount);     // Calculates the total tax amount for items
```
In this revised code, we have a single ```calculateTotal``` function that takes an array of items and a calculation function. This function abstracts away the repetitive iteration logic. We then define separate calculation functions (```getPriceAmmount``` and ```getTaxAmmount```) that are passed to calculateTotal based on the specific calculation needed.

By following the DRY principle, we have eliminated code duplication and made the code more maintainable. If you need to change the calculation logic, you only need to update it in one place, reducing the risk of introducing errors.  

**Naive Duplication**  

*Naive Duplication* refers to the practice of duplicating code or logic without fully considering the implications and potential consequences. It often involves copying and pasting sections of code without thoroughly understanding the purpose or behaviour of the code being duplicated. Naive duplication can lead to problems such as inconsistency, maintenance challenges, and increased risk of errors.  

