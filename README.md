# natscpp

## Getting started
natscpp is a C++ wrapper for the nats client provided by Synadia.\n
It works by adding reactors to the client with a topic name and a callback.

## Easy to use

### The client
Create a client and connect to a running NATS server.
````
  nats_client my_nats_client(NATS_DEFAULT_URL)
````

### Callback
You can easily create a callback with NCALLBACK(callback name)
The callback name should not be a string!
````
  NCALLBACK(sms_callback)
  {
    /* Callback body */

    natsMsg_Destroy(msg); /* DON'T FORGET THIS AT THE END OF YOUR CB */
  }
````

### Reactors
To create reactor(s), just use the function add_reactor
````
  add_reactor(topic name, callback)
````
For example
````
  my_nats_client.add_reactor("sms.out.*", sms_callback);
````

### Run the client
When you are done with your reactors, just run the client
````
  my_nats_client.run(true); /* pass true for some output */
````
