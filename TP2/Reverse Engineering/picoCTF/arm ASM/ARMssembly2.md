# ARmssembly 2

**Flag:** `picoCTF{ed2c0662} `

Approach

- step 1<br>
We are given the  arguement 4189673334 which is stored in [sp+12].
We intialize two counters in [sp+24] and [sp+28]
Now the loop starts at L2 Label and continues as logne the increment-1 counter is less than than w0.
Inside the loop  [sp+24] and [sp+28] are incremented by 3 and 1 respectively.
When the loop ends the [sp+24} returns its value which is 3 times the arguement i.e.(4189673334*3=12569020002)

```
	.arch armv8-a
	.file	"chall_2.c"
	.text
	.align	2
	.global	func1
	.type	func1, %function
func1:
	sub	sp, sp, #32
	str	w0, [sp, 12]
	str	wzr, [sp, 24]
	str	wzr, [sp, 28]
	b	.L2
.L3:
	ldr	w0, [sp, 24]
	add	w0, w0, 3
	str	w0, [sp, 24]
	ldr	w0, [sp, 28]
	add	w0, w0, 1
	str	w0, [sp, 28]
.L2:
	ldr	w1, [sp, 28]
	ldr	w0, [sp, 12]
	cmp	w1, w0
	bcc	.L3
	ldr	w0, [sp, 24]
	add	sp, sp, 32
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
Then 12569020002 is converted to its hex representation without 0x and in lowercase and last 8 characters of the string are taken.


What you learned through solving this challenge:
<br>
- Learned the concept of counters and loops within labels.


Other incorrect methods you tried:
<br>
- none


References
<br>
-[ARM Assembly Tutorial](https://www.youtube.com/watch?v=gfmRrPjnEw4&t=2597s)

