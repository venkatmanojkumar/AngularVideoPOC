# AngularVideoPOC

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 14.0.0.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The application will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via a platform of your choice. To use this command, you need to first add a package that implements end-to-end testing capabilities.

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI Overview and Command Reference](https://angular.io/cli) page.



in this project i have faced problem in installing bootstrap into it.

HOW TO FIX IT ,

Step 1: npm install ngx-bootstrap bootstrap --save  or npm install bootstrap.
Step 2: Then add the needed script file to apps[0].scripts in the angular.json file:

          "scripts": [
    "./node_modules/bootstrap/dist/js/bootstrap.bundle.min.js"
    ],

Step 3: Finally add the Bootstrap CSS file to the apps[0].styles array in the angular.json file:

           "styles": [
    "styles.css",
    "./node_modules/bootstrap/dist/css/bootstrap.min.css"
    ],

Step 4: For style.css
    
     /* You can add global styles to this file, and also import other style files */
@import "../node_modules/bootstrap/dist/css/bootstrap.min.css";

***************************************************************************************
here we are creating an recipe 

52) adding content to the recipe component 

to add in the recipe component first create an model.ts file

*the model.ts file is used to add arrays and the some of objects into it becoz in the component.ts file it tooks lots of space
 so an model file is created to add array and objects into it in this file we will no write any conditions . at here we only export the arrays and objects and import in some component.ts file  

*now in the recipe-list.component.ts file we are importing the recipe model 


*ngFor;
     NgFor is a built-in template directive that makes it easy to iterate over something like an array or an object and create a template for each item.

* in model;

export class Recipe {
    public name: string;
    public description: string;
    public imagePath: string;
    
    constructor(name:string, desc:string, imagePath:string){
        this.name = name;
        this.description = desc;
        this.imagePath = imagePath;
    }
}

* in ts;

import { Component, OnInit } from '@angular/core';
import { Recipe } from '../recipe.model';

@Component({
  selector: 'app-recipe-list',
  templateUrl: './recipe-list.component.html',
  styleUrls: ['./recipe-list.component.css']
})
export class RecipeListComponent implements OnInit {
   recipes: Recipe[] = [
    new Recipe('A Test Recipr', 'This is Simply a Test', 'assets/images/chicken.jpg'),
    new Recipe('A Test Recipr', 'This is Simply a Test', 'assets/images/chicken.jpg')
   ];
  constructor() { }

  ngOnInit(): void {
  }
}

* in html ;

<div class="row">
    <div class="col-xs-12">
        <button class="btn btn-success">New Recipe</button>
    </div>
</div>
<hr>
<div class="row">
    <div class="col-xs-12">
        <a href="#" class="list-group-item clearfix" *ngFor="let recipe of recipes">
            <div class="pull-left">
            <h4 class="list-group-item-heading">{{ recipe.name }}</h4>
            <p class="list-group-item-text">{{ recipe.description }}</p>    
            </div>
            <span class="pull-right">
                <img  [src]="recipe.imagePath"  alt="{{ recipe.name }}" class="img-responsive" style="max-height: 50px;">
            </span>
        </a>
        <app-recipe-items></app-recipe-items>
    </div>
</div>

-->as like above shopping-list also have been added same as with the help of forloop as for forloop we would create an interface or model file but here we creaded the model file in this model file and the type is defined and it is exported  

* shared.model.ts file 

export class Ingredient {
    constructor(public name: string , public amount: number) {}
}

* shopping-list-component.ts 

here the exported shopping list from shared.model.ts file is imported into the shoping-list component 

import { Component, OnInit } from '@angular/core';
import { Ingredient } from '../shared/ingredient.model';

@Component({
  selector: 'app-shopping-list',
  templateUrl: './shopping-list.component.html',
  styleUrls: ['./shopping-list.component.css']
})
export class ShoppingListComponent implements OnInit {
  ingredients : Ingredient [] = [
    new Ingredient('apples', 5),
    new Ingredient('tomatos', 10)
  ] ;
  constructor() { }

  ngOnInit(): void {
  }

}

* in html

<div class="row">
    <div class="col-xs-12">
        <app-shopping-edit></app-shopping-edit>
        <hr>
        <ul class="list-group">
            <a class="list-group-item" style="cursor: pointer;" *ngFor="let ingredient of ingredients">
            {{ ingredient.name }} ({{ ingredient.amount }})  /* here string implementation also been done inside the brackets */
            </a>
        </ul>
    </div>
</div>

86) video 

in this we have been adding  -