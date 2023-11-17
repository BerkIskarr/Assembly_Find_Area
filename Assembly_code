extern printf         ; External reference to the printf function

section .data
    pi          dq 3.1415    ; Definition of the pi constant
    sentence    db "Area is %f", 0 ; String format for the sentence

section .bss
    area    resq 1    ; Reserved space to store the calculated area

section .text
global main

main:
    push rbp
    mov rbp, rsp

    ; Calculate the area
    movsd xmm0, $s0          ; Load the value of $s0 (assuming it represents the R)
    mulsd xmm0, xmm0         ; Square the radius
    mulsd xmm0, qword ptr[pi]         ; Multiply by pi
    movsd xmm1, $s1          ; Load the value of $s1 (assuming it represents the b)
    movsd xmm2, qword ptr[2.0]  ; Load the value 2.0 into xmm2
    mulsd xmm0, xmm2         ; Multiply by 2.0
    divsd xmm0, xmm1         ; Divide by the value in $s1
    movsd qword ptr[area], xmm0       ; Store the calculated area in memory, 

; The size of the operand is specified in the MOVSD instruction. The XMM registers are 128-bit wide and need to use 'qword ptr' to specify the size of the operand as 64 bits. Without the ptr specifier, the assembler might assume a different default size based on the register being used or the surrounding code, potentially resulting in incorrect memory access or unexpected behavior.

; The reason I pass to xmm register is that in x86-64 assembly, floating-point values are typically passed in the XMM registers, not the general-purpose registers (such as rax, rsi, rdi, and rdx) used for integer values.

    mov rdi, sentence        ; Set the first argument (format string) for printf
    mov rsi, qword ptr[area]          ; Set the second argument (area value) for printf
    mov rax, 0              ; Clear the value in rax (to prepare for the call)
    call printf             ; Call the printf function to print the formatted string

    mov rsp, rbp
    pop rbp

    mov rax, 60             ; System call number for exit
    mov rdi, 0              ; Exit with return code 0
    syscall                 ; Perform the exit system call
