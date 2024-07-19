### Containers

#### Sequence Containers
- **Vector (`std::vector`)**
  - Dynamic array.
  - `push_back(value)`, `pop_back()`, `front()`, `back()`, `size()`, `clear()`, `insert(position, value)`, `erase(position)`

- **Deque (`std::deque`)**
  - Double-ended queue.
  - `push_back(value)`, `push_front(value)`, `pop_back()`, `pop_front()`, `front()`, `back()`, `size()`

- **List (`std::list`)**
  - Doubly linked list.
  - `push_back(value)`, `push_front(value)`, `pop_back()`, `pop_front()`, `insert(position, value)`, `erase(position)`, `size()`

- **Array (`std::array`)**
  - Fixed-size array.
  - `at(index)`, `front()`, `back()`, `size()`, `fill(value)`

#### Associative Containers
- **Set (`std::set`)**
  - Unique sorted elements.
  - `insert(value)`, `erase(value)`, `find(value)`, `count(value)`, `size()`

- **Unordered Set (`std::unordered_set`)**
  - Unique elements, no particular order.
  - `insert(value)`, `erase(value)`, `find(value)`, `count(value)`, `size()`

- **Map (`std::map`)**
  - Key-value pairs, sorted by keys.
  - `insert({key, value})`, `erase(key)`, `find(key)`, `operator[key]`, `size()`

- **Unordered Map (`std::unordered_map`)**
  - Key-value pairs, no particular order.
  - `insert({key, value})`, `erase(key)`, `find(key)`, `operator[key]`, `size()`







#### Other Containers
- **Stack (`std::stack`)**
  - LIFO (Last In First Out).
  - `push(value)`, `pop()`, `top()`, `size()`, `empty()`

- **Queue (`std::queue`)**
  - FIFO (First In First Out).
  - `push(value)`, `pop()`, `front()`, `back()`, `size()`, `empty()`

- **Priority Queue (`std::priority_queue`)**
  - Max heap by default.
  - `push(value)`, `pop()`, `top()`, `size()`, `empty()`

### Algorithms
- **Sorting**
  - `sort(begin, end)`, `sort(begin, end, comparator)`
  - `stable_sort(begin, end)`, `stable_sort(begin, end, comparator)`

- **Searching**
  - `binary_search(begin, end, value)`
  - `lower_bound(begin, end, value)`
  - `upper_bound(begin, end, value)`

- **Permutations**
  - `next_permutation(begin, end)`
  - `prev_permutation(begin, end)`

- **Set Operations**
  - `set_union(begin1, end1, begin2, end2, output_iterator)`
  - `set_intersection(begin1, end1, begin2, end2, output_iterator)`
  - `set_difference(begin1, end1, begin2, end2, output_iterator)`

- **Others**
  - `reverse(begin, end)`
  - `rotate(begin, middle, end)`
  - `unique(begin, end)`








### Utility Functions
- **Pairs (`std::pair`)**
  - `make_pair(first, second)`
  - `pair.first`, `pair.second`

- **Tuples (`std::tuple`)**
  - `make_tuple(values...)`
  - `std::get<index>(tuple)`
  - `std::tie(vars...) = tuple`

### Useful Tricks
- **Lambda Functions**
  ```cpp
  auto comp = [](int a, int b) { return a > b; };
  sort(vec.begin(), vec.end(), comp);
  ```

- **Fast I/O**
  ```cpp
  ios::sync_with_stdio(false);
  cin.tie(0);
  ```

- **Counting frequency of elements**
  ```cpp
  unordered_map<int, int> freq;
  for (auto &x : vec) freq[x]++;
  ```

- **Finding GCD and LCM**
  ```cpp
  #include <numeric>
  int g = gcd(a, b);
  int l = lcm(a, b);
  ```

- **Bit Manipulation**
  ```cpp
  int bit_count = __builtin_popcount(x); // count set bits
  int leading_zeros = __builtin_clz(x); // leading zeros
  int trailing_zeros = __builtin_ctz(x); // trailing zeros
  ```


- **Initialize 2D Vector**
  ```cpp
  vector<vector<int>> matrix(n, vector<int>(m, initial_value));
  ```

### Debugging Tips
- **Print Container Elements**
  ```cpp
  for (auto &x : container) cout << x << " ";
  ```

- **Print Pair or Tuple**
  ```cpp
  cout << "(" << p.first << ", " << p.second << ")";
  cout << "(" << get<0>(t) << ", " << get<1>(t) << ")";
  ```

