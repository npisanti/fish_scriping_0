
---

# SETUP

---

## osx
aprire il terminale e incollare il codice da:
https://brew.sh/

per installare homebrew, poi digitare: 
```
brew install fish imagemagick sox ffmpeg wget
```
per istallare i programmi necessari al corso 

---

## windows

installare MSYS2
https://www.msys2.org/

lanciare dal terminale "MSYS2 MinGW 64bit" 

poi digitare:
```
pacman -Syu
```
e poi
```
pacman -S fish mingw64/mingw-w64-x86_64-sox \
		mingw64/mingw-w64-x86_64-imagemagick \
		mingw64/mingw-w64-x86_64-ffmpeg \
		mingw-w64-x86_64-wget 
```

---

## linux

ubuntu / debian:
```
sudo apt-get install fish imagemagick sox ffmpeg wget
``` 

archlinux:
```
pacman -S fish
```

---

## EDITOR DI TESTO

Per la corso sarà è necessario anche usare un 
editor di "plain text" cioè di testo non 
formattato, come ad esempio il blocco note di 
windows o textedit di osx.

Esistono molti editor di testo specifici per 
scrivere codice, che hanno tra le funzioni utili 
l'evidenziamento della sintassi. 

---

## VARI EDITOR 

Alcuni editor possono essere avviati nel terminale:

- `micro` è molto intuitivo da utilizzare 
( per installarlo su osx potete usare 
`brew install micro` )

- `nano` è spesso già disponibile in vari terminali

- `vim` e `emacs` sono molto più avanzati 

Al di fuori del terminale buone scelte possono 
essere:

- `visual studio code` 
- `sublime text` 
