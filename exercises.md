## O notations:
### 1)
```
int product(int a, int b) {
    int sum = 0;
    for (int i= 0; i < b; i++) {
        sum += a;
    }
    return sum;
}

--> O(b)
```


### 2)
```
int power(int a, int b) {
    if (b < 0) {
        return 0; // error
    } else if (b == 0) {
        return 1;
    } else {
        return a* power(a, b - 1);
    }
}

--> O(b) //remember: linear recursion
```


### 3)
```
int mod(int a, int b) {
    if (b <= 0) {
        return -1;
    }
    int div = a / b;
    return a - div * b;
}

--> O(1)
```

### 4)
```
int div(int a, int b) {
    int count = 0;
    int sum = b· ,
    while (sum <= a) {
        sum += b;
        count++;
    }
    return count;
}

--> O(a/b)
```

### 5)
```
int sqrt(int n) {
return sqrt_helper(n, 1, n);
}
int sqrt_helper(int n, int min, int max) {
    if (max < min) return -1; // no square root
        int guess = (min + max) / 2·,
        if (guess *guess == n) { // found it!
            return guess;
    } else if (guess * guess < n) { // too low
        return sqrt_helper(n, guess + 1, max); // try higher
    } else { // too high
        return sqrt_helper(n, min, guess - l); // try lower
    }
} 
--> O(max-min) // the trick here is to know what is the worst case scenario (when it doesn't find the numeber) + we have linear recursion (not in tree form)
```

### 6)
```
int sqrt(int n) {
    for (int guess = 1; guess * guess <= n; guess++) {
        if (guess * guess == n) {
            return guess;
        }
    }
    return -1; 
}

--> O(sqrt(n))
```

### 7)
If a binary search tree is not balanced, how long might it take (worst case) to find an element in it? 
--> O(n) where n is the number of nodes in the tree

### 8)
You are looking for a specific value in a binary tree, but the tree is not a binary search tree. What is the time complexity of this?
--> O(n) because we are searching in all the tree 

### 9)
```
int[] copyArray(int[] array) {
    int[] copy= new int[0];
    for (int value : array) {
        copy= appendToNew(copy, value);
    }
    return copy;
}

int[] appendToNew(int[] array, int value) {
    // copy all elements over to new array
    int[] bigger= new int[array.length + 1];

    for (int i= 0; i < array.length; i++) {
        bigger[i] = array[i];
    }
    // add new element
    bigger[bigger.length - 1]
    return bigger; 
}

--> O(N^2) because for each element we have an incrementation 
    for first element we have 1 (creation of array element 1 + filling)
    for second element we have 2 (creation of array element 2 + filling)
    for the third element we have 3 (creation of array element 3 + filling)
    ..
    and so on until n
    and thus we have 1 + 2 +... + n = (n+1)*n/2 which will result in the end with o(n^2)
```

### 10)
```
int sumDigits(int n) {
    int sum = 0;
    while (n > 0) {
        sum += n % 10;
        n /= 10;
    }
    return sum;
}

--> O(Log_10(n))
```

### 11)
The following code prints all strings of length k where the characters are in sorted order. It does this by generating all strings of 
length k and then checking if each is sorted. What is its runtime?

```
int numChars = 26;
void printSortedStrings(int remaining) {
    printSortedStrings(remaining, "");
}

void printSortedStrings(int remaining, String prefix) {
    if (remaining== 0) {
        if (isinOrder(prefix)) {
            System.out.println(prefix);
        }
    } else {
        for (int i= 0; i < numchars; i++) {
            char c = ithletter(i);
            printSortedStrings(remaining - 1, prefix + c);
        }
    }
}


boolean isinOrder(String s) {
    for (int i= 1; i < s.length(); i++) {
        int prev ithLetter(s.charAt(i - 1));
        int curr = ithLetter(s.charAt(i));
        if (prev > curr) {
            return false;
        }
    }
    return true;
}



char ithLetter(int i) {
    return (char) (((int) 'a') + i);
} 

```

### 12)

```
The following code computes the intersection (the number of elements in common) of two arrays. It assumes that neither array has duplicates.
It computes the intersection by sorting one array (array b) and then iterating through array a checking (via binary search) if each value is in b. What is its runtime? 


int intersection(int[] a, int[] b) {
    mergesort(b);
    int intersect = 0;
    for (int x : a) {
        if (binarySearch(b, x) >= 0) {
            intersect++;
        }
    }
    return intersect;
}

```