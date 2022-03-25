# Template-relazione-LaTex

Questo che vedete è un template per scrivere le relazioni di laboratorio in LaTex, ha un impronta prevalentemente chimica ma può essere adattato a qualsiasi esigenza.
Un esempio di questo template è disponibile a [Template_relazioni](https://github.com/MGriot/Template-relazione-LaTex/blob/master/.out/main.pdf).

Questa guida però non vuole essere un tutorial su come si scriva in LaTex e quindi da per scontato che sappiate come si scrive un file LaTex.

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

Questa prima parte in particolare va a formare tutto quello che è racchiuso nel rettangolo in rosso nell'immagine sottostante:

![Titolo](img/GitHub/titolo.png)


Subito dopo viene una parte importante che definisce la testatina e il piedipagina.
```LaTex
%page style
\pagestyle{fancy}
\fancypagestyle{plain}{}
\fancyhf{}
\rhead{\nome \ \cognome \\ Data consegna: xxxx}
\lhead{Relazione n° x \\ Classe: XE}
\rfoot{Pag. \thepage \hspace{1pt} di \pageref{LastPage}}
\lfoot{\includegraphics[scale=0.1]{img/GitHub/qrcode_github.com.png} Template \LaTeX \;di M.Griot}
\setlength{\headheight}{22.54448pt}
```

`\rhead{\nome \ \cognome \\ Data consegna: xxxx}` si occupa di andare a mettere il nome e il cognome dell'autore, questa parte in automatico, e la data di consegna nella testatina del documento di ogni pagina. Per la data occorre mettere al posto di _"xxxx"_ la data di consegna della relazione. Questo serve per avere un tracciamento migliore dello svolgimento delle attività di laboratorio.

La riga `\lhead{Relazione n° x \\ Classe: XE}` permette di srivere il numero della relazione, nel caso si scrivessero più relazioni nel corso del tempo, occorre sostituire _"x"_ con il numero corretto. Vi è anche la possibilità di inserire la classe o corso andado a modificare _"Classe: XE"_ con quella vostra.

`\rfoot{Pag. \thepage \hspace{1pt} di \pageref{LastPage}}`, invece, va a scrivere il numero di pagina a pie di pagina destro mettendo il numero della pagina corrente e il numero totale di pagine, utile se si ha paura che alcuni fogli possano essere persi. Si consiglia di non modificare più di tanto.

`\lfoot{\includegraphics[scale=0.1]{img/GitHub/qrcode_github.com.png} Template \LaTeX \;di M.Griot}` è la penultima riga e crea in basso a sinistra un QRcode con il link a questa pagina e indica l'autore del template. Nel caso non si voglia quest'aggiunta basta eliminare per intero la riga. Ovviamente, qualora venga utilizzato questo template fa piacere che venga riportato l'indirizzo di questa pagina o il nome del suo autore ma la decisione spetta a te!

L'utlima riga, `\setlength{\headheight}{22.54448pt}`, sistema l'altezza della testatina e il pie di pagina e si consiglia di non modificare.

Questa seconda parte va a formare tutto quello che è racchiuso nei rettangoli in rosso nell'immagine sottostante:

![Testatina](img/GitHub/testatina_e_piedipagina.png)

In ultimo viene la sezione del testo vero e proprio.
```LaTex
\hypersetup{pdftitle={Template Example}, pdfauthor={\cognome \; \nome}}

\begin{document}

\maketitle 
\input{section/0_Sommario} 
\input{section/1_Obbiettivo}
\input{section/2_Principio_del_metodo}
\input{section/3_Strumenti}
\input{section/4_Reagenti}
\input{section/5_Procedimento}
\input{section/6_Reazioni}
\input{section/7_Dati_e_Calcoli}
\input{section/8_Conclusioni}
\input{section/9_Bibliografia}
\input{section/10_H_e_P_frasi} 

\input{section/link_utili}
\input{section/esempi}
\end{document}
```
La prima riga `\hypersetup{pdftitle={Template Example}, pdfauthor={\cognome \; \nome}}` serve per mostrare il nome del file e l'autore come proprietà del pdf generato.

`\maketitle` consente di costruire la sezione di Titolo che prima abbiamo discusso. Non va cencellata altrimenti il titolo del documento sparirebbe.

Tutte le righe comprese tra `\maketitle` e `\end{document}` sono tutte le sezioni che vengono importate per comporre il documento. Quelle che vedono un numero prima del nome, es `\input{section/1_Obbiettivo}`, sono da mantenere, in base alla necessità, mentre le ultime due righe si possono cancellare in quanto caricano del testo utile al Template ma inutile al fine di una relazione.

## settings
Questo file che si raggiunge tramite il percorso: `config/settings` è il file dedicato a tenere le informazioni e preferenze per la costruzione del documento.
Le linee di codice che lo compongono sono poche e semplici.
```LaTex
%%%%%Colors
\definecolor{red}{RGB}{255,0,0}
\definecolor{orange}{RGB}{255,165,0}
\definecolor{blue}{RGB}{0,0,255}
\definecolor{green}{RGB}{143,206,0}

%%%%%%%%%% ToDo notes
% \usepackage[colorinlistoftodos,prependcaption,textsize=tiny,disable]{todonotes}
\newcommandx{\unsure}[2][1=]{\todo[linecolor=red,backgroundcolor=red!25,bordercolor=red,#1]{#2}}
\newcommandx{\change}[2][1=]{\todo[linecolor=orange,backgroundcolor=orange!25,bordercolor=orange,#1]{#2}}
\newcommandx{\info}[2][1=]{\todo[linecolor=blue,backgroundcolor=blue!25,bordercolor=blue,#1]{#2}}
\newcommandx{\improvement}[2][1=]{\todo[linecolor=green,backgroundcolor=green!25,bordercolor=green,#1]{#2}}
\newcommandx{\thiswillnotshow}[2][1=]{\todo[disable,#1]{#2}}

%per flowchart
\tikzstyle{startstop} = [rectangle, rounded corners, minimum width=3cm, minimum height=1cm,text centered, draw=black, fill=red!30]
\tikzstyle{io} = [trapezium, trapezium left angle=70, trapezium right angle=110, minimum width=3cm, minimum height=1cm, text centered, draw=black, fill=blue!30]
\tikzstyle{process} = [rectangle, minimum width=3cm, minimum height=1cm, text centered, draw=black, fill=orange!30]
\tikzstyle{decision} = [diamond, minimum width=3cm, minimum height=1cm, text centered, draw=black, fill=green!30]
\tikzstyle{arrow} = [thick,->,>=stealth]
\pgfplotsset{compat=1.18}

%per frasi H e P
\input{config/H_P_command}

%aggiunge il file di bibliografia per fare le citazioni
\addbibresource{bibliography.bib} %Import the bibliography file
```