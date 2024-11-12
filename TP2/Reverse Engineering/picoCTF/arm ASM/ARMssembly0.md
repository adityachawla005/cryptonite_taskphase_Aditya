# ARmssembly 0		

**Flag:** `picoCTF{6d1d2dd1} `

Approach

- step 1<br>
We are given the following ARM assembly code.
The function takes two integer arguments (in registers w0 and w1).
It compares these two arguments and sets w0 to the smaller value. This is done by storing and comparing them, and loading the smaller of the two back into w0.
The stack is adjusted accordingly.So the bigger arguement will be loaded 1830628817.

```
.arch armv8-a
	.file	"chall.c"
	.text
	.align	2
	.global	func1
	.type	func1, %function
func1:
	sub	sp, sp, #16
	str	w0, [sp, 12]
	str	w1, [sp, 8]
	ldr	w1, [sp, 12]
	ldr	w0, [sp, 8]
	cmp	w1, w0
	bls	.L2
	ldr	w0, [sp, 12]
	b	.L3
.L2:
	ldr	w0, [sp, 8]
.L3:
	add	sp, sp, 16
	ret
	.size	func1, .-func1
	.section	.rodata
	.align	3
.LC0:
	.string	"Result: %ld\n"
	.text
	.align	2
	.global	main
	.type	main, %function
main:
	stp	x29, x30, [sp, -48]!
	add	x29, sp, 0
	str	x19, [sp, 16]
	str	w0, [x29, 44]
	str	x1, [x29, 32]
	ldr	x0, [x29, 32]
	add	x0, x0, 8
	ldr	x0, [x0]
	bl	atoi
	mov	w19, w0
	ldr	x0, [x29, 32]
	add	x0, x0, 16
	ldr	x0, [x0]
	bl	atoi
	mov	w1, w0
	mov	w0, w19
	bl	func1
	mov	w1, w0
	adrp	x0, .LC0
	add	x0, x0, :lo12:.LC0
	bl	printf
	mov	w0, 0
	ldr	x19, [sp, 16]
	ldp	x29, x30, [sp], 48
	ret
	.size	main, .-main
	.ident	"GCC: (Ubuntu/Linaro 7.5.0-3ubuntu1~18.04) 7.5.0"
	.section	.note.GNU-stack,"",@progbits
```

- step 2<br>
Then 1830628817 is converted to its hex representation without 0x prefixand in lowercase.


What you learned through solving this challenge:
<br>
- We learn about labels,functions,stack operations,branching to functions and calling conventions etc.


Other incorrect methods you tried:
<br>
- none


References
<br>
-[ARM Assembly Tutorial](https://www.youtube.com/watch?v=gfmRrPjnEw4&t=2597s)

