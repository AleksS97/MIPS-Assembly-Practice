#all comments relate to either the text directly to the left or to the line/function/stanza at the bottom of said comments

.data
	prompt1: .asciiz "Please enter a number: "
	output: .asciiz "The sum of all numbers between that number and 0, inclusive, is "
.text
	#prompt user to enter an integer
	li $v0, 4
	la $a0, prompt1
	syscall
	#user inputs an integer
	li $v0, 5
	syscall
	move $s0, $v0
	
	add $t0, $0, $0 #running sum, initialized to 0
	add $t1, $s0, $0 #initialize the operand of the while loop to the input number, located at s0
	
	#until the counter which was initialized  to the value of the second input operant reaches 0,
	#keep looping around. When it reaches that condition, we will descent to the "done:" function.
	loop:
		beq $t1, $0, done
		#set the register with the running sum as its own value and the value of the decrement
		add $t0, $t0, $t1
		#decrement the counter
		subiu $t1, $t1, 1
		j loop
	
	#when the loop function terminates, we will call this function
	#display the output which is the summation result
	li $v0, 1
	
	done:
		#print the output string
		li $v0, 4
		la $a0, output
		syscall
		#move to a0 and print the contents of the register containing the value of repeated summation (t0)
		li $v0, 1
		move $a0, $t0
		syscall
	
	#exit the function by calling syscall 10
	exit:
		li $v0, 10
		syscall
