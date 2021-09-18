---
layout: post
title:  "JAVASCRIPT(JS) 숫자 가격 표시 천단위 콤마"
date:   2021-08-04 22:25:41 +0900
categories: javascript
---

## JavaScript(js) 숫자 가격 표시 천단위 콤마(javascript(js) thousand separator)

``` javascript
function numberWithCommas(x) {
    return x.toString().replace(/\B(?<!\.\d*)(?=(\d{3})+(?!\d))/g, ",");
}
```

### TEST

``` javascript
function numberWithCommas(x) {
    return x.toString().replace(/\B(?<!\.\d*)(?=(\d{3})+(?!\d))/g, ",");
}

function test(x, expect) {
    const result = numberWithCommas(x);
    const pass = result === expect;
    console.log(`${pass ? "✓" : "ERROR ====>"} ${x} => ${result}`);
    return pass;
}

let failures = 0;
failures += !test(0,        "0");
failures += !test(100,      "100");
failures += !test(1000,     "1,000");
failures += !test(10000,    "10,000");
failures += !test(100000,   "100,000");
failures += !test(1000000,  "1,000,000");
failures += !test(10000000, "10,000,000");
if (failures) {
    console.log(`${failures} test(s) failed`);
} else {
    console.log("All tests passed");
}
```

출처: [https://stackoverflow.com/questions/2901102/how-to-print-a-number-with-commas-as-thousands-separators-in-javascript](https://stackoverflow.com/questions/2901102/how-to-print-a-number-with-commas-as-thousands-separators-in-javascript)