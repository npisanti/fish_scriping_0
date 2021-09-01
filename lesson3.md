
## SCRIPTING

La parte più interessante di usare un interfaccia 
testuale è che tutte le operazioni che facciamo 
una per una possono essere collezionate in un 
singolo file di testo detto "script", che poi può 
essere lanciato per eseguirle tutte successivamente 

---
## HELLO WORLD 

Uno script più essenziale possibile può essere 
questo 

```
#!/usr/bin/fish

echo "hello world"

exit
```

`echo` è un comando che serve a emettere in output 
una stringa, cioè una sequenza di caratteri 
alfanumerici

in fish le stringhe possono essere delimitate da 
" o ' 

---

## ESEGUIRE UNO SCRIPT

Per eseguire uno script possiamo usare il 
comando `fish`
```
fish hello_world.sh
```

Gli script possono essere eseguiti come dei 
programmi nel caso sia dato loro il permesso di 
esecuzione con `chmod`. 

Si può eseguire un programma nella directory 
corrente con `./nomeprogramma`
```
chmod +x hello_world.sh
./hello_world.sh
```

---

## COMMENTI

`#` viene usato in fish ed in altre shell per 
scrivere commenti all'interno degli script, tutti 
i comandi che seguono un `#` non verranno eseguiti 

```
#!/usr/bin/fish

# questo è un commento 

echo "hello world"

# echo "io non parlo"

exit
```

---

## VARIABILI

Le variabili sono come dei "contenitori" 
etichettati per poter mantenere in memoria delle 
stringhe. Si possono usare le variabili come 
opzioni usando il simbolo `$`

```
#!/usr/bin/fish

set a "-----"
set x "hello"
set y "world"

echo $a
echo "$x $y"

exit
```
in fish ogni operazione è un comando, perciò a 
differenza di altre shell si usa `set` 
invece di `=` per assegnare variabili

---

## OPZIONI AGLI SCRIPT

quando si esegue uno script, possono essere date 
altre stringhe in output dopo il nome dello script 
```
./mioscript.sh uno due tre 
```
si può accedere a queste stringe con la variabile 
argv, alla quale si accede come se fosse un "array"

```
#!/usr/bin/fish

echo "1) $argv[1]"
echo "2) $argv[2]"

exit
```

---

## IF THEN ELSE 

`if` e `else` possono essere usato, 
insieme a `test`, per eseguire parti dello script 
solo in certe condizioni 
```
#!/usr/bin/fish

if test "$argv[1]" = "ciao"
	echo "ciao anche a te!"
else 
	echo "scostumato!" 
end

exit
```
solo se viene dato "ciao" in input, rispondiamo 
bene:
```
./mioscript.sh ciao 
```

---

## TEST

`test` può essere usato per comparare 
stringhe e numeri:

```
test "uno" == "uno"  # true
test "uno" != "due"  # true
test -n "uno"        # true
test -z "uno"        # false
```

```
test 3 -eq 4               # false
test 3 -ne 4               # true
test "3" -gt "4"           # false
test "3" -ge (math "2*2")  # false
test "3" -lt 3             # false
test "3" -le 3             # true
```
spesso in fish si posson usare le parentesi `( )` 
per assegnare ad una variabile un comando o in 
questo caso usarlo direttamente all'interno di un 
altro comando, `(math "2*2")` vale come 4 

---

## CICLI DI FOR  

`for` può essere usato per ripetere la stessa parte
di script su più variabili
```
#!/usr/bin/fish

# le variabili possono essere liste
set numeri "uno" "due" "tre"

for x in $numeri
	echo $x
end

exit
```
In questo caso usiamo `x` come nome della variabile
che rappresenta l'elemento su cui stiamo operando

---
 
## CICLI DI FOR /2  

Il comando `seq` ci permette di generare una lista
di numeri su cui operare. Inoltre possiamo usare i
cicli  di for anche senza scrivere un file di
script, ma direttamente dal terminale

```
for v in (seq 2 8) 
	set res (math "$v^3")
	echo "$v al cubo = $res"
end
```
^^^ opera su numeri da 2 a 8 (8 incluso) 

---

## CICLI DI FOR /3  

possiamo usare `*` insieme ad un percorso per
definire un insieme di file su cui eseguire il
codice nel `for`

```
for f in *.png 
	echo "$f è un file png"
end
```
fare un `echo` dei file su cui si vuole operare è
molto utile prima di sostituire ad `echo` le
operazioni che vogliamo eseguire su quei file 

---

## ALTRI COMANDI 

`find` : cerca dei file 
`grep` : cerca una parola all'interno del testo
`string` : operazioni sulle stringhe  
`curl` : prende un singolo file da un URL sul web
`diff` : mostra le differenze tra due file di testo
`ping` : verifica la connetività ad internet 
`whoami` : restituisce il nome dell'utente corrente
`head` : mostra solo le prime 10 linee dell'input
`tail` ; mostra solo le ultime 10 linee dell'input
`history` : mostra una lista degli ultimi comandi 

esempio: cancella i file extra che crea OSX
```
find . -name '._*' -delete
find . -name '.DS*' -delete
```

---

## PIPING

una delle funzionalità più potenti del terminale è 
la  possibilità di usare gli output testuali di un 
comando come input di un altro comando grazie al
simbolo di pipe: `|` 

```
ls -la | grep .png 
```
il comando precendete prende l'output di `ls` e lo
usa come input di `grep`, che restituisce in output
solo le linee che contengono la stringa ".png" 

```
history | grep ffmpeg | head 
```
mostra come abbiamo usato `ffmpeg` le ultime 
10 volte 

---

## ESERCIZI 

> trasformare il procedimento che splitta un video 
in frames e poi in gif in uno script

> scrivere uno script per impaginare una serie di 
	file .png, può essere utile `convert -rotate 90` 

> in generale, potete scrivere script anche solo 
per tenere a mente comandi molto complessi 
