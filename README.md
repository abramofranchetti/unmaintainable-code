# Come Scrivere Codice Inmanutenibile

## Garantisciti un lavoro a vita ;)

**Roedy Green**
 [**Canadian Mind Products**](http://mindprod.com/jgloss/unmain.html)

<sup>Riprodotto [con il permesso dell'autore](https://github.com/Droogans/unmaintainable-code/issues/3#issuecomment-235317722), circa 2015</sup>

* * *

## Introduzione

> _Non ascrivere mai alla malizia, quello che può essere spiegato con l'incompetenza._ - Napoleone

Con l'intento di creare opportunità d'impiego nel campo della programmazione Java, sto tramandando questi consigli da maestro su come scrivere del codice ceh sia così difficile da manutenere, che le persone che verranno dopo di te ci metteranno anni per effettuare anche i più piccoli cambiamenti. Inoltre, se seguirai queste norme religiosamente, garantirari a **te stesso** un impiego vita natural durante, dato che nessuno oltre a te avrà speranze di successo nell'infernale lavoro di manutere il tuo codice. Inoltre, se seguirai religiosamente **tutte** queste regole, nemmeno tu stesso sarai più in grado di manutenere il tuo stesso codice!

Però non devi strafare. Il tuo codice non deve **sembrare** irrimediabilmente inmanutenibile, deve solo **essere** così. Altrimenti correrà il rischio di essere riscritto o rifattorizzato (_refactored_).

## Principi Generali

> _Quidquid latine dictum sit, altum sonatur._
> _- Qualsiasi cosa detta in latino sembra profonda._

Per ingannare il programmatore che dovrà lavorare sul tuo codice, devi innanzitutto capire come pensa. Ha un programma gigantesco da gestire. Non ha tempo di leggerlo tutto, e ancora meno di capirlo. Vuole solo trovare velocemente il punto dove effettuare le sue modifiche, farle e basta e non avere comportamenti imprevisti che derivino dalla sua modifica.

Lui vede il tuo codice attraverso il tuo di cartone della carta igenica. Può vedere solamente una piccola porzione del tuo programma per volta. Tu vuoi assicurarti che non riesca mai a comprendere il quadro generale. Vuoi rendergli il più complicato possibile trovare il codice che sta cercando. Ma ancora più importante, vuoi rendirgli il più difficile possibile **ignorare** qualcosa con sicurezza.

I programmatori sono cullati dall'autocompiacimento dalle convenzioni. Ma ogni tanto, violando sottilmente le convenzioni, li costringi a leggere ogni riga del tuo codice con una lente d'ingrandimento.

Protesti farti l'idea che ogni funzionalità del linguaggio renda il codice inmanutenibile -- non è così, lo fanno solo se usate in modo improprio.

## Denominazione delle variabili (_Naming_)

> _"Quando uso una parola," disse Humpty Dumpty, in tono piuttosto sprezzante, "significa proprio quello che scelgo che significhi, né più né meno."_
> - Lewis Carroll -- Attraverso lo specchio e quel che Alice vi trovò (_Through the Looking-glass and what Alice Found There_), Capitolo 6

La maggior parte dell'abilità nel scrivere codice inmanutenibile riguarda l'arte della scelta del nome delle variabili e dei metodi. Questi non importano al compilatore. Ti danno un ampio raggio d'azione per confondere il programmatore che dovrà mettere mano al codice.

#### Nuovi usi per <cite>Nomi per bambini</cite>

Compra una copia di un libro di nomi per bambini e non sarai mai più a corto di nomi per le variabili. Fred è un nome meraviglioso, e facile da scrivere. Se stai cercando un nome per una variabile che sia di facile scrittura, prova `asdf` o `aoeu` se stai scrivendo con una tastiera con layout DSK.

#### Nomi di variabili con una singola lettera

Se chiami le tue variabili `a`, `b`, `c`, allora sarà impossibile cercare le loro occorrenze usanto un semplice editor di testo. Inoltre, nessuno sarà in grado di indovinare a cosa servissero. Se qualcuno accenna anche a infrangere la tradizione onorata da FØRTRAN di usare `i`, `j` e `k` per indicizzare le variabili, vale a dire sostituirle con `ii`, `jj` e `kk`, avvisalo di ciò che l'Inquisizione Spagnola fece agli eretici.

#### Errori di ortografia creativi.

Se devi usare nomi di variabili e di funzione parlanti, riempili di errori ortografici. Inserendo qualche errore di ortografia in qualche nome funzione o nome di variabile, e invece scrivendoli correttamente in altri (es: `SetPintleOpening` and `SetPintalClosing`) possiamo impedire efficacemente l'uso di *grep* or altre tecniche di ricerca degli IDE. Funziona in modo incredibilmente efficace. Aggiungi qualche fragranza internazionale per esempio _tory_ o _tori_ oppure theatres/theaters

#### Sii astratto

Nella scelta dei nomi delle funzioni e delle variabili, fa largo uso di parole astratte come _it_, _everything_, _data_, _handle_, _stuff_, _do_, _routine_, _perform_ e mescolaci anche delle cifre es. `routineX48`, `PerformDataFunction`, `DoIt`, `HandleStuff` e `do_args_method`.

#### A.C.R.O.N.I.M.I.

Usa acronimi per tenere il codice pulito. I veri uomini non definiscono mai gli acronimi, li comprendono geneticamente.

#### Surrogazione del thesaurus

Per rompere la noia, usa un thesaurus per cercare quanti più sinonimi possibili per riferirti alla stessa azione es: _display_, _show_, _present_. Accenna vagamente a qualche sottile differenza, quando non ce n'è nessuna. Comunque, se ci sono 2 funzioni simili che hanno differenze cruciali, usa sempre la stessa parole per descrivere entrambe le funzioni es. _print_ per indicare la "scrivi su file", "stampa su carta" e "visualizza a schermo"). Sotto nessuna circostanza, soccombi alle richieste di scrivere un glossario con lo scopo specifico scopo di disambiguare il vocabolario del progetto. Questo sarebbe una falla altamente poco professionale del princio di design della _information hiding_.

#### Usa Forme Plurali Da Altre Lingue.

Uno script VMS tiene traccia dei vari "statii" ritornati da varie "Vaxen". Esperanto , [Klingon](http://www.kli.org/) e la lingua degli Hobbit sono tutte lingue valide per questi scopi. Per il pseudo-Esperanto pluraloj, add oj. Stai facendo la tua parte per la pace nel mondo.

#### CapiTaliZzaZione

Capitalizza in modo random le prime lettere di ogni sillaba in mezzo alle parole. Per esempio `ComputeRasterHistoGram()`.

#### Riusa i Nomi

Ogni volta che le regole del linguaggio lo permettono, dai alle classi, ai costruttori, ai metod, ai nome dei campi, i parametri e le variabili locali gli stessi nomi. Per ottenere punti extra, riusa i nomi di variabili locali all'interno di blocchi `{}`. Lo scopo è di obbligare il manutentore ad esaminare attentamente lo scope di ogni istanza, In particolare, in Java, maschera i metodi ordinari da costruttori.

#### Lettere Åccentate

Usa le lettere accentate nei nomi delle variabili es:

```c
typedef struct { int i; } ínt;
```

dove la seconda í di ínt è una i acuta. Con l'uso di un semplice editor di testo è quasi impossibile distinguere l'accento dal puntino.

#### Sfrutta I Limiti Di Lunghezza Dei Nomi Del Compilatore

Se il compilatore distingue solo, per esempio, le prime 8 lettere dei nomi, allora cambia la fine delle parole es: `var_unit_update()` in un caso e `var_unit_setup()` in un altro.

#### Underscore, un vero amico

Usa `_` e `__` come identificatori (nomi di variabile).

#### Mescola i Linguaggi

Interseca casualmente due linguaggi (umano o di programmazione). Se il tuo capo insiste nell'usare il suo linguaggio, digli che riesci a organizzare i tuoi pensieri solo nel tuo linguaggio oppure, se questo non funziona, denuncialo per discriminazione linguistica e minaccialo di citare in giudizio i datori di lavoro per una grossa somma.

#### Extended ASCII

I caratteri Extended ASCII sono perfettamente validi come nome di variabili, incluse ß, Ð, and ñ. Sono quasi impossibili da digitare senza usare copia/incolla in un semplice editor di testo.

#### Nomi Da Altri Linguaggi

Usa nomi da lingue straniere come fonte per i nomi delle variabili. Per esempio, usa il Tedesco _punkt_ for _punto_. I manutentori non dotati della tua padronanza del tedesco,trarranno giovamento dalla esperienza multiculturale di decifrarne i significati.

#### Nomi dalla Matematica

Scegli i nomi delle variabili che si mascherano da operatori matematici es:

```js
openParen = (slash + asterix) / equals;
```

#### Nomi sbalorditivi

Scegli nomi di variabili che hanno rilevanti connatazioni emozionali es:

```js
marypoppins = (superman + starship) / god;
```

Questo confonderà il lettore perchè avranno difficoltà nel separare le connotazioni emozionali delle parole dalla logica dell'algoritmo sottostante.


#### Rinomina e Riusa

Questo trucco funziona particolarmente bene in Ada, un linguaggio immune alle principali tecniche di offuscamento. Le persone  che originariamente diedero i nomi agli oggetti e ai pacchetti erano degli idioti. Invece di convincerli a cambiarli, usa semplicemente ridenominazioni e sottotipi per rinominare tutto con nomi di tua ideazione. Assicurati di lasciare alcuni riferimenti ai vecchi nomi, come trappola per gli incauti.

#### Quando usare i

Non usare mai `i` per le variabili interne ai cicli. Usa qualsialsi altra lettera ma non `i`. Usa `i` liberamente per ogni altro scopo specialmente per variabili non int. Allo stesso modo usa `n` come indice dei loop.

#### Conventions Schmentions

Ignora i [Sun Java Coding Conventions](http://web.archive.org/web/20091003224540/http://java.sun.com/docs/codeconv/), dopo tutto, lo fa anche Sun. Per fortuna , il compilatore non si offenderà se violate quelle raccomandazioni. Lo scopo è di usare comunque nomi che differiscono solo leggermente dalle convenzioni. Se sei forzato a usare la capitalizzazione, puoi ancora sovvertirla dove questa scelta è ambigua es: use *both* _input**F**ile**n**ame_ and _input**f**ile**N**ame_. Inventa le tue convenzioni di denominazione irrimediabilmente complesse, quindi rimprovera tutti gli altri per non averle seguite.

#### La l minuscola Assomiglia un sacco alla cifra 1

Usa la l minuscola per indicare le constanti long es: `10l` è molto facile che sia scambiata per `101` invece di essere riconosciuta per `10L`. Vieta ogni font che distingue chiaramente `uvw`, `wW`, `gq9`, `2z`, `5s`, `il17|!j`, `oO08`, `` `'" ``, `;,.`, `m nn rn`, e `{[()]}`. Sii creativo.

#### Riuso dei Nomi Globali come Nomi Privati.

Dichiara un array globale nel modulo A, e un array privato con lo stesso nome nell'header del modulo B, così sembrerà che è lo stesso array globale che stai usando nel modulo B, ma non lo è. NOn fare alcun riferimento nei commenti a questa duplicazione.

#### Riciclaggio Rivisitato

Usa lo scoping nel modo più confusionario possibile, reciclando i nomi delle variabili in modo contraddittorio. Per esempio supponi di avere una variabile `A` e una `B`, e delle funzioni `foo` e `bar`. Se sai che la variabile `A` sarà di solito passata a `foo` e la `B` a `bar`, assicurati di definire le funzioni come `function foo(B)` e `function bar(A)` così che dentro la funzione `A` sarà sempre chiamata `B` and vice versa. Con molte funzioni e variabili globali, puoi creare una vasta ragnatela di variabili mutualmente contraddittorie che usano gli stessi nomi.

#### Ricicla le tue variabili.

Ogni volta che le regole dello scope lo permettono, riusa nomi delle variabili che non centrano nulla. Allo stesso modo, usa variabili temporanee per due scopi non correlati. Per una variamente più amichevole, modifica la variabile, per esempio, assegna un valore alla variabile all'inizio di un metodo molto lungo, e da qualche parte nel mezzo, cambiaci signicifato in qualche modo sottile, come convertire da coordinate in base 0 a coordinate in base 1. Assicurati di non documentare questo cambio di significato.

#### Cd wrttn wtht vwls s mch trsr

Quando usi le abbreviazioni dentro i nomi di variabili o metodi, rompi la noia con molte varianti della stessa parola, e ogni tanto scrivila per intero. Questo aiuta a sconfiggere i pigroni che usano le ricerca testuale per comprendere solo alcuni aspetti del tuo programma. Considera le varianti nello spelling come varianti dello stratagemma es: mescola International _colour_, con l'americano _color_ e il più colorito _kulerz_. Se scrivi i nomi per intero, c'è un solo modo per scrivere ogni nome. Questo rende troppo semplice per i manutentori ricordarsi le cose. Ma dato che ci sono così tanti modi di abbrviare una parola, con le abbreviazioni, puoi avere molte diverse variabili che hanno tutte lo stesso significato apparente. Come bonus aggiunto, il manutentore potrebbe anche non accorgersi che sono variabili diverse.

#### Nomi Ingannevoli

Assicurati che ogni metodo faccia qualcosian in più (o in meno) di quello che il suo nome suggerisce. Ad esempio, un metodo chiamato `isValid(x)` dovrebbe, come side effect, convertire `x` in binario e salvare il risultato su un database.

#### m_

Una naming convention che si usa nel mondo del C++ è quella di usare una `m_` davanti ai nomi dei membri. Questo dovrebbe aiutarti a distinguerli dai metodi, almeno fino a che non ti ricordi che "metodo" inizia a sua volta con la lettera "m"

#### o_apple obj_apple

Usa una "o" o "obj" come prefisso per goni istanza di una classe per mostrare che hai in mente un grande progetto polimorfico.

#### Notazione Ungherese

La notazione ungherese è l'arma nucleare tattica delle tecniche di offuscamento del codice; usala! Grazie al gigantesco volume di codice sorgente contiminato da questo idioma niente può ammazzare un ingegnere manutentore più velocemente che un attacco Notazione Ungherese ben pianificato. I seguenti suggerimenti ti aiuteranno a corrompere gli scopi originari della Notazione Ungherese:

 - Insisti ad usare "c" per le costanti in C++ e degli altri linguaggi che impongono direttamente la non-constanza di una variabile.

 - Ricerca e usa i prefissi della Notazione Ungherese che hanno significati in linguaggi diversi da quello che stai usando ora. Per esempio continua ad usare i prefissi `l_` e `a_` {local and argument} e usa sempre lo stile VB  di avere dei prefissi Ungheresi per ogni tipo di controllo quando programmi in C++. Cerca di ignorare il fatto che megabyte di codice sorgente MFC non usa i prefissi Ungheresi nei tipi di controllo.

 - Viola sempre il principio Ungherese secondo il quale le variabili usate comunemente dovrebbero portarsi dietro il minor numero di informazioni extra. Ottieni questo scopo attraverso le tecniche discusse sopra e continunando a fare in modo che ogni classe abbia un prefisso Ungherese personalizzato. Non permettere a nessuno di ricordarti che **nessun** prefisso ti dice che qualcosa **è** una classe. L'importanza di questa regola non può essere sopravvalutata se non si rispettano i suoi principi, il codice sorgente potrebbe essere invaso da nomi di variabili più brevi che hanno un rapporto vocale/consonante più elevato. Nel peggiore dei casi ciò può portare a un completo collasso dell'offuscamento e alla ricomparsa spontanea della notazione inglese nel codice!

 - Viola in modo palese il concetto Ungherese che i parametri delle funzioni e di altri simboli debbano avere nomi significativi, ma ricordati che i prefissi Ungheresi per se stessi possono diventare eccellenti nomi di variabili temporanee.

 - Insist on carrying outright orthogonal information in your Hungarian warts. Consider this real world example `a_crszkvc30LastNameCol`. It took a team of maintenance engineers nearly 3 days to figure out that this whopper variable name described a const, reference, function argument that was holding information from a database column of type Varchar[30] named "LastName" which was part of the table's primary key. When properly combined with the principle that "all variables should be public" this technique has the power to render thousands of lines of source code obsolete instantly!

 - Use to your advantage the principle that the human brain can only hold 7 pieces of information concurrently. For example code written to the above standard has the following properties:

    * A single assignment statement carries 14 pieces of type and name information.
    * A single function call that passes three parameters and assigns a result carries 29 pieces of type and name information.
    * Seek to improve this excellent, but far too concise, standard. Impress management and coworkers by recommending a 5 letter day of the week prefix to help isolate code written on `Monam` and `FriPM`.
    * It is easy to overwhelm the short term memory with even a moderately complex nesting structure, **especially** when the maintenance programmer can't see the start and end of each block on screen simultaneously.

#### Hungarian Notation Revisited

One follow-on trick in the Hungarian notation is "change the type of a variable but leave the variable name unchanged". This is almost invariably done in windows apps with the migration from Win16:

```c
WndProc(HWND hW, WORD wMsg, WORD wParam, LONG lParam)
```

to Win32

```c
WndProc(HWND hW, UINT wMsg, WPARAM wParam, LPARAM lParam)
```

where the `w` values hint that they are words, but they really refer to longs. The real value of this approach comes clear with the Win64 migration, when the parameters will be 64 bits wide, but the old `w` and `l` prefixes will remain forever.

#### Reduce, Reuse, Recycle

If you have to define a structure to hold data for callbacks, always call the structure `PRIVDATA`. Every module can define its own `PRIVDATA`. In VC++, this has the advantage of confusing the debugger so that if you have a `PRIVDATA` variable and try to expand it in the watch window, it doesn't know which `PRIVDATA` you mean, so it just picks one.

#### Obscure film references

Use constant names like `LancelotsFavouriteColour` instead of `blue` and assign it a hex value of `$0204FB`. The color looks identical to pure blue on the screen, and a maintenance programmer would have to work out `0204FB` (or use some graphic tool) to know what it looks like. Only someone intimately familiar with Monty Python and the Holy Grail would know that Lancelot's favorite color was blue. If a maintenance programmer can't quote entire Monty Python movies from memory, he or she has no business being a programmer.

## Camouflage

> _The longer it takes for a bug to surface, the harder it is to find._ - Roedy Green

Much of the skill in writing unmaintainable code is the art of camouflage, hiding things, or making things appear to be what they are not. Many depend on the fact the compiler is more capable at making fine distinctions than either the human eye or the text editor. Here are some of the best camouflaging techniques.

#### Code That Masquerades As Comments and Vice Versa

Include sections of code that are commented out but at first glance do not appear to be.

```js
for (j=0; j<array_len; j+=8) {
    total += array[j+0];
    total += array[j+1];
    total += array[j+2]; /* Main body of
    total += array[j+3]; * loop is unrolled
    total += array[j+4]; * for greater speed.
    total += array[j+5]; */
    total += array[j+6];
    total += array[j+7];
}
```

Without the colour coding would you notice that three lines of code are commented out?

#### namespaces

Struct/union and typedef struct/union are different name spaces in C (not in C++). Use the same name in both name spaces for structures or unions. Make them, if possible, nearly compatible.

```c
typedef struct {
    char* pTr;
    size_t lEn;
} snafu;

struct snafu {
    unsigned cNt
    char* pTr;
    size_t lEn;
} A;
```

#### Hide Macro Definitions

Hide macro definitions in amongst rubbish comments. The programmer will get bored and not finish reading the comments thus never discover the macro. Ensure that the macro replaces what looks like a perfectly legitimate assignment with some bizarre operation, a simple example:

```c
#define a=b a=0-b
```

#### Look Busy

Use `define` statements to make made up functions that simply comment out their arguments, e.g.:

```c
#define fastcopy(x,y,z) /*xyz*/
// ...
fastcopy(array1, array2, size); /* does nothing */
```

#### Use Continuation to hide variables

Instead of using

```c
#define local_var xy_z
```

break up `xy_z` onto two lines:

```c
#define local_var xy\
_z // local_var OK
```

That way a global search for `xy_z` will come up with nothing for that file. To the C preprocessor, the `\` at the end of the line means glue this line to the next one.

#### Arbitrary Names That Masquerade as Keywords

When documenting, and you need an arbitrary name to represent a filename use _"file"_. Never use an obviously arbitrary name like _"Charlie.dat"_ or _"Frodo.txt"_. In general, in your examples, use arbitrary names that sound as much like reserved keywords as possible. For example, good names for parameters or variables would be `bank`, `blank`, `class`, `const`, `constant`, `input`, `key`, `keyword`, `kind`, `output`, `parameter`, `parm`, `system`, `type`, `value`, `var` and `variable`. If you use actual reserved words for your arbitrary names, which would be rejected by your command processor or compiler, so much the better. If you do this well, the users will be hopelessly confused between reserved keywords and arbitrary names in your example, but you can look innocent, claiming you did it to help them associate the appropriate purpose with each variable.

#### Code Names Must Not Match Screen Names

Choose your variable names to have absolutely no relation to the labels used when such variables are displayed on the screen. E.g. on the screen label the field "Postal Code" but in the code call the associated variable `zip`.

#### Don't Change Names

Instead of globally renaming to bring two sections of code into sync, use multiple TYPEDEFs of the same symbol.

#### How to Hide Forbidden Globals

Since global variables are "evil", define a structure to hold all the things you'd put in globals. Call it something clever like `EverythingYoullEverNeed`. Make all functions take a pointer to this structure (call it `handle` to confuse things more). This gives the impression that you're not using global variables, you're accessing everything through a "handle". Then declare one statically so that all the code is using the same copy anyway.

#### Hide Instances With Synonyms

Maintenance programmers, in order to see if they'll be any cascading effects to a change they make, do a global search for the variables named. This can be defeated by this simple expedient of having synonyms, such as

```c
#define xxx global_var // in file std.h
#define xy_z xxx // in file ..\other\substd.h
#define local_var xy_z // in file ..\codestd\inst.h
```

These defs should be scattered through different include-files. They are especially effective if the include-files are located in different directories. The other technique is to reuse a name in every scope. The compiler can tell them apart, but a simple minded text searcher cannot. Unfortunately SCIDs in the coming decade will make this simple technique impossible, since the editor understands the scope rules just as well as the compiler.

#### Long Similar Variable Names

Use very long variable names or class names that differ from each other by only one character, or only in upper/lower case. An ideal variable name pair is `swimmer` and `swimner`. Exploit the failure of most fonts to clearly discriminate between `ilI1|` or `oO08` with identifier pairs like `parselnt` and `parseInt` or `D0Calc` and `DOCalc`. `l` is an exceptionally fine choice for a variable name since it will, to the casual glance, masquerade as the constant `1`. In many fonts rn looks like an m. So how about a variable `swirnrner`. Create variable names that differ from each other only in case e.g. `HashTable` and `Hashtable`.

#### Similar-Sounding Similar-Looking Variable Names

Variables that resemble others except for capitalization and underlines have the advantage of confounding those who like remembering names by sound or letter-spelling, rather than by exact representations.

#### Overload and Bewilder

In C++, overload library functions by using `#define`. That way it looks like you are using a familiar library function where in actuality you are using something totally different.

#### Choosing The Best Overload Operator

In C++, overload `+`, `-`, `*`, and `/` to do things totally unrelated to addition, subtraction etc. After all, if the Stroustroup can use the shift operator to do I/O, why should you not be equally creative? If you overload `+`, make sure you do it in a way that `i = i + 5;` has a totally different meaning from `i += 5;`. Here is an example of elevating overloading operator obfuscation to a high art. Overload the `!` operator for a class, but have the overload have nothing to do with inverting or negating. Make it return an integer. Then, in order to get a logical value for it, you must use `! !`. However, this inverts the logic, so [drum roll] you must use `! ! !`. Don't confuse the `!` operator, which returns a boolean 0 or 1, with the `~` bitwise logical negation operator.

#### Overload new

Overload the `new` operator - much more dangerous than overloading the `+-/*`. This can cause total havoc if overloaded to do something different from its original function (but vital to the object's function so it's very difficult to change). This should ensure users trying to create a dynamic instance get really stumped. You can combine this with the case sensitivity trick also have a member function, and variable called "New".

#### #define

`#define` in C++ deserves an entire essay on its own to explore its rich possibilities for obfuscation. Use lower case `#define` variables so they masquerade as ordinary variables. Never use parameters to your preprocessor functions. Do everything with global `#defines`. One of the most imaginative uses of the preprocessor I have heard of was requiring five passes through CPP before the code was ready to compile. Through clever use of `defines` and `ifdefs`, a master of obfuscation can make header files declare different things depending on how many times they are included. This becomes especially interesting when one header is included in another header. Here is a particularly devious example:

```cpp
#ifndef DONE

#ifdef TWICE

// put stuff here to declare 3rd time around
void g(char* str);
#define DONE

#else // TWICE
#ifdef ONCE

// put stuff here to declare 2nd time around
void g(void* str);
#define TWICE

#else // ONCE

// put stuff here to declare 1st time around
void g(std::string str);
#define ONCE

#endif // ONCE
#endif // TWICE
#endif // DONE
```

This one gets fun when passing `g()` a `char*`, because a different version of `g()` will be called depending on how many times the header was included.

#### Compiler Directives

Compiler directives were designed with the express purpose of making the same code behave completely differently. Turn the boolean short-circuiting directive on and off repeatedly and vigorously, as well as the long strings directive.

## Documentation

> _Any fool can tell the truth, but it requires a man of some sense to know how to lie well._ - Samuel Butler (1835 - 1902)

> _Incorrect documentation is often worse than no documentation._ - Bertrand Meyer

Since the computer ignores comments and documentation, you can lie outrageously and do everything in your power to befuddle the poor maintenance programmer.

#### Lie in the comments

You don't have to actively lie, just fail to keep comments as up to date with the code.

#### Document the obvious

Pepper the code with comments like `/* add 1 to i */` however, never document woolly stuff like the overall purpose of the package or method.

#### Document How Not Why

Document only the details of what a program does, not what it is attempting to accomplish. That way, if there is a bug, the fixer will have no clue what the code should be doing.

#### Avoid Documenting the "Obvious"

If, for example, you were writing an airline reservation system, make sure there are at least 25 places in the code that need to be modified if you were to add another airline. Never document where they are. People who come after you have no business modifying your code without thoroughly understanding every line of it.

#### On the Proper Use of Documentation Templates

Consider function documentation prototypes used to allow automated documentation of the code. These prototypes should be copied from one function (or method or class) to another, but never fill in the fields. If for some reason you are forced to fill in the fields make sure that all parameters are named the same for all functions, and all cautions are the same but of course not related to the current function at all.

#### On the Proper Use of Design Documents

When implementing a very complicated algorithm, use the classic software engineering principles of doing a sound design before beginning coding. Write an extremely detailed design document that describes each step in a very complicated algorithm. The more detailed this document is, the better.
In fact, the design doc should break the algorithm down into a hierarchy of structured steps, described in a hierarchy of auto-numbered individual paragraphs in the document. Use headings at least 5 deep. Make sure that when you are done, you have broken the structure down so completely that there are over 500 such auto-numbered paragraphs. For example, one paragraph might be(this is a real example)

1.2.4.6.3.13 - Display all impacts for activity where selected mitigations can apply (short pseudocode omitted).

**then**... (and this is the kicker) when you write the code, for each of these paragraphs you write a corresponding global function named:

```c
Act1_2_4_6_3_13()
```

Do not document these functions. After all, that's what the design document is for!

Since the design doc is auto-numbered, it will be extremely difficult to keep it up to date with changes in the code (because the function names, of course, are static, not auto-numbered.) This isn't a problem for you because you will not try to keep the document up to date. In fact, do everything you can to destroy all traces of the document.

Those who come after you should only be able to find one or two contradictory, early drafts of the design document hidden on some dusty shelving in the back room near the dead 286 computers.

#### Units of Measure

Never document the units of measure of any variable, input, output or parameter. e.g. feet, metres, cartons. This is not so important in bean counting, but it is very important in engineering work. As a corollary, never document the units of measure of any conversion constants, or how the values were derived. It is mild cheating, but very effective, to salt the code with some incorrect units of measure in the comments. If you are feeling particularly malicious, make up your **own** unit of measure; name it after yourself or some obscure person and never define it. If somebody challenges you, tell them you did so that you could use integer rather than floating point arithmetic.

#### Gotchas

Never document gotchas in the code. If you suspect there may be a bug in a class, keep it to yourself. If you have ideas about how the code should be reorganised or rewritten, for heaven's sake, do not write them down. Remember the words of Thumper in the movie Bambi, _"If you can't say anything nice, don't say anything at all"_? What if the programmer who wrote that code saw your comments? What if the owner of the company saw them? What if a customer did? You could get yourself fired. An anonymous comment that says "This needs to be fixed!" can do wonders, especially if it's not clear what the comment refers to. Keep it vague, and nobody will feel personally criticised.

#### Documenting Variables

**Never** put a comment on a variable declaration. Facts about how the variable is used, its bounds, its legal values, its implied/displayed number of decimal points, its units of measure, its display format, its data entry rules (e.g. total fill, must enter), when its value can be trusted etc. should be gleaned from the procedural code. If your boss forces you to write comments, lard method bodies with them, but never comment a variable declaration, not even a temporary!

#### Disparage In the Comments

Discourage any attempt to use external maintenance contractors by peppering your code with insulting references to other leading software companies, especially anyone who might be contracted to do the work. e.g.:

```c
/* The optimised inner loop.
This stuff is too clever for the dullard at Software Services Inc., who would
probably use 50 times as memory & time using the dumb routines in <math.h>.
*/
class clever_SSInc {
    .. .
}
```

If possible, put insulting stuff in syntactically significant parts of the code, as well as just the comments so that management will probably break the code if they try to sanitise it before sending it out for maintenance.

#### COMMENT AS IF IT WERE CØBØL ON PUNCH CARDS

Always refuse to accept advances in the development environment arena, especially SCIDs. Disbelieve rumors that all function and variable declarations are never more than one click away and always assume that code developed in Visual Studio 6.0 will be maintained by someone using edlin or vi. Insist on Draconian commenting rules to bury the source code proper.

#### Monty Python Comments

On a method called makeSnafucated insert only the JavaDoc `/* make snafucated */`. Never define what _snafucated_ means **anywhere**. Only a fool does not already know, with complete certainty, what _snafucated_ means. For classic examples of this technique, consult the Sun AWT JavaDOC.

## Program Design

> _The cardinal rule of writing unmaintainable code is to specify each fact in as many places as possible and in as many ways as possible._ - Roedy Green

The key to writing maintainable code is to specify each fact about the application in only one place. To change your mind, you need to change it in only one place, and you are guaranteed the entire program will still work. Therefore, the key to writing unmaintainable code is to specify a fact over and over, in as many places as possible, in as many variant ways as possible. Happily, languages like Java go out of their way to make writing this sort of unmaintainable code easy. For example, it is almost impossible to change the type of a widely used variable because all the casts and conversion functions will no longer work, and the types of the associated temporary variables will no longer be appropriate. Further, if the variable is displayed on the screen, all the associated display and data entry code has to be tracked down and manually modified. The Algol family of languages which include C and Java treat storing data in an array, Hashtable, flat file and database with **totally** different syntax. In languages like Abundance, and to some extent Smalltalk, the syntax is identical; just the declaration changes. Take advantage of Java's ineptitude. Put data you know will grow too large for RAM, for now into an array. That way the maintenance programmer will have a horrendous task converting from array to file access later. Similarly place tiny files in databases so the maintenance programmer can have the fun of converting them to array access when it comes time to performance tune.

#### Java Casts

Java's casting scheme is a gift from the Gods. You can use it without guilt since the language requires it. Every time you retrieve an object from a Collection you must cast it back to its original type. Thus the type of the variable may be specified in dozens of places. If the type later changes, all the casts must be changed to match. The compiler may or may not detect if the hapless maintenance programmer fails to catch them all (or changes one too many). In a similar way, all matching casts to `(short)` need to be changed to `(int)` if the type of a variable changes from `short` to `int`. There is a movement afoot to invent a generic cast operator `(cast)` and a generic conversion operator `(convert)` that would require no maintenance when the type of variable changes. Make sure this heresy never makes it into the language specification. Vote no on RFE 114691 and on genericity which would eliminate the need for many casts.

#### Exploit Java's Redundancy

Java insists you specify the type of every variable twice. Java programmers are so used to this redundancy they won't notice if you make the two types slightly different, as in this example:

```java
Bubblegum b = new Bubblegom();
```

Unfortunately the popularity of the ++ operator makes it harder to get away with pseudo-redundant code like this:

```java
swimmer = swimner + 1;
```

#### Never Validate

Never check input data for any kind of correctness or discrepancies. It will demonstrate that you absolutely trust the company's equipment as well as that you are a perfect team player who trusts all project partners and system operators. Always return reasonable values even when data inputs are questionable or erroneous.

#### Be polite, Never Assert

Avoid the `assert()` mechanism, because it could turn a three-day debug fest into a ten minute one.

#### Avoid Encapsulation

In the interests of efficiency, avoid encapsulation. Callers of a method need all the external clues they can get to remind them how the method works inside.

#### Clone & Modify

In the name of efficiency, use cut/paste/clone/modify. This works much faster than using many small reusable modules. This is especially useful in shops that measure your progress by the number of lines of code you've written.

#### Use Static Arrays

If a module in a library needs an array to hold an image, just define a static array. Nobody will ever have an image bigger than 512 x 512, so a fixed-size array is OK. For best precision, make it an array of doubles. Bonus effect for hiding a 2 Meg static array which causes the program to exceed the memory of the client's machine and thrash like crazy even if they never use your routine.

#### Dummy Interfaces

Write an empty interface called something like `WrittenByMe`, and make all of your classes implement it. Then, write wrapper classes for any of Java's built-in classes that you use. The idea is to make sure that every single object in your program implements this interface. Finally, write all methods so that both their arguments and return types are `WrittenByMe`. This makes it nearly impossible to figure out what some methods do, and introduces all sorts of entertaining casting requirements. For a further extension, have each team member have his/her own personal interface (e.g., `WrittenByJoe`); any class worked on by a programmer gets to implement his/her interface. You can then arbitrarily refer to objects by any one of a large number of meaningless interfaces!

#### Giant Listeners

Never create separate Listeners for each Component. Always have one listener for every button in your project and simply use massive if...else statements to test for which button was pressed.

#### Too Much Of A Good Thing<sup>TM</sup>

Go wild with encapsulation and oo. For example:

```java
myPanel.add( getMyButton() );
private JButton getMyButton() {
    return myButton;
}
```

That one probably did not even seem funny. Don't worry. It will some day.

#### Friendly Friend

Use as often as possible the friend-declaration in C++. Combine this with handing the pointer of the creating class to a created class. Now you don't need to fritter away your time in thinking about interfaces. Additionally you should use the keywords _private_ and _protected_ to prove that your classes are well encapsulated.

#### Use Three Dimensional Arrays

Lots of them. Move data between the arrays in convoluted ways, say, filling the columns in `arrayB` with the rows from `arrayA`. Doing it with an offset of 1, for no apparent reason, is a nice touch. Makes the maintenance programmer nervous.

#### Mix and Match

Use both accessor methods and public variables. That way, you can change an object's variable without the overhead of calling the accessor, but still claim that the class is a "Java Bean". This has the additional advantage of frustrating the maintenance programmer who adds a logging function to try to figure out who is changing the value.

#### Wrap, wrap, wrap

Whenever you have to use methods in code you did not write, insulate your code from that other _dirty_ code by at least one layer of wrapper. After all, the other author **might** some time in the future recklessly rename every method. Then where would you be? You could of course, if he did such a thing, insulate your code from the changes by writing a wrapper or you could let VAJ handle the global rename. However, this is the perfect excuse to preemptively cut him off at the pass with a wrapper layer of indirection, **before** he does anything idiotic. One of Java's main faults is that there is no way to solve many simple problems without dummy wrapper methods that do nothing but call another method of the same name, or a closely related name. This means it is possible to write wrappers four-levels deep that do absolutely nothing, and almost no one will notice. To maximise the obscuration, at each level, rename the methods, selecting random synonyms from a thesaurus. This gives the illusion something of note is happening. Further, the renaming helps ensure the lack of consistent project terminology. To ensure no one attempts to prune your levels back to a reasonable number, invoke some of your code bypassing the wrappers at each of the levels.

#### Wrap Wrap Wrap Some More

Make sure all API functions are wrapped at least 6-8 times, with function definitions in separate source files. Using `#defines` to make handy shortcuts to these functions also helps.

#### No Secrets!

Declare every method and variable `public`. After all, somebody, sometime might want to use it. Once a method has been declared public, it can't very well be retracted, now can it? This makes it very difficult to later change the way anything works under the covers. It also has the delightful side effect of obscuring what a class is for. If the boss asks if you are out of your mind, tell him you are following the classic principles of transparent interfaces.

#### The Kama Sutra

This technique has the added advantage of driving any users or documenters of the package to distraction as well as the maintenance programmers. Create a dozen overloaded variants of the same method that differ in only the most minute detail. I think it was Oscar Wilde who observed that positions 47 and 115 of the Kama Sutra were the same except in 115 the woman had her fingers crossed. Users of the package then have to carefully peruse the long list of methods to figure out just which variant to use. The technique also balloons the documentation and thus ensures it will more likely be out of date. If the boss asks why you are doing this, explain it is solely for the convenience of the users. Again for the full effect, clone any common logic and sit back and wait for the copies to gradually get out of sync.

#### Permute and Baffle

Reverse the parameters on a method called `drawRectangle(height, width)` to `drawRectangle(width, height)` without making any change whatsoever to the name of the method. Then a few releases later, reverse it back again. The maintenance programmers can't tell by quickly looking at any call if it has been adjusted yet. Generalisations are left as an exercise for the reader.

#### Theme and Variations

Instead of using a parameter to a single method, create as many separate methods as you can. For example instead of `setAlignment(int alignment)` where `alignment` is an enumerated constant, for left, right, center, create three methods `setLeftAlignment`, `setRightAlignment`, and `setCenterAlignment`. Of course, for the full effect, you must clone the common logic to make it hard to keep in sync.

#### Static Is Good

Make as many of your variables as possible static. If _you_ don't need more than one instance of the class in this program, no one else ever will either. Again, if other coders in the project complain, tell them about the execution speed improvement you're getting.

#### Cargill's Quandary

Take advantage of Cargill's quandary (I think this was his) "any design problem can be solved by adding an additional level of indirection, except for too many levels of indirection." Decompose OO programs until it becomes nearly impossible to find a method which actually updates program state. Better yet, arrange all such occurrences to be activated as callbacks by traversing pointer forests which are known to contain every function pointer used within the entire system. Arrange for the forest traversals to be activated as side-effects from releasing reference counted objects previously created via deep copies which aren't really all that deep.

#### Packratting

Keep all of your unused and outdated methods and variables around in your code. After all - if you needed to use it once in 1976, who knows if you will want to use it again sometime? Sure the program's changed since then, but it might just as easily change back, you "don't want to have to reinvent the wheel" (supervisors love talk like that). If you have left the comments on those methods and variables untouched, and sufficiently cryptic, anyone maintaining the code will be too scared to touch them.

#### And That's Final

Make all of your leaf classes final. After all, _you're_ done with the project - certainly no one else could possibly improve on your work by extending your classes. And it might even be a security flaw - after all, isn't java.lang.String final for just this reason? If other coders in your project complain, tell them about the execution speed improvement you're getting.

#### Eschew The Interface

In Java, disdain the interface. If your supervisors complain, tell them that Java interfaces force you to "cut-and-paste" code between different classes that implement the same interface the same way, and they know how hard that would be to maintain. Instead, do as the Java AWT designers did - put lots of functionality in your classes that can only be used by classes that inherit from them, and use lots of "instanceof" checks in your methods. This way, if someone wants to reuse your code, they have to extend your classes. If they want to reuse your code from two different classes - tough luck, they can't extend both of them at once! If an interface is unavoidable, make an all-purpose one and name it something like `ImplementableIface`. Another gem from academia is to append "Impl" to the names of classes that implement interfaces. This can be used to great advantage, e.g. with classes that implement `Runnable`.

#### Avoid Layouts

Never use layouts. That way when the maintenance programmer adds one more field he will have to manually adjust the absolute co-ordinates of every other thing displayed on the screen. If your boss forces you to use a layout, use a single giant `GridBagLayout`, and hard code in absolute grid co-ordinates.

#### Environment variables

If you have to write classes for some other programmer to use, put environment-checking code (`getenv()` in C++ / `System.getProperty()` in Java) in your classes' nameless static initializers, and pass all your arguments to the classes this way, rather than in the constructor methods. The advantage is that the initializer methods get called as soon as the class program binaries get loaded, even before any of the classes get instantiated, so they will usually get executed before the program `main()`. In other words, there will be no way for the rest of the program to modify these parameters before they get read into your classes - the users better have set up all their environment variables just the way you had them!

#### Table Driven Logic

Eschew any form of table-driven logic. It starts out innocently enough, but soon leads to end users proofreading and then _shudder_, even modifying the tables for themselves.

#### Modify Mom's Fields

In Java, all primitives passed as parameters are effectively read-only because they are passed by value. The callee can modify the parameters, but that has no effect on the caller's variables. In contrast all objects passed are read-write. The reference is passed by value, which means the object itself is effectively passed by reference. The callee can do whatever it wants to the fields in your object. Never document whether a method actually modifies the fields in each of the passed parameters. Name your methods to suggest they only look at the fields when they actually change them.

#### The Magic Of Global Variables

Instead of using exceptions to handle error processing, have your error message routine set a global variable. Then make sure that every long-running loop in the system checks this global flag and terminates if an error occurs. Add another global variable to signal when a user presses the 'reset' button. Of course all the major loops in the system also have to check this second flag. Hide a few loops that **don't** terminate on demand.

#### Globals, We Can't Stress These Enough!

If God didn't want us to use global variables, he wouldn't have invented them. Rather than disappoint God, use and set as many global variables as possible. Each function should use and set at least two of them, even if there's no reason to do this. After all, any good maintenance programmer will soon figure out this is an exercise in detective work, and she'll be happy for the exercise that separates real maintenance programmers from the dabblers.

#### Globals, One More Time, Boys

Global variables save you from having to specify arguments in functions. Take full advantage of this. Elect one or more of these global variables to specify what kinds of processes to do on the others. Maintenance programmers foolishly assume that C functions will not have side effects. Make sure they squirrel results and internal state information away in global variables.

#### Side Effects

In C, functions are supposed to be idempotent, (without side effects). I hope that hint is sufficient.

#### Backing Out

Within the body of a loop, assume that the loop action is successful and immediately update all pointer variables. If an exception is later detected on that loop action, back out the pointer advancements as side effects of a conditional expression following the loop body.

#### Local Variables

Never use local variables. Whenever you feel the temptation to use one, make it into an instance or static variable instead to unselfishly share it with all the other methods of the class. This will save you work later when other methods need similar declarations. C++ programmers can go a step further by making all variables global.

#### Configuration Files

These usually have the form keyword=value. The values are loaded into Java variables at load time. The most obvious obfuscation technique is to use slightly different names for the keywords and the Java variables. Use configuration files even for constants that never change at run time. Parameter file variables require at least five times as much code to maintain as a simple variable would.

#### Bloated classes

To ensure your classes are bounded in the most obtuse way possible, make sure you include peripheral, obscure methods and attributes in every class. For example, a class that defines astrophysical orbit geometry really should have a method that computes ocean tide schedules and attributes that comprise a Crane weather model. Not only does this over-define the class, it makes finding these methods in the general system code like looking for a guitar pick in a landfill.

#### Subclass With Abandon

Object oriented programming is a godsend for writing unmaintainable code. If you have a class with 10 properties (member/method) in it, consider a base class with only one property and subclassing it 9 levels deep so that each descendant adds one property. By the time you get to the last descendant class, you'll have all 10 properties. If possible, put each class declaration in a separate file. This has the added effect of bloating your `INCLUDE` or `USES` statements, and forces the maintainer to open that many more files in his or her editor. Make sure you create at least one instance of each subclass.

## Coding Obfuscation

> _Sedulously eschew obfuscatory hyperverbosity and prolixity._

#### Obfuscated C

Follow the obfuscated C contests on the Internet and sit at the lotus feet of the masters.

#### Find a Forth or APL Guru

In those worlds, the terser your code and the more bizarre the way it works, the more you are revered.

#### I'll Take a Dozen

Never use one housekeeping variable when you could just as easily use two or three.

#### Jude the Obscure

Always look for the most obscure way to do common tasks. For example, instead of using arrays to convert an integer to the corresponding string, use code like this:

```c
char *p;
switch (n) {
    case 1:
        p = "one";
        if (0)
    case 2:
        p = "two";
        if (0)
    case 3:
        p = "three";
        printf("%s", p);
        break;
}
```

#### Foolish Consistency Is the Hobgoblin of Little Minds

When you need a character constant, use many different formats `' '`, `32`, `0x20`, `040`. Make liberal use of the fact that `10` and `010` are not the same number in C or Java.

#### Casting

Pass all data as a `void *` and then typecast to the appropriate structure. Using byte offsets into the data instead of structure casting is fun too.

#### The Nested Switch

(a switch within a switch) is the most difficult type of nesting for the human mind to unravel.

#### Exploit Implicit Conversion

Memorize all of the subtle implicit conversion rules in the programming language. Take full advantage of them. Never use a picture variable (in COBOL or PL/I) or a general conversion routine (such as `sprintf` in C). Be sure to use floating-point variables as indexes into arrays, characters as loop counters, and perform string functions on numbers. After all, all of these operations are well-defined and will only add to the terseness of your source code. Any maintainer who tries to understand them will be very grateful to you because they will have to read and learn the entire chapter on implicit data type conversion; a chapter that they probably had completely overlooked before working on your programs.

#### Raw ints

When using ComboBoxes, use a switch statement with integer cases rather than named constants for the possible values.

#### Semicolons!

Always use semicolons whenever they are syntactically allowed. For example:

```java
if(a);
else;
{
int d;
d = c;
}
;
```

#### Use Octal

Smuggle octal literals into a list of decimal numbers like this:

```java
array = new int [] {
    111,
    120,
    013,
    121,
};
```

#### Convert Indirectly

Java offers a great opportunity for obfuscation whenever you have to convert. As a simple example, if you have to convert a double to a String, go circuitously, via Double with `new Double(d).toString()` rather than the more direct `Double.toString(d)`. You can, of course, be far more circuitous than that! Avoid any conversion techniques recommended by the Conversion Amanuensis. You get bonus points for every extra temporary object you leave littering the heap after your conversion.

#### Nesting

Nest as deeply as you can. Good coders can get up to 10 levels of `( )` on a single line and 20 `{ }` in a single method. C++ coders have the additional powerful option of preprocessor nesting totally independent of the nest structure of the underlying code. You earn extra Brownie points whenever the beginning and end of a block appear on separate pages in a printed listing. Wherever possible, convert nested ifs into nested [?:] ternaries. If they span several lines, so much the better.

#### Numeric Literals

If you have an array with 100 elements in it, hard code the literal 100 in as many places in the program as possible. Never use a static final named constant for the 100, or refer to it as `myArray.length`. To make changing this constant even more difficult, use the literal 50 instead of 100/2, or 99 instead of 100-1. You can further disguise the 100 by checking for `a == 101` instead of `a > 100`, or `a > 99` instead of `a >= 100`.
Consider things like page sizes, where the lines consisting of x header, y body, and z footer lines, you can apply the obfuscations independently to each of these and to their partial or total sums.

These time-honoured techniques are especially effective in a program with two unrelated arrays that just accidentally happen to both have 100 elements. If the maintenance programmer has to change the length of one of them, he will have to decipher every use of the literal 100 in the program to determine which array it applies to. He is almost sure to make at least one error, hopefully one that won't show up for years later.

There are even more fiendish variants. To lull the maintenance programmer into a false sense of security, dutifully create the named constant, but very occasionally "accidentally" use the literal 100 value instead of the named constant. Most fiendish of all, in place of the literal 100 or the correct named constant, sporadically use some other unrelated named constant that just accidentally happens to have the value 100, for now. It almost goes without saying that you should avoid any consistent naming scheme that would associate an array name with its size constant.

#### C's Eccentric View Of Arrays

C compilers transform `myArray[i]` into `*(myArray + i)`, which is equivalent to `*(i + myArray)` which is equivalent to `i[myArray]`. Experts know to put this to good use. To really disguise things, generate the index with a function:

```c
int myfunc(int q, int p) { return p%q; }
// ...
myfunc(6291, 8)[Array];
```

Unfortunately, these techniques can only be used in native C classes, not Java.

#### L o n g   L i n e s

Try to pack as much as possible into a single line. This saves the overhead of temporary variables, and makes source files shorter by eliminating new line characters and white space. Tip: remove all white space around operators. Good programmers can often hit the 255 character line length limit imposed by some editors. The bonus of long lines is that programmers who cannot read 6 point types must scroll to view them.

#### Exceptions

I am going to let you in on a little-known coding secret. Exceptions are a pain in the behind. Properly-written code never fails, so exceptions are actually unnecessary. Don't waste time on them. Subclassing exceptions is for incompetents who know their code will fail. You can greatly simplify your program by having only a single try/catch in the entire application (in main) that calls System.exit(). Just stick a perfectly standard set of throws on every method header whether they could actually throw any exceptions or not.

#### When To Use Exceptions

Use exceptions for non-exceptional conditions. Routinely terminate loops with an `ArrayIndexOutOfBoundsException`. Pass return standard results from a method in an exception.

#### Use threads With Abandon

Title says it all.

#### Lawyer Code

Follow the language lawyer discussions in the newsgroups about what various bits of tricky code should do e.g. `a=a++;` or `f(a++,a++);` then sprinkle your code liberally with the examples. In C, the effects of pre/post decrement code such as

```c
*++b ? (*++b + *(b-1)) : 0
```

are not defined by the language spec. Every compiler is free to evaluate in a different order. This makes them doubly deadly. Similarly, take advantage of the complex tokenizing rules of C and Java by removing all spaces.

#### Early Returns

Rigidly follow the guidelines about no goto, no early returns, and no labelled breaks especially when you can increase the if/else nesting depth by at least 5 levels.

#### Avoid {}

Never put in any `{ }` surrounding your if/else blocks unless they are syntactically obligatory. If you have a deeply nested mixture of if/else statements and blocks, especially with misleading indentation, you can trip up even an expert maintenance programmer. For best results with this technique, use Perl. You can pepper the code with additional ifs _after_ the statements, to amazing effect.

#### Tabs From Hell

Never underestimate how much havoc you can create by indenting with tabs instead of spaces, especially when there is no corporate standard on how much indenting a tab represents. Embed tabs inside string literals, or use a tool to convert spaces to tabs that will do that for you.

#### Magic Matrix Locations

Use special values in certain matrix locations as flags. A good choice is the `[3][0]` element in a transformation matrix used with a homogeneous coordinate system.

#### Magic Array Slots revisited

If you need several variables of a given type, just define an array of them, then access them by number. Pick a numbering convention that only you know and don't document it. And don't bother to define `#define` constants for the indexes. Everybody should just know that the global variable `widget[15]` is the cancel button. This is just an up-to-date variant on using absolute numerical addresses in assembler code.

#### Never Beautify

Never use an automated source code tidier (beautifier) to keep your code aligned. Lobby to have them banned from your company on the grounds they create false deltas in PVCS/CVS (version control tracking) or that every programmer should have his own indenting style held forever sacrosanct for any module he wrote. Insist that other programmers observe those idiosyncratic conventions in "his " modules. Banning beautifiers is quite easy, even though they save the millions of keystrokes doing manual alignment and days wasted misinterpreting poorly aligned code. Just insist that everyone use the **same** tidied format, not just for storing in the common repository, but also while they are editing. This starts an RWAR and the boss, to keep the peace, will ban automated tidying. Without automated tidying, you are now free to _accidentally_ misalign the code to give the optical illusion that bodies of loops and ifs are longer or shorter than they really are, or that else clauses match a different if than they really do. e.g.

```c
if(a)
  if(b) x=y;
else x=z;
```

#### The Macro Preprocessor

It offers great opportunities for obfuscation. The key technique is to nest macro expansions several layers deep so that you have to discover all the various parts in many different *.hpp files. Placing executable code into macros then including those macros in every *.cpp file (even those that never use those macros) will maximize the amount of recompilation necessary if ever that code changes.

#### Exploit Schizophrenia

Java is schizophrenic about array declarations. You can do them the old C, way `String x[]`, (which uses mixed pre-postfix notation) or the new way `String[] x`, which uses pure prefix notation. If you want to really confuse people, mix the notations e.g.

```java
byte[ ] rowvector, colvector , matrix[ ];
```

which is equivalent to:

```java
byte[ ] rowvector;
byte[ ] colvector;
byte[ ][] matrix;
```

#### Hide Error Recovery Code

Use nesting to put the error recovery for a function call as far as possible away from the call. This simple example can be elaborated to 10 or 12 levels of nest:

```javascript
if ( function_A() == OK )
    {
    if ( function_B() == OK )
        {
        /* Normal completion stuff */
        }
    else
        {
        /* some error recovery for Function_B */
        }
    }
    else
        {
        /* some error recovery for Function_A */
        }
```

#### Pseudo C

The real reason for `#define` was to help programmers who are familiar with another programming language to switch to C. Maybe you will find declarations like `#define begin {` or `#define end }` useful to write more interesting code.

#### Confounding Imports

Keep the maintenance programmer guessing about what packages the methods you are using are in. Instead of:

```java
import MyPackage.Read;
import MyPackage.Write;
```

use:

```java
import Mypackage.*;
```

Never fully qualify any method or class no matter how obscure. Let the maintenance programmer guess which of the packages/classes it belongs to. Of course, inconsistency in when you fully qualify and how you do your imports helps most.

#### Toilet Tubing

Never under any circumstances allow the code from more than one function or procedure to appear on the screen at once. To achieve this with short routines, use the following handy tricks:
Blank lines are generally used to separate logical blocks of code. Each line is a logical block in and of itself. Put blank lines between each line.
Never comment your code at the end of a line. Put it on the line above. If you're forced to comment at the end of the line, pick the longest line of code in the entire file, add 10 spaces, and left-align all end-of-line comments to that column.

Comments at the top of procedures should use templates that are at least 15 lines long and make liberal use of blank lines. Here's a handy template:

```java
/*
/* Procedure Name:
/*
/* Original procedure name:
/*
/* Author:
/*
/* Date of creation:
/*
/* Dates of modification:
/*
/* Modification authors:
/*
/* Original file name:
/*
/* Purpose:
/*
/* Intent:
/*
/* Designation:
/*
/* Classes used:
/*
/* Constants:
/*
/* Local variables:
/*
/* Parameters:
/*
/* Date of creation:
/*
/* Purpose:
*/
```

The technique of putting so much redundant information in documentation almost guarantees it will soon go out of date, and will help befuddle maintenance programmers foolish enough to trust it.

## Testing

> _I don't need to test my programs. I have an error-correcting modem._
> - Om I. Baud

Leaving bugs in your programs gives the maintenance programmer who comes along later something interesting to do. A well done bug should leave absolutely no clue as to when it was introduced or where. The laziest way to accomplish this is simply never to test your code.

#### Never Test

Never test any code that handles the error cases, machine crashes, or OS glitches. Never check return codes from the OS. That code never gets executed anyway and slows down your test times. Besides, how can you possibly test your code to handle disk errors, file read errors, OS crashes, and all those sorts of events? Why, you would have to have either an incredibly unreliable computer or a test scaffold that mimicked such a thing. Modern hardware never fails, and who wants to write code just for testing purposes? It isn't any fun. If users complain, just blame the OS or hardware. They'll never know.

#### Never, Ever Do Any Performance Testing

Hey, if it isn't fast enough, just tell the customer to buy a faster machine. If you did do performance testing, you might find a bottleneck, which might lead to algorithm changes, which might lead to a complete redesign of your product. Who wants that? Besides, performance problems that crop up at the customer site mean a free trip for you to some exotic location. Just keep your shots up-to-date and your passport handy.

#### Never Write Any Test Cases

Never perform code coverage or path coverage testing. Automated testing is for wimps. Figure out which features account for 90% of the uses of your routines, and allocate 90% of the tests to those paths. After all, this technique probably tests only about 60% of your source code, and you have just saved yourself 40% of the test effort. This can help you make up the schedule on the back-end of the project. You'll be long gone by the time anyone notices that all those nice "marketing features" don't work. The big, famous software companies test code this way; so should you. And if for some reason, you are still around, see the next item.

#### Testing is for cowards

A brave coder will bypass that step. Too many programmers are afraid of their boss, afraid of losing their job, afraid of customer hate mail and afraid of being sued. This fear paralyzes action, and reduces productivity. Studies have shown that eliminating the test phase means that managers can set ship dates well in advance, an obvious aid in the planning process. With fear gone, innovation and experimentation can blossom. The role of the programmer is to produce code, and debugging can be done by a cooperative effort on the part of the help desk and the legacy maintenance group.
If we have full confidence in our coding ability, then testing will be unnecessary. If we look at this logically, then any fool can recognise that testing does not even attempt to solve a technical problem, rather, this is a problem of emotional confidence. A more efficient solution to this lack of confidence issue is to eliminate testing completely and send our programmers to self-esteem courses. After all, if we choose to do testing, then we have to test every program change, but we only need to send the programmers to one course on building self-esteem. The cost benefit is as amazing as it is obvious.

#### Ensuring It Only Works In Debug Mode

If you've defined TESTING as 1

```c
#define TESTING 1
```

this gives you the wonderful opportunity to have separate code sections, such as

```c
#if TESTING==1
#endif
```

which can contain such indispensable tidbits as

```c
x = rt_val;
```

so that if anyone resets TESTING to 0, the program won't work. And with the tiniest bit of imaginative work, it will not only befuddle the logic, but confound the compiler as well.

## Choice Of Language

> _Philosophy is a battle against the bewitchment of our intelligence by means of language._
> - Ludwig Wittgenstein

Computer languages are gradually evolving to become more fool proof. Using state of the art languages is unmanly. Insist on using the oldest language you can get away with, octal machine language if you can (Like Hans und Frans, I am no girlie man; I am so virile I used to code by plugging gold tipped wires into a plugboard of IBM unit record equipment (punch cards), or by poking holes in paper tape with a hand punch), failing that assembler, failing that FORTRAN or COBOL, failing that C, and BASIC, failing that C++.

#### FØRTRAN

Write all your code in FORTRAN. If your boss asks why, you can reply that there are lots of very useful libraries that you can use thus saving time. However the chances of writing maintainable code in FORTRAN are zero, and therefore following the unmaintainable coding guidelines is a lot easier.

#### Avoid Ada

About 20% of these techniques can't be used in Ada. Refuse to use Ada. If your manager presses you, insist that no-one else uses it, and point out that it doesn't work with your large suite of tools like lint and plummer that work around C's failings.

#### Use ASM

Convert all common utility functions into asm.

#### Use QBASIC

Leave all important library functions written in QBASIC, then just write an asm wrapper to handle the large->medium memory model mapping.

#### Inline Assembler

Sprinkle your code with bits of inline assembler just for fun. Almost no one understands assembler anymore. Even a few lines of it can stop a maintenance programmer cold.

#### MASM call C

If you have assembler modules which are called from C, try to call C back from the assembler as often as possible, even if it's only for a trivial purpose and make sure you make full use of the goto, bcc and other charming obfuscations of assembler.

#### Avoid Maintainability Tools

Avoid coding in Abundance, or using any of its principles kludged into other languages. It was **designed** from the ground up with the primary goal of making the maintenance programmer's job easier. Similarly avoid Eiffel or Ada since they were designed to catch bugs before a program goes into production.

## Dealing With Others

> _Hell is other people._
> - Jean-Paul Sartre, No Exit, 1934

There are many hints sprinkled throughout the tips above on how to rattle maintenance programmers though frustration, and how to foil your boss's attempts to stop you from writing unmaintainable code, or even how to foment an RWAR that involves everyone on the topic of how code should be formatted in the repository.

#### Your Boss Knows Best

If your boss thinks that his or her 20 year old FORTRAN experience is an excellent guide to contemporary programming, rigidly follow all his or her recommendations. As a result, the boss will trust you. That may help you in your career. You will learn many new methods to obfuscate program code.

#### Subvert The Help Desk

One way to help ensure the code is full of bugs is to ensure the maintenance programmers never hear about them. This requires subverting the help desk. Never answer the phone. Use an automated voice that says "thank you for calling the helpline. To reach a real person press "1" or leave a voicemail wait for the tone". Email help requests should be ignored other than to assign them a tracking number. The standard response to any problem is " I think your account is locked out. The person able to authorise reinstatement is not available just now."

#### Keep Your Mouth Shut

Be never vigilant of the next Y2K. If you ever spot something that could sneak up on a fixed deadline and destroy all life in the western hemisphere then **do not** openly discuss it until we are under the critical 4 year event window of panic and opportunity. Do not tell friends, coworkers, or other competent people of your discovery. Under no circumstances attempt to publish anything that might hint at this new and tremendously profitable threat. Do send one normal priority, jargon encrypted, memo to upper management to cover-your-a$$. If at all possible attach the jargon encrypted information as a rider on an otherwise unrelated plain-text memo pertaining to a more immediately pressing business concern. Rest assured that we all see the threat too. Sleep sound at night knowing that long after you've been forced into early retirement you will be begged to come back at a logarithmically increased hourly rate!

#### Baffle 'Em With Bullshit

Subtlety is a wonderful thing, although sometimes a sledge-hammer is more subtle than other tools. So, a refinement on misleading comments creates classes with names like `FooFactory` containing comments with references to the GoF creational patterns (ideally with http links to bogus UML design documents) that have nothing to do with object creation. Play off the maintainer's delusions of competence. More subtly, create Java classes with protected constructors and methods like `Foo f = Foo.newInstance()` that return actual **new instances**, rather than the expected singleton. The opportunities for side-effects are endless.

#### Book Of The Month Club

Join a computer book of the month club. Select authors who appear to be too busy writing books to have had any time to actually write any code themselves. Browse the local bookstore for titles with lots of cloud diagrams in them and no coding examples. Skim these books to learn obscure pedantic words you can use to intimidate the whippersnappers that come after you. Your code should impress. If people can't understand your vocabulary, they must assume that you are very intelligent and that your algorithms are very deep. Avoid any sort of homely analogies in your algorithm explanations.

## Roll Your Own

You've always wanted to write system level code. Now is your chance. Ignore the standard libraries and [write your own](http://www.roll-your-own.com). It will look great on your resumé.

#### Roll Your Own BNF

Always document your command syntax with your own, unique, undocumented brand of BNF notation. Never explain the syntax by providing a suite of annotated sample valid and invalid commands. That would demonstrate a complete lack of academic rigour. Railway diagrams are almost as gauche. Make sure there is no obvious way of telling a terminal symbol (something you would actually type) from an intermediate one -- something that represents a phrase in the syntax. Never use typeface, colour, caps, or any other visual clues to help the reader distinguish the two. Use the exact same punctuation glyphs in your BNF notation that you use in the command language itself, so the reader can never tell if a `(...)`, `[...]`, `{...}` or `"..."` is something you actually type as part of the command, or is intended to give clues about which syntax elements are obligatory, repeatable or optional in your BNF notation. After all, if they are too stupid to figure out your variant of BNF, they have no business using your program.

#### Roll Your Own Allocator

Everyone knows that debugging your dynamic storage is complicated and time consuming. Instead of making sure each class has no storage leaks, reinvent your own storage allocator. It just mallocs space out of a big arena. Instead of freeing storage, force your users to periodically perform a system reset that clears the heap. There's only a few things the system needs to keep track of across resets -- lots easier than plugging all the storage leaks; and so long as the users remember to periodically reset the system, they'll never run out of heap space. Imagine them trying to change this strategy once deployed!

## Tricks In Offbeat Languages

> _Programming in Basic causes brain damage._
> - Edsger Wybe Dijkstra

#### SQL Aliasing

Alias table names to one or two letters. Better still alias them to the names of other unrelated existing tables.

#### SQL Outer Join

Mix the various flavours of outer join syntax just to keep everyone on their toes.

#### JavaScript Scope

"Optimise" JavaScript code taking advantage of the fact a function can access all local variables in the scope of the caller.

#### Visual Basic Declarations

Instead of:

```vbnet
dim Count_num as string
dim Color_var as string
dim counter as integer
```

use:

```vbnet
Dim Count_num$, Color_var$, counter%
```

#### Visual Basic Madness

If reading from a text file, read 15 characters more than you need to then embed the actual text string like so:

```vbnet
ReadChars = .ReadChars (29,0)
ReadChar = trim(left(mid(ReadChar,len(ReadChar)-15,len(ReadChar)-5),7))
If ReadChars = "alongsentancewithoutanyspaces"
Mid,14,24 = "withoutanys"
and left,5 = "without"
```

#### Delphi/Pascal Only

Don't use functions and procedures. Use the label/goto statements then jump around a lot inside your code using this. It'll drive 'em mad trying to trace through this. Another idea is just to use this for the hang of it and scramble your code up jumping to and fro in some haphazard fashion.

#### Perl

Use trailing if's and unless's especially at the end of really long lines.

#### Lisp

LISP is a dream language for the writer of unmaintainable code. Consider these baffling fragments:

```lisp
(lambda (*<8-]= *<8-[= ) (or *<8-]= *<8-[= ))
(defun :-] (<) (= < 2))

(defun !(!)(if(and(funcall(lambda(!)(if(and '(< 0)(< ! 2))1 nil))(1+ !))
(not(null '(lambda(!)(if(< 1 !)t nil)))))1(* !(!(1- !)))))
```

#### Visual Foxpro

This one is specific to Visual Foxpro. A variable is undefined and can't be used unless you assign a value to it. This is what happens when you check a variable's type:

```foxpro
lcx = TYPE('somevariable')
```

The value of `lcx` will be `'U'` or `undefined`. BUT if you assign scope to the variable it sort of defines it and makes it a logical `FALSE`. Neat, huh!?

```foxpro
LOCAL lcx
lcx = TYPE('somevariable')
```

The value of lcx is now `'L'` or logical. It further defined the value of `FALSE`. Just imagine the power of this in writing unmaintainable code.

```foxpro
LOCAL lc_one, lc_two, lc_three... , lc_n
IF lc_one
DO some_incredibly_complex_operation_that_will_neverbe_executed WITH
make_sure_to_pass_parameters
ENDIF

IF lc_two
DO some_incredibly_complex_operation_that_will_neverbe_executed WITH
make_sure_to_pass_parameters
ENDIF

PROCEDURE some_incredibly_complex_oper....
* put tons of code here that will never be executed
* why not cut and paste your main procedure!
ENDIF
```

## Miscellaneous Techniques

> _If you give someone a program, you will frustrate them for a day; if you teach them how to program, you will frustrate them for a lifetime._
> - Anonymous

#### Don't Recompile

Let's start off with probably the most fiendish technique ever devised: Compile the code to an executable. If it works, then just make one or two small little changes in the source code...in each module. **But don't bother recompiling these.** You can do that later when you have more time, and when there's time for debugging. When the hapless maintenance programmer years later makes a change and the code no longer works, she will erroneously assume it must be something she recently changed. You will send her off on a wild goose chase that will keep her busy for weeks.

#### Foiling Debuggers

A very simple way to confound people trying to understand your code by tracing it with a line debugger, is to make the lines long. In particular, put the then clause on the same line as the if. They can't place breakpoints. They can't tell which branch of an if was taken.

#### S.I. vs American Measure

In engineering work there are two ways to code. One is to convert all inputs to S.I. (metric) units of measure, then do your calculations then convert back to various civil units of measure for output. The other is to maintain the various mixed measure systems throughout. Always choose the second. It's the American way!

#### CANI

**C**onstant **A**nd **N**ever-ending **I**mprovement. Make "improvements" to your code often, and force users to upgrade often - after all, no one wants to be running an outdated version. Just because they think they're happy with the program as it is, just think how much happier they will be after you've "fixed" it! Don't tell anyone what the differences between versions are unless you are forced to - after all, why tell someone about bugs in the old version they might never have noticed otherwise?

#### About Box

The About Box should contain only the name of the program, the names of the coders and a copyright notice written in legalese. Ideally it should link to several megs of code that produce an entertaining animated display. However, it should **never** contain a description of what the program is for, its minor version number, or the date of the most recent code revision, or the website where to get the updates, or the author's email address. This way all the users will soon all be running on different versions, and will attempt to install version N+2 before installing version N+1.

#### Ch ch ch Changes

The more changes you can make between versions the better, you don't want users to become bored with the same old API or user interface year after year. Finally, if you can make this change without the users noticing, this is better still - it will keep them on their toes, and keep them from becoming complacent.

#### Put C Prototypes In Individual Files

Instead of common headers. This has the dual advantage of requiring a change in parameter data type to be maintained in every file, **and** avoids any chance that the compiler or linker will detect type mismatches. This will be especially helpful when porting from 32 -> 64 bit platforms.

#### No Skill Required

You don't need great skill to write unmaintainable code. Just leap in and start coding. Keep in mind that management still measures productivity in lines of code even if you have to delete most of it later.

#### Carry Only One Hammer

Stick with what you know and travel light; if you only carry a hammer then all problems are nails.

#### Standards Schmandards

Whenever possible ignore the coding standards currently in use by thousands of developers in your project's target language and environment. For example, insist on STL style coding standards when writing an MFC based application.

#### Reverse the Usual True False Convention

Reverse the usual definitions of true and false. Sounds very obvious but it works great. You can hide:

```c
#define TRUE 0
#define FALSE 1
```

somewhere deep in the code so that it is dredged up from the bowels of the program from some file that no-one ever looks at anymore. Then force the program to do comparisons like:

```c
if ( var == TRUE )
if ( var != FALSE )
```

someone is bound to "correct" the apparent redundancy, and use var elsewhere in the usual way:

```c
if ( var )
```

Another technique is to make `TRUE` and `FALSE` have the same value, though most would consider that out and out cheating. Using values 1 and 2 or -1 and 0 is a more subtle way to trip people up and still look respectable. You can use this same technique in Java by defining a static constant called `TRUE`. Programmers might be more suspicious you are up to no good since there is a built-in literal `true` in Java.

#### Third Party Libraries

Include powerful third party libraries in your project and then don't use them. With practice you can remain completely ignorant of good tools and add the unused tools to your resumé in your "Other Tools" section.

#### Avoid Libraries

Feign ignorance of libraries that are directly included with your development tool. If coding in Visual C++ ignore the presence of MFC or the STL and code all character strings and arrays by hand; this helps keep your pointer skills sharp and it automatically foils any attempts to extend the code.

#### Create a Build Order

Make it so elaborate that no maintainer could ever get any of his or her fixes to compile. Keep secret SmartJ which renders `make` scripts almost obsolete. Similarly, keep secret that the `javac` compiler is also available as a class. On pain of death, never reveal how easy it is to write and maintain a speedy little custom java program to find the files and do the make that directly invokes the `sun.tools.javac.Main` compile class.

#### More Fun With Make

Have the makefile-generated-batch-file copy source files from multiple directories with undocumented overwrite rules. This permits code branching without the need for any fancy source code control system, and stops your successors ever finding out which version of `DoUsefulWork()` is the one they should edit.

#### Collect Coding Standards

Find all the tips you can on writing maintainable code such as the [Square Box Suggestions](http://www.squarebox.co.uk/download/javatips.html) and flagrantly violate them.

#### IDE, Not Me!

Put all the code in the makefile. Your successors will be really impressed how you managed to write a makefile which generates a batch file that generates some header files and then builds the app, such that they can never tell what effects a change will have, or be able to migrate to a modern IDE. For maximum effect use an obsolete make tool, such as an early brain dead version of NMAKE without the notion of dependencies.

#### Bypassing Company Coding Standards

Some companies have a strict policy of no numeric literals; you must use named constants. It is fairly easy to foil the intent of this policy. For example, one clever C++ programmer wrote:

```cpp
#define K_ONE 1
#define K_TWO 2
#define K_THOUSAND 999
```

#### Compiler Warnings

Be sure to leave in some compiler warnings. Use the handy "-" prefix in make to suppress the failure of the make due to any and all compiler errors. This way, if a maintenance programmer carelessly inserts an error into your source code, the make tool will nonetheless try to rebuild the entire package; it might even succeed! And any programmer who compiles your code by hand will think that they have broken some existing code or header when all that has really happened is that they have stumbled across your harmless warnings. They will again be grateful to you for the enjoyment of the process that they will have to follow to find out that the error was there all along. Extra bonus points make sure that your program cannot possibly compile with any of the compiler error checking diagnostics enabled. Sure, the compiler may be able to do subscripts bounds checking, but real programmers don't use this feature, and neither should you. Why let the compiler check for errors when you can use your own lucrative and rewarding time to find these subtle bugs?

#### Combine Bug Fixes With Upgrades

Never put out a "bug fix only" release. Be sure to combine bug fixes with database format changes, complex user interface changes, and complete rewrites of the administration interfaces. That way, it will be so hard to upgrade that people will get used to the bugs and start calling them features. And the people that really want these "features" to work differently will have an incentive to upgrade to the new versions. This will save you maintenance work in the long run, and get you more revenue from your customers.

#### Change File Formats With Each Release Of Your Product

Yeah, your customers will demand upwards compatibility, so go ahead and do that. But make sure that there is no backwards compatibility. That will prevent customers from backing out the newer release, and coupled with a sensible bug fix policy (see above), will guarantee that once on a newer release, they will stay there. For extra bonus points figure out how to get the old version to not even recognise files created by the newer versions. That way, they not only can't read them, they will deny that they are even created by the same application! _Hint_: PC word processors provide a useful example of this sophisticated behaviour.

#### Compensate For Bugs

Don't worry about finding the root cause of bugs in the code. Simply put in compensating code in the higher-level routines. This is a great intellectual exercise, akin to 3D chess, and will keep future code maintainers entertained for hours as they try to figure out whether the problem is in the low-level routines that generate the data or in the high-level routines that change various cases all around. This technique is great for compilers, which are inherently multi-pass programs. You can completely avoid fixing problems in the early passes by simply making the later passes more complicated. With luck, you will never have to speak to the little snot who supposedly maintains the front-end of the compiler. Extra bonus points make sure the back-end breaks if the front-end ever generates the correct data.

#### Use Spin Locks

Avoid actual synchronization primitives in favor of a variety of spin locks -- repeatedly sleep then test a (non-volatile) global variable until it meets your criterion. Spin locks are much easier to use and more "general" and "flexible " than the system objects.

#### Sprinkle sync code liberally

Sprinkle some system synchronization primitives in places where they are **not** needed. I came across one critical section in a section of code where there was no possibility of a second thread. I challenged the original developer and he indicated that it helped document that the code was, well, "critical!"

#### Graceful Degradation

If your system includes an NT device driver, require the application to malloc I/O buffers and lock them in memory for the duration of any transactions, and free/unlock them after. This will result in an application that crashes NT if prematurely terminated with that buffer locked. But nobody at the client site likely will be able to change the device driver, so they won't have a choice.

#### Custom Script Language

Incorporate a scripting command language into your client/server apps that is byte compiled at runtime.

#### Compiler Dependent Code

If you discover a bug in your compiler or interpreter, be sure to make that behaviour essential for your code to work properly. After all you don't use another compiler, and neither should anyone else!

#### A Real Life Example

Here's a real life example written by a master. Let's look at all the different techniques he packed into this single C function.

```c
void* Realocate(void*buf, int os, int ns)
{
    void*temp;
    temp = malloc(os);
    memcpy((void*)temp, (void*)buf, os);
    free(buf);
    buf = malloc(ns);
    memset(buf, 0, ns);
    memcpy((void*)buf, (void*)temp, ns);
    return buf;
}
```

*   Reinvent simple functions which are part of the standard libraries.
*   The word _Realocate_ is not spelled correctly. Never underestimate the power of creative spelling.
*   Make a temporary copy of an input buffer for no real reason.
*   Cast things for no reason. `memcpy()` takes `(void*)`, so cast our pointers even though they're already `(void*)`. Bonus for the fact that you could pass anything anyway.
*   Never bothered to free temp. This will cause a slow memory leak, that may not show up until the program has been running for days.
*   Copy more than necessary from the buffer just in case. This will only cause a core dump on Unix, not Windows.
*   It should be obvious that `os` and `ns` stand for "old size" and "new size".
*   After allocating `buf`, `memset` it to `0\`. Don't use `calloc()` because somebody might rewrite the ANSI spec so that `calloc()` fills the buffer with something other than `0\`. (Never mind the fact that we're about to copy exactly the same amount of data into `buf`.)

#### How To Fix Unused Variable Errors

If your compiler issues "unused local variable" warnings, don't get rid of the variable. Instead, just find a clever way to use it. My favorite is...

```java
i = i;
```

#### It's The Size That Counts

It almost goes without saying that the larger a function is, the better it is. And the more jumps and GOTOs the better. That way, any change must be analysed through many scenarios. It snarls the maintenance programmer in the spaghettiness of it all. And if the function is truly gargantuan, it becomes the Godzilla of the maintenance programmers, stomping them mercilessly to the ground before they have an idea of what's happened.

#### A Picture is a 1000 Words; A Function is a 1000 Lines

Make the body of every method as long as possible - hopefully you never write any methods or functions with fewer than a thousand lines of code, deeply nested, of course.

#### One Missing File

Make sure that one or more critical files are missing. This is best done with includes of includes. For example, in your main module, you have

```c
#include <stdcode.h>
```

`stdcode.h` is available. But in stdcode.h, there's a reference to

```c
#include "a:\\refcode.h"
```

and `refcode.h` is nowhere to be found.

#### Write Everywhere, Read Nowhere

At least one variable should be set everywhere and used almost nowhere. Unfortunately, modern compilers usually stop you from doing the reverse, read everywhere, write nowhere, but you can still do it in C or C++.

## Philosophy

The people who design languages are the people who write the compilers and system classes. Quite naturally they design to make their work easy and mathematically elegant. However, there are 10,000 maintenance programmers to every compiler writer. The grunt maintenance programmers have absolutely no say in the design of languages. Yet the total amount of code they write dwarfs the code in the compilers.

An example of the result of this sort of elitist thinking is the JDBC interface. It makes life easy for the JDBC implementer, but a nightmare for the maintenance programmer. It is far **clumsier** than the FORTRAN interface that came out with SQL three decades ago.

Maintenance programmers, if somebody ever consulted them, would demand ways to hide the housekeeping details so they could see the forest for the trees. They would demand all sorts of shortcuts so they would not have to type so much and so they could see more of the program at once on the screen. They would complain loudly about the myriad petty time-wasting tasks the compilers demand of them.

There are some efforts in this direction [NetRexx](http://www2.hursley.ibm.com/netrexx/), Bali, and visual editors (e.g. IBM's Visual Age is a start) that can collapse detail irrelevant to the current purpose.

## The Shoemaker Has No Shoes

Imagine having an accountant as a client who insisted on maintaining his general ledgers using a word processor. You would do your best to persuade him that his data should be structured. He needs validation with cross field checks. You would persuade him he could do so much more with that data when stored in a database, including controlled simultaneous update.

Imagine taking on a software developer as a client. He insists on maintaining all his data (source code) with a text editor. He is not yet even exploiting the word processor's colour, type size or fonts.

Think of what might happen if we started storing source code as structured data. We could view the **same** source code in many alternate ways, e.g. as Java, as NextRex, as a decision table, as a flow chart, as a loop structure skeleton (with the detail stripped off), as Java with various levels of detail or comments removed, as Java with highlights on the variables and method invocations of current interest, or as Java with generated comments about argument names and/or types. We could display complex arithmetic expressions in 2D, the way TeX and mathematicians do. You could see code with additional or fewer parentheses, (depending on how comfortable you feel with the precedence rules). Parenthesis nests could use varying size and colour to help matching by eye. With changes as transparent overlay sets that you can optionally remove or apply, you could watch in real time as other programmers on your team, working in a different country, modified code in classes that you were working on too.

You could use the full colour abilities of the modern screen to give subliminal clues, e.g. by automatically assigning a portion of the spectrum to each package/class using a pastel shades as the backgrounds to any references to methods or variables of that class. You could bold face the definition of any identifier to make it stand out.

You could ask what methods/constructors will produce an object of type X? What methods will accept an object of type X as a parameter? What variables are accessible in this point in the code? By clicking on a method invocation or variable reference, you could see its definition, helping sort out which version of a given method will actually be invoked. You could ask to globally visit all references to a given method or variable, and tick them off once each was dealt with. You could do quite a bit of code writing by point and click.

Some of these ideas would not pan out. But the best way to find out which would be valuable in practice is to try them. Once we had the basic tool, we could experiment with hundreds of similar ideas to make life easier for the maintenance programmer.

I discuss this further in the SCID student project.

An early version of this article appeared in Java Developers' Journal (volume 2 issue 6). I also spoke on this topic in 1997 November at the [Colorado Summit Conference](http://www.SoftwareSummit.com). It has been gradually growing ever since.

This essay is a **joke**! I apologise if anyone took this literally. Canadians think it gauche to label jokes with a :-). People paid no attention when I harped about how to write __maintainable code. I found people were more receptive hearing all the goofy things people often do to muck it up. Checking for **un**maintainable design patterns is a rapid way to defend against malicious or inadvertent sloppiness.

_**<small>The original was published on [Roedy Green's Mindproducts](http://mindprod.com/jgloss/unmain.html) site.</small>**_
