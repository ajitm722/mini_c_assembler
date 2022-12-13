# mini_c_assembler Interpreter

## Build

1. clone the repository
2. call `make` in the main directory of the repo on Linux (compilation using gcc), 

```sh
make
```


## Usage

executable file is in *build* directory;
Executing from console is expected on Linux using 
```sh
./build/mini_c_assembler mini_c_samples/1.mini 
```

### Input

Input of the program is a name of the file that is to be interpreted. The file is expected to contain a program written in the mini_c language, 

## Example


```
/* My first mini program */

int pow2(n)
{
    int a = 2;
    int i = 1;
    while (i < n)
    {
        a = a * 2;
        i = i + 1;
    }
    return a;
}

int main()
{
    return pow2(10);
}
```

### Output

```
-------------------------
Success
-------------------------
Assembler----------------

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
38: function main
start:
      op_stk_adj  0
      op_int      10
      op_call     1, pow2
      op_return
end:

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
2: function pow2
      local       a, @1
      local       i, @2
      local       n, @0
start:
      op_stk_adj  3
      op_int      2
      op_store    a
      op_int      1
      op_store    i
12:
      op_load     i
      op_load     n
      op_lt
      op_jump_if  35
      op_load     a
      op_int      2
      op_mul
      op_store    a
      op_load     i
      op_int      1
      op_add
      op_store    i
      op_jump     12
35:
      op_load     a
      op_return
end:

-------------------------
Result: 1024
-------------------------
```
