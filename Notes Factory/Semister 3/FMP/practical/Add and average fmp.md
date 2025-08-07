sum and average of an array
``` alp
.model small

.data
arr db 05,03,05,02,05h

.code
mov ax,@data
mov ds,ax

lea si,arr
mov dh,05h
mov al,00h

back:add al,[si]
inc si
dec dh
jnz back

mov ch,02h
mov bl,al

i2:rol bl,cl
mov dl,bl
and dl,0fh

cmp dl,09h
jbe i4
add dl,07

i4:add dl,30h
mov ah,02h
int 21h
dec ch
jnz i2

mov dl,' '
mov ah,02h
int 21h

mov bl,05h
div bl

mov ch,02h
mov cl,04h

mov bl,al
i3:rol bl,cl
mov dl,bl

and dl,0fh
cmp dl,09h
jbe i5

add dl,07
i5:add dl,3ch

mov ah,02h
int 21h

dec ch
jnz i3

mov ah,4ch
int 21h
end
```

min and max number of an array
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
output: A5 B0