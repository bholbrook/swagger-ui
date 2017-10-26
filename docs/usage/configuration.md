# Configuration

Parameters with dots in their names are single strings used to organize subordinate parameters, and are not indicative of a nested structure.

Parameter Name | Description
--- | ---
url | The url pointing to API definition (normally `swagger.json` or `swagger.yaml`). Will be ignored if `urls` or `spec` is used.
urls | An array of API definition objects (`{url: "<url>", name: "<name>"}`) used by Topbar plugin. When used and Topbar plugin is enabled, the `url` parameter will not be parsed. Names and URLs must be unique among all items in this array, since they're used as identifiers.
urls.primaryName | When using `urls`, you can use this subparameter. If the value matches the name of a spec provided in `urls`, that spec will be displayed when Swagger-UI loads, instead of defaulting to the first spec in `urls`.
spec | A JSON object describing the OpenAPI Specification. When used, the `url` parameter will not be parsed. This is useful for testing manually-generated specifications without hosting them.
validatorUrl | By default, Swagger-UI attempts to validate specs against swagger.io's online validator. You can use this parameter to set a different validator URL, for example for locally deployed validators ([Validator Badge](https://github.com/swagger-api/validator-badge)). Setting it to `null` will disable validation.
dom_id | The id of a dom element inside which SwaggerUi will put the user interface for swagger.
domNode | The HTML DOM element inside which SwaggerUi will put the user interface for swagger. Overrides `dom_id`.
oauth2RedirectUrl | OAuth redirect URL
tagsSorter | Apply a sort to the tag list of each API. It can be 'alpha' (sort by paths alphanumerically) or a function (see [Array.prototype.sort()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort) to learn how to write a sort function). Two tag name strings are passed to the sorter for each pass. Default is the order determined by Swagger-UI.
operationsSorter | Apply a sort to the operation list of each API. It can be 'alpha' (sort by paths alphanumerically), 'method' (sort by HTTP method) or a function (see Array.prototype.sort() to know how sort function works). Default is the order returned by the server unchanged.
defaultModelRendering | Controls how models are shown when the API is first rendered. (The user can always switch the rendering for a given model by clicking the 'Model' and 'Example Value' links.) It can be set to 'model' or 'example', and the default is 'example'.
defaultModelExpandDepth | The default expansion depth for models.  The default value is 1.
configUrl | Configs URL
parameterMacro | MUST be a function. Function to set default value to parameters. Accepts two arguments parameterMacro(operation, parameter). Operation and parameter are objects passed for context, both remain immutable
modelPropertyMacro | MUST be a function. Function to set default values to each property in model. Accepts one argument modelPropertyMacro(property), property is immutable
docExpansion | Controls the default expansion setting for the operations and tags. It can be 'list' (expands only the tags), 'full' (expands the tags and operations) or 'none' (expands nothing). The default is 'list'.
displayOperationId | Controls the display of operationId in operations list. The default is `false`.
displayRequestDuration | Controls the display of the request duration (in milliseconds) for `Try it out` requests. The default is `false`.
maxDisplayedTags | If set, limits the number of tagged operations displayed to at most this many. The default is to show all operations.
filter | If set, enables filtering. The top bar will show an edit box that you can use to filter the tagged operations that are shown. Can be true/false to enable or disable, or an explicit filter string in which case filtering will be enabled using that string as the filter expression. Filtering is case sensitive matching the filter expression anywhere inside the tag.
deepLinking | If set to `true`, enables dynamic deep linking for tags and operations. [Docs](https://github.com/swagger-api/swagger-ui/blob/master/docs/deep-linking.md)
requestInterceptor | MUST be a function.  Function to intercept document fetching and try-it-out requests.  Accepts one argument requestInterceptor(request) and MUST return the potentially modified request.
responseInterceptor | MUST be a function.  Function to intercept document fetching and try-it-out responses.  Accepts one argument responseInterceptor(response) and MUST return the potentially modified response.
showMutatedRequest | If set to `true` (the default), uses the mutated request returned from a rquestInterceptor to produce the curl command in the UI, otherwise the request before the requestInterceptor was applied is used.