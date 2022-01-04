# mulberry32
The fastest, 32-bit state, seeded random number generator function in Javascript. 

## Version 1: Function
###### Credit: https://stackoverflow.com/questions/521295/seeding-the-random-number-generator-in-javascript
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
## Version 2: Oneliner Assigned to Variable
###### Credit: https://gist.github.com/blixt/f17b47c62508be59987b
```
var mb32=a=>(t)=>(a=a+1831565813|0,t=Math.imul(a^a>>>15,1|a),t=t+Math.imul(t^t>>>7,61|t)^t,(t^t>>>14)>>>0)/2**32;
```
