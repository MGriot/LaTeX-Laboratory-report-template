# Template-relazione-LaTex

Questo che vedete è un template per scrivere le relazioni di laboratorio in LaTex, ha un impronta prevalentemente chimica ma può essere adattato a qualsiasi esigenza.
Un esempio di questo template è disponibile a [Template_relazioni](https://github.com/MGriot/Template-relazione-LaTex/blob/master/.out/main.pdf).

## Introduzione
Il template è strutturato in maniera da poter scrivere comodamente una relazione suddividendo ogni sezione in un file diverso collocato nella cartella `section`.
Ci sono però dei file di più grande importanza che vengono elencati qua sotto e affrontati in una sezione apposita uno per volta.
* `main`
* `config/settings`
* `config/package`
* `bibliography`
* `img/`
* `section/`

## main.tex
In questo file, cuore pulsante del template trovi nelle prime righe:
```LaTex
\documentclass[a4paper]{article} %struttura del file
\usepackage[utf8]{inputenc}

\input{config/package} %package utilizzati
\input{config/settings} %file con settaggi
```

`\input{config/package}` indica dove sono collocati tutti i package utilizzati per la costruzione del file di output, è da modificare solo se si sa cosa si sta facendo perchè l'eleiminazione dei pacchetti può compromettere la corretta composizione del `main.tex`.

`\input{config/settings}` è invece la parte che dà lo stile al file finale, qui sono contenute le impostazioni, i comandi e le impostazioni dei pacchetti usati. Verrà analizzato nel dettaglio in una sezione apposita.

Continuando a scorrere il file ci si imbatte in:

```LaTex
%Nome e Cognome 
\def \nome {Nome}
\def \cognome {Cognome}

%titolo e data
\title{Laboratorio di xxxx \\ \huge{Template relazioni}}
\author{\nome \ \cognome}
\date{\today}
```
In `\def \nome {Nome}` e `\def \cognome {Cognome}`, al posto di Nome  e Cognome dentro parentesi graffe "`{}`" va messo il nome e il cognome dell'autore del documento. Questo andrà a collocare il nome e cognome dell'autore in tutte le parti in cui è necessario all'interno del documento.

Per quanto riguarda `\title{Laboratorio di xxxx \\ \huge{Template relazioni}}` è il comando che permette la creazione del titolo, al posto di _"xxxx"_ va messo il nome della materia, in caso di necessità può essere cambiata tutta la parte _"Laboratorio di xxxx"_. Il secondo pezzo, invecem è il titolo vero e proprio e quindi bisogna sostituire _"Template relazioni"_ con il proprio titolo. 

`\date{\today}` Inserisce la data di compilazione del file, generalmente però conviene mettere la data di svolgimento dell'esperienza che si vuole riportare.

Subito dopo viene una parte importante che definisce la testatina e il piedipagina.
```LaTex
%page style
\pagestyle{fancy}
\fancypagestyle{plain}{} %prima pagina uguale alle altre
\fancyhf{}
\rhead{\nome \ \cognome \\ Data consegna: xxxx}
\lhead{Relazione n° x \\ Classe: XE}
\rfoot{Pag. \thepage \hspace{1pt} di \pageref{LastPage}}
\lfoot{\includegraphics[scale=0.1]{img/GitHub/qrcode_github.com.png} Template \LaTeX \;di M.Griot}
\setlength{\headheight}{22.54448pt}
```