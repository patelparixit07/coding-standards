# Coding Standards

This repository represents basic coding standards that one can use while creating packages or working with team.

Agreeing on one coding standard helps to keep code neat and easy to read and also makes it easy to see the difference in code when reviewing them.

## Classes
Class names must use studly case format

```php
// Good

class StandardPlans {} 

// Bad

class standard_plans {}
```

## Methods
Methods must use camel case format

```php
// Good

class StandardPlans 
{    
    public function getStandardPlans() {}
}

// Bad

class StandardPlans 
{
    public function GetStandardPlans() {}
    // OR
    public function get_standard_plans() {}
}
```

## Properties
Class properties must use camel case format

```php
// Good

class StandardPlans
{
    protected $planName  = '';
}

// Bad

class StandardPlans
{
    protected $plan_name = ''; 
    // OR
    protected $PlanName  = '';
}
```

## Constants
Class constants must use uppercase format

```php
// Good

class StandardPlans
{
    const PLAN_PRICE = 10000;
    // OR
    const STORAGE = 2;
}

// Bad

class StandardPlans
{
    const planPrice = 10000;
    // OR
    const storage = 2;
}
```

## Variables
Variables must use camel case format

```php
// Good

$planName = "Hello world";

// Bad

$PlanName = "Hello world";
```

## Strings

```php
// Good

$message = "Hi, I am {$name}.";

// Bad

$message = 'Hi, I am ' . $name . '.';
```

## Statements

```php
// Good

if (condition) {
    
} else if (condition) {
    
} else {
    
}

// Bad

if(condition){  // No space before opening parenthesis and after closing parenthesis
    
}
else { // `else` must be right after `if` closing bracket
    
}
```

## Comments
Comments should be avoided as much as possible by writing expressive code. 

If need to use a comment, format it like this :

```php
// There should be a space before a single line comment.

/*
 * If you need to explain a lot you can use a comment block. Notice the
 * single * on the first line. Comment blocks don't need to be three
 * lines long or three characters shorter than the previous line.
 */
```

#  Laravel Specific

## Configuration
Configuration file names must use kebab case format

```php
config/
  plans-list.php
```

Configuration keys must use snake case format

```php
// config/plans-list.php
return [
    'standard_plan' => env('STANDARD_PLAN'),
];
```

## Artisan Commands
The artisan commands names must use kebab case format

```php
// Good

php artisan update-plan-prices

// Bad

php artisan updatePlanPrices
```

## Routes
Public facing urls routes must use kebab case format

```php
// https://yourwebsite.com/standard-plans

// Route names must use camel case format
// Route parameters must use camel case format

Route::get('standard-plans', 'PlansController@index')->name('standardPrices'); 
Route::get('standard-plans/{planId}', 'PlansController@index')

// All http verbs come first

// Good 

Route::get('/', 'HomeController@index')->name('home');
Route::get('standard-plans', 'PlansController@index')->middleware('frontUser');

// Bad

Route::name('home')->get('/', 'HomeController@index');
Route::middleware('frontUser')->get('PlansController@index');

```

## Views
View file names must use camel case format

```php
resources/
  views/
    standardPlans.blade.php

class PlansController
{
    public function index() {
        return view('standardPlans');
    }
}

```

## Translations
Translations must be rendered with the __ function

```php
<h2>{{ __('standardPlans.form.title') }}</h2>

{!! __('standardPlans.form.description') !!}
```

## RESOURCES AND TRANSFORMERS

### JOBS & EVENTS

A job's and Event's name should be describe its action. Events names should be very clear by the tense used in their name.

E.g. JOBS : CreatePlans, UpdatePlansPrice. EVENTS : PriceUpdated

### LISTENERS, COMMANDS & MAILABLES

Their names should reflect that action with a suffix to avoid naming collisions.

E.g. LISTENERS : SendPlanPurchasedMailListener. COMMANDS : UpdatePlanPricesCommand. MAILABLES : PlanPurchasedMail
