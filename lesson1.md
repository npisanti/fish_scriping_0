
# FISH WORKSHOP


---

# FISH 

FISH sta per "Friendly Interactive Shell".

- è un INTERPRETE dei comandi
- un intefaccia testuale invece che grafica
- serie di comandi sono facili da automatizzare

```
nomecomando
```
^^^ le parti evidenziate sono comandi da digitare 

---
## osx
installare Homebrew
https://brew.sh/

poi	dal Terminale 
```
brew install fish
```
		
## windows

installare MSYS2
https://www.msys2.org/

lanciare dal terminale "MSYS2 MinGW 64bit" 
```
pacman -S fish
```

## linux

ubuntu / debian:
```
sudo apt-get install fish
``` 

archlinux:
```
pacman -S fish
```

---

fish non è l'unica shell disponibile, ( quella di 
default è `bash` ) 

```console
fish
``` 

da digitare non appena aperto il terminale
per passare ad usare fish come shell

( ci sono varie maniere di rendere fish la shell di 
default a seconda del sistema operativo ) 

## vantaggi di fish:
- più coerente e semplice di bash
- molto più interattivo 

---

## LS

```           
ls 
```

- stampa come output una lista di file e cartelle della directory in cui vi trovate

- la directory corrente è mostrata nel PROMPT

- si possono aggiungere dei caratteri al comando per avere più informazioni 
		
```
ls -a
```
mostra anche file nascosti

```
ls -l
``` 
mostra più dettagli 

```
ls -l -a 
ls -la 
```
si possono anche combinare 

---

## CD
```
cd percorso/cartella/che/vuoi
```
^^^	è l'equivalente testuale di cliccare su una 
	cartella per entrarci dentro

```
cd ..
```
^^^ serve ad uscire dalla cartella ed entrare 
	nella cartella superiore 

---

## AUTOCOMPLETAMENTO

ogni shell dispone della capacità di provare a completare
i comandi che state scrivendo premendo il tasto TAB 

potete inoltre scorrere gli ultimi comandi che avete 
eseguito con i tasti freccia su/giù 	

per accedere ad una lista di tutti gli ultimi comandi 
eseguiti si può usare il comando `history` 

---

## MANPAGES

`man` è un comando che permette di aprire nel 
terminale il manuale per un comando specifico 

```
man ls 
```
^^^ apre il manuale di ls con la lista di tutte
	le opzioni aggiuntive

dare un occhiata con `man` dovrebbe essere la 
prima cosa quando non si sa che fare di un
comando, prima ancora di cercare su internet

---


## TOUCH

`touch` serve a creare un file vuoto con il nome dato
dat

```
touch test.txt
```
^^^ crea "test.txt" nella cartella corrente 
è un file di testo vuoto

NB:
> windows ha molti caratteri che non è possibile usare 
		come nomi di file: / ? < > \ : * | " ^ 
		e ogni carattere che viene digitato con CTRL

> nella shell il carattere `~` serve ad indicare la 
	cartella di "home" dell'utente corrente, di solito 
	`/home/nomeutente`

---
## MKDIR
`mkdir` crea una cartella col nome dato 
```
mkdir nuova
```
^^^ crea una cartella chiamata "nuova" 

```
mkdir -p nuova1/nuova2
```
^^^ con -p crea anche le cartelle precedenti se 
non esistono
	          
---
## MV
`mv` serve a spostare i file da una cartella 
all'altra o a rinominarli, per esempio:

```
mv file1.txt cartella/
```
^^^ muove "file1.txt" in "cartella"

```
mv cartella/file1.txt file2.txt
```
^^^ muove file1.txt da dentro cartella alla 
	cartella corrente e lo rinomina file2.txt

---

## CP

`cp` è come `mv`, ma copia i file invece di 
muoverli o rinominarli 

```
cp file1.txt file2.md
```
^^^ copia e cambia estensione

un file copiato su un altro file esistente lo 
sostituisce, senza possibilità di recupero del 
file sostituito 

---

## RM 
              
`rm` cancella irrimediabilmente uno o più file. 
non è possibile più recuperarli, in sistemi con 
cestino a volte ci sta un equivalente comando 
`trash` che sposta i file nel cestino 
```
rm file1.txt
```
^^^ addio file1.txt, ci mancherai 

esiste un comando `rmdir` per rimuovere cartelle, 
ma solo quando sono state già svuotate, mentre `rm -rf`
rimuove una cartella e tutto il suo contenuto (anche 
altre cartelle) 


## ESERCIZIO
>	usate `cd` ed `ls` per navigare all'interno 
	del vostro filesystem, create cartelle con `mkdir` 
	e file con `touch`


---
## MATH
`math` è un comando che fa da calcolatrice

```
math 2 + 2 
```
^^^ resituisce 4

```
math "6*7" 
```
^^^ * non viene eseguito se non messo tra
	virgolette, meglio usare sempre le virgolette
```
math "(4+23.3) * 12.77" 
```
^^^ si possono usare le parentesi per esprimere 
	la precedenza

---

## CLEAR

`clear` fa in modo di scorrere le righe del terminale 
cosi che sia totalmente vuoto 
```
clear 
```
## CAT

`cat` stampa nel terminale il contenuto del file 
(che sia un file di testo o meno, nel secondo caso il 
contenuto sarà illegibile)
```
cat nomefile.txt
```

---

## PROGRAMMI

- i comandi eseguiti da shell sono PROGRAMMI
- input = testo 
- output = testo o azioni compiute sul sistema

## PACKAGE MANAGER

- i programmi da usare in un terminale possono essere 
	installati facilmente con un "package manager"

- ci sono differenti package manager a seconda
	del vostro sistema operativo  

---
## osx 
```
brew install nomeprogramma
```

## window
```
pacmans -S nomeprogramma
```

## linux (debian/ubuntu*)
```
apt-get install nomeprogramma
```

*) linux ha diversi package manager a 
	seconda della distro usata

---

installiamo alcuni programmi utili per dopo:

## osx 
```
brew install imagemagick sox ffmpeg wget
```
## windows
```
pacmans -S mingw64/mingw-w64-x86_64-sox \
		mingw64/mingw-w64-x86_64-imagemagick \
		mingw64/mingw-w64-x86_64-ffmpeg \
		mingw-w64-x86_64-wget 
```
## linux (debian/ubuntu*)
```
apt-get install imagemagick sox ffmpeg wget
```
