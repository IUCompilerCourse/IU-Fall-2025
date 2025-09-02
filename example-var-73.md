
# Source Program

    (let ([x (let ([x (+ (- (read)) (read))])
                (+ x x))])
       (+ (+ x 42) (- x)))

# Uniquify Output

    (let ([x9 (let ([x8 (+ (- (read)) (read))])
                      (+ x8 x8))])
       (+ (+ x9 42) (- x9)))

# Remove Complex Operands Output

    (let ([x9 (let ([x8 (let ([tmp0 (read)])
                             (let ([tmp1 (- tmp0)])
                                  (let ([tmp2 (read)])
                                       (+ tmp1 tmp2))))])
                      (+ x8 x8))])
       (let ([tmp3 (+ x9 42)])
          (let ([tmp4 (- x9)])
             (+ tmp3 tmp4))))

# Explicate Control Output

    start:
        tmp0 = (read);
        tmp1 = (- tmp0);
        tmp2 = (read);
        x8 = (+ tmp1 tmp2);
        x9 = (+ x8 x8);
        tmp3 = (+ x9 42);
        tmp4 = (- x9);
        return (+ tmp3 tmp4);

# Select Instructions Output

    locals-types:
        x8 : 'Integer, tmp0 : 'Integer, x9 : 'Integer, tmp2 : 'Integer, tmp1 : 'Integer, tmp4 : 'Integer, tmp3 : 'Integer, 
    start:
        callq read_int
        movq %rax, tmp0
        movq tmp0, tmp1
        negq tmp1
        callq read_int
        movq %rax, tmp2
        movq tmp1, x8
        addq tmp2, x8
        movq x8, x9
        addq x8, x9
        movq x9, tmp3
        addq $42, tmp3
        movq x9, tmp4
        negq tmp4
        movq tmp3, %rax
        addq tmp4, %rax
        jmp conclusion

# Assign Homes Output

    stack-space:
    64
    start:
        callq read_int
        movq %rax, -16(%rbp)
        movq -16(%rbp), -40(%rbp)
        negq -40(%rbp)
        callq read_int
        movq %rax, -32(%rbp)
        movq -40(%rbp), -8(%rbp)
        addq -32(%rbp), -8(%rbp)
        movq -8(%rbp), -24(%rbp)
        addq -8(%rbp), -24(%rbp)
        movq -24(%rbp), -56(%rbp)
        addq $42, -56(%rbp)
        movq -24(%rbp), -48(%rbp)
        negq -48(%rbp)
        movq -56(%rbp), %rax
        addq -48(%rbp), %rax
        jmp conclusion
    

# Patch Instructions Output

    stack-space:
    64
    start:
        callq read_int
        movq %rax, -16(%rbp)
        movq -16(%rbp), %rax
        movq %rax, -40(%rbp)
        negq -40(%rbp)
        callq read_int
        movq %rax, -32(%rbp)
        movq -40(%rbp), %rax
        movq %rax, -8(%rbp)
        movq -32(%rbp), %rax
        addq %rax, -8(%rbp)
        movq -8(%rbp), %rax
        movq %rax, -24(%rbp)
        movq -8(%rbp), %rax
        addq %rax, -24(%rbp)
        movq -24(%rbp), %rax
        movq %rax, -56(%rbp)
        addq $42, -56(%rbp)
        movq -24(%rbp), %rax
        movq %rax, -48(%rbp)
        negq -48(%rbp)
        movq -56(%rbp), %rax
        addq -48(%rbp), %rax
        jmp conclusion
    
# Prelude and Conclusion

            .globl _main
            .align 8
    _main:
            pushq	%rbp
            movq	%rsp, %rbp
            subq	$64, %rsp
            jmp _start

            .align 8
    _start:
            callq	_read_int
            movq	%rax, -16(%rbp)
            movq	-16(%rbp), %rax
            movq	%rax, -40(%rbp)
            negq	-40(%rbp)
            callq	_read_int
            movq	%rax, -32(%rbp)
            movq	-40(%rbp), %rax
            movq	%rax, -8(%rbp)
            movq	-32(%rbp), %rax
            addq	%rax, -8(%rbp)
            movq	-8(%rbp), %rax
            movq	%rax, -24(%rbp)
            movq	-8(%rbp), %rax
            addq	%rax, -24(%rbp)
            movq	-24(%rbp), %rax
            movq	%rax, -56(%rbp)
            addq	$42, -56(%rbp)
            movq	-24(%rbp), %rax
            movq	%rax, -48(%rbp)
            negq	-48(%rbp)
            movq	-56(%rbp), %rax
            addq	-48(%rbp), %rax
            jmp _conclusion

            .align 8
    _conclusion:
            addq	$64, %rsp
            popq	%rbp
            retq


