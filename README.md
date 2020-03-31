# A Playground Backend

A web-based IDE with a containerized backend might look like:

```
                         +
                         |
+------------------+     |        +-----------------+
|                  +------------->+                 |
|     Front End    |     |        |   Web Service   |
|                  +<-------------+                 |
+------------------+     |        +----+-------+----+
                         |             |       ^
                         |             |       |
                         +             v       |
                        K8S       +----+-------+----+
                                  |                 |
                                  | Compile Service |
                                  |                 |
                                  +-----------------+
```

There are others. The web service could drop jobs on a queue, and the compile service could scale against the queue size. Or, the web service and compile service could be scaled together as a K8S "pod." (Or, podman, or whatever container technology is everyone's favorite right now.) For testing, the "web service" and the compiler service can be rolled into a single container, so that a JSON request comes in, a system call is made, and a response is sent.

## API

There are fancy API specification formats. For the moment...

* **POST /compile**
  Expects: `{ "code" : string }`
  Return: `{ "}


