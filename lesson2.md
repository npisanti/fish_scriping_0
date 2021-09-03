
---

# FISH SCRIPTING ZERO

---

## FISH 

FISH sta per "Friendly Interactive Shell".

- è un INTERPRETE dei comandi
- un intefaccia testuale invece che grafica
- serie di comandi sono facili da automatizzare

```
nomecomando
```
^^^ le parti evidenziate sono comandi da digitare 

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

tutti i comandi mostrati in questa e la prossima 
lezione possono essere usati in una shell qualunque

---

## LS

```           
ls 
```

- stampa come output una lista di file e cartelle 
della directory in cui vi trovate

- la directory corrente è mostrata nel PROMPT

- si possono aggiungere dei caratteri al comando 
per avere più informazioni 
		
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

ogni shell dispone della capacità di provare a 
completare i comandi che state scrivendo premendo 
il tasto TAB 

potete inoltre scorrere gli ultimi comandi che 
avete eseguito con i tasti freccia su/giù 	

per accedere ad una lista di tutti gli ultimi 
comandi eseguiti si può usare il comando `history` 

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

`touch` serve a creare un file vuoto

```
touch test.txt
```
^^^ crea "test.txt" nella cartella corrente 
è un file di testo vuoto

NB:
> windows ha molti caratteri che non è possibile 
usare come nomi di file: / ? < > \ : * | " ^ 
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
```
cp -ar cartella nuovacartella
```
^^^ con `-ar` copia intere cartelle ed il 
loro contenuto

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
ma solo quando sono state già svuotate, mentre 
`rm -rf` rimuove una cartella e tutto il suo
contenuto (anche altre cartelle) 


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

`clear` fa in modo di scorrere le righe del 
terminale cosi che sia totalmente vuoto 
```
clear 
```
## CAT

`cat` stampa nel terminale il contenuto del file 
(che sia un file di testo o meno, nel secondo caso 
il contenuto sarà illegibile)
```
cat nomefile.txt
```

---

## PROGRAMMI

- i comandi eseguiti da shell sono PROGRAMMI
- input = testo 
- output = testo o azioni compiute sul sistema

## PACKAGE MANAGER

- i programmi da usare in un terminale possono 
essere 	installati facilmente con un 
"package manager"

- ci sono differenti package manager a seconda
del vostro sistema operativo  

---

## RICAPITOLANDO

- `ls` : mostra file e cartelle 
- `cd` : cambia directory 
- `man` : manuale di un comando
- `touch` : crea un file vuoto
- `mkdir` : crea una cartella
- `mv` : muove cartelle e file
- `cp` : copia cartelle e file 
- `rm` : rimuove file e cartelle
- `math` : esegue calcoli matematici
- `cat` : emette in output il testo di un file
- `clear` : "pulisce" il terminale 

---

## IMAGEMAGICK
					
"imagemagick" è un programma che serve a convertire 
immagini ed a applicare trasformazioni grafiche
```
convert image.png image.jpg
```
^^^ converte image.png in un nuovo file JPEG 

```
mogrify image.jpg -resize 600x500
```
^^^ cambia le dimensioni di image.jpg in modo che 
entrino in un rettangolo di 600x500 pixel, 
mantenendo l'aspetto 

mogrify usa le stesse opzioni di convert, ma invece 
di salvare il risultato in un nuovo file applica le 
trasformazioni sul file originale 

---

## ASTERISCO

l'asterisco `*` serve come "wildcard" per indicare 
tutti i file presenti che possono soddisfare la 
stringa nel quale è usato
```
mogrify -resize 500x500 *.png
```
^^^ ridimensiona solo i file che finiscono in .png
i file JPEG non verranno ridimensionati e nemmeno
i file che finiscono con .PNG 

l'asterisco è molto importante per permetterci di 
operare  su molti file usando un singolo comando

l'asterisco è una delle tecniche di "regex" ovvero 
"Regular Expression", che permettono di usare 
caratteri particolari per definire un insieme di 
possibili stringhe di input ( non studieremo regex 
durante questi tutorial) 

---
## FFMPEG / 1

ffmpeg è un comando che serve ad operare sui video, 
include moltissime operazioni tra cui:
- convertire e ridimensionare video
- unire un file video ad uno audio
- creare un video da molte immagini
- creare molte immagini da un video 

molti comandi richiedono un gran numero di opzioni 
quindi molto spesso è necessario trovare il comando 
giusto sul manuale online o altrove su internet 
(stackoverflow, etc etc)

NB: se volete interrompere un comando che avete 
digitato per errore, potete usare CTRL+C 

---

## FFMPEG / 2

```
ffmpeg -i input.mp4 -c:v libx264 -b 500k output.mp4
```
^^^ converte input.mp4 in un file h264 a 500 kb/s

```
ffmpeg -i input.mp4 thumb%04d.jpg 
```
^^^ converte input.mp4 in frame separate in formato 
jpg %04d significa che 4 cifre decimali verranno 
usate per numerarli, quindi fino a 9999 frame 
verranno salvati 
```
$ ffmpeg -r 60 -f image2 -s 1920x1080 -i pic%04d.png 
	-vcodec libx264 -crf 25  -pix_fmt yuv420p test.mp4
```
^^^ è un unico comando, converte molte immagini in 
un video
-r : è il framerate, 60fps
-s : è per la dimensione, full hd
verranno prese immagini png nominate come 
pic0001.png, pic0002.png, etc (4 cifre decimali)
-vcoded libx264 : il video sarà codificato in h264 
-pix_fmt yuv420p : formato dei pixel 

---

## SOX 

`sox` è un programma che serve a manipolare i file 
audio da terminale

```
sox input.wav chop_n.wav silence 1 0.1 1% 1 0.1 1% 
		: newfile : restart
```
taglia un file audio con dei silenzi tra un suono 
e l'altro in diversi file chiamati "chop_n001.wac", 
"chop_n002.wav", etc

```
sox input.wav out_left.wav remix 1
sox input.wav out_right.wav remix 2
```
estrae solo il canale destro o sinistro da un file  

---
## ALTRI ESEMPI / 1 

```
mogrify -colorspace Gray *.png
mogrify -monochrome *.png
```
^^^ la prima converte in toni di grigio, la seconda 
	solo in bianco/nero con dithering 

```
mogrify -ordered-dither o2x2 *.png
mogrify -ordered-dither o3x3 *.png
mogrify -ordered-dither o4x4 *.png
```
^^^ varie modalità di dithering per immagini già 
in bianco e nero

```
mogrify -transparent black *.png
```
^^^ converte il nero (o un altro colore) 
in trasparente

---

## ALTRI ESEMPI / 2 

```
convert -delay 40 -loop 0 *.jpg output.gif
```
^^^ crea una gif

```
convert -coalesce output.gif -delete -1 -delete 0 
-reverse -coalesce output.gif -loop 0 boomerang.gif
```
^^^ rende la gif di prima palindroma ("boomerang")

---
# ALTRI ESEMPI

```
optipng *.png
jpegoptim *.jpg
```

`optipng` e `jpegoptim` servono ad ottimizzare la 
dimensione e la codifica dei file, sono utili per 
tenere sotto bassa la quantità di banda utilizzata 
da un sito 

---

## ESERCIZIO

>scaricatevi un video da 
`https://test-videos.co.uk/` 

oppure scrivete nel terminale:

```
wget http://nonmateria.com/jellyfish.mp4
```
>poi generate una gif con la seguente serie 
di comandi:
```
mkdir output 
ffmpeg -i jellyfish.mp4 output/frame%04d.png
mogrify -resize 500x500 output/*
convert -delay 5 -loop 0 output/frame* output.gif
```
