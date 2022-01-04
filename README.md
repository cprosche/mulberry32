# mulberry32
The fastest, 32-bit state, seeded random number generator function in Javascript. 

Pulled from this Stack Overflow post: https://stackoverflow.com/questions/521295/seeding-the-random-number-generator-in-javascript

```
function mulberry32(a) {
    return function() {
      var t = a += 0x6D2B79F5;
      t = Math.imul(t ^ t >>> 15, t | 1);
      t ^= t + Math.imul(t ^ t >>> 7, t | 61);
      return ((t ^ t >>> 14) >>> 0) / 4294967296;
    }
}
```
