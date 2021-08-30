
#						IMAGEMAGICK
					
"imagemagick" è un programma che serve a convertire immagini
ed a applicare trasformazioni grafiche
```
convert image.png image.jpg
```
^^^ converte image.png in un nuovo file JPEG image.jpg 

```
mogrify image.jpg -resize 600x500
```
^^^ cambia le dimensioni di image.jpg in modo che entrino in 
	un rettangolo di 600x500 pixel, mantenendo l'aspetto 

mogrify usa le stesse opzioni di convert, ma invece di
salvare il risultato in un nuovo file applica le 
trasformazioni sul file originale 

---

#						ASTERISCO

l'asterisco `*` serve come "wildcard" per indicare tutti i file
presenti che possono soddisfare la stringa nel quale è usato
```
mogrify -resize 500x500 *.png
```
^^^ ridimensiona solo i file che finiscono in .png
	i file JPEG non verranno ridimensionati e nemmeno
	i file che finiscono con .PNG 

l'asterisco è molto importante per permetterci di operare 
su molti file usando un singolo comando

l'asterisco è una delle tecniche di "regex" ovvero 
"Regular Expression", che permettono di usare caratteri 
particolari per definire un insieme di possibili stringhe
di input ( non studieremo regex durante questi tutorial) 

---
# FFMPEG / 1

ffmpeg è un comando che serve ad operare sui video, include 
moltissime operazioni tra cui:
- convertire e ridimensionare video
- unire un file video ad uno audio
- creare un video da molte immagini
- creare molte immagini da un video 

molti comandi richiedono un gran numero di opzioni quindi 
molto spesso è necessario trovare il comando giusto sul 
manuale online o altrove su internet (stackoverflow, etc etc)

NB: se volete interrompere un comando che avete digitato per 
errore, potete usare CTRL+C 

---

# FFMPEG / 2

```
ffmpeg -i input.mp4 -c:v libx264 -b 500k output.mp4
```
^^^ converte input.mp4 in un file h264 a 500 kb/s

```
ffmpeg -i input.mp4 thumb%04d.jpg 
```
^^^ converte input.mp4 in frame separate in formato jpg
	%04d significa che 4 cifre decimali verranno usate per 
	numerarli, quindi fino a 9999 frame verranno salvati 
```
$ ffmpeg -r 60 -f image2 -s 1920x1080 -i pic%04d.png 
	-vcodec libx264 -crf 25  -pix_fmt yuv420p test.mp4
```
^^^ è un unico comando, converte molte immagini in un video
	-r : è il framerate, 60fps
	-s : è per la dimensione, full hd
	verranno prese immagini png nominate come pic0001.png
		pic0002.png, pic0003.png, etc (4 cifre decimali)
	-vcoded libx264 : il video sarà codificato in h264 
	-pix_fmt yuv420p : formato dei pixel 

---

#						SOX 

`sox` è un programma che serve a manipolare i file audio da
terminale

```
sox input.wav chop_n.wav silence 1 0.1 1% 1 0.1 1% 
		: newfile : restart
```
taglia un file audio con dei silenzi tra un suono e l'altro
in diversi file chiamati "chop_n001.wac", "chop_n002.wav", etc

```
sox input.wav out_left.wav remix 1
sox input.wav out_right.wav remix 2
```
estrae solo il canale destro o sinistro da un file audio 


---
# ALTRI ESEMPI / 1 

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
^^^ varie modalità di dithering per immagini già in b&w

```
mogrify -transparent black *.png
```
^^^ converte il nero (o un altro colore) in trasparente

---

# ALTRI ESEMPI / 2 

```
convert -delay 40 -loop 0 *.jpg output.gif
```
^^^ crea una gif

```
convert -coalesce output.gif -delete -1 -delete 0 -reverse 
		-coalesce output.gif -loop 0 boomerang.gif
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
tenere sotto bassa la quantità di banda utilizzata da
un sito 

---
# ESERCIZIO

>scaricatevi un video da `https://test-videos.co.uk/` 
oppure scrivete nel terminale:

```
wget http://nonmateria.com/jellyfish.mp4
```
>poi generate una gif con la seguente serie di comandi:
```
mkdir output 
ffmpeg -i jellyfish.mp4 output/frame%04d.png
mogrify -resize 500x500 output/*
convert -delay 5 -loop 0 output/frame* output.gif
```

---

#	EDITOR DI TESTO

Per la prossima lezione è necessario usare un editor di
"plain text" cioè di testo non formattato, come ad esempio 
il blocco note di windows o textedit di osx.

Esistono molti editor di testo specifici per la scrivere 
codice, che hanno tra le funzioni utili l'evidenziamento 
della sintassi. 

---

#	VARI EDITOR 

Alcuni editor possono essere avviati nel terminale:

- `micro` è il mio preferito, usa dei comandi classici 
- `nano` è spesso già disponibile in vari terminali
- `vim` e `emacs` sono degli editor molto più avanzati 

Al di fuori del terminale buone scelte possono essere:

- `visual studio code` 
- `sublime text` 
