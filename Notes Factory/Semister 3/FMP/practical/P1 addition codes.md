11/07/24 FMP practical
8 bit addition fmp code
```
.model small

.data
a db 02h
b db 02h

.code 
mov ax,@data
mov ds,ax

mov al,a
mov bl,b
add al,bl
mov dl,al

add dl,30h
mov ah,02h
int 21h
mov ah,4ch
int 21h

end
```

output = 4

perform 8 bit addition for 13h and 02h 
```
.model small

.data
a db 13h
b db 02h

.code
mov ax,@data
mov ds,ax

mov al,a
mov bl,b
add al,bl

mov ch,02h
mov cl,04h
mov bh,al

I2:rol bh,cl
mov dl,bh
and dl,0fh
cmp dl,09
jbe I4

add dl,07
I4:add dl,30h

mov ah,02h
int 21h
dec ch
jnz I2

mov ah,4ch
int 21h

end
```
output:
15

16 bit addition of 0001 and 0002
```
.model small
.data

a dw 0001h
b dw 0002h

.code
mov ax,@data
mov ds,ax

mov ax,a
mov bx,b
add ax,bx ;change this to sub 4 2bit sub

mov ch,04h
mov cl,04h
mov bx,ax
i2:rol bx,cl

mov dx,bx
and dl,0fh

cmp dl,09
jbe i4
add dl,07

i4: add dl,30h
mov ah,02h
int 21h
dec ch

jnz i2

mov ah,4ch
int 21h

end
```
output: 3


for sub of two 8 bit number follow the above code jusf change add to sub
> [!hint] Commands for Tasm
> edit to open editor
>tasm (filename).asm to check for errors
>tlink (filename).obj for execution
> td (filename) for step by step execution
> press f8 to go next , in end it will terminate by itself just press ok




