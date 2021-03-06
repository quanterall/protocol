[back](./README.md)
# Account management - intended usage

Each node handles one account.

The following assumes that the node exposes at address 127.0.0.1 the following ports:
* User API external HTTP endpoint: 3013
* User API internal HTTP endpoint: 3113

## Retrieve your public key

Retrieve the public key of your node:
```bash
curl http://127.0.0.1:3113/v2/debug/accounts/node
```
You shall read output like the following:
```
{"pub_key":"ak_N1WLMewMQPUyQBdEhXRSYee84RQNKJrECwbbseMkNsZhv1X"}
```

## Retrieve your balance

In order to retrieve your balance, fetch your public key then use it to get the balance associated to that public key (replace the public key in the command):
```bash
curl -G 'http://127.0.0.1:3013/v2/accounts/ak_N1WLMewMQPUyQBdEhXRSYee84RQNKJrECwbbseMkNsZhv1X'
```
You shall read output like the following...
```
{"balance":80, "id":"ak_N1WLMewMQPUyQBdEhXRSYee84RQNKJrECwbbseMkNsZhv1X", "nonce":0}
```
... or - if you do not have tokens yet e.g. because you have not yet mined a block successfully - the following:
```
{"reason":"Account not found"}
```
