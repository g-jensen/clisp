Client should be able to specify what words convert to functions call, lets, assignments, etc...

Example:
```
{"include"  :include
 "def"      :define-global
 "@"        :deref-ptr
 "defn"     :define-function
 "let"      :define-local
 "set!"     :assign-var
 "nth"      :array-access}
```

Other random ideas:

---
```
(include <stdio.h>)

(def void* my-ptr nullptr)

(defn int main []
  (printf "Hello, World!")
  (set! @my-ptr 5)
  (return 0))
```
=>
```
#include <stdio.h>

void* my_ptr = nullptr;

int main() {
  printf("Hello, World!");
  *my_ptr = 5;
  return 0;
}
```
---
```
(let [int* arr (malloc (* (sizeof int) 3))]
  (set! (nth arr 0) 5)
  (set! (nth arr 1) 10)
  (set! (nth arr 2) 7))
```
=>
```
int* arr = malloc(sizeof(int) * 3);
arr[0] = 5;
arr[1] = 10;
arr[2] = 7;
```
---
