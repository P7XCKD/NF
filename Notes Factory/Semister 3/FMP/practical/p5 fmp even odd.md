even odd program
```asm
.model small

.data
a db 09h
b db 01h

.code
mov ax,@data
mov ds,ax

mov al,a
mov bl,b
and al,bl

mov bh,al
mov ch,02h
mov cl,04h

i2:rol bh,cl
mov dl,bh

and dl,0fh
cmp dl,09

jbe i4
add dl,07
i4:add dl,30H

mov ah,02h
int 21H
dec ch
jnz i2

mov ah,4ch
int 21H
end

```
output: 01h