---
title: Ports and Adapters

---
# Ports and Adapters

A reminder that codebases are not nails. Patterns are not hammers.

## What's the point?

The Ports and Adapters pattern is for when you want to keep the core of your application clean from external concepts.

If some external interface updates, you don't want to be diving through the core of your application to fix it. If we have to change the API to return `business_number` rather than `ABN` then we should be able to just change the adapter, not the entire database.

It also makes testing easier, since you should be able to test the interior without a heavy reliance on mocks. Your adapters can be tested in isolation.

## Ports vs Adapters

A port is an interface to the core

A primary port is something an upstream service calls to interact with the core.

A secondary port is something the core calls to interact with a downstream service.

An adapter is a "thing" that implements the interface, be it a function, a code block, a class.

* In 3 tier architecture, controllers and repositories are BOTH adapters

## Primary Port and Adapter Example

This CONTROLLER adapts to the world of the core. 

    AccountController {
        private as: AccountService;

        constructor(as: AccountService) {
            this.as = as;
        }

        function createAccount({ name }: AccountDTO) {
            account = new Account(name);
            as.createAccount(account);
        }
    }


A `DTO` is a representation of some external object.

And you'd probably have the `AccountService` interface as the type there.

You could have a mapper to create a `Account` from an `AccountDTO` and that would live with the adapter.

## Secondary Port and Adapter Example

    AccountApi implements AccountRepository {
        function updateAccount({ name }: Account) {
            subAccount = new SubscriptionAccount(name);
            response = got.get(apiUrl, subAccount);
        }
    }
    
## Keeping the Core Clean

You can do some things in certain languages to protect your core. For example you could make your DTO entities protected, so that the core literally can't access them.

## Inversion of Dependency

Don't create an interface for your core to implement. Create an interface for your core, and then have your adapter implement that.

## Questions

How does this work in the other direction? What if the core needs other information?