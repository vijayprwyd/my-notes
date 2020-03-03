---
tags: [JS_DS]
title: JS
created: '2020-02-14T04:28:11.110Z'
modified: '2020-02-14T04:31:30.059Z'
---

# JS

```
1. Given two lists of closed intervals, each list of intervals is pairwise disjoint and in sorted order.
Return the intersection of these two interval lists.

Input: A = [[0,2],[5,10],[13,23],[24,25]], B = [[1,5],[8,12],[15,24],[25,26]]
Output: [[1,2],[5,5],[8,10],[15,23],[24,24],[25,25]]
Reminder: The inputs and the desired output are lists of Interval objects, and not arrays or lists.



```


```js

//  A = [[0,2],[5,10],[13,23],[24,25]], B = [[1,5],[8,12],[15,24],[25,26]]
//[[1,2],[5,5],[8,10],[15,23],[24,24],[25,25]]


let result = [], A = [[0,2],[5,10],[13,23],[24,25]], B = [[1,5],[8,12],[15,24],[25,26]]

const min = (a, b) => a > b ? b : a;
const max = (a, b) => a > b ? a : b;

for(let i = 0, j = 0; i < A.length && j < B.length;) {

  if(!(A[i][1] < B[j][0] || B[j][1] < A[i][0])) {
 	 	result.push([max(A[i][0], B[j][0]), min(A[i][1], B[j][1])]);
  }

  	A[i][1] > B[j][1] ? j++ : i++;
}

console.log(result);

```


```
2. Input: numerator = 1, denominator = 2
  Output: "0.5"

  Input: numerator = 3, denominator = 1
  Output: "3"

  Input: numerator = 2, denominator = 3
  Output: "0.(6)"

```



```js


function fraction(numerator, denominator) {

	let numberSet = new Set();
  	let rem = 0, str = "";
    let lhs = `${Math.floor(numerator/denominator)}`
    numerator = (numerator % denominator) * 10;
  	while(!numberSet.has(numerator) && numerator !== 0) {
          numberSet.add(numerator);
          let div = Math.floor(numerator / denominator);
      	  let rem = (numerator % denominator) * 10;
      	  str += div;
      	  numerator = rem;      
     }
	return numerator === 0 ? `${lhs}.${str === "" ? "0" : str}` : `${lhs}.(${str})`;
}

console.log(fraction(20, 10));
console.log(fraction(20, 7));
console.log(fraction(1, 3));
console.log(fraction(0, 3));
console.log(fraction(4, 333));



```

