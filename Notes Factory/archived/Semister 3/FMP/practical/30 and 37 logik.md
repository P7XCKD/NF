8bit version
```alp
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
16bit version
```
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