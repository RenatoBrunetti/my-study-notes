# Redis
[main](../../../README.md) | [database](../../README.md) | [nosql](../README.md) | [redis](README.md)

## Description
**Redis** is an in-memory data structure store, used as a distributed, in-memory key–value database, cache and message broker, with optional durability. Redis supports different kinds of abstract data structures, such as strings, lists, maps, sets, sorted sets, HyperLogLogs, bitmaps, streams, and spatial indices.

---

## Redis Commands

### Start the Redis CLI
```sh
# Open Redis CLI on a command line
redis-cli
```

---

### Basic Commands
```sh (redis-cli)
# SET or UPDATE an Object |> SET [KEY] [VALUE]
SET "web:user:name" "John"

# SET or UPDATE multiple Objects |> MSET [KEY] [VALUE] [KEY] [VALUE] ...
MSET "web:user:name" "John" "web:user:surname" "McFly"

# GET an Object |> GET [KEY]
GET "web:user:name"

# DEL an Object |> DEL [KEY]
DEL "web:user:name"

# FLUSH all Objects |> FLUUSHALL
FLUSHALL
```
---

### Hash Object
```sh (redis-cli)
# SET or UPDATE a hash Object |> HSET [KEY] [FIELD] [VALUE]
HSET "web:user" "name" "John"

# GET a hash Object Field |> HGET [KEY] [FIELD]
HGET "web:user" "name"

# SET or UPDATE multiple hash Objects |> HMSET [KEY] [FIELD] [VALUE] [FIELD] [VALUE] ...
HMSET "web:user" "name" "John" "surname" "McFly"

# GET multiple hash Object Fields |> HMGET [KEY] [FIELD] [FIELD] ...
HMGET "web:user" "name" "surname"
```

---

### Keys
```sh (redis-cli)
# GET all keys |> KEYS *
KEYS *

# GET a key by name |> KEYS [KEY]
KEYS "web:user:name"

# GET a filtered keys |> KEYS [FILTER]
KEYS "web*" # Receive a list of keys beginning with "web"
KEYS "*name" # Receive a list of keys ending with "name"
KEYS "2023-01-1?" # Receive a list of keys in a range of day from 10 to 19
KEYS "2023-01-1[012]" # Receive a list of keys in a range of options [10, 11, 12]
```

---

### Expiration
```sh (redis-cli)
# Set an expire for an object |> EXPIRE [KEY] [SECONDS]
EXPIRE "web:user:name" 1800

# Check expiration time |> TTL [KEY]
TTL "web:user:name"
```

### Increment and Decrement
```sh (redis-cli)
# Increment +1 |> INCR [KEY]
INCR "web:access"

# Increment a given value |> INCRBY [KEY] [INCREMENT]
INCRBY "web:access" 10

# Increment a given FLOAT value |> INCRBYFLOAT [KEY] [INCREMENT]
INCRBYFLOAT "web:cart:amount" 15.50

# Decrement -1 |> DECR [KEY]
DECR "web:access"

# Decrement a given value |> DECRBY [KEY] [INCREMENT]
DECRBY "web:access" 10

# DEcrement a given FLOAT value |> DECRBYFLOAT [KEY] [INCREMENT]
DECRBYFLOAT "web:cart:amount" 15.50
```

### Bitset
```sh (redis-cli)
# SET a bit (0 or 1) |> SETBIT [KEY] [OFFSET] [VALUE]
SETBIT "web:unauthorized:user:access" 23012 1

# GET a bit value (0 or 1) |> GETBIT [KEY] [OFFSET]
GETBIT "web:unauthorized:user:access" 23012

# Count true offsets by KEY |> BITCOUNT [KEY]
BITCOUNT "web:unauthorized:user:access"

# SET a new BITSET by operation |> BITOP [OPERATION] [DESTKEY] [KEY] [KEY] ...
BITOP AND "and:20230101:20230102" "20230101" "20230102"
BITOP OR "or:20230101:20230102" "20230101" "20230102"
```
