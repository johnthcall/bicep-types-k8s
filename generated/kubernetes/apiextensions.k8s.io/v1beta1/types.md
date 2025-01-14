# apiextensions.k8s.io @ v1beta1

## Resource apiextensions.k8s.io/CustomResourceDefinition@v1beta1
* **Valid Scope(s)**: Unknown
### Properties
* **apiVersion**: 'apiextensions.k8s.io/v1beta1' (ReadOnly, DeployTimeConstant): The api version.
* **kind**: 'CustomResourceDefinition' (ReadOnly, DeployTimeConstant): The resource kind.
* **metadata**: [metadata](#metadata) (Required): The resource metadata.
* **spec**: [IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1CustomResourceDefinitionSpec](#iok8sapiextensionsapiserverpkgapisapiextensionsv1beta1customresourcedefinitionspec) (Required): CustomResourceDefinitionSpec describes how a user wants their resource to appear
* **status**: [IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1CustomResourceDefinitionStatus](#iok8sapiextensionsapiserverpkgapisapiextensionsv1beta1customresourcedefinitionstatus): CustomResourceDefinitionStatus indicates the state of the CustomResourceDefinition

## metadata
### Properties
* **annotations**: [annotations](#annotations): The annotations for the resource.
* **labels**: [labels](#labels): The labels for the resource.
* **name**: string (Required, DeployTimeConstant): The name of the resource.

## annotations
### Properties
### Additional Properties
* **Additional Properties Type**: string

## labels
### Properties
### Additional Properties
* **Additional Properties Type**: string

## IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1CustomResourceDefinitionSpec
### Properties
* **additionalPrinterColumns**: [IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1CustomResourceColumnDefinition](#iok8sapiextensionsapiserverpkgapisapiextensionsv1beta1customresourcecolumndefinition)[]: additionalPrinterColumns specifies additional columns returned in Table output. See https://kubernetes.io/docs/reference/using-api/api-concepts/#receiving-resources-as-tables for details. If present, this field configures columns for all versions. Top-level and per-version columns are mutually exclusive. If no top-level or per-version columns are specified, a single column displaying the age of the custom resource is used.
* **conversion**: [IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1CustomResourceConversion](#iok8sapiextensionsapiserverpkgapisapiextensionsv1beta1customresourceconversion): CustomResourceConversion describes how to convert different versions of a CR.
* **group**: string (Required): group is the API group of the defined custom resource. The custom resources are served under `/apis/<group>/...`. Must match the name of the CustomResourceDefinition (in the form `<names.plural>.<group>`).
* **names**: [IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1CustomResourceDefinitionNames](#iok8sapiextensionsapiserverpkgapisapiextensionsv1beta1customresourcedefinitionnames) (Required): CustomResourceDefinitionNames indicates the names to serve this CustomResourceDefinition
* **preserveUnknownFields**: bool: preserveUnknownFields indicates that object fields which are not specified in the OpenAPI schema should be preserved when persisting to storage. apiVersion, kind, metadata and known fields inside metadata are always preserved. If false, schemas must be defined for all versions. Defaults to true in v1beta for backwards compatibility. Deprecated: will be required to be false in v1. Preservation of unknown fields can be specified in the validation schema using the `x-kubernetes-preserve-unknown-fields: true` extension. See https://kubernetes.io/docs/tasks/access-kubernetes-api/custom-resources/custom-resource-definitions/#pruning-versus-preserving-unknown-fields for details.
* **scope**: string (Required): scope indicates whether the defined custom resource is cluster- or namespace-scoped. Allowed values are `Cluster` and `Namespaced`. Default is `Namespaced`.
* **subresources**: [IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1CustomResourceSubresources](#iok8sapiextensionsapiserverpkgapisapiextensionsv1beta1customresourcesubresources): CustomResourceSubresources defines the status and scale subresources for CustomResources.
* **validation**: [IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1CustomResourceValidation](#iok8sapiextensionsapiserverpkgapisapiextensionsv1beta1customresourcevalidation): CustomResourceValidation is a list of validation methods for CustomResources.
* **version**: string: version is the API version of the defined custom resource. The custom resources are served under `/apis/<group>/<version>/...`. Must match the name of the first item in the `versions` list if `version` and `versions` are both specified. Optional if `versions` is specified. Deprecated: use `versions` instead.
* **versions**: [IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1CustomResourceDefinitionVersion](#iok8sapiextensionsapiserverpkgapisapiextensionsv1beta1customresourcedefinitionversion)[]: versions is the list of all API versions of the defined custom resource. Optional if `version` is specified. The name of the first item in the `versions` list must match the `version` field if `version` and `versions` are both specified. Version names are used to compute the order in which served versions are listed in API discovery. If the version string is "kube-like", it will sort above non "kube-like" version strings, which are ordered lexicographically. "Kube-like" versions start with a "v", then are followed by a number (the major version), then optionally the string "alpha" or "beta" and another number (the minor version). These are sorted first by GA > beta > alpha (where GA is a version with no suffix such as beta or alpha), and then by comparing major version, then minor version. An example sorted list of versions: v10, v2, v1, v11beta2, v10beta3, v3beta1, v12alpha1, v11alpha2, foo1, foo10.

## IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1CustomResourceColumnDefinition
### Properties
* **description**: string: description is a human readable description of this column.
* **format**: string: format is an optional OpenAPI type definition for this column. The 'name' format is applied to the primary identifier column to assist in clients identifying column is the resource name. See https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#data-types for details.
* **JSONPath**: string (Required): JSONPath is a simple JSON path (i.e. with array notation) which is evaluated against each custom resource to produce the value for this column.
* **name**: string (Required): name is a human readable name for the column.
* **priority**: int: priority is an integer defining the relative importance of this column compared to others. Lower numbers are considered higher priority. Columns that may be omitted in limited space scenarios should be given a priority greater than 0.
* **type**: string (Required): type is an OpenAPI type definition for this column. See https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md#data-types for details.

## IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1CustomResourceConversion
### Properties
* **conversionReviewVersions**: string[]: conversionReviewVersions is an ordered list of preferred `ConversionReview` versions the Webhook expects. The API server will use the first version in the list which it supports. If none of the versions specified in this list are supported by API server, conversion will fail for the custom resource. If a persisted Webhook configuration specifies allowed versions and does not include any versions known to the API Server, calls to the webhook will fail. Defaults to `["v1beta1"]`.
* **strategy**: string (Required): strategy specifies how custom resources are converted between versions. Allowed values are: - `None`: The converter only change the apiVersion and would not touch any other field in the custom resource. - `Webhook`: API Server will call to an external webhook to do the conversion. Additional information
  is needed for this option. This requires spec.preserveUnknownFields to be false, and spec.conversion.webhookClientConfig to be set.
* **webhookClientConfig**: [IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1WebhookClientConfig](#iok8sapiextensionsapiserverpkgapisapiextensionsv1beta1webhookclientconfig): WebhookClientConfig contains the information to make a TLS connection with the webhook.

## IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1WebhookClientConfig
### Properties
* **caBundle**: any: caBundle is a PEM encoded CA bundle which will be used to validate the webhook's server certificate. If unspecified, system trust roots on the apiserver are used.
* **service**: [IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1ServiceReference](#iok8sapiextensionsapiserverpkgapisapiextensionsv1beta1servicereference): ServiceReference holds a reference to Service.legacy.k8s.io
* **url**: string: url gives the location of the webhook, in standard URL form (`scheme://host:port/path`). Exactly one of `url` or `service` must be specified.

The `host` should not refer to a service running in the cluster; use the `service` field instead. The host might be resolved via external DNS in some apiservers (e.g., `kube-apiserver` cannot resolve in-cluster DNS as that would be a layering violation). `host` may also be an IP address.

Please note that using `localhost` or `127.0.0.1` as a `host` is risky unless you take great care to run this webhook on all hosts which run an apiserver which might need to make calls to this webhook. Such installs are likely to be non-portable, i.e., not easy to turn up in a new cluster.

The scheme must be "https"; the URL must begin with "https://".

A path is optional, and if present may be any string permissible in a URL. You may use the path to pass an arbitrary string to the webhook, for example, a cluster identifier.

Attempting to use a user or basic auth e.g. "user:password@" is not allowed. Fragments ("#...") and query parameters ("?...") are not allowed, either.

## IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1ServiceReference
### Properties
* **name**: string (Required): name is the name of the service. Required
* **namespace**: string (Required): namespace is the namespace of the service. Required
* **path**: string: path is an optional URL path at which the webhook will be contacted.
* **port**: int: port is an optional service port at which the webhook will be contacted. `port` should be a valid port number (1-65535, inclusive). Defaults to 443 for backward compatibility.

## IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1CustomResourceDefinitionNames
### Properties
* **categories**: string[]: categories is a list of grouped resources this custom resource belongs to (e.g. 'all'). This is published in API discovery documents, and used by clients to support invocations like `kubectl get all`.
* **kind**: string (Required): kind is the serialized kind of the resource. It is normally CamelCase and singular. Custom resource instances will use this value as the `kind` attribute in API calls.
* **listKind**: string: listKind is the serialized kind of the list for this resource. Defaults to "`kind`List".
* **plural**: string (Required): plural is the plural name of the resource to serve. The custom resources are served under `/apis/<group>/<version>/.../<plural>`. Must match the name of the CustomResourceDefinition (in the form `<names.plural>.<group>`). Must be all lowercase.
* **shortNames**: string[]: shortNames are short names for the resource, exposed in API discovery documents, and used by clients to support invocations like `kubectl get <shortname>`. It must be all lowercase.
* **singular**: string: singular is the singular name of the resource. It must be all lowercase. Defaults to lowercased `kind`.

## IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1CustomResourceSubresources
### Properties
* **scale**: [IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1CustomResourceSubresourceScale](#iok8sapiextensionsapiserverpkgapisapiextensionsv1beta1customresourcesubresourcescale): CustomResourceSubresourceScale defines how to serve the scale subresource for CustomResources.
* **status**: any: Any object

## IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1CustomResourceSubresourceScale
### Properties
* **labelSelectorPath**: string: labelSelectorPath defines the JSON path inside of a custom resource that corresponds to Scale `status.selector`. Only JSON paths without the array notation are allowed. Must be a JSON Path under `.status` or `.spec`. Must be set to work with HorizontalPodAutoscaler. The field pointed by this JSON path must be a string field (not a complex selector struct) which contains a serialized label selector in string form. More info: https://kubernetes.io/docs/tasks/access-kubernetes-api/custom-resources/custom-resource-definitions#scale-subresource If there is no value under the given path in the custom resource, the `status.selector` value in the `/scale` subresource will default to the empty string.
* **specReplicasPath**: string (Required): specReplicasPath defines the JSON path inside of a custom resource that corresponds to Scale `spec.replicas`. Only JSON paths without the array notation are allowed. Must be a JSON Path under `.spec`. If there is no value under the given path in the custom resource, the `/scale` subresource will return an error on GET.
* **statusReplicasPath**: string (Required): statusReplicasPath defines the JSON path inside of a custom resource that corresponds to Scale `status.replicas`. Only JSON paths without the array notation are allowed. Must be a JSON Path under `.status`. If there is no value under the given path in the custom resource, the `status.replicas` value in the `/scale` subresource will default to 0.

## IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1CustomResourceValidation
### Properties
* **openAPIV3Schema**: [IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1JsonSchemaProps](#iok8sapiextensionsapiserverpkgapisapiextensionsv1beta1jsonschemaprops): JSONSchemaProps is a JSON-Schema following Specification Draft 4 (http://json-schema.org/).

## IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1JsonSchemaProps
### Properties
* **$ref**: string
* **$schema**: string
* **additionalItems**: any: Anything
* **additionalProperties**: any: Anything
* **allOf**: [IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1JsonSchemaProps](#iok8sapiextensionsapiserverpkgapisapiextensionsv1beta1jsonschemaprops)[]: Array of io.k8s.apiextensions-apiserver.pkg.apis.apiextensions.v1beta1.JSONSchemaProps
* **anyOf**: [IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1JsonSchemaProps](#iok8sapiextensionsapiserverpkgapisapiextensionsv1beta1jsonschemaprops)[]: Array of io.k8s.apiextensions-apiserver.pkg.apis.apiextensions.v1beta1.JSONSchemaProps
* **default**: any: Anything
* **definitions**: [IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1JsonSchemaPropsDefinitions](#iok8sapiextensionsapiserverpkgapisapiextensionsv1beta1jsonschemapropsdefinitions): Dictionary of <io.k8s.apiextensions-apiserver.pkg.apis.apiextensions.v1beta1.JSONSchemaProps>
* **dependencies**: [IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1JsonSchemaPropsDependencies](#iok8sapiextensionsapiserverpkgapisapiextensionsv1beta1jsonschemapropsdependencies): Dictionary of <any>
* **description**: string
* **enum**: any[]: Array of any
* **example**: any: Anything
* **exclusiveMaximum**: bool
* **exclusiveMinimum**: bool
* **externalDocs**: [IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1ExternalDocumentation](#iok8sapiextensionsapiserverpkgapisapiextensionsv1beta1externaldocumentation): ExternalDocumentation allows referencing an external resource for extended documentation.
* **format**: string: format is an OpenAPI v3 format string. Unknown formats are ignored. The following formats are validated:

- bsonobjectid: a bson object ID, i.e. a 24 characters hex string - uri: an URI as parsed by Golang net/url.ParseRequestURI - email: an email address as parsed by Golang net/mail.ParseAddress - hostname: a valid representation for an Internet host name, as defined by RFC 1034, section 3.1 [RFC1034]. - ipv4: an IPv4 IP as parsed by Golang net.ParseIP - ipv6: an IPv6 IP as parsed by Golang net.ParseIP - cidr: a CIDR as parsed by Golang net.ParseCIDR - mac: a MAC address as parsed by Golang net.ParseMAC - uuid: an UUID that allows uppercase defined by the regex (?i)^[0-9a-f]{8}-?[0-9a-f]{4}-?[0-9a-f]{4}-?[0-9a-f]{4}-?[0-9a-f]{12}$ - uuid3: an UUID3 that allows uppercase defined by the regex (?i)^[0-9a-f]{8}-?[0-9a-f]{4}-?3[0-9a-f]{3}-?[0-9a-f]{4}-?[0-9a-f]{12}$ - uuid4: an UUID4 that allows uppercase defined by the regex (?i)^[0-9a-f]{8}-?[0-9a-f]{4}-?4[0-9a-f]{3}-?[89ab][0-9a-f]{3}-?[0-9a-f]{12}$ - uuid5: an UUID5 that allows uppercase defined by the regex (?i)^[0-9a-f]{8}-?[0-9a-f]{4}-?5[0-9a-f]{3}-?[89ab][0-9a-f]{3}-?[0-9a-f]{12}$ - isbn: an ISBN10 or ISBN13 number string like "0321751043" or "978-0321751041" - isbn10: an ISBN10 number string like "0321751043" - isbn13: an ISBN13 number string like "978-0321751041" - creditcard: a credit card number defined by the regex ^(?:4[0-9]{12}(?:[0-9]{3})?|5[1-5][0-9]{14}|6(?:011|5[0-9][0-9])[0-9]{12}|3[47][0-9]{13}|3(?:0[0-5]|[68][0-9])[0-9]{11}|(?:2131|1800|35\d{3})\d{11})$ with any non digit characters mixed in - ssn: a U.S. social security number following the regex ^\d{3}[- ]?\d{2}[- ]?\d{4}$ - hexcolor: an hexadecimal color code like "#FFFFFF: following the regex ^#?([0-9a-fA-F]{3}|[0-9a-fA-F]{6})$ - rgbcolor: an RGB color code like rgb like "rgb(255,255,2559" - byte: base64 encoded binary data - password: any kind of string - date: a date string like "2006-01-02" as defined by full-date in RFC3339 - duration: a duration string like "22 ns" as parsed by Golang time.ParseDuration or compatible with Scala duration format - datetime: a date time string like "2014-12-15T19:30:20.000Z" as defined by date-time in RFC3339.
* **id**: string
* **items**: any: Anything
* **maximum**: int
* **maxItems**: int
* **maxLength**: int
* **maxProperties**: int
* **minimum**: int
* **minItems**: int
* **minLength**: int
* **minProperties**: int
* **multipleOf**: int
* **not**: [IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1JsonSchemaProps](#iok8sapiextensionsapiserverpkgapisapiextensionsv1beta1jsonschemaprops): JSONSchemaProps is a JSON-Schema following Specification Draft 4 (http://json-schema.org/).
* **nullable**: bool
* **oneOf**: [IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1JsonSchemaProps](#iok8sapiextensionsapiserverpkgapisapiextensionsv1beta1jsonschemaprops)[]: Array of io.k8s.apiextensions-apiserver.pkg.apis.apiextensions.v1beta1.JSONSchemaProps
* **pattern**: string
* **patternProperties**: [IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1JsonSchemaPropsPatternProperties](#iok8sapiextensionsapiserverpkgapisapiextensionsv1beta1jsonschemapropspatternproperties): Dictionary of <io.k8s.apiextensions-apiserver.pkg.apis.apiextensions.v1beta1.JSONSchemaProps>
* **properties**: [IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1JsonSchemaPropsProperties](#iok8sapiextensionsapiserverpkgapisapiextensionsv1beta1jsonschemapropsproperties): Dictionary of <io.k8s.apiextensions-apiserver.pkg.apis.apiextensions.v1beta1.JSONSchemaProps>
* **required**: string[]: Array of IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1JsonSchemaPropsRequiredItem
* **title**: string
* **type**: string
* **uniqueItems**: bool
* **x-kubernetes-embedded-resource**: bool: x-kubernetes-embedded-resource defines that the value is an embedded Kubernetes runtime.Object, with TypeMeta and ObjectMeta. The type must be object. It is allowed to further restrict the embedded object. kind, apiVersion and metadata are validated automatically. x-kubernetes-preserve-unknown-fields is allowed to be true, but does not have to be if the object is fully specified (up to kind, apiVersion, metadata).
* **x-kubernetes-int-or-string**: bool: x-kubernetes-int-or-string specifies that this value is either an integer or a string. If this is true, an empty type is allowed and type as child of anyOf is permitted if following one of the following patterns:

1) anyOf:
   - type: integer
   - type: string
2) allOf:
   - anyOf:
     - type: integer
     - type: string
   - ... zero or more
* **x-kubernetes-list-map-keys**: string[]: x-kubernetes-list-map-keys annotates an array with the x-kubernetes-list-type `map` by specifying the keys used as the index of the map.

This tag MUST only be used on lists that have the "x-kubernetes-list-type" extension set to "map". Also, the values specified for this attribute must be a scalar typed field of the child structure (no nesting is supported).

The properties specified must either be required or have a default value, to ensure those properties are present for all list items.
* **x-kubernetes-list-type**: string: x-kubernetes-list-type annotates an array to further describe its topology. This extension must only be used on lists and may have 3 possible values:

1) `atomic`: the list is treated as a single entity, like a scalar.
     Atomic lists will be entirely replaced when updated. This extension
     may be used on any type of list (struct, scalar, ...).
2) `set`:
     Sets are lists that must not have multiple items with the same value. Each
     value must be a scalar, an object with x-kubernetes-map-type `atomic` or an
     array with x-kubernetes-list-type `atomic`.
3) `map`:
     These lists are like maps in that their elements have a non-index key
     used to identify them. Order is preserved upon merge. The map tag
     must only be used on a list with elements of type object.
Defaults to atomic for arrays.
* **x-kubernetes-map-type**: string: x-kubernetes-map-type annotates an object to further describe its topology. This extension must only be used when type is object and may have 2 possible values:

1) `granular`:
     These maps are actual maps (key-value pairs) and each fields are independent
     from each other (they can each be manipulated by separate actors). This is
     the default behaviour for all maps.
2) `atomic`: the list is treated as a single entity, like a scalar.
     Atomic maps will be entirely replaced when updated.
* **x-kubernetes-preserve-unknown-fields**: bool: x-kubernetes-preserve-unknown-fields stops the API server decoding step from pruning fields which are not specified in the validation schema. This affects fields recursively, but switches back to normal pruning behaviour if nested properties or additionalProperties are specified in the schema. This can either be true or undefined. False is forbidden.

## IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1JsonSchemaPropsDefinitions
### Properties
### Additional Properties
* **Additional Properties Type**: [IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1JsonSchemaProps](#iok8sapiextensionsapiserverpkgapisapiextensionsv1beta1jsonschemaprops)

## IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1JsonSchemaPropsDependencies
### Properties
### Additional Properties
* **Additional Properties Type**: any

## IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1ExternalDocumentation
### Properties
* **description**: string
* **url**: string

## IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1JsonSchemaPropsPatternProperties
### Properties
### Additional Properties
* **Additional Properties Type**: [IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1JsonSchemaProps](#iok8sapiextensionsapiserverpkgapisapiextensionsv1beta1jsonschemaprops)

## IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1JsonSchemaPropsProperties
### Properties
### Additional Properties
* **Additional Properties Type**: [IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1JsonSchemaProps](#iok8sapiextensionsapiserverpkgapisapiextensionsv1beta1jsonschemaprops)

## IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1CustomResourceDefinitionVersion
### Properties
* **additionalPrinterColumns**: [IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1CustomResourceColumnDefinition](#iok8sapiextensionsapiserverpkgapisapiextensionsv1beta1customresourcecolumndefinition)[]: additionalPrinterColumns specifies additional columns returned in Table output. See https://kubernetes.io/docs/reference/using-api/api-concepts/#receiving-resources-as-tables for details. Top-level and per-version columns are mutually exclusive. Per-version columns must not all be set to identical values (top-level columns should be used instead). If no top-level or per-version columns are specified, a single column displaying the age of the custom resource is used.
* **deprecated**: bool: deprecated indicates this version of the custom resource API is deprecated. When set to true, API requests to this version receive a warning header in the server response. Defaults to false.
* **deprecationWarning**: string: deprecationWarning overrides the default warning returned to API clients. May only be set when `deprecated` is true. The default warning indicates this version is deprecated and recommends use of the newest served version of equal or greater stability, if one exists.
* **name**: string (Required): name is the version name, e.g. “v1”, “v2beta1”, etc. The custom resources are served under this version at `/apis/<group>/<version>/...` if `served` is true.
* **schema**: [IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1CustomResourceValidation](#iok8sapiextensionsapiserverpkgapisapiextensionsv1beta1customresourcevalidation): CustomResourceValidation is a list of validation methods for CustomResources.
* **served**: bool (Required): served is a flag enabling/disabling this version from being served via REST APIs
* **storage**: bool (Required): storage indicates this version should be used when persisting custom resources to storage. There must be exactly one version with storage=true.
* **subresources**: [IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1CustomResourceSubresources](#iok8sapiextensionsapiserverpkgapisapiextensionsv1beta1customresourcesubresources): CustomResourceSubresources defines the status and scale subresources for CustomResources.

## IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1CustomResourceDefinitionStatus
### Properties
* **acceptedNames**: [IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1CustomResourceDefinitionNames](#iok8sapiextensionsapiserverpkgapisapiextensionsv1beta1customresourcedefinitionnames): CustomResourceDefinitionNames indicates the names to serve this CustomResourceDefinition
* **conditions**: [IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1CustomResourceDefinitionCondition](#iok8sapiextensionsapiserverpkgapisapiextensionsv1beta1customresourcedefinitioncondition)[]: conditions indicate state for particular aspects of a CustomResourceDefinition
* **storedVersions**: string[]: storedVersions lists all versions of CustomResources that were ever persisted. Tracking these versions allows a migration path for stored versions in etcd. The field is mutable so a migration controller can finish a migration to another version (ensuring no old objects are left in storage), and then remove the rest of the versions from this list. Versions may not be removed from `spec.versions` while they exist in this list.

## IoK8SApiextensionsApiserverPkgApisApiextensionsV1Beta1CustomResourceDefinitionCondition
### Properties
* **lastTransitionTime**: string: Time is a wrapper around time.Time which supports correct marshaling to YAML and JSON.  Wrappers are provided for many of the factory methods that the time package offers.
* **message**: string: message is a human-readable message indicating details about last transition.
* **reason**: string: reason is a unique, one-word, CamelCase reason for the condition's last transition.
* **status**: string (Required): status is the status of the condition. Can be True, False, Unknown.
* **type**: string (Required): type is the type of the condition. Types include Established, NamesAccepted and Terminating.

