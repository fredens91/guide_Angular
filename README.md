# guide_Angular
https://angular.io/start

## Installazione di Angular

Installazione globale del CLI di Angular
```
npm install -g @angular/cli
```
Creare nuovo progetto ng
```
ng new nome-del-progetto
```
Installare da terminale la cartella di lavoro .html (e le varie componenti) su Angular
```
ng generate component pages/myPage.html
```
Installare i services
```
ng generate service services/myService
```
Installare i components
```
ng generate component components/myComponents
```
Installare Bootstrap
```
ng add @ng-bootstrap/ng-bootstrap
```
Avviare il client
```
ng serve --open
```

# Struttura di Angular

- [Directive](#Directive)
- [Template](#Template)
- [Dependency Injection (DI)](#Dependency-injection-DI)

## Directive
Le Directive sono classi che aggiungono comportamenti aggiuntivi agli elementi nelle tue applicazioni Angular. Gestiscono [Module](#module), elenchi, stili e ciò che gli utenti vedono. 
Tipi principali di Directive:
- [Component](#component)
- [Directive strutturali](#directive-strutturali) (ad esempio `*ngIf` `*ngFor` `ngSwitch`)
- [Directive di attributo](#directive-di-attributo) (ad esempio `ngModel` `ngClass` `ngStyle`)

### Component
Rappresenta un'unità logica riutilizzabile di un'app Angular e gestisce una particolare parte dell'interfaccia utente (UI). É costituita da 3 file: .TS, .HTML, .CSS. La classe TypeScript definisce l'interazione del template HTML e la struttura DOM renderizzata, mentre il foglio di stile descrive il suo aspetto.

#### @Component (decorator di un component)
- Il [Decorator](#decorator) `@Component` specifica i metadati associati a un componente specifico. 
- Configurazioni del decorator: 
    - **standalone** TRUE quando questo è un componente "auto-descrittivo" o "standalone". FALSE o non specificato, il componente deve essere dichiarato in un ngModule, che è uno stile più vecchio. Da preferire TRUE.
    - **selector** indica ad Angular di inserire il componente dentro il tag HTML corrispondente. 
    Ad esempio, \<app-nome-selettore\> il componente viene inserito qui \</app-nome-selettore\>
    - **templateUrl** è l'indirizzo relativo del template HTML di questo componente. In alternativa, puoi fornire il template HTML direttamente, come valore della proprietà template. Questo template definisce la vista principale del componente.
    - **imports** è un array delle Directive e dei pacchetti a cui il tuo template fa riferimento. Essenziale per i componenti Standalone.
    - **provider** è un array di provider per i servizi di cui il componente ha bisogno -> vedi [Dependency Injection (DI)](#Dependency-Injection-DI).

### Directive strutturali
Sono Directive speciali che modificano la struttura del DOM manipolando la visualizzazione dei suoi elementi. Si riconoscono perché utilizzano un asterisco (*) prima del loro nome quando vengono applicate ad un elemento HTML. Le più comuni sono `*ngIf`, `*ngFor` e `*ngSwitch`.
- `*ngIf`: aggiunge o rimuove elementi DOM in base al valore di una condizione
```
<div *ngIf="mostraElemento">
  <!-- Contenuto dell'elemento che verrà mostrato solo se mostraElemento è true -->
</div>

```
- `*ngFor`: serve per iterare su una collezione di elementi e generare dinamicamente elementi HTML ripetuti in base ai dati forniti. Questa direttiva è particolarmente utile quando si lavora con array o oggetti che contengono una serie di elementi da visualizzare nel template HTML. Ad esempio, supponiamo di avere un array di oggetti elementi nel nostro componente Angular. Possiamo utilizzare la direttiva *ngFor per iterare su questo array e generare dinamicamente elementi HTML per ciascun elemento nell'array:
```
<ul>
  <li *ngFor="let elemento of elementi">
    {{ elemento.nome }}
  </li>
</ul>
```
### Directive di attributo
Sono Directive che modificano l'aspetto o il comportamento di un elemento nel DOM. Esempi di Directive di attributo sono:
- `[ngModel]`: fondamentale per gestire l'input dell'utente all'interno di form. In modo più dettagliato, ecco cosa fa e come funziona:
    - **Two-Way Data Binding**: stabilisce un collegamento bidirezionale tra un elemento di input HTML e una variabile nel componente Angular.
    - Quando [ngModel] è utilizzata su un elemento di input, come ad esempio `<input [(ngModel)]="nome">`, il valore inserito dall'utente in quell'input viene automaticamente associato alla variabile nome nel componente.
    - Sincronizzazione automatica dei cambiamenti: Qualsiasi modifica al valore dell'elemento di input nell'interfaccia utente viene immediatamente riflesso nella variabile del componente, e viceversa. Ciò significa che se l'utente modifica il valore nell'input, la variabile nel componente verrà automaticamente aggiornata per riflettere quel nuovo valore, e se la variabile nel componente cambia per qualsiasi motivo, l'elemento di input sarà aggiornato di conseguenza nell'interfaccia utente.
- `[ngClass]`: consente di applicare o rimuovere classi CSS dinamicamente in base alle condizioni definite nel template. Questo è utile per cambiare lo stile degli elementi HTML in risposta a variabili o condizioni nel componente.
- `[ngStyle]`: consente di applicare stili CSS dinamicamente agli elementi HTML in base alle espressioni nel template.

## Template
I Template definiscono la struttura e il layout della vista (il Component gestisce la logica e i dati associati alla View).
Un Template assomiglia all'HTML standard ma include anche una sintassi Angular che modifica l'HTML in base alla logica della tua applicazione, permettendo funzionalità come ad esempio: 
- **Data binding** per coordinare i dati dell'applicazione e del DOM
- **[Pipe](#pipe)** per trasformare i dati prima che vengano visualizzati 
- **[Directive](#directive)** per applicare la logica dell'applicazione a ciò che viene visualizzato.
- **Event listener** per ascoltare gli eventi dell'interfaccia utente
- **Template reference variable** per accedere al DOM

## Dependency Injection DI
Concetti fondamentale in Angular. La DI consente alle classi con [Decorator](#decorator) (come [Directive](#directive), [Pipe](#pipe) e [Injectables](#injectables)) di configurare le dipendenze di cui hanno bisogno.
- Nel sistema DI esistono due ruoli principali: **dependency consumer** e **dependency provider**.
- Angular facilita l'interazione tra consumer e provider utilizzando un'astrazione chiamata **Injector**. Quando viene richiesta una dipendenza, l'Injector controlla il suo registro per vedere se è già disponibile un'istanza. Se non lo è, viene creata una nuova istanza e memorizzata nel registro. 
- Angular crea un Injector a livello di applicazione (noto anche come Injector "root") durante il processo di avvio dell'applicazione, così come ogni altro Injector necessario. Nella maggior parte dei casi non è necessario creare manualmente degli Injector, ma è importante sapere che esiste uno strato che collega i fornitori e i consumatori.
- Il primo passo è aggiungere il Decorator`@Injectable` per indicare che una classe può essere iniettata.
- Si rende quindi la classe disponibile nella DI, fornendola dipendneza in più posizioni:
  - A livello del **[Component](#component)**, inserendo la configurazione **provider** sotto il Decorator`@Component` (provider: \[nomeClasse\]).
  - A livello di **Module**, inserendo la configurazione **provider** sotto il Decorator`@NgModule`.
- Il modo più comune per iniettare una dipendenza è dichiararla nel costruttore di una classe. Quando Angular crea una nuova istanza di una classe Component, Directive o Pipe, determina quali servizi o altre dipendenze quella classe necessita guardando i tipi dei parametri del costruttore.
- Quando Angular scopre che un Component dipende da un [Service](#service), prima controlla se l'Injector ha delle istanze esistenti di quel Service. Se un'istanza del Service richiesta non esiste ancora, l'Injector ne crea una utilizzando il provider registrato e la aggiunge all'Injector prima di restituire il Service ad Angular.
- Quando tutti i Service richiesti sono stati risolti e restituiti, Angular può chiamare il costruttore del Component con quei Service come argomenti.

# Definizioni generiche

## Service
- Un Service è una classe che fornisce un insieme di funzionalità riutilizzabili in tutta l'applicazione. I Service sono utilizzati per gestire la logica di business, l'accesso ai dati, le operazioni di rete, l'interazione con i Component e molte altre operazioni.
- I Service sono spesso utilizzati per mantenere la separazione delle responsabilità e la modularità dell'applicazione. Possono essere iniettati in altri [Directive](#directive) o Service mediante il meccanismo di [Dependency Injection (DI)](#dependency-injection-di), consentendo una maggiore flessibilità e riutilizzo del codice.
- I Service possono essere registrati e forniti a livello di [Component](#component), Module o applicazione ed è possibile utilizzarli per condividere dati, gestire lo stato dell'applicazione, effettuare chiamate HTTP, manipolare i dati del modello e molto altro ancora.

## Decorator
- Un Decorator è una funzione che consente di modificare in modo dichiarativo il comportamento di una classe o di un'altra struttura del linguaggio, come una proprietà o un metodo. I Decorator sono una caratteristica di TypeScript.
- Esempi di Decorator includono `@Component`, `@NgModule`, `@Injectable`, `@Input`, `@Output`, `@ViewChild`, `@ContentChild`, e così via. Ognuno di questi Decorator ha uno scopo specifico e viene utilizzato per annotare diversi aspetti dell'applicazione.
- In sintesi, un Decorator è un meccanismo fondamentale per aggiungere metadati e configurare il comportamento delle classi e dei membri nelle applicazioni. Aiutano a rendere il codice più chiaro, dichiarativo e manutenibile.

## View
Rappresenta la parte visibile dell'interfaccia di un [Component](#component). È il risultato della combinazione tra un Template HTML e le proprietà e i metodi del Component. 
Può essere organizzata gerarchicamente ed è quindi costituita da Component e [Template](#template). Ogni Template può avere View figlie.

## Pipe
Una Pipe è una funzione che trasforma il valore di un'espressione da un template. Le pipe sono utilizzate per formattare i dati visualizzati nell'interfaccia utente in modo leggibile e significativo. Le pipe possono essere utilizzate per formattare le stringhe, le date, i numeri e persino per creare filtri personalizzati.
Ad esempio, se hai una data che vuoi visualizzare in un formato diverso o un numero che vuoi formattare con un certo numero di cifre decimali, puoi utilizzare le pipe per fare ciò.

## Injectables

## Module
- I Module sono strutture organizzative che consentono di suddividere l'applicazione in blocchi funzionali autonomi e riutilizzabili. Ogni Module raggruppa un insieme di [Direttive](#directive), [Pipe](#pipe), [Service](#service) e altri oggetti Angular correlati che collaborano per fornire una determinata funzionalità o caratteristica dell'applicazione.
- I Module sono definiti utilizzando il [Decorator](#decorator) @NgModule, che viene utilizzato per dichiarare e configurare il Module. 
- Un Module può includere diverse dichiarazioni, importazioni, esportazioni e fornitori che specificano quali Directive, Pipe e Service sono disponibili all'interno del Module stesso e quali dipendenze sono fornite agli altri Module.
- Tra le principali caratteristiche dei moduli in Angular:
  1. Organizzazione e suddivisione del codice: I Module consentono di organizzare il codice in blocchi funzionali autonomi, migliorando la manutenibilità e la scalabilità dell'applicazione.
  2. Riutilizzo: I Module possono essere riutilizzati in diverse parti dell'applicazione o in applicazioni diverse, poiché rappresentano unità logiche indipendenti.
  3. Gestione delle dipendenze: I Module consentono di gestire le dipendenze e le relazioni tra i diversi componenti, servizi e altre risorse dell'applicazione, facilitando la gestione delle dipendenze e la separazione delle responsabilità.
  4. Lazy loading: Angular supporta il caricamento pigro (lazy loading) dei Module, consentendo di caricare i Module solo quando sono necessari, migliorando le prestazioni e l'esperienza dell'utente.