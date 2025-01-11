ORG 100h

MENU:
    MOV DX, OFFSET MENU_TEXT
    MOV AH, 09h
    INT 21h

    MOV DX, OFFSET NAME_PROMPT
    MOV AH, 09h
    INT 21h

    MOV AH, 0Ah
    MOV DX, OFFSET NAME_BUFFER
    INT 21h

    MOV DX, OFFSET DEST_PROMPT
    MOV AH, 09h
    INT 21h

    MOV AH, 0Ah
    MOV DX, OFFSET DEST_BUFFER
    INT 21h

    MOV DX, OFFSET TICKETS_PROMPT
    MOV AH, 09h
    INT 21h

    MOV AH, 01h
    INT 21h
    SUB AL, '0'
    MOV NUM_TICKETS, AL

    MOV DX, OFFSET SUMMARY_TEXT
    MOV AH, 09h
    INT 21h

    MOV DX, OFFSET NAME_BUFFER+2
    MOV AH, 09h
    INT 21h

    MOV DX, OFFSET DEST_TEXT
    MOV AH, 09h
    INT 21h

    MOV DX, OFFSET DEST_BUFFER+2
    MOV AH, 09h
    INT 21h

    MOV DX, OFFSET TICKET_COUNT_TEXT
    MOV AH, 09h
    INT 21h

    MOV AL, NUM_TICKETS
    ADD AL, '0'
    MOV DL, AL
    MOV AH, 02h
    INT 21h

    MOV AH, 4Ch
    INT 21h

MENU_TEXT DB 'Program Tiket Bus$'
NAME_PROMPT DB 0Dh, 0Ah, 'Masukkan Nama Penumpang: $'
NAME_BUFFER DB 21, 0, 21 DUP('$')
DEST_PROMPT DB 0Dh, 0Ah, 'Masukkan Tujuan: $'
DEST_BUFFER DB 21, 0, 21 DUP('$')
TICKETS_PROMPT DB 0Dh, 0Ah, 'Masukkan Jumlah Tiket: $'
SUMMARY_TEXT DB 0Dh, 0Ah, 'Ringkasan Pemesanan:', 0Dh, 0Ah, 'Nama: $'
DEST_TEXT DB 0Dh, 0Ah, 'Tujuan: $'
TICKET_COUNT_TEXT DB 0Dh, 0Ah, 'Jumlah Tiket: $'
NUM_TICKETS DB 0
