# Documentation
general syntax
    
    AbstractType<T>(constructor_argument) : return


## Directive | directive
https://angular.io/api/core/Directive

Decorator that marks a class as an Angular directive. You can define your own directives to attach custom behavior to elements in the DOM.

Option	| Description
--------|--------------
selector |	The CSS selector that identifies this directive in a template and triggers instantiation of the directive.

inputs	| Enumerates the set of data-bound input properties for a directive

outputs	| Enumerates the set of event-bound output properties.

providers |	Configures the injector of this directive or component with a token that maps to a provider of a dependency.

exportAs | Defines the name that can be used in the template to assign this directive to a variable.

queries	| Configures the queries that will be injected into the directive.

host | Maps class properties to host element bindings for properties, attributes, and events, using a set of key-value pairs.

jit	| If true, this directive/component will be skipped by the AOT compiler and so will always be compiled using JIT.

## AbstractControl | class
https://angular.io/api/forms/AbstractControl

This is the base class for FormControl, FormGroup, and FormArray.

    abstract class AbstractControl {
        constructor(validator: ValidatorFn, asyncValidator: AsyncValidatorFn)
        value: any
        validator: ValidatorFn | null
        asyncValidator: AsyncValidatorFn | null
        parent: FormGroup | FormArray
        status: string
        valid: boolean
        invalid: boolean
        pending: boolean
        disabled: boolean
        enabled: boolean
        errors: ValidationErrors | null
        pristine: boolean
        dirty: boolean
        touched: boolean
        untouched: boolean
        valueChanges: Observable<any>
        statusChanges: Observable<any>
        updateOn: FormHooks
        root: AbstractControl
        setValidators(newValidator: ValidatorFn | ValidatorFn[]): void
        setAsyncValidators(newValidator: AsyncValidatorFn | AsyncValidatorFn[]): void
        clearValidators(): void
        clearAsyncValidators(): void
        markAsTouched(opts: { onlySelf?: boolean; } = {}): void
        markAllAsTouched(): void
        markAsUntouched(opts: { onlySelf?: boolean; } = {}): void
        markAsDirty(opts: { onlySelf?: boolean; } = {}): void
        markAsPristine(opts: { onlySelf?: boolean; } = {}): void
        markAsPending(opts: { onlySelf?: boolean; emitEvent?: boolean; } = {}): void
        disable(opts: { onlySelf?: boolean; emitEvent?: boolean; } = {}): void
        enable(opts: { onlySelf?: boolean; emitEvent?: boolean; } = {}): void
        setParent(parent: FormGroup | FormArray): void
        abstract setValue(value: any, options?: Object): void
        abstract patchValue(value: any, options?: Object): void
        abstract reset(value?: any, options?: Object): void
        updateValueAndValidity(opts: { onlySelf?: boolean; emitEvent?: boolean; } = {}): void
        setErrors(errors: ValidationErrors, opts: { emitEvent?: boolean; } = {}): void
        get(path: string | (string | number)[]): AbstractControl | null
        getError(errorCode: string, path?: string | (string | number)[]): any
        hasError(errorCode: string, path?: string | (string | number)[]): boolean
    }

## Directive | decorator
https://angular.io/api/core/Directive

Decorator that marks a class as an Angular directive. You can define your own directives to attach custom behavior to elements in the DOM.

## forwardRef | fucntion
https://angular.io/api/core/forwardRef

Allows to refer to references which are not yet defined.

## catchError | function
https://rxjs-dev.firebaseapp.com/api/operators/catchError

Catches errors on the observable to be handled by returning a new observable or throwing an error.
    
    catchError<T, O extends ObservableInput<any>>(selector: (err: any, caught: Observable<T>) => O): OperatorFunction<T, T | ObservedValueOf<O>>

## map | function
https://rxjs-dev.firebaseapp.com/api/operators/map

Applies a given project function to each value emitted by the source Observable, and emits the resulting values as an Observable.

    map<T, R>(project: (value: T, index: number) => R, thisArg?: any): OperatorFunction<T, R>

## 