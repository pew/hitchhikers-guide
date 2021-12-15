# dns

dns things… okay?

## host level dns resolution

things like *dig* and *dog* use their own mechanism, sometimes, for debugging things you might want to do a lookup how the OS would do it:

**linux:**

```
getent ahosts google.com
```

**macos:**

```
dscacheutil -q host -a name google.com
```

## query dns over tls (dot)

want to test dns over tls? there's *[dog](https://github.com/ogham/dog)* and possibly *dig* available to test things:

```
dog --tls @one.one.one.one ilayk.com
```

```
dig +tls @one.one.one.one ilayk.com
```
