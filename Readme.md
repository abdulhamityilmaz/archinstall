#Archlinux Installation (Virtualbox)

## Tastatur Layout
	'Loadkeys de-latin1 '
## erstes Bild
 ![Alt-text](bilder/git_repository.png)
### Überprüfen wie die Festplatte heißt

	lsblk
### Datenbank refresh
	pacman -Syy

### Mirrors aktualisieren (reflector)
	reflector -c Germany -a 6 --sort rate --save /etc/pacman.d/mirrorlist
### Datenbank refresh
	pacman -Syy
### Partitionierungstools starten
	cfdisk /dev/sda
 gpt Partitionstabelle erstellen 
 1. 300>> EFI >> EFI System
 2. 4GB>> SWAP >> Swapfile
 3. 30GB >> / >> LinuxFileSystem 
 4. Rest >> /home >> LinuxFileSystem
 5. Write >> Quit
### List Block
 	lslblk
### Partitionsformat
#### EFI Format
	mkfs.fat -F32 /dev/sda1
#### SWAP FOrmat 
	mkswap /dev/sda2
#### SWAP aktivieren
	swapon /dev/sda2
#### Root Format ext4
	mkfs.ext4 /dev/sda3
#### /home Format ext4 
	mkfs.ext4 /dev/sda4
