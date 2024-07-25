# fmp 25/07/2024
1c of a 8bit number
```alp
.model small

.data
a db 02h
b db 01h

.code
mov ax,@data
mov ds,ax

mov al,a
not al

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
output: fd

2c of a 8bit number
```alp
.model small

.data
a db 02h
b db 01h

.code
mov ax,@data
mov ds,ax

mov al,a
mov bl,b
not al ; you can also use neg al
add al,bl ;if you follow above

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
output: fe

1c of 16bit number
```alp
.model small

.data
a dw 0002h
b dw 0001h

.code
mov ax,@data
mov ds,ax

mov ax,a
not ax

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
output: fffd
2c of 16 bit number
```alp
.model small

.data
a dw 0002h
b dw 0001h

.code
mov ax,@data
mov ds,ax

mov ax,a
not ax ;you can also use neg ax
add ax,bx ;if you follow above then dont write this line

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
output: fffe

wap to count and display no. of 1 in 8bit
```alp
.model small

.data
a db 0Fh
b db 00h

.code
mov ax,@data
mov ds,ax

mov al,a
mov bl,b

mov cl,08h
i4: rcr al,01h
dec c1

jnc i2
inc bl
i2: jnz i4


mov ch,02h
mov cl,04h
mov bh,bl

I3:rol bh,cl
mov dl,bh
and dl,0fh
cmp dl,09
jbe I5

add dl,07
I5:add dl,30h

mov ah,02h
int 21h
dec ch
jnz I3

mov ah,4ch
int 21h

end
```
output:
04

wap to count and display no. of 1 in 16bit
wap to count and display no. of 0 in 8bit
wap to count and display no. of 0 in 16bit