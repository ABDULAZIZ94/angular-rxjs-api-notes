## Create an AppRouting module in the /app folder to contain the routing configuration
## The routing module is helpful as your app growns and when the configuration includes specialized guard and resolver services.
    ng generate module app-routing --module app --flat

## create heroes module with routing in heroes folderand register it with root app
    ng generate module heroes/heroes --module app --flat --routing

## observale parammap allow router reuse the same intance of a component by only change its parameter.
## snapshot alternatively, only use this approach if there's a possibility that the router could re-use the component

## create crisis-center component
    ng generate component crisis-center/crisis-center

# useful api documentation
## Angular
https://angular.io/api

## rxjs
#rxjs api
https://rxjs-dev.firebaseapp.com/api

https://angular.io/guide/rx-library

--------------------------------------------------------------------------------------------------------

## Observable
https://rxjs-dev.firebaseapp.com/guide/observable

Observables are lazy Push collections of multiple values. They fill the missing spot in the following table:
 x | Single | Multiple
---|--------|---------------
Pull | Function | Iterator
Push | Promise | Observable

- [x] Observables are like functions with zero arguments, but generalize those to allow multiple values.
- [x] Subscribing to an Observable is analogous to calling a Function.
- [x] Observables are able to deliver values either synchronously or asynchronously.
- [x] Observables can be created with new Observable. Most commonly, observables are created using creation functions, like of, from, interval, etc.

Core Observable concerns:

* Creating Observables
* Subscribing to Observables
    const subscription = observable.subscribe(x => console.log(x));
* Executing the Observable
 - There are three types of values an Observable Execution can deliver:
    - "Next" notification: sends a value such as a Number, a String, an Object, etc.
    - "Error" notification: sends a JavaScript Error or exception.
    - "Complete" notification: does not send a value.
#
    next*(error|complete)?
* Disposing Observables.
#
    import { from } from 'rxjs';

    const observable = from([10, 20, 30]);
    const subscription = observable.subscribe(x => console.log(x));
    // Later:
    subscription.unsubscribe();

## from
https://rxjs-dev.firebaseapp.com/api/index/function/from

Creates an Observable from an Array, an array-like object, a Promise, an iterable object, or an Observable-like object.

    from<T>(input: any, scheduler?: SchedulerLike): Observable<T>

## of
https://rxjs-dev.firebaseapp.com/api/index/function/of

Converts the arguments to an observable sequence.

    of<T>(...args: (SchedulerLike | T)[]): Observable<T>

## Params
https://angular.io/api/router/Params


## A collection of matrix and query URL parameters.

    type Params = {
        [key: string]: any;
    };


## ParamMap
https://angular.io/api/router/ParamMap

A map that provides access to the required and optional parameters specific to a route. The map supports retrieving a single value with get() or multiple values with getAll().

    interface ParamMap {
        keys: string[]
        has(name: string): boolean
        get(name: string): string | null
        getAll(name: string): string[]
    }

## switchMap
https://rxjs-dev.firebaseapp.com/api/operators/switchMap

Projects each source value to an Observable which is merged in the output Observable, emitting values only from the most recently projected Observable.

    switchMap<T, R, O extends ObservableInput<any>>
    (project: (value: T, index: number) => O, resultSelector?: (outerValue: T, innerValue: ObservedValueOf<O>, outerIndex: number, innerIndex: number) => R): OperatorFunction<T, ObservedValueOf<O> | R>


## EMPTY
https://rxjs-dev.firebaseapp.com/api/index/const/EMPTY

The same Observable instance returned by any call to empty without a scheduler. It is preferrable to use this over empty().

    const EMPTY: any;

## mergeMap
https://rxjs-dev.firebaseapp.com/api/operators/mergeMap

Projects each source value to an Observable which is merged in the output Observable

    mergeMap<T, R, O extends ObservableInput<any>>(project: (value: T, index: number) => O, resultSelector?: number | ((outerValue: T, innerValue: ObservedValueOf<O>, outerIndex: number, innerIndex: number) => R), concurrent: number = Number.POSITIVE_INFINITY): OperatorFunction<T, ObservedValueOf<O> | R>

## take
https://rxjs-dev.firebaseapp.com/api/operators/take

Emits only the first count values emitted by the source Observable.

    take<T>(count: number): MonoTypeOperatorFunction<T>

## tap
https://rxjs-dev.firebaseapp.com/api/operators/tap

Perform a side effect for every emission on the source Observable, but return an Observable that is identical to the source.

    tap<T>(nextOrObserver?: NextObserver<T> | ErrorObserver<T> | CompletionObserver<T> | ((x: T) => void), error?: (e: any) => void, complete?: () => void): MonoTypeOperatorFunction<T>

## delay
https://rxjs-dev.firebaseapp.com/api/operators/delay

Delays the emission of items from the source Observable by a given timeout or until a given Date.

delay<T>(delay: number | Date, scheduler: SchedulerLike = async): MonoTypeOperatorFunction<T>

## BehaviorSubject
https://rxjs-dev.firebaseapp.com/api/index/class/BehaviorSubject

A variant of Subject that requires an initial value and emits its current value whenever it is subscribed to.

    class BehaviorSubject<T> extends Subject {
        constructor(_value: T)
        get value: T
        _subscribe(subscriber: Subscriber<T>): Subscription
        getValue(): T
        next(value: T): void
        
        // inherited from index/Subject
        static create: Function
        constructor()
        observers: Observer<T>[]
        closed: false
        isStopped: false
        hasError: false
        thrownError: any
        lift<R>(operator: Operator<T, R>): Observable<R>
        next(value?: T)
        error(err: any)
        complete()
        unsubscribe()
        _trySubscribe(subscriber: Subscriber<T>): TeardownLogic
        _subscribe(subscriber: Subscriber<T>): Subscription
        asObservable(): Observable<T>
        
        // inherited from index/Observable
        static create: Function
        static if: typeof iif
        static throw: typeof throwError
        constructor(subscribe?: (this: Observable<T>, subscriber: Subscriber<T>) => TeardownLogic)
        _isScalar: boolean
        source: Observable<any>
        operator: Operator<any, T>
        lift<R>(operator: Operator<T, R>): Observable<R>
        subscribe(observerOrNext?: NextObserver<T> | ErrorObserver<T> | CompletionObserver<T> | ((value: T) => void), error?: (error: any) => void, complete?: () => void): Subscription
        _trySubscribe(sink: Subscriber<T>): TeardownLogic
        forEach(next: (value: T) => void, promiseCtor?: PromiseConstructorLike): Promise<void>
        pipe(...operations: OperatorFunction<any, any>[]): Observable<any>
        toPromise(promiseCtor?: PromiseConstructorLike): Promise<T>
    }

--------------------------------------------------------------------------------------------------------

## ActivatedRoute
https://angular.io/api/router/ActivatedRoute

Provides access to information about a route associated with a component that is loaded in an outlet. Use to traverse the RouterState tree and extract information from nodes.

    interface ActivatedRoute {
        snapshot: ActivatedRouteSnapshot
        url: Observable<UrlSegment[]>
        params: Observable<Params>
        queryParams: Observable<Params>
        fragment: Observable<string>
        data: Observable<Data>
        outlet: string
        component: Type<any> | string | null
        routeConfig: Route | null
        root: ActivatedRoute
        parent: ActivatedRoute | null
        firstChild: ActivatedRoute | null
        children: ActivatedRoute[]
        pathFromRoot: ActivatedRoute[]
        paramMap: Observable<ParamMap>
        queryParamMap: Observable<ParamMap>
        toString(): string
    }

## pipe()
https://angular.io/guide/rx-library#operators

You can use pipes to link operators together. Pipes let you combine multiple functions into a single function. The pipe() function takes as its arguments the functions you want to combine, and returns a new function that, when executed, runs the composed functions in sequence.

https://rxjs-dev.firebaseapp.com/guide/operators

A Pipeable Operator is a function that takes an Observable as its input and returns another Observable. It is a pure operation: the previous Observable stays unmodified.

stand alone pipe()

    import { filter, map } from 'rxjs/operators';

    const nums = of(1, 2, 3, 4, 5);

    // Create a function that accepts an Observable.
    const squareOddVals = pipe(
    filter((n: number) => n % 2 !== 0),
    map(n => n * n)
    );

    // Create an Observable that will run the filter and map functions
    const squareOdd = squareOddVals(nums);

    // Subscribe to run the combined functions
    squareOdd.subscribe(x => console.log(x));

observable pipe()

    import { filter, map } from 'rxjs/operators';

    const squareOdd = of(1, 2, 3, 4, 5)
    .pipe(
        filter(n => n % 2 !== 0),
        map(n => n * n)
    );

    // Subscribe to get values
    squareOdd.subscribe(x => console.log(x));

## Router
https://angular.io/api/router/Router

A service that provides navigation and URL manipulation capabilities.

    class Router {
        constructor(rootComponentType: Type<any>, urlSerializer: UrlSerializer, rootContexts: ChildrenOutletContexts, location: Location, injector: Injector, loader: NgModuleFactoryLoader, compiler: Compiler, config: Routes)
        events: Observable<Event>
        routerState: RouterState
        errorHandler: ErrorHandler
        malformedUriErrorHandler: (error: URIError, urlSerializer: UrlSerializer, url: string) => UrlTree
        navigated: boolean
        urlHandlingStrategy: UrlHandlingStrategy
        routeReuseStrategy: RouteReuseStrategy
        onSameUrlNavigation: 'reload' | 'ignore'
        paramsInheritanceStrategy: 'emptyOnly' | 'always'
        urlUpdateStrategy: 'deferred' | 'eager'
        relativeLinkResolution: 'legacy' | 'corrected'
        config: Routes
        url: string
        initialNavigation(): void
        setUpLocationChangeListener(): void
        getCurrentNavigation(): Navigation | null
        resetConfig(config: Routes): void
        ngOnDestroy(): void
        dispose(): void
        createUrlTree(commands: any[], navigationExtras: NavigationExtras = {}): UrlTree
        navigateByUrl(url: string | UrlTree, extras: NavigationExtras = { skipLocationChange: false }): Promise<boolean>
        navigate(commands: any[], extras: NavigationExtras = { skipLocationChange: false }): Promise<boolean>
        serializeUrl(url: UrlTree): string
        parseUrl(url: string): UrlTree
        isActive(url: string | UrlTree, exact: boolean): boolean
    }

## Routes
https://angular.io/api/router/Routes

Represents a route configuration for the Router service. An array of Route objects, used in Router.config and for nested route configurations in Route.children.

    type Routes = Route[];

## @Injectable
https://angular.io/api/core/Injectable

Decorator that marks a class as available to be provided and injected as a dependency.

Options | Descriptions
--------|--------------
providedIn | Determines which injectors will provide the injectable, by either associating it with an @NgModule or other InjectorType, or by specifying that 

providedIn

    providedIn: Type<any> | 'root' | 'platform' | 'any' | null

This injectable should be provided in one of the following injectors: 
* 'root' : The application-level injector in most apps. 
* 'platform' : A special singleton platform injector shared by all applications on the page. 
* 'any' : Provides a unique instance in every module (including lazy modules) that injects the token.

## CanActivate
https://angular.io/api/router/CanActivate

Interface that a class can implement to be a guard deciding if a route can be activated. If all guards return true, navigation will continue. If any guard returns false, navigation will be cancelled. If any guard returns a UrlTree, current navigation will be cancelled and a new navigation will be kicked off to the UrlTree returned from the guard.

    interface CanActivate {
        canActivate(route: ActivatedRouteSnapshot, state: RouterStateSnapshot): Observable<boolean | UrlTree> | Promise<boolean | UrlTree> | boolean | UrlTree
    }

## CanActivateChild
https://angular.io/api/router/CanActivateChild

Interface that a class can implement to be a guard deciding if a child route can be activated. If all guards return true, navigation will continue. If any guard returns false, navigation will be cancelled. If any guard returns a UrlTree, current navigation will be cancelled and a new navigation will be kicked off to the UrlTree returned from the guard.

    interface CanActivateChild {
        canActivateChild(childRoute: ActivatedRouteSnapshot, state: RouterStateSnapshot):       Observable<boolean | UrlTree> | Promise<boolean | UrlTree> | boolean | UrlTree
    }

## CanDeactivate
https://angular.io/api/router/CanDeactivate

Interface that a class can implement to be a guard deciding if a route can be deactivated. If all guards return true, navigation will continue. If any guard returns false, navigation will be cancelled. If any guard returns a UrlTree, current navigation will be cancelled and a new navigation will be kicked off to the UrlTree returned from the guard.

    interface CanDeactivate<T> {
        canDeactivate(component: T, currentRoute: ActivatedRouteSnapshot, currentState: RouterStateSnapshot, nextState?: RouterStateSnapshot): Observable<boolean | UrlTree> | Promise<boolean | UrlTree> | boolean | UrlTree
    }

## CanLoad
Interface that a class can implement to be a guard deciding if children can be loaded.

    interface CanLoad {
        canLoad(route: Route, segments: UrlSegment[]): Observable<boolean> | Promise<boolean> | boolean
    }

## ActivatedRouteSnapshot
https://angular.io/api/router/ActivatedRouteSnapshot

Contains the information about a route associated with a component loaded in an outlet at a particular moment in time. ActivatedRouteSnapshot can also be used to traverse the router state tree

    interface ActivatedRouteSnapshot {
        routeConfig: Route | null
        url: UrlSegment[]
        params: Params
        queryParams: Params
        fragment: string
        data: Data
        outlet: string
        component: Type<any> | string | null
        root: ActivatedRouteSnapshot
        parent: ActivatedRouteSnapshot | null
        firstChild: ActivatedRouteSnapshot | null
        children: ActivatedRouteSnapshot[]
        pathFromRoot: ActivatedRouteSnapshot[]
        paramMap: ParamMap
        queryParamMap: ParamMap
        toString(): string
    }

## RouterStateSnapshot
https://angular.io/api/router/RouterStateSnapshot

Represents the state of the router at a moment in time.

    interface RouterStateSnapshot extends Tree {
        url: string
        toString(): string
    }

## NavigationExtras
https://angular.io/api/router/NavigationExtras

Options that modify the navigation strategy.

    interface NavigationExtras {
        relativeTo?: ActivatedRoute | null
        queryParams?: Params | null
        fragment?: string
        preserveQueryParams?: boolean
        queryParamsHandling?: QueryParamsHandling | null
        preserveFragment?: boolean
        skipLocationChange?: boolean
        replaceUrl?: boolean
        state?: {...}
    }

## PreloadingStrategy
https://angular.io/api/router/PreloadingStrategy

Provides a preloading strategy.

    abstract class PreloadingStrategy {
        abstract preload(route: Route, fn: () => Observable<any>): Observable<any>
    }

