  # p2 18/07/2024

addition program for first 5 digits 

multiplication code of 2 8bit numbers (h3)
```
.model small
.data

a db 04h
b db 02h

.code
mov ax,@data
mov ds,ax

mov al,a
mov bl,b
mul bl
mov ah,02h

mov ch,02h
mov cl,04h

mov bh,al
i2:rol bh,cl
mov dl,bh

and dl,0fh
cmp dl,09
jbe i4
add dl,07

i4:add dl,30h
mov ah,02h

int 21h
dec ch
jnz I2

mov ah,4ch
int 21h

end

```
16 bit multiplication
```
.model small

.data
a dw 1000h
b dw 1234h

.code
mov ax,@data
mov ds,ax

mov ax,a
mov bx,b
mul bx

mov ch,04h
mov cl,04h
mov bx,ax

i2:rol bx,cl
mov dx,bx
and dl,0fh
cmp dl,09

jbe i4
add dl,07
i4:add dl,30h
mov ah,02h

int 21h
dec ch
jnz i2
mov ah,4ch
int 21h

end
```
> [!warning] commands
> when using division or average , always clear the register ax after data segment or output will always be incorrect

 
 division code 

```
.model small

.data
a dw 08h
b dw 04h

.code
mov ax,@data
mov ds,ax

mov ax,a
mov bx,b
div bl

mov ch,04h
mov cl,04h
mov bx,ax

i2:rol bx,cl
mov dx,bx
and dl,0fh
cmp dl,09

jbe i4
add dl,07
i4:add dl,30h
mov ah,02h

int 21h
dec ch
jnz i2
mov ah,4ch
int 21h

end
```












