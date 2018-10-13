event_base is a centralized place to register events to monitor and folly::EventBase is a wrapper around event_base. 
One event_base creates one thread to check on the event. Callback gets executed in the same thread so it better be quick in order not to block other events from fires in time

EventHandler does the registering an event to watch and what callback function to call when the event is ready. 

event_set() sets an event object. It does not registers the event, yet.
event_base_set() sets the event to right event_base object. If this is not called, it defaults to most recently created event_base. 
event_add() actually registers the event to the event_base to take effect.

http://blog.gaurav.im/2014/12/15/a-gentle-intro-to-libevent/

In action in folly: https://github.com/facebook/folly/blob/master/folly/io/async/EventHandler.cpp#L26
