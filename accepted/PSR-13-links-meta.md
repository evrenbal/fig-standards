# Link Definition Meta Document

## 1. Summary

Hypermedia links are becoming an increasingly important part of the web, in both HTML contexts
and various API format contexts. However, there is no single common hypermedia format, nor
is there a common way to represent Links between formats.

This specification aims to provide PHP developers with a simple, common way of representing a
hypermedia link independently of the serialization format that is used. That in turn allows
a system to serialize a response with hypermedia links into one or more wire formats independently
of the process of deciding what those links should be.

## 2. Scope

### 2.1 Goals

* This specification aims to extract and standardize hypermedia link representation between different
formats.

### 2.2 Non-Goals

* This specification does not seek to standardize or favor any particular hypermedia serialization format.

## 3. Design Decisions

### Why no mutator methods?

One of the key targets for this specification is PSR-7 Response objects.  Response objects by design must be
immutable.  Other value-object implementations likely would also require an immutable interface.

Additionally, some Link Provider objects may not be value objects but other objects within a given
domain, which are able to generate Links on the fly, perhaps off of a database result or other underlying
representation.  In those cases a writeable provider definition would be incompatible.

Therefore, this specification splits accessor methods and evolvable methods into separate interfaces,
allowing objects to implement just the read-only or evolvable versions as appropriate to their use case.

### Why is rel on a Link object multi-value?

Different hypermedia standards handle multiple links with the same relationship differently. Some have a single
link that has multiple rel's defined. Others have a single rel entry that then contains multiple links.

Defining each Link uniquely but allowing it to have multiple rels provides a most-compatible-denominator definition.
A single LinkInterface object may be serialized to one or more link entries in a given hypermedia format, as
appropriate.  However, specifying multiple link objects each with a single rel yet the same URI is also legal, and
a hypermedia format can serialize that as appropriate, too.

### Why is a LinkProviderInterface needed?

In many contexts, a set of links will be attached to some other object.  Those objects may be used in situations
where all that is relevant is their links, or some subset of their links. For example, various different value
objects may be defined that represent different REST formats such as HAL, JSON-LD, or Atom.  It may be useful
to extract those links from such an object uniformly for further processing. For instance, next/previous links
may be extracted from an object and added to a PSR-7 Response object as Link headers.  Alternatively, many links
would make sense to represent with a "preload" link relationship, which would indicate to an HTTP 2-compatible
web server that the linked resources should be streamed to a client in anticipation of a subsequent request.

All of those cases are independent of the payload or encoding of the object. By providing a common interface
to access such links, we enable generic handling of the links themselves regardless of the value object or
domain object that is producing them.

## 4. People

### 4.1 Editor(s)

* Larry Garfield

### 4.2 Sponsors

* Matthew Weier O'Phinney (coordinator)
* Marc Alexander

### 4.3 Contributors

* Evert Pot

## 5. Votes

## 6. Relevant links

* [What's in a link?](http://evertpot.com/whats-in-a-link/) by Evert Pot
* [FIG Link Working Group List](https://groups.google.com/forum/#!forum/php-fig-link)

## 7. Errata

### 7.1 Type additions

The 1.1 release of the `psr/link` package includes scalar parameter types.  The 2.0 release of the package includes return types.  This structure leverages PHP 7.2 covariance support to allow for a gradual upgrade process, but requires PHP 8.0 for type compatibility.

Implementers MAY add return types to their own packages at their discretion, provided that:

* the return types match those in the 2.0 package.
* the implementation specifies a minimum PHP version of 8.0.0 or later.

Implementers MAY add parameter types to their own packages in a new major release, either at the same time as adding return types or in a subsequent release, provided that:

* the parameter types match those in the 1.1 package.
* the implementation specifies a minimum PHP version of 8.0.0 or later.
* the implementation depends on `"psr/link": "^1.1 || ^2.0"` so as to exclude the untyped 1.0 version.

Implementers are encouraged but not required to transition their packages toward the 2.0 version of the package at their earliest convenience.

### 7.2 Attribute type handling

The original specification contained an inconsistency regarding array values for attributes.  The text of the specification states in section 1.2 that attribute values (as passed to `EvolvableLinkInterface::withAttribute()`) could be of multiple types, some of which allowed for special handling (such as booleans or arrays).  However, the docblock for that method specified that the `$value` parameter had to be a string, which was incorrect.

To address this issue, the interface has been corrected in later releases to allow `$value` to be of type `string|\Stringable|int|float|bool|array`.  Implementers SHOULD treat a `Stringable` object the same as a `string` parameter.  Implementers MAY serialize `int`, `float`, or `bool` in alternate, type-aware ways for a particular serialization format as appropriate.  Other object types or resources remain disallowed.

Multiple calls to `withAttribute()` with the same `$name` MUST override previously provided values, as the spec already states.  To provide multiple values to a particular attribute, pass an `array` with the desired values.

All other guidelines and requirements in section 1.2 remain valid.
