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

1. Components
2. Templates
3. Directives
4. Dependency injection

### 1. Components
- Rappresenta un'unità logica riutilizzabile di un'app Angular e gestisce una particolare parte dell'interfaccia utente (UI). É costituita da 3 file: .TS, .HTML, .CSS. La classe TypeScript definisce l'interazione del template HTML e la struttura DOM renderizzata, mentre il foglio di stile descrive il suo aspetto.

#### @Component (decorator di un component)
- Il decorator `@Component` specifica i metadati associati a un componente specifico. 
- Configurazioni del decorator: 
    - `standalone` TRUE quando questo è un componente "auto-descrittivo" o "standalone". FALSE o non specificato, il componente deve essere dichiarato in un ngModule, che è uno stile più vecchio. Da preferire TRUE.
    - `selector` indica ad Angular di inserire il componente dentro il tag HTML corrispondente. 
    Ad esempio, \<app-nome-selettore\> il componente viene inserito qui \</app-nome-selettore\>
    - `templateUrl` è l'indirizzo relativo del template HTML di questo componente. In alternativa, puoi fornire il template HTML direttamente, come valore della proprietà template. Questo template definisce la vista principale del componente.
    - `imports` è un array dei componenti, delle direttive e dei pacchetti a cui il tuo template fa riferimento. Essenziale per i componenti Standalone.
    - `provider` è un array di provider per i servizi di cui il componente ha bisogno. Nell'esempio, questo indica ad Angular come fornire l'istanza di HeroService che il costruttore del componente utilizza per ottenere l'elenco degli eroi da visualizzare.

#### View
Rappresenta la parte visibile dell'interfaccia di un componente. È il risultato della combinazione tra un Template HTML e le proprietà e i metodi del componente. 
Può essere organizzata gerarchicamente ed è quindi costituita da Component e Template. Ogni Template può avere View figlie.

### 2. Templates
I Template definiscono la struttura e il layout della vista (il Component gestisce la logica e i dati associati alla View).
Un Template assomiglia all'HTML standard ma include anche una sintassi Angular che modifica l'HTML in base alla logica della tua applicazione, permettondo funzionalità come ad esempio: 
- `data binding` per coordinare i dati dell'applicazione e del DOM
- `pipe` per trasformare i dati prima che vengano visualizzati 
- `directive` per applicare la logica dell'applicazione a ciò che viene visualizzato.
- `event listener` per ascoltare gli eventi dell'interfaccia utente
- `template reference variable` per accedere al DOM

### 3. Directives



## Definizioni generiche

#### Decorator
- Un decorator in Angular è una funzione che consente di modificare in modo dichiarativo il comportamento di una classe o di un'altra struttura del linguaggio, come una proprietà o un metodo. I decorator sono una caratteristica di TypeScript, il linguaggio utilizzato per lo sviluppo di applicazioni Angular.
- Esempi di decorator utilizzati in Angular includono @Component, @NgModule, @Injectable, @Input, @Output, @ViewChild, @ContentChild, e così via. Ognuno di questi decorator ha uno scopo specifico e viene utilizzato per annotare diversi aspetti dell'applicazione Angular.
- In sintesi, un decorator in Angular è un meccanismo fondamentale per aggiungere metadati e configurare il comportamento delle classi e dei membri nelle applicazioni Angular. Aiutano a rendere il codice più chiaro, dichiarativo e manutenibile.
