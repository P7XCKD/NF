block exchange code
```alp
.model small

.data
arr db 01,02,03,04,05h
arr2 db 06,07,08,09,0Ah
arr3 db 05 dup(?)

.code
mov ax,@data
mov ds,ax

lea si,arr
mov es,ax
lea di,arr3
mov cx,05h

cld
rep movsb
mov cx,05h
lea si,arr2
lea di,arr

cld
rep movsb

lea si,arr3
lea di,arr2

cld
rep movsb 

lea si,arr
mov dh,05h
back:mov al,[si]

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
i4:add dl,30h
mov ah,02h
int 21h

dec ch
jnz i2
mov dl," "
mov ah,02h

int 21h
dec dh
jnz back

mov ah,4ch
int 21h
end
```
output : 06 07 08 09 0A
***
search index number using string (NOT)
```alp
.model small

.data
arr db 05,02,03,04,01h
search db 02h

.code
mov ax,@data
mov ds,ax

lea si,arr
mov al,[si]
inc si
mov bl,search

cmp al,bl
mov cl,05h
CLD

repne scasb
mov bl,dl
mov cl,02h
mov ch,04h

mov bh,bl
i2: rol bh,cl
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

mov ah,02h
int 21h

mov ah,4ch
int 21h
end

```