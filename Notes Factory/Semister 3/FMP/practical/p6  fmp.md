
sorting assending
```alp
.model small

.data
arr db 05,02,03,04,01H

.code
mov ax,@data
mov ds,ax

mov ax,0000h
mov dl,04h

i1:mov dh,04h
lea si,arr

back:mov al,[si]
mov bl,[si+1]
cmp al,bl

jbe i3
xchg al,bl

i3:mov[si],al
mov[si+1],bl

inc si
dec dh
jnz back

dec dl
jnz i1

mov dh,05H
lea si,arr
print:mov al,[si]

inc si
mov dl,al

mov ch,02h
mov cl,04H

mov bh,al
i2:rol bh,cl
mov dl,bh

and dl,0fH
cmp dl,09H

jbe i4
add dl,07h
i4:add dl,30h

mov ah,02h
int 21h
dec ch

jnz i2

mov dl,' '
mov ah,02h
int 21h

dec dh

jnz print

mov ah,4ch
int 21h

end
```

sorting descending 
> [!info] CHECK THE BELOW CODE  ;  COMMENTS PART TO  SWITCH TO DESCEINDING
```
.model small

.data
arr db 05,02,03,04,01H

.code
mov ax,@data
mov ds,ax

mov ax,0000h
mov dl,04h

i1:mov dh,04h
lea si,arr

back:mov al,[si]
mov bl,[si+1]
cmp al,bl

jae i3   ; CHECK THIS LINE 
xchg al,bl

i3:mov[si],al
mov[si+1],bl

inc si
dec dh
jnz back

dec dl
jnz i1

mov dh,05H
lea si,arr
print:mov al,[si]

inc si
mov dl,al

mov ch,02h
mov cl,04H

mov bh,al
i2:rol bh,cl
mov dl,bh

and dl,0fH
cmp dl,09H

jbe i4
add dl,07h
i4:add dl,30h

mov ah,02h
int 21h
dec ch

jnz i2

mov dl,' '
mov ah,02h
int 21h

dec dh

jnz print

mov ah,4ch
int 21h

end
```

normal search 
```alp
.model small

.data
arr db 03,04,02,01,06h
b db 01h

.code
mov ax,@data
mov ds,ax
lea si,arr

mov al,b

mov ch,00h
mov dh,05h
back: mov bl,[si]
cmp al,bl
je I1
inc si
inc ch
dec dh
jmp back



I1: mov bl,ch

mov ch,02h
mov cl,04h
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

mov ah,4ch
int 21h
end

```

index version 
```
.model small

.data
arr db 03, 04, 02, 01, 06h
b db 01h

.code
mov ax, @data
mov ds, ax
lea si, arr

mov al, b

mov ch, 00h
mov dh, 05h

back: mov bl, [si]
cmp al, bl

je I1
inc si
inc ch
dec dh

jmp back

I1:mov bl, ch

mov ch, 02h
mov cl, 04h
mov bh, b1

i2:rol bh, cl
mov dl, bh
and dl, 0fh
cmp dl, 09h

jbe i4
add dl, 07h
i4:add dl, 30h

mov ah, 02h
int 21h
dec ch
jnz i2

mov ah, 4ch
int 21h
end
```
