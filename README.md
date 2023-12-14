<div rel="foaf:primaryTopic" resource="#" typeof="owl:Ontology">

Author  
<a href="http://doriantaylor.com/person/dorian-taylor#me"
rel="dct:creator" typeof="foaf:Person"><span property="foaf:name">Dorian
Taylor</span></a>

Created  
September 6, 2023

Updated  
October 9, 2023

October 29, 2023

November 18, 2023

Namespace URI  
[`https://vocab.methodandstructure.com/intertwingler#`](https://vocab.methodandstructure.com/intertwingler#)

Preferred Namespace Prefix  
`itcv`

This document specifies the on-line configuration vocabulary for
<a href="https://intertwingler.net/" rel="dct:subject">Intertwingler</a>,
a <span class="dfn">dense hypermedia</span> engine.

This ontology works in conjunction with the
<a href="https://vocab.methodandstructure.com/transformation#"
rel="owl:imports"><span property="dct:title">Transformation Functions
Ontology</span></a> to organize handlers and transforms for
<a href="https://intertwingler.net/"
rel="dct:subject"><code>Intertwingler</code></a>.

</div>

<div class="section">

## Classes

![](https://vocab.methodandstructure.com/intertwingler-classes)

<div id="Handler" class="section" about="[itcv:Handler]"
typeof="owl:Class">

### `Handler`

An `itcv:Handler` is the basic unit of functionality in Intertwingler.
Handlers are <span class="dfn">microservices</span> that serve one or
more URIs via one or more HTTP request methods.

Subclass of:  
<a href="https://vocab.methodandstructure.com/transformation#Bundle"
rel="rdfs:subClassOf"><code>tfo:Bundle</code></a>

Properties:  
<a href="https://vocab.methodandstructure.com/intertwingler#queue"
rev="rdfs:domain"><code>itcv:queue</code></a>

<a
href="https://vocab.methodandstructure.com/intertwingler#response-queue"
rev="rdfs:domain"><code>itcv:response-queue</code></a>

<a href="https://vocab.methodandstructure.com/intertwingler#"
rel="rdfs:isDefinedBy">Back to Top</a>

</div>

<div id="Engine" class="section" about="[itcv:Engine]"
typeof="owl:Class">

### `Engine`

An `itcv:Engine` is *the* (as in the only one per instance) specialized
`itcv:Handler` that is responsible for marshalling all other handlers
and transforms.

Subclass of:  
<a href="https://vocab.methodandstructure.com/intertwingler#Handler"
rel="rdfs:subClassOf"><code>itcv:Handler</code></a>

Properties:  
<a href="https://vocab.methodandstructure.com/intertwingler#resolver"
rev="rdfs:domain"><code>itcv:resolver</code></a>

<a href="https://vocab.methodandstructure.com/intertwingler#handler"
rev="rdfs:domain"><code>itcv:handler</code></a>

<a
href="https://vocab.methodandstructure.com/intertwingler#handler-list"
rev="rdfs:domain"><code>itcv:handler-list</code></a>

<a
href="https://vocab.methodandstructure.com/intertwingler#request-queue"
rev="rdfs:domain"><code>itcv:request-queue</code></a>

<a href="https://vocab.methodandstructure.com/intertwingler#"
rel="rdfs:isDefinedBy">Back to Top</a>

</div>

<div id="Transform" class="section" about="[itcv:Transform]"
typeof="owl:Class">

### `Transform`

An `itcv:Transform` is a special-purpose `itcv:Handler` that
encapsulates a set of *actual* transformation functions, identified by
their URIs, that interact via HTTP `POST`.

The `itcv:Transform` class is different from the `tfo:Transform` insofar
as the former is a *handler*, a potentially stand-alone <span
class="dfn">microservice</span> that bundles together a set of
individual service <span class="dfn">endpoints</span>, while the latter
describes the individual service endpoints themselves.

Subclass of:  
<a href="https://vocab.methodandstructure.com/intertwingler#Handler"
rel="rdfs:subClassOf"><code>itcv:Handler</code></a>

See also:  
<a href="https://vocab.methodandstructure.com/transformation#Transform"
rel="rdfs:seeAlso"><code>tfo:Transform</code></a>

<a href="https://vocab.methodandstructure.com/intertwingler#"
rel="rdfs:isDefinedBy">Back to Top</a>

</div>

<div id="HandlerList" class="section" about="[itcv:HandlerList]"
typeof="owl:Class">

### `HandlerList`

An `itcv:HandlerList` is a list of handlers and only handlers.

Subclass of:  
<a href="https://www.w3.org/TR/rdf-schema/#ch_list"
rel="rdfs:subClassOf" resource="rdf:List"><code>rdf:List</code></a>

Property restrictions:  
<a href="https://www.w3.org/TR/rdf-schema/#ch_first"
rel="owl:onProperty" resource="rdf:first"><code>rdf:first</code></a> ∈
<a href="https://vocab.methodandstructure.com/intertwingler#Handler"
rel="owl:allValuesFrom"><code>itcv:Handler</code></a>

<a href="https://www.w3.org/TR/rdf-schema/#ch_rest" rel="owl:onProperty"
resource="rdf:rest"><code>rdf:rest</code></a> ∈ <span
rel="owl:allValuesFrom" resource="_:uo1"> <span rel="owl:unionOf"
resource="_:q1">(<a href="https://vocab.methodandstructure.com/intertwingler#HandlerList"
rel="rdf:first"><code>itcv:HandlerList</code></a> <span about="_:q1"
rel="rdf:rest" resource="_:q2">∪</span> <span about="_:q2"
rel="rdf:first"
resource="_:hv1">{<a href="https://www.w3.org/TR/rdf-schema/#ch_nil" rel="owl:hasValue"
resource="rdf:nil"><code>rdf:nil</code></a>}<span about="_:q2"
rel="rdf:rest" resource="rdf:nil">)</span></span> </span> </span>

<a href="https://vocab.methodandstructure.com/intertwingler#"
rel="rdfs:isDefinedBy">Back to Top</a>

</div>

<div id="Resolver" class="section" about="[itcv:Resolver]"
typeof="owl:Class">

### `Resolver`

An `itcv:Engine` has an `itcv:Resolver` for each website under its
management. Resolvers map the dereferenceable—yet *perishable*—Web
addresses to more durable identifiers like UUIDs and cryptographic
hashes, as well as determine how to treat certain classes of resource,
i.e., whether “sovereign” document or fragment thereof.

Properties:  
<a href="https://vocab.methodandstructure.com/intertwingler#manages"
rev="rdfs:domain"><code>itcv:manages</code></a>

<a href="https://vocab.methodandstructure.com/intertwingler#prefix"
rev="rdfs:domain"><code>itcv:prefix</code></a>

<a href="https://vocab.methodandstructure.com/intertwingler#document"
rev="rdfs:domain"><code>itcv:document</code></a>

<a href="https://vocab.methodandstructure.com/intertwingler#fragment"
rev="rdfs:domain"><code>itcv:fragment</code></a>

<a href="https://vocab.methodandstructure.com/intertwingler#"
rel="rdfs:isDefinedBy">Back to Top</a>

</div>

<div id="FragmentList" class="section" about="[itcv:FragmentList]"
typeof="owl:Class">

### `FragmentList`

An `itcv:FragmentList` is a list of fragments and only fragments.

Subclass of:  
<a href="https://www.w3.org/TR/rdf-schema/#ch_list"
rel="rdfs:subClassOf" resource="rdf:List"><code>rdf:List</code></a>

Property restrictions:  
<a href="https://www.w3.org/TR/rdf-schema/#ch_rest" rel="owl:onProperty"
resource="rdf:rest"><code>rdf:rest</code></a> ∈ <span
rel="owl:allValuesFrom" resource="_:EDH1Pu2CLR0UcP3ruqS0WJ"> <span
rel="owl:unionOf" resource="_:EFNairIJBEcuyeqMUhxNSI">(<a
href="https://vocab.methodandstructure.com/intertwingler#FragmentList"
rel="rdf:first"><code>itcv:FragmentList</code></a> <span
about="_:EFNairIJBEcuyeqMUhxNSI" rel="rdf:rest"
resource="_:EcsJIlAboV0u-cVjx_cxSK">∪</span> <span
about="_:EcsJIlAboV0u-cVjx_cxSK" rel="rdf:first"
resource="_:EokiswwNRR4Nqyww5XrRsL">{<a href="https://www.w3.org/TR/rdf-schema/#ch_nil" rel="owl:hasValue"
resource="rdf:nil"><code>rdf:nil</code></a>}<span
about="_:EcsJIlAboV0u-cVjx_cxSK" rel="rdf:rest"
resource="rdf:nil">)</span></span> </span> </span>

<a href="https://vocab.methodandstructure.com/intertwingler#"
rel="rdfs:isDefinedBy">Back to Top</a>

</div>

<div id="FragmentSpecifier" class="section"
about="[itcv:FragmentSpecifier]" typeof="owl:Class">

### `FragmentSpecifier`

A fragment specifier tells a resolver to treat a particular class of
resource as a document *fragment*, rather than a full document, as well
how to relate said fragment to a host document.

Properties:  
<a
href="https://vocab.methodandstructure.com/intertwingler#fragment-class"
rev="rdfs:domain"><code>itcv:fragment-class</code></a>

<a href="https://vocab.methodandstructure.com/intertwingler#host-class"
rev="rdfs:domain"><code>itcv:host-class</code></a>

<a
href="https://vocab.methodandstructure.com/intertwingler#except-class"
rev="rdfs:domain"><code>itcv:except-class</code></a>

<a href="https://vocab.methodandstructure.com/intertwingler#via"
rev="rdfs:domain"><code>itcv:via</code></a>

<a href="https://vocab.methodandstructure.com/intertwingler#supersedes"
rev="rdfs:domain"><code>itcv:supersedes</code></a>

<a href="https://vocab.methodandstructure.com/intertwingler#"
rel="rdfs:isDefinedBy">Back to Top</a>

</div>

</div>

<div class="section">

## Properties

![](https://vocab.methodandstructure.com/intertwingler-properties)

<div class="section">

### Describing Resolvers

At the core of the `Intertwingler` engine is at least one resolver that
maps HTTP(S) URIs to more durable underlying identifiers. The resolver
also manages prefix mappings for namespaces, as well as a mapping of RDF
classes to entire documents versus fragment identifiers.

<div id="resolver" class="section" about="[itcv:resolver]"
typeof="owl:ObjectProperty">

#### `resolver`

This property maps the `itcv:Engine` to an `itcv:Resolver`.

Domain:  
<a href="https://vocab.methodandstructure.com/intertwingler#Engine"
rel="rdfs:domain"><code>itcv:Engine</code></a>

Domain:  
<a href="https://vocab.methodandstructure.com/intertwingler#Resolver"
rel="rdfs:domain"><code>itcv:Resolver</code></a>

<a href="https://vocab.methodandstructure.com/intertwingler#"
rel="rdfs:isDefinedBy">Back to Top</a>

</div>

<div id="manages" class="section" about="[itcv:manages]"
typeof="owl:ObjectProperty owl:FunctionalProperty">

#### `manages`

Denotes the base URI under management from this resolver.

Domain:  
<a href="https://vocab.methodandstructure.com/intertwingler#Resolver"
rel="rdfs:domain"><code>itcv:Resolver</code></a>

<a href="https://vocab.methodandstructure.com/intertwingler#"
rel="rdfs:isDefinedBy">Back to Top</a>

</div>

<div id="alias" class="section" about="[itcv:alias]"
typeof="owl:ObjectProperty owl:FunctionalProperty">

#### `alias`

Denotes, ultimately, an HTTP `Host:` header that is an acceptable
substitute for the authority under management.

Domain:  
<a href="https://vocab.methodandstructure.com/intertwingler#Resolver"
rel="rdfs:domain"><code>itcv:Resolver</code></a>

<a href="https://vocab.methodandstructure.com/intertwingler#"
rel="rdfs:isDefinedBy">Back to Top</a>

</div>

<div id="prefix" class="section" about="[itcv:prefix]"
typeof="owl:ObjectProperty">

#### `prefix`

This is a prefix declaration borrowed from SHACL.

Domain:  
<a href="https://vocab.methodandstructure.com/intertwingler#Resolver"
rel="rdfs:domain"><code>itcv:Resolver</code></a>

Range:  
<a href="https://www.w3.org/TR/shacl/#sparql-prefixes" rel="rdfs:range"
resource="sh:PrefixDeclaration"><code>sh:PrefixDeclaration</code></a>

<a href="https://vocab.methodandstructure.com/intertwingler#"
rel="rdfs:isDefinedBy">Back to Top</a>

</div>

<div id="vocab" class="section" about="[itcv:vocab]"
typeof="owl:DatatypeProperty owl:FunctionalProperty">

#### `vocab`

Defines the null prefix vocabulary, e.g. for use with RDFa.

Domain:  
<a href="https://vocab.methodandstructure.com/intertwingler#Resolver"
rel="rdfs:domain"><code>itcv:Resolver</code></a>

Range:  
<a href="https://www.w3.org/TR/xmlschema-2/#anyURI" rel="rdfs:range"
resource="xsd:anyURI"><code>xsd:anyURI</code></a>

<a href="https://vocab.methodandstructure.com/intertwingler#"
rel="rdfs:isDefinedBy">Back to Top</a>

</div>

<div id="document" class="section" about="[itcv:document]"
typeof="owl:ObjectProperty">

#### `document`

Denotes a class which is always to be treated as a stand-alone document.

Domain:  
<a href="https://vocab.methodandstructure.com/intertwingler#Resolver"
rel="rdfs:domain"><code>itcv:Resolver</code></a>

Range:  
<a href="https://www.w3.org/TR/rdf-schema/#ch_class" rel="rdfs:range"
resource="rdfs:Class"><code>rdfs:Class</code></a>

<a href="https://vocab.methodandstructure.com/intertwingler#"
rel="rdfs:isDefinedBy">Back to Top</a>

</div>

<div id="fragment-spec" class="section" about="[itcv:fragment-spec]"
typeof="owl:ObjectProperty">

#### `fragment-spec`

Denotes an `itcv:FragmentSpecifier` that describes how a given class is
to be treated as a fragment of another document.

Domain:  
<a href="https://vocab.methodandstructure.com/intertwingler#Resolver"
rel="rdfs:domain"><code>itcv:Resolver</code></a>

Range:  
<a
href="https://vocab.methodandstructure.com/intertwingler#FragmentSpecifier"
rel="rdfs:range"><code>itcv:FragmentSpecifier</code></a>

<a href="https://vocab.methodandstructure.com/intertwingler#"
rel="rdfs:isDefinedBy">Back to Top</a>

</div>

<div id="fragment-list" class="section" about="[itcv:fragment-list]"
typeof="owl:ObjectProperty">

#### `fragment-list`

Denotes an ordered list of `itcv:FragmentSpecifier`s that describes how
a given class is to be treated as a fragment of another document.

Domain:  
<a href="https://vocab.methodandstructure.com/intertwingler#Resolver"
rel="rdfs:domain"><code>itcv:Resolver</code></a>

Range:  
<a
href="https://vocab.methodandstructure.com/intertwingler#FragmentList"
rel="rdfs:range"><code>itcv:FragmentList</code></a>

<a href="https://vocab.methodandstructure.com/intertwingler#"
rel="rdfs:isDefinedBy">Back to Top</a>

</div>

<div id="fragment" class="section" about="[itcv:fragment]"
typeof="owl:ObjectProperty">

#### `fragment`

A target class of an `itcv:FragmentSpecifier`.

Domain:  
<a
href="https://vocab.methodandstructure.com/intertwingler#FragmentSpecifier"
rel="rdfs:domain"><code>itcv:FragmentSpecifier</code></a>

Range:  
<a href="https://www.w3.org/TR/rdf-schema/#ch_class" rel="rdfs:range"
resource="rdfs:Class"><code>rdfs:Class</code></a>

<a href="https://vocab.methodandstructure.com/intertwingler#"
rel="rdfs:isDefinedBy">Back to Top</a>

</div>

<div id="host" class="section" about="[itcv:host]"
typeof="owl:ObjectProperty">

#### `host`

Specifies a class of host document.

Domain:  
<a
href="https://vocab.methodandstructure.com/intertwingler#FragmentSpecifier"
rel="rdfs:domain"><code>itcv:FragmentSpecifier</code></a>

Range:  
<a href="https://www.w3.org/TR/rdf-schema/#ch_class" rel="rdfs:range"
resource="rdfs:Class"><code>rdfs:Class</code></a>

<a href="https://vocab.methodandstructure.com/intertwingler#"
rel="rdfs:isDefinedBy">Back to Top</a>

</div>

<div id="except" class="section" about="[itcv:except]"
typeof="owl:ObjectProperty">

#### `except`

Specifies an `rdfs:Class`, e.g. a subclasswhich is explicitly *not* a
host.

Domain:  
<a
href="https://vocab.methodandstructure.com/intertwingler#FragmentSpecifier"
rel="rdfs:domain"><code>itcv:FragmentSpecifier</code></a>

Range:  
<a href="https://www.w3.org/TR/rdf-schema/#ch_class" rel="rdfs:range"
resource="rdfs:Class"><code>rdfs:Class</code></a>

<a href="https://vocab.methodandstructure.com/intertwingler#"
rel="rdfs:isDefinedBy">Back to Top</a>

</div>

<div id="via" class="section" about="[itcv:via]"
typeof="owl:ObjectProperty">

#### `via`

Specifies the relationship between a fragment and its host document.

Rather than type out a formal definition of the range of this property,
note that it is intended to be the same range as a [SHACL property
path](https://www.w3.org/TR/shacl/#property-paths) (the SHACL people
didn't formally define this either).

Domain:  
<a
href="https://vocab.methodandstructure.com/intertwingler#FragmentSpecifier"
rel="rdfs:domain"><code>itcv:FragmentSpecifier</code></a>

See also:  
<a href="https://www.w3.org/TR/shacl/#property-paths"
rel="rdfs:seeAlso">SHACL property paths</a>

<a href="https://vocab.methodandstructure.com/intertwingler#"
rel="rdfs:isDefinedBy">Back to Top</a>

</div>

<div id="supersedes" class="section" about="[itcv:supersedes]"
typeof="owl:ObjectProperty">

#### `supersedes`

Identifies a fragment specifier over which the subject is intended to
take precedence.

Domain:  
<a
href="https://vocab.methodandstructure.com/intertwingler#FragmentSpecifier"
rel="rdfs:domain"><code>itcv:FragmentSpecifier</code></a>

Range:  
<a
href="https://vocab.methodandstructure.com/intertwingler#FragmentSpecifier"
rel="rdfs:range"><code>itcv:FragmentSpecifier</code></a>

<a href="https://vocab.methodandstructure.com/intertwingler#"
rel="rdfs:isDefinedBy">Back to Top</a>

</div>

</div>

<div class="section">

### Specifying Handlers

<div id="handler" class="section" about="[itcv:handler]"
typeof="owl:ObjectProperty">

#### `handler`

This property relates a handler to the engine.

Domain:  
<a href="https://vocab.methodandstructure.com/intertwingler#Engine"
rel="rdfs:domain"><code>itcv:Engine</code></a>

Range:  
<a href="https://vocab.methodandstructure.com/intertwingler#Handler"
rel="rdfs:range"><code>itcv:Handler</code></a>

<a href="https://vocab.methodandstructure.com/intertwingler#"
rel="rdfs:isDefinedBy">Back to Top</a>

</div>

<div id="handler-list" class="section" about="[itcv:handler-list]"
typeof="owl:ObjectProperty owl:FunctionalProperty">

#### `handler-list`

This property relates an ordered list of handlers to the engine.

Domain:  
<a href="https://vocab.methodandstructure.com/intertwingler#Engine"
rel="rdfs:domain"><code>itcv:Engine</code></a>

Range:  
<a href="https://vocab.methodandstructure.com/intertwingler#HandlerList"
rel="rdfs:range"><code>itcv:HandlerList</code></a>

<a href="https://vocab.methodandstructure.com/intertwingler#"
rel="rdfs:isDefinedBy">Back to Top</a>

</div>

</div>

<div class="section">

### Selecting Transform Queues

<div id="queue" class="section" about="[itcv:queue]"
typeof="owl:ObjectProperty">

#### `queue`

This property generically relates a transform queue to a handler without
specifying what else to do with it.

Domain:  
<a href="https://vocab.methodandstructure.com/intertwingler#Handler"
rel="rdfs:domain"><code>itcv:Handler</code></a>

Range:  
<a href="https://vocab.methodandstructure.com/transformation#Queue"
rel="rdfs:range"><code>tfo:Queue</code></a>

<a href="https://vocab.methodandstructure.com/intertwingler#"
rel="rdfs:isDefinedBy">Back to Top</a>

</div>

<div id="request-queue" class="section" about="[itcv:request-queue]"
typeof="owl:ObjectProperty owl:FunctionalProperty">

#### `request-queue`

The engine, which inherits the relation `itcv:queue`, also has a queue
for *request* transforms.

Sub-property of:  
<a href="https://vocab.methodandstructure.com/intertwingler#queue"
rel="rdfs:subPropertyOf"><code>itcv:queue</code></a>

Domain:  
<a href="https://vocab.methodandstructure.com/intertwingler#Engine"
rel="rdfs:domain"><code>itcv:Engine</code></a>

Range:  
<a href="https://vocab.methodandstructure.com/transformation#Queue"
rel="rdfs:range"><code>tfo:Queue</code></a>

<a href="https://vocab.methodandstructure.com/intertwingler#"
rel="rdfs:isDefinedBy">Back to Top</a>

</div>

<div id="response-queue" class="section" about="[itcv:response-queue]"
typeof="owl:ObjectProperty owl:FunctionalProperty">

#### `response-queue`

This property denotes the entry point for the response <span
class="dfn">transform</span> queue associated with the `itcv:Handler`.
It also specifies the default queue associated with the `itcv:Engine`.

Sub-property of:  
<a href="https://vocab.methodandstructure.com/intertwingler#queue"
rel="rdfs:subPropertyOf"><code>itcv:queue</code></a>

Domain:  
<a href="https://vocab.methodandstructure.com/intertwingler#Handler"
rel="rdfs:domain"><code>itcv:Handler</code></a>

Range:  
<a href="https://vocab.methodandstructure.com/transformation#Queue"
rel="rdfs:range"><code>tfo:Queue</code></a>

<a href="https://vocab.methodandstructure.com/intertwingler#"
rel="rdfs:isDefinedBy">Back to Top</a>

</div>

</div>

</div>

<div class="section">

## References

-   <a href="https://intertwingler.net/" about="#"
    rel="foaf:primaryTopic">Intertwingler — Retrofitting the Web</a>
-   <a href="https://github.com/doriantaylor/rb-intertwingler" about="#"
    rel="dct:references">Intertwingler reference implementation</a>
-   <a href="https://vocab.methodandstructure.com/transformation#" about="#"
    rel="owl:imports">Transformation Functions Ontology</a>
-   <a href="https://www.w3.org/TR/shacl/" about="#" rel="owl:imports"
    resource="sh:">Shapes Constraint Language (SHACL)</a>

</div>
