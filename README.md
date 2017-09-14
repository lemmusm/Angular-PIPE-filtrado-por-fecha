# Angular PIPE (filtrado por fecha en orden ascendente y descendente)
Creado con el objetivo de ordenar una lista por fecha mediante el uso de pipes en *ngFor

## Creamos un nuevo archivo typescript (.ts) para el nuevo pipe y agregamos lo siguiente:

```
import { Pipe, PipeTransform } from '@angular/core';

@Pipe({
  name: 'datePipe'
})
export class DatePipe implements PipeTransform {
  transform(value: any, args?: any): any {
    //Order ascendente
        let newVal = value.sort((a: any, b: any) => {
            let date1 = new Date(a.date);
            let date2 = new Date(b.date);
        
            if (date1 > date2) {
                return 1;
            } else if (date1 < date2) {
                return -1;
            } else {
                return 0;
            }
        });
        
        return newVal;

//Order descendente
        let newVal = value.sort((a: any, b: any) => {
            let date1 = new Date(a.date);
            let date2 = new Date(b.date);

            if (date2 > date1) {
                return 1;
            } else if (date2 < date1) {
                return -1;
            } else {
                return 0;
            }
        });

        return newVal;
    }
}
```

## Agregamos el pipe a nuestro app.module.ts

```
  import {DatePipe} from 'path-to-source';
  
  @NgModule({
  declarations: [
    AppComponent,
    DatePipe
  ]
```
## Por último lo importamos a nuestro componente dentro del archivo .ts y dentro del .html hacemos uso del pipe mediante *ngFor

```
component.ts

import {DatePipe} from 'path-to-source';
  
  ```
  
  ```
component.html

*ngFor="let item of items | async | datePipe;"
  
  ```
