# gridfw-session


## Options
* expires: integer - session timeout, default to 1day
* setCookie: function(ctx, sessionId, expires){ ctx.setCookie('SESSIONID', sessionId, expires)} - Customize set cookie function to get more control on it
* getCookie: function(ctx){ ctx.cookies.SESSIONID } - Customize how to get session key from cookie or any other source
* createId: function(ctx){ UUID.create() } - Customize session id generator

## Methods
All methods returns promises, use "await" to get value
* ctx.session.get() : get all stored session values, @return object
* ctx.session.get('sessionParam') : Get session param value from the store, @return value
* ctx.session.get('param1', 'param2', ...) : Get session param value from the store, @return object
* ctx.session.set('sessionParam', 'value'): set session value
* ctx.session.set({key: value}) : set those keys values
* ctx.session.has('param1', 'param2', ...) : true when session has those params

* ctx.session.reload(): Reload the session, generate new session id (must be called before sending data to user)
* ctx.session.destroy(): Destroy the session
* ctx.session.clear(): Remove all data of current session

* app.session.all(): get all stored sessions
* app.session.get('sessionId'): get session from the store

## Attributes
* id: session id
* expires: get session timeout
* expired: true when session is expired
