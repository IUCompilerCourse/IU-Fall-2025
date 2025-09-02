# source program: eg73

    x = (-(input_int()) + input_int())
    y = (x + x)
    print(((x + 42) - x))

# remove_complex_operands

    tmp.0 = input_int()
    tmp.1 = -(tmp.0)
    tmp.2 = input_int()
    x = (tmp.1 + tmp.2)
    y = (x + x)
    tmp.3 = (x + 42)
    tmp.4 = (tmp.3 - x)
    print(tmp.4)

# select_instructions

            .globl _main
    _main:
        callq _read_int
        movq %rax, tmp.0
        movq tmp.0, tmp.1
        negq tmp.1
        callq _read_int
        movq %rax, tmp.2
        movq tmp.1, x
        addq tmp.2, x
        movq x, y
        addq x, y
        movq x, tmp.3
        addq $42, tmp.3
        movq tmp.3, tmp.4
        subq x, tmp.4
        movq tmp.4, %rdi
        callq _print_int

# assign_homes

            .globl _main
    _main:
        callq _read_int
        movq %rax, -32(%rbp)
        movq -32(%rbp), -56(%rbp)
        negq -56(%rbp)
        callq _read_int
        movq %rax, -48(%rbp)
        movq -56(%rbp), -24(%rbp)
        addq -48(%rbp), -24(%rbp)
        movq -24(%rbp), -8(%rbp)
        addq -24(%rbp), -8(%rbp)
        movq -24(%rbp), -16(%rbp)
        addq $42, -16(%rbp)
        movq -16(%rbp), -40(%rbp)
        subq -24(%rbp), -40(%rbp)
        movq -40(%rbp), %rdi
        callq _print_int

# patch_instructions

            .globl _main
    _main:
        callq _read_int
        movq %rax, -32(%rbp)
        movq -32(%rbp), %rax
        movq %rax, -56(%rbp)
        negq -56(%rbp)
        callq _read_int
        movq %rax, -48(%rbp)
        movq -56(%rbp), %rax
        movq %rax, -24(%rbp)
        movq -48(%rbp), %rax
        addq %rax, -24(%rbp)
        movq -24(%rbp), %rax
        movq %rax, -8(%rbp)
        movq -24(%rbp), %rax
        addq %rax, -8(%rbp)
        movq -24(%rbp), %rax
        movq %rax, -16(%rbp)
        addq $42, -16(%rbp)
        movq -16(%rbp), %rax
        movq %rax, -40(%rbp)
        movq -24(%rbp), %rax
        subq %rax, -40(%rbp)
        movq -40(%rbp), %rdi
        callq _print_int

# prelude_and_conclusion

            .globl _main
    _main:
        pushq %rbp
        movq %rsp, %rbp
        subq $64, %rsp
        callq _read_int
        movq %rax, -32(%rbp)
        movq -32(%rbp), %rax
        movq %rax, -56(%rbp)
        negq -56(%rbp)
        callq _read_int
        movq %rax, -48(%rbp)
        movq -56(%rbp), %rax
        movq %rax, -24(%rbp)
        movq -48(%rbp), %rax
        addq %rax, -24(%rbp)
        movq -24(%rbp), %rax
        movq %rax, -8(%rbp)
        movq -24(%rbp), %rax
        addq %rax, -8(%rbp)
        movq -24(%rbp), %rax
        movq %rax, -16(%rbp)
        addq $42, -16(%rbp)
        movq -16(%rbp), %rax
        movq %rax, -40(%rbp)
        movq -24(%rbp), %rax
        subq %rax, -40(%rbp)
        movq -40(%rbp), %rdi
        callq _print_int
        addq $64, %rsp
        popq %rbp
        retq 

