# functional programming in javascript

Sarah Ransohoff
August 20, 2015
BrooklynJS

^ who i am, venmo is hiring

---

# what is functional programming

- based on mathematical notion of functional composition
- list of characteristics (immutable data, first class functions, tail call optimization)
- mentions of mapping, reducing, recursing, currying, etc

---

# what is functional programming

- the absence of side effects

^ lots of complicated definitions out there, this one seems to be the uniting factor

---

## example of non functional, with side effects

```
var a = 0;
var addOne = function() {
	console.log(a);
	return a += 1;
}
```

^ unnecessary global var; we’re logging

---

## example of functional, sans side effects

```
var addOne = function(a) {
	return a += 1;
}
```

^ no more var, passing it in as an arg; no log ;)

---

![](graduation.jpg)

# we did it!

---

# to get the full picture, what else do we need to know about functional programming

---

# 1. don’t iterate over lists

use map and reduce

---

## why use map and reduce over iterating?

- less chance for side effects
- encourages immutable data
- code in a loop can affect variables outside of it

^ rather than changing the original object, create and return a new data structure; NO SIDE EFFECTS

---

## map

- takes a function and a collection of items
- runs function on each item in the original collection
- inserts each return val into a new collection
- returns new collection

---

## map - an example

```
<tbody>
	{this.props.apps.map(this.renderApp)}
</tbody>
```

^ in new settings page on venom (we’re building a new web app! finally!)

---

![](anchorman.jpg)

---

## map - an example

```
<tbody>
	{this.props.apps.map(this.renderApp)}
</tbody>
```

^ at venom we use a lot of react. this returns table rows for each app

---

![](settings.png)

---

![](developer.png)

---

## reduce

- takes a function and a collection of items
- returns the value that is created by combining the items

---

## reduce - an example

```
errors = this.state.errors.reduce(function(acc, err) {
	var orientation = 'left';
		if ( err.field === 'lastName' ) {
			orientation = 'right';
		}

		acc[err.field] = <Tooltip message={err.error} orientation={orientation} />;
		return acc;
}, {});

```

^ where acc is the accumulator — we start w objects (error, field) and end up with (field, react component)

---

![](errors.png)

---

# 2. write declaratively, not imperatively 

- describes what to do rather than how to do it (tell comp the problem, not how to solve it)

---

![](therapy.jpg)

## declarative feels sort of like therapy

---

## react is declarative

```
render: function() {
	return (
		<div className="sign-in" onClick={this.handleClick}>
			<a className="icon-lock-blue">Sign in</a>
			{ this.state.showForm ? <SignInForm /> : null }
		</div>
	);

}

```

^ any react render function: is given a new state, returns new dom

---

## whereas jQuery is not (it’s imperative)

```
$(‘.sign-in-form’).show();

```

---

![](bad-therapy.jpg)

## aka *not* a good therapist

---

## can also make program more declarative (and therefore more functional) by using functions

---

# a relatively convoluted statement i know but bear with me

---

## more declarative = more functions = more functional

```
loginAsGroup(groupId) {
	return this.apiClient.loginAsGroup(groupId)
		.then((resp) => {
			return this.apiClient.loginAsGroupDjango(resp.access_token);
	}).then(this.goToHomePage);
}
```

---

# 3. remove state

- function should perform every time as if for the first time

---

![](./madonna-like-a-virgin.jpg)

---

## remove state - an example

```
statics: {
	requestSendToken: function(secret, via) {
		return VenmoAPI.twoFactorAuth.sendToken(secret, via);
	}
}
SendTokenButton.requestSendToken(this.props.secret, this.props.via)
	.then(function() {
		this.setState({ spinning: false });
		// code code code
	});

```

^ tough to do with react; operating in a vacuum

---

# why functional programming is great

- allows programs to be broken down into smaller, simpler pieces
	- makes them more reliable, testable, understandable, readable
- co-exists very well with code written in other styles
- often tends to be more readable

---

# using functional programming

- functional languages: Haskell, Clojure, Scala
- libs: underscore.js, bacon.js
- can write functional code in any language that supports first-class functions

^ functional language simple force you to adhere

---

# what did we learn

- functional programming is essentially the absence of side effects
- other good notes
	- use map and reduce
	- write declaratively, not imperatively
	- remove state

---

![](graduation.jpg)

# we did it!?

---

![](beach.jpg)

# yeah, we did it.

---

# sources

- http://maryrosecook.com/blog/post/a-practical-introduction-to-functional-programming
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/
- http://www.smashingmagazine.com/2014/07/dont-be-scared-of-functional-programming/

---

# [fit] Thank You.
# [fit] I’m **sranso**
# [fit] everywhere.
