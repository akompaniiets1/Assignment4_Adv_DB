# Redis Notes

## What is Redis?

Redis is an in-memory key-value database. It stores data in RAM, so read and write operations are very fast. Redis is often used for caching, sessions, counters, queues, leaderboards, and temporary data.

## Redis Data Structures Used

### Strings

Strings are the simplest Redis data type. In this assignment, strings were used to store separate product values:

```redis
product:1:name
product:1:price
product:1:category
```

This is useful when an application needs to quickly read a single value.

### Hashes

Hashes store multiple fields inside one key. They are useful for objects such as products, users, or orders.

Example:

```redis
product:2
```

Fields:

```text
name
price
category
stock
```

This structure is better than separate strings when the data belongs to one object.

### Lists

Lists store ordered values. In this assignment, a list was used for recent orders:

```redis
recent_orders
```

Lists are useful for queues, logs, activity feeds, and storing recent events.

### Sets

Sets store unique values. In this assignment, a set was used for product tags:

```redis
product_tags
```

Redis automatically prevents duplicates, so the same tag cannot be added twice.

### Sorted Sets

Sorted sets store values with scores. In this assignment, a sorted set was used for a sales leaderboard:

```redis
sales_leaderboard
```

The sales count was used as the score. This allows Redis to return products ordered by sales.

## TTL and Expiration

Redis supports expiration time for keys using TTL. This means that a key can automatically disappear after a selected number of seconds.

In this assignment:

```redis
featured_product
```

was set with a TTL of 60 seconds. TTL is useful for temporary data, such as login tokens, verification codes, temporary offers, and cached pages.

## Cache Simulation

The key:

```redis
cache:product:1001
```

was used to simulate a cached product page. Caching improves application performance because the application does not need to load the same data from the main database every time. Instead, it can read the prepared value from Redis, which is much faster.

Caching can also reduce database load, improve response time, and make frequently requested pages faster for users.

## Common Redis Use Cases

Redis is commonly used for:

- caching product pages and API responses;
- storing user sessions;
- storing temporary tokens;
- creating queues;
- tracking recent activity;
- building leaderboards;
- counting views, likes, or sales;
- storing real-time data.
