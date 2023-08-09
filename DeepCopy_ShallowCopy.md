### Deep copy and Shallow Copy   

In JavaScript when we copy an object or an Array, the address is passed to the variable instead of the data present in that object or array.
So, If we do any modification in the new object it also reflects in the old object or array. To overcome this problem we have the concept of ```Shallow copy``` and ```Deep Copy```.

**Ex**  
```javascript
let obj={
    name:"debashis",
    role:"developer"
}

let newObj=obj;
newObj.name='deb'

console.log(obj);
```
**Output**  
```{ name: 'deb', role: 'developer' }```

Here we copy the ```obj``` to ```newObj``` & we did modifications in ```newObj.name```. When we tried to print the obj, the the value of object also got modified.

**Shallow Copy** 


