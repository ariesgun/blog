---
layout: post
title:  "Modern C++ 14/17 Visited"
date:   2021-05-14 10:17:00 +0200
categories: videos c++
---
{% timeago 2021-5-14 %}

# How to adopt Modern C++ 17
By Herb Sutter

{% youtube "https://youtu.be/UsrHQAzSXkA?t=251" %}
<br />

## What's new
Several features that you can adopt when you are writing a new code:
- Range
- `make_unique` or `make_shared`
- `auto` type deduction

06:50. Compute arithmetic mean using `reduce` combined with `par_unseq` to achieve parallel STL. It is comparable to python's `sum`.

08:51. Value types & `move` efficiency. It is okay to return by value now in C++ 17 since C++ now has `move` operation. 

11:20. Four vocabulary types in C++17: `string_view`, `optional<T>`, `variant<Ts...>`, and `any`.

`string_view` is a non-owning const view of a contiguous sequence of characters (NOT null-terminated).

`optional<T>` contains a T value or "empty". Combined with `result.value_or()`.

`variant<Ts...>`. Contains one value of a fixed set of types.

`any<T>` contains one value of any type, fully dynamic type.

## Top two general issues/ techniques

- RAII + scopes
Scoped lifetime = efficient + exception-safe. Even if a class contains an object by value, it will be destructed at the end of the enclosing object's lifetime. 

- Error handling
Prefer exceptions. Use error codes on boundaries with non-C++ code. 
Use assertion for non-recoverable bugs, so that developers can fix it during test time.

- Smart Pointers
As function parameter and return value, raw pointers and raw references are just fine.

{% highlight cpp %}
unique_ptr<widget> factory();

void caller() {
    auto w = factory();
    auto g = make_unique<gadget>();
    use(*w, *g);
}

// Inner pointer and outer pointer share the same counter reference
struct Node { Data data; };
shared_prt<Data> get_data(const shared_ptr<Node>& pn) {
    return { pn, &(pn->data) };
}

{% endhighlight %}

Be careful when you pass a shared_ptr by value because it can cause performance hits (i.e. hittung the cache lines.).

Summary: 43:30.

[How to adopt Modern C++17 Into Your C++ Code][jekyll-video].

[jekyll-video]: https://youtu.be/UsrHQAzSXkA?t=251
