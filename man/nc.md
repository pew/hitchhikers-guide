# nc / netcat

there are a lot of use cases... let's start with. 1.

## file transfer

sender:

```
tar -czf - folder | nc -l 9999
```
 
receiver:

```
nc <senderip> 9999|tar xvf -
```
