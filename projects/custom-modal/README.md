
# Custom Modal For Angular

Simple, lightweight and configurable modal box component to implemnt your dynamic pop up component.  


## ๐งพ Features

- Dynamic injection
- Customization (Size, Color, Content, etc..)
- Multiple modal at once
- Host's component interaction wih model's actions (๐ button)
- Auto closeable configuration


## โจ Installation

```bash
  npm i ya-custom-modal-lib
```
    
## ๐ Usage

Three steps and roll out ๐

* Import CustomModalModule to your root AppModule
```bash
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { CustomModalModule } from 'custom-modal';

import { AppComponent } from './app.component';

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule,
    CustomModalModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }

```

* Inject fallowing two services to component where you want to add custom modal

```bash
  
import { Component, ViewContainerRef } from '@angular/core';
import { ModalService } from 'custom-modal';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.scss']
})
export class AppComponent {
  
  constructor(
    private modalService: ModalService,
    private componentReference: ViewContainerRef
  ) { }

}


```

* Create a function and call openModel function in ModalService with custom configuration.(You can pass prefered configuration by using parameters)

```bash
  
import { Component, ViewContainerRef } from '@angular/core';
import { ModalService } from 'custom-modal';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.scss']
})
export class AppComponent {
  
  constructor(
    private modalService: ModalService,
    private componentReference: ViewContainerRef
  ) { }

  onOpenModal() : void{
    this.modalService.openModel({
      viewContainerRef: this.componentReference,
      title: 'one',
      height: '500px',
      width: '500px',
      backgroundColor: '#f00',
      bodyText: 'one works!',
      closeAfter: 2000
    }).subscribe((res) => {

    });
  }

}

```
## API Reference

#### openModel({modalConfigurations})

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `viewContainerRef`      | `ViewContainerRef` | **Required**. Component Reference where need to be added modal |
| `title`      | `string` | Title for modal box |
| `bodyText`      | `string` | Body text for the modal box |
| `height`      | `string` | Height of the modal box |
| `backgroundColor`      | `string` |  Background Color (Only applicable CSS colors) |
| `closeAfter`      | `number` | If required auto closeable (milisecond)|


