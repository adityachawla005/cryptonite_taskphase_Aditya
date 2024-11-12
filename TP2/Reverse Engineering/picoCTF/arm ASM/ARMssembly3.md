# ARmssembly 3

**Flag:** `picoCTF{00000024} `

Approach

- step 1<br>
It starts by initializing the integer in w0 and then enters a loop.
Checks if the LSB of the integer is 1 using the and instruction.
If the LSB is 1, it calls func2 to add 3 to a result stored in w0.
The integer is then right-shifted (lsr) by 1 bit.
The loop continues until the integer becomes zero.
Finally, the result is printed, showing how many times the LSB was 1 and the corresponding increments.


```
	.arch armv8-a
	.file	"chall_3.c"
	.text
	.align	2
	.global	func1
	.type	func1, %function
func1:
	stp	x29, x30, [sp, -48]!
	add	x29, sp, 0
	str	w0, [x29, 28]
	str	wzr, [x29, 44]
	b	.L2
.L4:
	ldr	w0, [x29, 28]
	and	w0, w0, 1
	cmp	w0, 0
	beq	.L3
	ldr	w0, [x29, 44]
	bl	func2
	str	w0, [x29, 44]
.L3:
	ldr	w0, [x29, 28]
	lsr	w0, w0, 1
	str	w0, [x29, 28]
.L2:
	ldr	w0, [x29, 28]
	cmp	w0, 0
	bne	.L4
	ldr	w0, [x29, 44]
	ldp	x29, x30, [sp], 48
	ret
	.size	func1, .-func1
	.align	2
	.global	func2
	.type	func2, %function
func2:
	sub	sp, sp, #16
	str	w0, [sp, 12]
	ldr	w0, [sp, 12]
	add	w0, w0, 3
	add	sp, sp, 16
	ret
	.size	func2, .-func2
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
	str	w0, [x29, 28]
	str	x1, [x29, 16]
	ldr	x0, [x29, 16]
	add	x0, x0, 8
	ldr	x0, [x0]
	bl	atoi
	bl	func1
	str	w0, [x29, 44]
	adrp	x0, .LC0
	add	x0, x0, :lo12:.LC0
	ldr	w1, [x29, 44]
	bl	printf
	nop
	ldp	x29, x30, [sp], 48
	ret
	.size	main, .-main
	.ident	"GCC: (Ubuntu/Linaro 7.5.0-3ubuntu1~18.04) 7.5.0"
	.section	.note.GNU-stack,"",@progbits	
```

- step 2<br>
Then 36 is converted to its hex representation without 0x and in lowercase and 0s are added to make the string 32 bit.


What you learned through solving this challenge:
<br>
- Learned the concept of MSB and LSB in Assembly and bit shifting LSB.


Other incorrect methods you tried:
<br>
- none


References
<br>
-[ARM Assembly Tutorial](https://www.youtube.com/watch?v=gfmRrPjnEw4&t=2597s)

