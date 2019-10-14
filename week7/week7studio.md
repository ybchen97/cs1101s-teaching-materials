---
title: Week 7 Studio
theme: solarized
revealOptions:
    transition: 'slide'
---

# Week 7 Studio

---

### Matrices

> Write a function `matrix` that takes in a list of lists that represents a matrix. This function returns a matrix "object" which gives the entry at a given row and column

```javascript
const lst = list(list(1, 2, 3),
                 list(4, 5, 6),
                 list(7, 8, 9));

const m = matrix(lst);
// m(1)(1) === 1;
// m(2)(2) === 5;
// m(3)(1) === 7;
```

----

### [Matrices](https://sourceacademy.nus.edu.sg/playground#chap=2&exec=1000&ext=NONE&prgrm=GYVwdgxgLglg9mABAWwIZQE4wB4AoDOApgI4CUiA3gFCK2IaFQgZIaIC8AfIhB9wDYx8UAPoNguQcLGEJRYgBp6iALSIAjKSW81mgNxUAvlSoQEwxPwvtLQqJLu51SgExKAzFpp0fvn1PsAFiUAViUANi8-aP9HAHYlAA4lAE5SUgNTcygUDhR0LDwrKAyqAHoylCdSao52G3UDCqqXGta6mxCmyuRcT1r6mzi9IA)

```javascript
function matrix(seq) {
    return r => c => list_ref(list_ref(seq, r - 1), c - 1);
}
```

---

### Find Sum

> Given a list of numbers and a number, write a function `find_sum` that returns a list of lists containing all possible combinations of numbers that add up to the sum.

```javascript
find_sum(list(1, 2, 3, 4, 5), 5);
// returns [[5, null], [[2, [3, null]], [[1, [4, null]], null]]]
```

----

### Find Sum

```javascript
function find_sum(lst, sum) {
    if (sum === 0) {
        return list(null);
    } else if (is_null(lst) || sum < 0) {
        return null;
    } else {
        // don't use the head
        const no_use = find_sum(tail(lst), sum);
        // uses the head
        const first = head(lst);
        const sub = find_sum(tail(lst), sum - first);
        const use = map(xs => pair(first, xs), sub);
        return append(no_use, use);
    }
}
```

---

### [Can partition?](https://sourceacademy.nus.edu.sg/playground#chap=2&exec=1000&ext=NONE&prgrm=GYVwdgxgLglg9mABBAhmA%2BgBxQJ1rBACgBsBnKASkQG8AoRB5BcxKOKFYxAXkRQgggAtiGIooAU0KEAHgBpEATyrcAfIhmIA1EoUAGBWUoBueozMNQkAkgAWE4pgk4S5BaWFU6jH4hjBEQg8hRAAqRAAmHm5eNg5iLwtfHxwJKBAcJCgcEAlTZIYAX0QHUgk-AKDhMMjEdTjORAAfJr9SdDBRYldKRILfVPTMxGBOMvyC4tLy737GQYy7BycXDhhuowp3ap17FAATHooqFqS55PtHZ0I1jfItxGCKCeTCpOKkpP9Ahq4AUlqAEIYog9H0CgthqMyHl3iUYTQzgxIUsri4jPpnu8kQxaG9aKgMNg8DAbCQYORCABGBQRBQAZgUABZjsZEAB6dmIFGkVg5CQEtBYXD4eBgcmUmmRZkKACcrI5XJ5IzGEiAA)

> Given a list of numbers and a number, write a function `can_partition` that returns `true` if the list can be partitioned into 2 portions of equal sum and `false` otherwise.

```javascript
can_partition(list(1, 2, 3, 4)); // returns true
can_partition(list(1, 2, 4, 9)); // returns false
```
