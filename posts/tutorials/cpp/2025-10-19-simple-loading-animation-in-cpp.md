---
title: "Simple Loading Animation In C++"
date: 2025-10-19
author: "Chris Bradley"
tags: [cpp, c, c++, loading, terminal]
description: "Single line terminal loading animation in C++"
readtime: "5min"
---

# Simple Loading Animation In C++

This is way simple to do, were just using 4 characters to do this.

Lets include these 4 headers:
```cpp
#include <chrono> // duration
#include <thread> // sleep at current thread
#include <cstdio> // I/O, faster
#include <vector> // better alternative to C array
```

Now we need  two variables, one that loads until it reaches 100 and other that resets back to 0 to stay within the array limit. We'll name them as `load_percentage` and `iterator` respectively in the `main()`. And then we need a vector that holds the characters `|`, `/`, `-` and `\`.
```cpp
#include <chrono>
#include <thread>
#include <cstdio>
#include <vector>

int main() {
    int load_percentage = 0;
    int iterator = 0;
    
    std::vector<char> loader = {'|', '/', '-', '\\'};
    
    return 0;
}
```

Now we code the main part, this is where the loading stuff happens. We create a `while` loop that sleeps for 100 millisecondss, prints the information onto the console, set the number within the array limit and then increament the `load_percentage`. So the while loop pretty much looks like this.
```cpp
while (load_percentage <= 100) {
    std::this_thread::sleep_for(std::chrono::milliseconds(100));
    printf("\rLoading %3d%% %c", load_percentage, loader[iterator]);
    fflush(stdout);

    iterator = (iterator + 1) % loader.size();

    ++load_percentage;
}
```

If this feels overwhelming, lemme explain it as simple as possible:
- Sleep for 100 milliseconds, we used chrono here.
- Print the loading information:
  - Set the cursor to the beginning of the line with `\r`
  - Print the numbers taking up 3 spaces with `%3d`, basically you print numbers with `%d` to print numbers without any space.
  - `%%` will print `%` on the console
  - Since our vector contains `char`s we used `%c`
- We also then need the print the information quickly onto the console and `printf()` basically sends the text information to `stdout`, so we force that to happen with `fflush(stdout)`
- Making sure we don't access the vector beyond it's size by using the modulous operator like so `var = var + 1 % array_size`
- Finally pre-increament our variable `load_percentage`.

Finally with extra information, altogether the code looks like this:
```cpp
#include <chrono>
#include <thread>
#include <cstdio>
#include <vector>

int main() {
    int load_percentage = 0;
    int iterator = 0;

    std::vector<char> loader = {'|', '/', '-', '\\'};

    printf("Loading...\n");
    while (load_percentage <= 100) {
        std::this_thread::sleep_for(std::chrono::milliseconds(100));
        printf("\rLoading %3d%% %c", load_percentage, loader[iterator]);
        fflush(stdout);
        
        iterator = (iterator + 1) % loader.size();
        
        ++load_percentage;
    }
    
    printf("\rLoading Completed!\n");
    
    return 0;
}

```

Okay bye, writing this poster after some time lol.
Anyways bye!
