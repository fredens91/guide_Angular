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

## Components
- Rappresenta un'unità logica riutilizzabile di un'app Angular e gestisce una particolare parte dell'interfaccia utente (UI). É costituita da 3 file: .TS, .HTML, .CSS. La classe TypeScript definisce l'interazione del template HTML e la struttura DOM renderizzata, mentre il foglio di stile descrive il suo aspetto.

### Decoratori
- Il decoratore @Component identifica la classe immediatamente sotto di esso come una classe di componente e specifica i suoi metadati.
- Configurazioni del decoratore: 
    - Standalone: TRUE quando questo è un componente "auto-descrittivo" o "standalone". FALSE o non specificato, il componente deve essere dichiarato in un ngModule, che è uno stile più vecchio. Da preferire TRUE.
    - 
