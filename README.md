<div rel="foaf:primaryTopic" resource="#" typeof="owl:Ontology">

Author  
<a href="http://doriantaylor.com/person/dorian-taylor#me"
rel="dct:creator" typeof="foaf:Person"><span property="foaf:name">Dorian
Taylor</span></a>

Created  
September 6, 2023

Namespace URI  
[`https://vocab.methodandstructure.com/intertwingler#`](https://vocab.methodandstructure.com/intertwingler#)

Preferred Namespace Prefix  
`itcv`

This document specifies the on-line configuration vocabulary for
<a href="https://intertwingler.net/" rel="dct:subject">Intertwingler</a>,
a <span class="dfn">dense hypermedia</span> engine.

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

Properties:  
<a href="https://vocab.methodandstructure.com/intertwingler#queue"
rev="rdfs:domain"><code>itcv:queue</code></a>

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
<a href="https://vocab.methodandstructure.com/intertwingler#handler"
rev="rdfs:domain"><code>itcv:handler</code></a>

<a
href="https://vocab.methodandstructure.com/intertwingler#handler-list"
rev="rdfs:domain"><code>itcv:handler-list</code></a>

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

<a href="https://vocab.methodandstructure.com/intertwingler#"
rel="rdfs:isDefinedBy">Back to Top</a>

</div>

</div>

<div class="section">

## Properties

<div class="section">

### Bundling Handlers

<div id="queue" class="section" about="[itcv:queue]"
typeof="owl:ObjectProperty owl:FunctionalProperty">

#### `queue`

The queue head is the entry point for the <span
class="dfn">transform</span> queue associated with the `itcv:Handler`,
or the default queue associated with the `itcv:Engine`. There should be
exactly *one*.

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
