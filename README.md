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

## Component
- Rappresenta un'unità logica riutilizzabile di un'app Angular e gestisce una particolare parte dell'interfaccia utente (UI). É costituita da 3 file: .TS, .HTML, .CSS. La classe TypeScript definisce l'interazione del template HTML e la struttura DOM renderizzata, mentre il foglio di stile descrive il suo aspetto.

### Decorator
- Il decoratore `@Component` identifica la classe immediatamente sotto di esso come una classe di componente e specifica i suoi metadati.
- Configurazioni del decoratore: 
    - `standalone` TRUE quando questo è un componente "auto-descrittivo" o "standalone". FALSE o non specificato, il componente deve essere dichiarato in un ngModule, che è uno stile più vecchio. Da preferire TRUE.
    - `selector` indica ad Angular di inserire il componente dentro il tag HTML corrispondente. 
    Ad esempio, \<app-nome-selettore\> il componente viene inserito qui \</app-nome-selettore\>
    - `templateUrl` è l'indirizzo relativo del template HTML di questo componente. In alternativa, puoi fornire il template HTML direttamente, come valore della proprietà template. Questo template definisce la vista principale del componente.
    - `imports` è un array dei componenti, delle direttive e dei pacchetti a cui il tuo template fa riferimento. Essenziale per i componenti Standalone.
    - `provider` è un array di provider per i servizi di cui il componente ha bisogno. Nell'esempio, questo indica ad Angular come fornire l'istanza di HeroService che il costruttore del componente utilizza per ottenere l'elenco degli eroi da visualizzare.

### View e Template
- `View` rappresenta la parte visibile dell'interfaccia di un componente. È il risultato della combinazione tra un Template HTML e le proprietà e i metodi del componente.
- `Template` definisce la struttura e il layout della vista (il componente gestisce la logica e i dati associati alla vista).

Una View può essere organizzata gerarchicamente ed è quindi costituita da Component e Template. Ogni Template può avere view figlie.

#### Template
Un template assomiglia all'HTML standard, tranne che include anche la sintassi del template di Angular, che modifica l'HTML in base alla logica della tua applicazione e allo stato dei dati dell'applicazione e del DOM. Il tuo template può utilizzare il data binding per coordinare i dati dell'applicazione e del DOM, le pipe per trasformare i dati prima che vengano visualizzati e le direttive per applicare la logica dell'applicazione a ciò che viene visualizzato.
