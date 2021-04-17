![Screenshot_2021-04-17-18-51-18-02_a927ed2714ba3b9021f681846134c26f](https://user-images.githubusercontent.com/82490151/115117803-fc921700-9fbd-11eb-93aa-b21a144f1ff5.jpg)

![IMG_20210417_204746](https://user-images.githubusercontent.com/82490151/115117862-32cf9680-9fbe-11eb-9031-bf7d31cf7635.jpg)
# front-endDeveloper
Xyz
 q1.Get value display
 1  
 App. Component. Html
<H1>get value textbox in angular</H1>
<input type=”text” #box>
<button (click)=”get Val(box. Value)” >Get value</button>

2. app. component. ts  
import {component} from@angular/core;
import {for @Builder, validatiors } from @angular form;
       @component ({
Selector:'app-root;
Template:,/app.component.html;
Styleurls: [:/app.component.css’]
})
export class App component {
title='blog';
getVal(Val)
{
Console.warn(Val)
}

Q.2 dyanmic allocated nested manner
1.Button.component.ts
import { Component, OnInit, ViewEncapsulation, Input } from '@angular/core';
import { FormGroup } from '@angular/forms';

@Component({
  selector: 'app-button',
  templateUrl: './button.component.html',
  styleUrls: ['./button.component.scss'],
  encapsulation: ViewEncapsulation.None
})
export class ButtonComponent implements OnInit {

  @Input() group: FormGroup;
  @Input() type: string;
  @Input() description: string;
  @Input() class: string;
  @Input() data: string;
  @Input() callFunction: string;


  constructor() { }

  ngOnInit() {
  }

}
2.Button.compnent.html
<div [formGroup]="group">
  <button type="{{ type }}" class="{{ class }}" (click)="{{callFunction}}">{{ description }}</button>
</div>

3(2). buildLoginButton(){
    let data = {
      type: "button",
      class: "btn btn-primary px-4",
      description: this.translate.transform("pages[login_page][login_form][buttons][login]"),
      callFunction: "login()", //I have tried this.login() as well
      group: this.userForm
      }
    const inputFactory = this.resolver.resolveComponentFactory(ButtonComponent);
    const loginButton = this.login_button.createComponent(inputFactory);
    loginButton.instance.group = data.group;
    loginButton.instance.type = data.type;
    loginButton.instance.class = data.class;
    loginButton.instance.description = data.description;
    loginButton.instance.callFunction = data.callFunction;
  }

Q.3 Making A Form
  1.Form.component.html


 <form [formGroup]="registrationForm" (ngSubmit)="onSubmit()" novalidate>
  <input formControlName="firstName" placeholder="Your name">
  <input formControlName="email" placeholder="Your email">
  <input formControlName="phoneNumber" placeholder="Your message">

  <button type="submit">Register</button>
</form>


2.form.component.ts
import { Component } from '@angular/core';
import { FormBuilder, FormArray } from "@angular/forms";

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})

export class AppComponent {
  
  constructor(public fb: FormBuilder) {}

  registrationForm = this.fb.group({
    file: [null],
    fullName: this.fb.group({
      firstName: [''],
      lastName: ['']
    }),
    email: [''],
    phoneNumber: [''],
    address: this.fb.group({
      street: [''],
      city: [''],
      cityName: ['']
    }),
    gender: [''],
    PasswordValidation: this.fb.group({
      password: [''],
      confirmPassword: ['']
    }),
    addDynamicElement: this.fb.array([{phoneNumber1: **value form 1st field**},
{phoneNumber2: **value form 2nd field**},
{phoneNumber3: **value form 3rd field**},
......
{phoneNumberN: **value form Nth field**}, ])
  })  

}

Q.4 Html form show diagram 

Input html file 
And: coding:
 <!doctype html>
<html>
 <head> 
    <link rel="stylesheet" href="style.css"> 
  <link rel=" stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css" integrity="sha384-JcKb8q3iqJ61gNV9KGb8thSsNjpSL0n8PARn9HuZOnIxN0hoP+VmmDGMN5t9UJ0Z" crossorigin="anonymous"> 
 </head> 
 <body> 
  <div class="container  dear"> 
   <div class="row justify-content-between"> 
    <div class="col-md-2  deep  "> 
     <p>ABC123</p> 
    </div> 
    <div class="col-md-2  good "> 
     <p> ABC123</p> 
    </div> 
   </div> 
   <div class="row justify-content-center"> 
    <div class="col-md-5  night"> 
     <input type="text" required> 
    </div> 
   </div> 
   <div class="row justify-content-between"> 
    <div class="col-md-2 justify-content lood"> 
     <p> ABC123</p> 
    </div> 
    <div class="col-md-2 justify-content day"> 
     <p> ABC123</p> 
    </div> 
   </div> 
  </div> 
 </body>
</html>
    
Component.css
dear{
  border:3px solid black;
  width:50%;
  
}
.deep{
  background-color:black;
  width:50%;
  text-align:left;
  color: white;
}
.good{
  
  background-color:black;
  width:50%;
  text align: center;
  color:white;
}

.lood{
  background-color:black;
  width:50%;
  text align: center;
  color:white;
}

.day{
  background-color:black;
  width:50%;
  text align: center;
  color:white;
}
