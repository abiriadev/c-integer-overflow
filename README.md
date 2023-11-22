# Minimal showcase of [integer overflow](https://en.wikipedia.org/wiki/Integer_overflow) in C

## Code

<!-- AUTO-GENERATED-CONTENT:START (CODE:src=./main.c) -->
<!-- The below code snippet is automatically added from ./main.c -->
```c
#include <stdio.h>

int main() {
	for (char i = 0; i < 256; ++i)
		printf("i: %d\n", i);

	return 0;
}
```
<!-- AUTO-GENERATED-CONTENT:END -->

## Comments

In the actual test, [Clang](https://clang.llvm.org/) was able to detect the overflow issue, but [GCC](https://gcc.gnu.org/) was not.

```sh
main.c:4:21: warning: result of comparison of constant 256 with expression of type 'char' is always true [-Wtautological-constant-out-of-range-compare]
        for (char i = 0; i < 256; ++i)
                         ~ ^ ~~~
1 warning generated.
```
