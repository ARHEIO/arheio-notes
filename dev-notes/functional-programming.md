---
title: Functional Programming

---
# FP-TS

### `Map`

The inner function has the following signature:

`export declare const map: <A, B>(f: (a: A) => B) => (fa: IO<A>) => IO<B>`

Ignore the `IO` for the moment, what's important is the inner chunk.

`f: (a: A) => B`

When using map, it gives you the UNWRAPPED value.

And you can then RETURN THE UNWRAPPED VALUE.

    pipe(
        req.header('Authorization'),
        getAuthorizationHeader,
        E.map((encodedJwt: string) => encodedJwt.split('Bearer ')[1])
    )

Just like that

### `Chain`

The inner functions looks like this:

`export declare const chain: <A, B>(f: (a: A) => IO<B>) => (ma: IO<A>) => IO<B>`

Again, the inner chunk.

`f: (a: A) => IO<B>`

You have to return THE WRAPPED TYPE.

a