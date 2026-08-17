# X-Forwarded-For --- Understanding Client IPs Behind a Load Balancer

## What is `X-Forwarded-For`?

**`X-Forwarded-For` is an HTTP header used to tell your application the
original client's IP address.**

It is especially useful when a request passes through a **proxy or load
balancer** before reaching the application.

------------------------------------------------------------------------

## 1. The Problem It Solves

Imagine this architecture:

``` text
Your Computer
     |
     | IP = 203.0.113.50
     ↓
Application Load Balancer
     |
     | IP = 10.0.2.15
     ↓
Your Application
```

The request goes:

``` text
Client → ALB → Application
```

When the application receives the request, the immediate connection may
appear to come from the **ALB**, rather than directly from the original
client.

The application might therefore see:

``` text
10.0.2.15
```

and think:

> "The request came from the ALB."

But what we really want to know is:

> "Who was the actual client that made this request?"

That's where `X-Forwarded-For` comes in.

------------------------------------------------------------------------

## 2. The ALB Adds an HTTP Header

The Application Load Balancer can forward the request to the application
with an HTTP header such as:

``` http
GET /products HTTP/1.1
Host: example.com
X-Forwarded-For: 203.0.113.50
```

The application can then read:

``` text
X-Forwarded-For: 203.0.113.50
```

and understand:

> "The original client was `203.0.113.50`."

------------------------------------------------------------------------

## 3. Conceptual Flow

``` text
Client
  |
  | IP = 203.0.113.50
  ↓
┌──────────────────────┐
│ Application          │
│ Load Balancer (ALB)  │
└──────────────────────┘
  |
  | X-Forwarded-For:
  | 203.0.113.50
  ↓
Application
```

The ALB receives the request from the client and forwards it to the
application.

The `X-Forwarded-For` header carries information about the original
client IP.

------------------------------------------------------------------------

## 4. Why Is It Called "Forwarded"?

The ALB is acting as a **proxy**.

The request travels like this:

``` text
Client → ALB → Application
```

The ALB **forwards** the client's HTTP request to the application.

Because the ALB is now the intermediary, the application needs a way to
learn information about the original client.

`X-Forwarded-For` provides that information.

------------------------------------------------------------------------

## 5. Real-World Example

Suppose you're building an online store.

A customer has the IP:

``` text
203.0.113.50
```

They visit:

``` text
https://myshop.com/products
```

Your architecture looks like:

``` text
Customer
    ↓
   ALB
    ↓
EC2 Application
    ↓
Database
```

Your application might want the client's IP for:

-   Logging
-   Troubleshooting
-   Security monitoring
-   Rate limiting
-   Detecting suspicious activity
-   Analytics

The application can inspect:

``` http
X-Forwarded-For: 203.0.113.50
```

and record something like:

``` text
User 203.0.113.50 requested /products
```

------------------------------------------------------------------------

## 6. Why This Matters for AWS DVA-C02

A useful exam association is:

> **ALB = HTTP-aware**

Because an **Application Load Balancer operates at the HTTP/HTTPS
level**, it can work with HTTP headers.

Some important headers associated with load balancing include:

``` text
X-Forwarded-For
X-Forwarded-Proto
X-Forwarded-Port
```

The most important one to remember for the client IP question is:

> **`X-Forwarded-For` → identifies the original client's IP address.**

------------------------------------------------------------------------

## 7. DVA-C02 Exam Shortcut

When you see a question containing:

> **Application Load Balancer + need the original client's IP**

Think:

``` text
ALB
 ↓
X-Forwarded-For
 ↓
Original Client IP
```

### Example

**Question:**

> An application uses an HTTP/HTTPS listener and must access the client
> IP addresses. Which solution should be used?

**Answer:**

> **Use an Application Load Balancer and the `X-Forwarded-For`
> headers.**

------------------------------------------------------------------------

## Quick Memory Table

  Concept             Remember
  ------------------- ---------------------------------------------------
  ALB                 Layer 7 / HTTP & HTTPS
  `X-Forwarded-For`   Original client IP
  ALB + client IP     `X-Forwarded-For`
  NLB                 Layer 4 / TCP, UDP, TLS
  NLB client IP       Can preserve source IP natively
  Proxy Protocol      Another way to pass client connection information

## One-Line Summary

> **`X-Forwarded-For` is an HTTP header that allows an application
> behind a proxy or load balancer, such as an ALB, to determine the
> original client's IP address.**
