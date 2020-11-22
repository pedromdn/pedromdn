<a href="https://cooltext.com"><img src="https://images.cooltext.com/5466345.png" width="62" height="38" alt="Hola" /></a>
<br />Image by <a href="https://cooltext.com">Cool Text <a href="https://cooltext.com/Edit-Logo?LogoID=3636097667"></a>
## `Estudiante de ing. en Sistemas computacionales`



| <img src="https://devicons.github.io/devicon/devicon.git/icons/csharp/csharp-original.svg" alt="dotnet" width="40" height="40"/>  | <img src="https://devicons.github.io/devicon/devicon.git/icons/dot-net/dot-net-original-wordmark.svg" alt="dotnet" width="40" height="40"/>  | <img src="https://devicons.github.io/devicon/devicon.git/icons/html5/html5-original-wordmark.svg" alt="html5" width="40" height="40"/>  | <img src="https://devicons.github.io/devicon/devicon.git/icons/mysql/mysql-original-wordmark.svg" alt="mysql" width="40" height="40"/>  | <img src="https://devicons.github.io/devicon/devicon.git/icons/python/python-original.svg" alt="python" width="40" height="40"/>  |
|---|---|---|---|---|


![Texto alternativo](https://komarev.com/ghpvc/?username=pedromdn)
''' bash

@ greet.s - a little asm greeter.
@ programa corto que obtiene la entrada del teclado y luego lo imprime de nuevo en la pantalla.


.section	.bss
.comm buffer, 48	     @ reserve 48 byte buffer

.section	.data
msg:
	.ascii	"** Greeter **\nPlease enter your name: "
msgLen = . - msg
msg2:
	.ascii	"Hello "
msg2Len = . - msg2

.section	.text
.globl	_start
_start:

mov r0, $1		    @ print program's opening message	
ldr r1, =msg
ldr r2, =msgLen
mov r7, $4
svc $0

mov r7, $3		    @ read syscall
mov r0, $1		
ldr r1, =buffer
mov r2, $0x30
svc $0

mov r0, $1		    @ print msg2
ldr r1, =msg2
ldr r2, =msg2Len
mov r7, $4
svc $0

mov r0, $1		    @ now print the user input
ldr r1, =buffer
mov r2, $0x30
mov r7, $4
svc $0

mov r7, $1	            @ exit syscall
svc $0		            @ wake kernel
.end
'''
