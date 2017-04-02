# ES6 API Wrapper - About
A basic ES6 API class that wraps the fetch function and allows for a more dynamic and robust interface to interact with any API - easily extendable and mighty flexible.

---

# What issues does this solve?
If you're wanting to interact with a complex API you'll want to make your API calls as structured and flexible as possible, this wrapper aims to solve that issue.

Simply extendable and suited for your API's needs, you can implement more complex functionality or simply use what's currently available.

# How do I use it?
A demo implementation can be found in this projects index.html file.

### Constructing the wrapper
To construct the API wrapper, you'll need to provide a __host url__ (the API's domain), an __object of endpoints__ and if you desire, a __response type__ (Content-Type).

---

#### Endpoints format - Required properties
All endpoints should be listed in the endpoints object.

The endpoints object only requires two properties to function properly: __url__ (string) and __methods__ (array).

The __url__ property must be the trailing endpoint that this endpoint should hit, for example if I wanted to hit a __posts__ endpoint, my __url__ property would be equal to `/posts`.

The __methods__ property is an __array__ of available HTTP methods that this endpoint has access to, for example my `/posts` endpoint has access to both __POST__ and __GET__, so my __methods__ property would be equal to `['POST', 'GET']`.

---

#### API fetch format
To fetch data from an endpoint, you can call `Api.fetch(method (string), endpoint (string), options (object))`.

When fetching data you may pass options to each endpoint as you desire, however there are reserved properties which perform special functions, these being __id__ (string), __filter__ (object) and __parent__ (string).

The __id__ property will simply request the current endpoint with a resource identifier, for example `http://myapi.com/posts/{id}`;

The __filter__ property is an object containing anything you'd like to filter against this endpoint, creating a query string that implements your filters, for example `http://myapi.com/posts?user=me`.

The __parent__ property is unique in that it can be used to retrieve a nested endpoint from a resource identifier. For example, if I have the endpoint `/posts` and that endpoint accepts a resource identifier such as `/posts/{id}`, but then also accepts a nested endpoint to retrieve comments like `/posts/{id}/comments` - the __parent__ property will allow you to do this.

I would still create a new endpoint for my posts comments, however its parent would obviously be the endpoint that it nests under, in this case __posts__.
