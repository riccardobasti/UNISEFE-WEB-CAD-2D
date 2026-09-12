# UNISEFE-WEB-CAD-2D
UNISEFE CAD

UNISEFE CAD è un progetto CAD tecnico open source pensato per offrire un ambiente di disegno 2D, 3D e Structural semplice, diretto e utilizzabile direttamente dal browser.

L'obiettivo è ridurre al minimo la complessità dell'interfaccia e mantenere in un unico ambiente disegno, modellazione e analisi strutturale.

Demo online

Prova UNISEFE CAD direttamente nel browser:

https://riccardobasti.github.io/UNISEFE-WEB-CAD-2D/

Non è richiesta installazione.

Caratteristiche principali

CAD 2D

Linee

Archi

Cerchi

Rettangoli

Testo

Selezione degli oggetti

Snap e riferimenti geometrici

Quote e misure

Disegno tramite mouse e tastiera

Supporto a regioni geometriche

Gestione di geometrie piene e forate

CAD 3D

Estrusione

Rivoluzione

Solidi derivati da geometrie 2D

Operazioni booleane

Unione

Sottrazione

Intersezione

Visualizzazione tridimensionale

Rotazione e navigazione del modello

Gestione di geometrie orientate nello spazio

Structural

UNISEFE CAD integra strumenti dedicati alla geometria e all'analisi strutturale.

Tra le proprietà previste o integrate nel progetto:

Area

Centroide

Momenti statici

Momenti d'inerzia

Prodotti d'inerzia

Assi principali

Momento polare

Costante torsionale J

Costante di warping Cw

Centro di taglio

Shear flow

Warping

Proprietà dipendenti dall'orientamento della geometria

L'obiettivo è permettere di disegnare una geometria e ottenere direttamente le relative proprietà tecniche senza passare da software separati.

Filosofia del progetto

UNISEFE CAD nasce con alcune idee molto semplici:

una sola interfaccia;

meno modalità e meno passaggi intermedi;

il disegno deve essere naturale;

la geometria deve restare comprensibile;

il software non deve obbligare l'utente a conoscere la struttura interna del programma;

2D, 3D e Structural devono poter convivere nello stesso ambiente;

il browser deve essere sufficiente per utilizzare il CAD.

Il progetto cerca quindi un approccio differente rispetto ai CAD tradizionali molto complessi o frammentati in numerosi ambienti di lavoro.

Tecnologia

Il progetto è sviluppato principalmente come applicazione web autonoma.

La base può essere eseguita direttamente tramite:

index.html

Questo permette di:

aprire il CAD localmente;

pubblicarlo tramite GitHub Pages;

integrarlo in un sito;

utilizzarlo come base per plugin o applicazioni web;

svilupparlo senza dipendere necessariamente da un backend.

Avvio locale

Scaricare il repository e aprire:

index.html

con un browser moderno.

In alternativa è possibile usare un piccolo server HTTP locale.

Esempio con Python:

python -m http.server 8000

Poi aprire:

http://localhost:8000

GitHub Pages

Questo repository può essere pubblicato senza workflow complessi.

In GitHub:

aprire Settings;

entrare in Pages;

scegliere Deploy from a branch;

selezionare il branch main;

selezionare / (root);

salvare.

La pagina viene quindi pubblicata automaticamente tramite GitHub Pages.

Struttura del progetto

La struttura può rimanere estremamente semplice:

UNISEFE-WEB-CAD-2D/
│
├── index.html
├── README.md
├── LICENSE
└── docs/

Con l'evoluzione del progetto potranno essere organizzate aree dedicate a:

/2d
/3d
/structural
/examples
/docs

senza perdere la possibilità di distribuire una versione autonoma del CAD.

Obiettivi

UNISEFE CAD vuole diventare un ambiente tecnico aperto che possa essere utilizzato per:

disegno tecnico;

carpenteria metallica;

strutture in acciaio;

geometria delle sezioni;

modellazione 3D;

analisi geometrica e strutturale;

sviluppo di strumenti CAD personalizzati;

ricerca su nuovi modelli di interazione CAD.

Stato del progetto

Il progetto è in sviluppo attivo.

Alcune parti possono essere sperimentali, incomplete o soggette a modifiche importanti.

La priorità attuale è mantenere:

semplicità;

leggibilità;

stabilità;

comportamento coerente tra 2D, 3D e Structural;

assenza di complessità non necessaria.

Contribuire

Contributi, test, suggerimenti e pull request sono benvenuti.

Sono particolarmente utili contributi relativi a:

CAD 2D;

modellazione 3D;

geometria computazionale;

strutture in acciaio;

proprietà delle sezioni;

FEM e meccanica strutturale;

interfaccia CAD;

import/export;

DXF;

STL;

PDF;

performance;

accessibilità e usabilità.

Procedura consigliata

fare un fork del repository;

creare un branch dedicato;

effettuare la modifica;

verificare che il CAD continui a funzionare;

aprire una Pull Request spiegando in modo semplice cosa è stato modificato.

Non è necessario proporre grandi modifiche: anche correzioni piccole e ben definite sono utili.

Segnalazione problemi

Per bug o proposte utilizzare la sezione Issues del repository.

Quando possibile indicare:

browser utilizzato;

operazione eseguita;

comportamento atteso;

comportamento ottenuto;

eventuale file o geometria di esempio.

Roadmap

Tra le aree di sviluppo:

perfezionamento CAD 2D;

miglioramento snap e riferimenti;

geometrie e regioni complesse;

maggiore integrazione tra 2D e 3D;

solidi e booleane;

proprietà strutturali universali;

import/export;

interfaccia responsive;

utilizzo da desktop, tablet e browser;

esempi tecnici;

documentazione;

apertura del progetto a contributori esterni.

Principio guida

Disegnare deve essere più semplice che imparare il programma.

UNISEFE CAD cerca di mantenere questa idea al centro dello sviluppo.

Autore

Progetto sviluppato da ITALFABER / UNISEFE.

Sito ITALFABER:

https://italfaber.com/

Licenza

La licenza del progetto deve essere indicata nel file LICENSE del repository.

Per un progetto open source possono essere valutate, ad esempio, licenze come MIT, GPL-3.0 o AGPL-3.0, in funzione delle modalità con cui si desidera permettere il riutilizzo del codice.

Link

Demo: https://riccardobasti.github.io/UNISEFE-WEB-CAD-2D/

Repository: https://github.com/riccardobasti/UNISEFE-WEB-CAD-2D

ITALFABER: https://italfaber.com/
