### 1st day
###### intro
> Change detection -> 
>>	On push -> 
>>>	immutability ; using async ->
>>>> Separate data from generator ->
>>>>> Pure pipes ; memoization in template ->
>>>>>> Memoization with closures: function inside a function ;;

_____________

### 2nd day
#### topic: nx ws
Nx ws -> abstruction : libraries -> scam 


add plugins: ``` npx nx list ```

Dev graph: ```nx graph ``` 


to serve:
``` npx nx run marketplace ```

____________

### 3rd day
<h5>
Key words:
#Npx run 
#Senver
#Treeshake
#ngrid
</h5>

> #### Roadmap:
>    State management  , store, build obvervable

#### types of Provided in:
|   |  |  |
------| -----|----------|
 Any | root | platform |
App	| Platform	| Null injector 
(singelton)

to see what is affected by the current changes: <br/>
Npx Nx affected: apps <br/>
See: ```nx ci```


_______________
### 4th day

* carousel: using ngtemplate as passing it as an Input <br/>
lib component:
    ``` ts  
    export class Component implements AfterViewInit {
    // ...
    // get template as input
      @Input() slidesTemplate?: TemplateRef<any>;
    }
    //...
     navigation = {
    prev: () => this.slide(-1),
    next: () => this.slide(1)
  };
  //...
    ``` 
    ``` html
    <!-->...<-->
    <ng-container 
            [ngTemplateOutlet]="slidesTemplate || defaultTemplate"
            [ngTemplateOutletContext]="{
                $implicit: slide,
                navigation
            }"></ng-container>

            <ng-template #defaultTemplate>
                <img [src]="slide">
            </ng-template>
    <!-->...<-->

    ```
app component:
``` html
<o-slide-show [slides]="names" [slidesTemplate]="myTemplate"></o-slide-show> 

<ng-template #myTemplate let-slide let-nav="navigation">
    My name is: {{slide}}
    <button (click)="nav.next()">NEXT</button>
    <button (click)="nav.prev()">PREV</button>
</ng-template>
```
* ControlValueAccessor

___________________________

### 5th

#### passing config from app to libs

* injection token
* modulewithproviders:
static function() in module
``` ts
@NgModule({…})
export class MyModule {
  static forRoot(config: SomeConfig): ModuleWithProviders<SomeModule> {
    return {
      ngModule: SomeModule,
      providers: [
        {provide: SomeConfig, useValue: config }
      ]
    };
  }
}
```