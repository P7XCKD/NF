ALP
set higher nibble of any 8bit (or)

```alp
.model small

.data
a db 02h

.code
mov ax,@data
mov ds,ax

mov al,a
or al,0f0h

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
output f2
***
set higher nibble of any 16bit (or)

 
```alp
.model small

.data
a dw 1234h

.code
mov ax,@data
mov ds,ax

mov ax,a
or ax,0ff00h

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
output: FF34
***

mask lower nibble for 8bit (and)
```alp
.model small

.data
a db 12h

.code
mov ax,@data
mov ds,ax

mov al,a
and al,0f0h

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
output: 10
***
mask lower nibble for 16bit (and)
```alp
.model small

.data
a dw 1234h

.code
mov ax,@data
mov ds,ax

mov ax,a
and ax,0ff00h

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
output: 1200
***
perform following conversion using logical instructions
input number is 55h and output is 5Ah

```alp
.model small

.data
a db 55h

.code
mov ax,@data
mov ds,ax

mov al,a
xor al,0fh

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

output: 5Ah


basic array code
```alp
.model small

.data
arr db 05,05,04,05,5h

.code
mov ax,@data
mov ds,ax

lea si,arr
mov dh,05h

back:mov al,[si]
inc si

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

mov dl,' '
mov ah,02h
int 21h

dec dh
jnz back

mov ah,4ch
int 21h

end

```
ouput: 
05 05 03 04 05
***

