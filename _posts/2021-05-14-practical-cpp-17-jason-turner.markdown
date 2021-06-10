---
layout: post
title:  "Practical C++17 - Jason Turner"
date:   2021-05-14 10:17:00 +0200
categories: videos c++
---
{% timeago 2021-5-14 %}

# Practical C++17
By Jason Turner

{% youtube "https://www.youtube.com/watch?v=nnY4e4faNp0" %}
<br />

Some useful C++17 features:
### Structured Bindings

Can be automatically split a structure into multiple variables.

{% highlight cpp %}

auto [a, b, c] = <expression>;

// If-init expressions: if (init; condition) {}
if (auto [key, value] = *my_map.begin(); key == "mykey"){}
{% endhighlight %}

### `emplace_back` 

In C++17, it returns reference to the objects that were just created for sequence containers.

### `std::string_view` added in C++17

### Nested Namespce

## Class Template Type Deduction

In C++11 and C++14, we need to define the type used when instantiating a class. 
In C++17, it is not needed anymore

{% highlight cpp %}

template<typename First, typename Second>
struct Pair {
  Pair(First t_first, Second t_second) : first(std::move(t_first)), second(std::move(t_second)) 
  {}

  First first;
  Second second;
};

int main() {
  Pair pair{1, 2.3};
}

{% endhighlight %}

### Class Template Deduction Guides

???

### `if constexpr`

{% highlight cpp %}

if constexpr( /* constant expression */ ) {
	// if true, this block is compiled
} else {
  // if false this block is compiled
}

{% endhighlight %}

### Fold Expressions

Unary left/right fold
Binary left/right fold

### `noexcept` is not part of the type system

`noexcept` function pointer can be converted to non-`noexcept`, but not the other way around.

{% highlight cpp %}

void use_func(void *(*func)() noexcept);
void my_func();

use_func(&my_func); // Won't compile anymore

{% endhighlight %}

[Practical C++17] [jekyll-video]

[jekyll-video]: https://youtu.be/UsrHQAzSXkA?t=251
