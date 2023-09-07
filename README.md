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
a dense hypermedia engine.

</div>

<div class="section">

## Classes

![](https://vocab.methodandstructure.com/intertwingler-classes)

<div id="Handler" class="section" about="[itcv:Handler]"
typeof="owl:Class">

### `Handler`

An `itcv:Handler` is the basic unit of functionality in Intertwingler.
Handlers are <span class="dfn">microservices</span> that serve one or
more URIs via one or more HTTP request metehods.

<a href="https://vocab.methodandstructure.com/intertwingler#"
rel="rdfs:isDefinedBy">Back to Top</a>

</div>

<div id="Engine" class="section" about="[itcv:Engine]"
typeof="owl:Class">

### `Engine`

An `itcv:Engine` is the (as in unitary per instance) specialized
`itcv:Handler` that is responsible for marshalling all other handlers
and transforms.

Subclass of:  
<a href="https://vocab.methodandstructure.com/intertwingler#Handler"
rel="rdfs:subClassOf"><code>itcv:Handler</code></a>

<a href="https://vocab.methodandstructure.com/intertwingler#"
rel="rdfs:isDefinedBy">Back to Top</a>

</div>

<div id="Transform" class="section" about="[itcv:Transform]"
typeof="owl:Class">

### `Transform`

An `itcv:Transform` is a special-purpose `itcv:Handler` that is
responsible for transforming HTTP message bodies.

Subclass of:  
<a href="https://vocab.methodandstructure.com/intertwingler#Handler"
rel="rdfs:subClassOf"><code>itcv:Handler</code></a>

<a href="https://vocab.methodandstructure.com/intertwingler#"
rel="rdfs:isDefinedBy">Back to Top</a>

</div>

</div>

<div class="section">

## Properties

</div>
