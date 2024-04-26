# guide_Angular
https://angular.io/start

## Installazione di Angular

### Installazione globale del CLI di Angular
```
npm install -g @angular/cli
```
### Creare nuovo progetto ng
```
ng new nome-del-progetto
```
### Installare da terminale la cartella di lavoro .html (e le varie componenti) su Angular
```
ng generate component pages/myPage.html
```
### Installare i services
```
ng generate service services/myService
```
### Installare i components
```
ng generate component components/myComponents
```
### Installare Bootstrap
```
ng add @ng-bootstrap/ng-bootstrap
```
### Avviare il client
```
ng serve --open
```

## Struttura di Angular

### Topics

1. [Directive](###-1.-Directive)
2. [Template](###-2.-Template)
3. [Dependency injection](###-3.-Dependency-injection)

### 1. Directive
Le Directive sono classi che aggiungono comportamenti aggiuntivi agli elementi nelle tue applicazioni Angular. Utilizza le direttive integrate in Angular per gestire moduli, elenchi, stili e ciò che gli utenti vedono.
Tipi principali di Directive:
- 1.1 `Component`
- 1.2 `Directive strutturali` (ad esempio *ngIf o *ngFor)
- 1.3 `Directive di attributo`

#### 1.1 Component
Rappresenta un'unità logica riutilizzabile di un'app Angular e gestisce una particolare parte dell'interfaccia utente (UI). É costituita da 3 file: .TS, .HTML, .CSS. La classe TypeScript definisce l'interazione del template HTML e la struttura DOM renderizzata, mentre il foglio di stile descrive il suo aspetto.

#### @Component (decorator di un component)
- Il decorator `@Component` specifica i metadati associati a un componente specifico. 
- Configurazioni del decorator: 
    - `standalone` TRUE quando questo è un componente "auto-descrittivo" o "standalone". FALSE o non specificato, il componente deve essere dichiarato in un ngModule, che è uno stile più vecchio. Da preferire TRUE.
    - `selector` indica ad Angular di inserire il componente dentro il tag HTML corrispondente. 
    Ad esempio, \<app-nome-selettore\> il componente viene inserito qui \</app-nome-selettore\>
    - `templateUrl` è l'indirizzo relativo del template HTML di questo componente. In alternativa, puoi fornire il template HTML direttamente, come valore della proprietà template. Questo template definisce la vista principale del componente.
    - `imports` è un array dei componenti, delle direttive e dei pacchetti a cui il tuo template fa riferimento. Essenziale per i componenti Standalone.
    - `provider` è un array di provider per i servizi di cui il componente ha bisogno. Nell'esempio, questo indica ad Angular come fornire l'istanza di HeroService che il costruttore del componente utilizza per ottenere l'elenco degli eroi da visualizzare.

#### 1.2 Directive strutturali
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
#### 1.3 Directive di attributo
Sono Directive che modificano l'aspetto o il comportamento di un elemento nel DOM. Esempi di Directive di attributo sono:
- `[ngModel]`: fondamentale per gestire l'input dell'utente all'interno di form. In modo più dettagliato, ecco cosa fa e come funziona:
    - Two-Way Data Binding: stabilisce un collegamento bidirezionale tra un elemento di input HTML e una variabile nel componente Angular.
    - Quando [ngModel] è utilizzata su un elemento di input, come ad esempio `<input [(ngModel)]="nome">`, il valore inserito dall'utente in quell'input viene automaticamente associato alla variabile nome nel componente.
    - Sincronizzazione automatica dei cambiamenti: Qualsiasi modifica al valore dell'elemento di input nell'interfaccia utente viene immediatamente riflesso nella variabile del componente, e viceversa. Ciò significa che se l'utente modifica il valore nell'input, la variabile nel componente verrà automaticamente aggiornata per riflettere quel nuovo valore, e se la variabile nel componente cambia per qualsiasi motivo, l'elemento di input sarà aggiornato di conseguenza nell'interfaccia utente.
- `[ngClass]`: consente di applicare o rimuovere classi CSS dinamicamente in base alle condizioni definite nel template. Questo è utile per cambiare lo stile degli elementi HTML in risposta a variabili o condizioni nel componente.
- `[ngStyle]`: consente di applicare stili CSS dinamicamente agli elementi HTML in base alle espressioni nel template.

### 2. Template
I Template definiscono la struttura e il layout della vista (il Component gestisce la logica e i dati associati alla View).
Un Template assomiglia all'HTML standard ma include anche una sintassi Angular che modifica l'HTML in base alla logica della tua applicazione, permettendo funzionalità come ad esempio: 
- `data binding` per coordinare i dati dell'applicazione e del DOM
- `pipe` per trasformare i dati prima che vengano visualizzati 
- `directive` per applicare la logica dell'applicazione a ciò che viene visualizzato.
- `event listener` per ascoltare gli eventi dell'interfaccia utente
- `template reference variable` per accedere al DOM

### 3. Dependency injection

## Definizioni generiche

### Decorator
- Un decorator in Angular è una funzione che consente di modificare in modo dichiarativo il comportamento di una classe o di un'altra struttura del linguaggio, come una proprietà o un metodo. I decorator sono una caratteristica di TypeScript, il linguaggio utilizzato per lo sviluppo di applicazioni Angular.
- Esempi di decorator utilizzati in Angular includono @Component, @NgModule, @Injectable, @Input, @Output, @ViewChild, @ContentChild, e così via. Ognuno di questi decorator ha uno scopo specifico e viene utilizzato per annotare diversi aspetti dell'applicazione Angular.
- In sintesi, un decorator in Angular è un meccanismo fondamentale per aggiungere metadati e configurare il comportamento delle classi e dei membri nelle applicazioni Angular. Aiutano a rendere il codice più chiaro, dichiarativo e manutenibile.

### View
Rappresenta la parte visibile dell'interfaccia di un componente. È il risultato della combinazione tra un Template HTML e le proprietà e i metodi del componente. 
Può essere organizzata gerarchicamente ed è quindi costituita da Component e Template. Ogni Template può avere View figlie.
