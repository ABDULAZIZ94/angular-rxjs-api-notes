# Documentation

## FormBuilder | class
https://angular.io/api/forms/FormBuilder

Creates an AbstractControl from a user-specified configuration.

    class FormBuilder {
        group(controlsConfig: { [key: string]: any; }, options: AbstractControlOptions | { [key: string]: any; } = null): FormGroup
        control(formState: any, validatorOrOpts?: ValidatorFn | AbstractControlOptions | ValidatorFn[], asyncValidator?: AsyncValidatorFn | AsyncValidatorFn[]): FormControl
        array(controlsConfig: any[], validatorOrOpts?: ValidatorFn | AbstractControlOptions | ValidatorFn[], asyncValidator?: AsyncValidatorFn | AsyncValidatorFn[]): FormArray
    }

## 