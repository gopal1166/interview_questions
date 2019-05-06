# Python IQ

range vs xrange:

```
range:
	returns list 
xrange:
	returns xrange object

	why: incase to generate a billion elements in an array
	yields a generator object

	synt: xrange(start, stop, step)
	eg: xrange(0, 10, 2)  #even numbers b/n 0 and 10

	deprected in 3.x version
```


factorial:

```
	fact of a num is the product of all integers from 1 to that numb
	For ex: fact of 6 (6!) = 1*2*3*4*5*6

	if n < 0 : sorry not for -ve
	if n = 0 : fact of 0 is 1
	else:
		logic
```


----------------------------------------------

palindrome:

```
	a string which is same  read  forward or backwards
	g: '121', 'aba'
	logic: 
		casefold,

List to string:
list1 = ['g', 'o', 'p']
"".join(list1)
```


numpy: To deal with large data sets


python memory management:

```
	private heap space
	python memory manager
	inbuilt garbage collector: frees unused memory
```

```
isupper(): to check all chars are capital or not

join(): to merge the elements

import: modules are used
```

# django IQ:

```
django version:
	i used: 1.11
	latest: 2.2

	now releasing 2. series till 2020
	after 2020 may be series 3
```


django request lify cycle:

```
	middlewares: to modify the request
	request'll be dispatched to urls.py 
	then to views.py(ORM, templates)
```

django dev & maintaned by: Django Software Foundation


django middlewares:

```
	a framework of hooks'll be  executed as part of request and response life cycle

ex: to modify the request
	to user request.user in views
	django add user object to request using AuthenticationMiddleware 

ex2: to modify the request object
	users from different timezones
	to display his timezone

	1.create custome TimezomeMiddleware(object):
	2.add time zone to the request.session object  (request.session['timezone'] = request.user.profile.timezone)
	3.register this in middlewares:
		order: after the AuthenticationMiddleware
		reason: this is depends on request.user

		so request.user is provided by AuthenticationMiddleware

Things to remember:
	1.middleware class should extends object class
	2.order in settings.py MIDDLEWARE_CLASSES
	3.may implement process_request(self, request), process_view(), 				process_response(self, request, respnose)

```
	

decorators in django:

```

to dynamically alter the functionality of a function

eg: @login_required
piece of code checks whether user is authenticated or not

```


















	












