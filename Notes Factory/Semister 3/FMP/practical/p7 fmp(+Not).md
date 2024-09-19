even odd seperator code (need a bit more fixing for below)

```alp
.model small
.data
arr db 03,04,06,02,01h
ev db 03 dup(?)
od db 02 dup(?)
.code
mov ax,@data
mov ds,ax

lea si,arr
lea di,od

mov dh,05h
back: mov al,[si]
mov bh,al
and bh,01h
jnz odd
jmp FR
odd: mov [di],al
inc di
FR:inc si
dec dh
jnz back

lea si,arr
lea di,ev
mov dh,05h
back1: mov al,[si]
mov bh,al
and bh,01h
jz ev1
jmp FR2
ev1: mov [di],al
inc di
FR2:inc si
dec dh
jnz back1


lea si,od
mov dh,05h
back3: mov al,[si]
inc si
mov ch,02h
mov cl,04h

mov bh,al
i2:rol bh,cl
mov dl,bh
and dl,0fh
cmp dl,09
jbe i4
add dl,07h

i4: add dl,30h
mov ah,02h
int 21h
dec ch
jnz i2

dec dh
jnz back3
mov ah,4ch
int 21h
end

```


alp to perform search index using string
```alp
.model small
.data
a db 03,01,05,02,04h
b db 05h

.code
mov ax,@data
mov ds,ax

lea di,a
mov al,b
mov ch,05h
mov dh,00h

cld
inc dh
repne scasb

mov bh,dh 

mov cl,04h
mov ch,02h

i2:rol bh,cl
mov dl,bh
and dl,0fh
cmp dl,09h
jbe i4
add dl,07h

i4:add dl,30h
mov ah,02h
int 21h
dec ch
jnz i2

mov ah,4ch
int 21h

end 

```


idk name of this code
```alp
.model small
.data
a db 01,02,03,04,05h
b db 06,07,08,09,0Ah
c db 05 dup(?)
.code
mov ax,@data
mov ds,ax
lea si,a
mov es,ax
lea di,c

mov cx,05h
cld
rep movsb

mov cx,05h
lea si,b
lea di,a
cld
rep movsb

mov cx,05h
lea si,c
lea di,b
cld
rep movsb

lea di,a
mov bl,05h
back:mov al,[di]
inc di
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

jnz i2
mov dl, ' '
mov ah,02h
int 21h

dec bl
jnz back

mov ah,4ch
int 21h
end






```


nakul this pdf was a literal skem to waste your time what you want is not here

by your's truly probz