# Mulberry32 in Javascript
A fast, seedable, psuedo-random number generator for Javascript.

## Why is this useful? 
This is useful in situation the you need to generate random numbers a list of random numbers, but you want to generate the same ones every time. 

In [this video](https://www.youtube.com/watch?v=ALKqavp9Fg0&ab_channel=GoogleChromeDevelopers), the Google Chrome Developers team uses Mulberry32 to generate a CSS texture that is always the same.


## Version 1: Function
###### Credit: https://stackoverflow.com/questions/521295/seeding-the-random-number-generator-in-javascript
```javascript
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
```javascript
var mb32=a=>(t)=>(a=a+1831565813|0,t=Math.imul(a^a>>>15,1|a),t=t+Math.imul(t^t>>>7,61|t)^t,(t^t>>>14)>>>0)/2**32;
```

## Version 3: Another Function
>Mulberry32 is minimalistic generator utilizing a 32-bit state, originally intended for embedded applications. It appears to be very good; the author states it passes all tests of gjrand, and this JavaScript implementation is very fast. But since the state is 32-bit like Xorshift, it's period (how long the random sequence lasts before repeating) is significantly less than those with 128-bit states, but it's still quite large, at around 4 billion.
- [Bryc](https://github.com/bryc/code/blob/master/jshash/PRNGs.md)

###### [Original C Implementation](https://gist.github.com/tommyettinger/46a874533244883189143505d203312c)

```javascript
function mulberry32(a) {
    return function() {
      a |= 0; a = a + 0x6D2B79F5 | 0;
      var t = Math.imul(a ^ a >>> 15, 1 | a);
      t = t + Math.imul(t ^ t >>> 7, 61 | t) ^ t;
      return ((t ^ t >>> 14) >>> 0) / 4294967296;
    }
}
```
