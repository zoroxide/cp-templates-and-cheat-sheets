### **Sorting Algorithms**

**Images**
![image](https://github.com/user-attachments/assets/218924d3-989f-40d8-8045-7cab6f0d26d1)



**1. Quick Sort:**
```cpp
void quickSort(vector<int>& arr, int low, int high) {
    if (low < high) {
        int pi = partition(arr, low, high);
        quickSort(arr, low, pi - 1);
        quickSort(arr, pi + 1, high);
    }
}

int partition(vector<int>& arr, int low, int high) {
    int pivot = arr[high];
    int i = (low - 1);
    for (int j = low; j <= high - 1; j++) {
        if (arr[j] < pivot) {
            i++;
            swap(arr[i], arr[j]);
        }
    }
    swap(arr[i + 1], arr[high]);
    return (i + 1);
}
```

**2. Merge Sort:**
```cpp
void merge(vector<int>& arr, int l, int m, int r) {
    int n1 = m - l + 1;
    int n2 = r - m;
    vector<int> L(n1), R(n2);
    for (int i = 0; i < n1; i++) L[i] = arr[l + i];
    for (int j = 0; j < n2; j++) R[j] = arr[m + 1 + j];
    int i = 0, j = 0, k = l;
    while (i < n1 && j < n2) {
        if (L[i] <= R[j]) arr[k++] = L[i++];
        else arr[k++] = R[j++];
    }
    while (i < n1) arr[k++] = L[i++];
    while (j < n2) arr[k++] = R[j++];
}

void mergeSort(vector<int>& arr, int l, int r) {
    if (l < r) {
        int m = l + (r - l) / 2;
        mergeSort(arr, l, m);
        mergeSort(arr, m + 1, r);
        merge(arr, l, m, r);
    }
}
```

### **Graph Algorithms**

**1. Depth First Search (DFS):**
```cpp
void DFS(int v, vector<bool>& visited, const vector<vector<int>>& adj) {
    visited[v] = true;
    cout << v << " ";
    for (int i : adj[v])
        if (!visited[i])
            DFS(i, visited, adj);
}
```

**2. Breadth First Search (BFS):**
```cpp
void BFS(int s, const vector<vector<int>>& adj, int V) {
    vector<bool> visited(V, false);
    queue<int> q;
    visited[s] = true;
    q.push(s);
    while (!q.empty()) {
        s = q.front();
        cout << s << " ";
        q.pop();
        for (int i : adj[s]) {
            if (!visited[i]) {
                visited[i] = true;
                q.push(i);
            }
        }
    }
}
```

### **Dynamic Programming**

**1. Longest Common Subsequence (LCS):**
```cpp
int LCS(string X, string Y) {
    int m = X.size(), n = Y.size();
    vector<vector<int>> L(m + 1, vector<int>(n + 1));
    for (int i = 0; i <= m; i++) {
        for (int j = 0; j <= n; j++) {
            if (i == 0 || j == 0)
                L[i][j] = 0;
            else if (X[i - 1] == Y[j - 1])
                L[i][j] = L[i - 1][j - 1] + 1;
            else
                L[i][j] = max(L[i - 1][j], L[i][j - 1]);
        }
    }
    return L[m][n];
}
```

**2. Knapsack Problem:**
```cpp
int knapSack(int W, vector<int> wt, vector<int> val, int n) {
    vector<vector<int>> K(n + 1, vector<int>(W + 1));
    for (int i = 0; i <= n; i++) {
        for (int w = 0; w <= W; w++) {
            if (i == 0 || w == 0)
                K[i][w] = 0;
            else if (wt[i - 1] <= w)
                K[i][w] = max(val[i - 1] + K[i - 1][w - wt[i - 1]], K[i - 1][w]);
            else
                K[i][w] = K[i - 1][w];
        }
    }
    return K[n][W];
}
```

### **STL (Standard Template Library) Cheatsheet**

**1. Vectors:**
```cpp
vector<int> v;
v.push_back(10);     // Add 10 at the end
v.pop_back();        // Remove last element
int x = v.size();    // Size of the vector
int y = v[0];        // First element
sort(v.begin(), v.end()); // Sort the vector
```

**2. Sets:**
```cpp
set<int> s;
s.insert(1);         // Add element 1
s.erase(1);          // Remove element 1
int x = s.size();    // Size of the set
auto it = s.find(1); // Iterator to element 1
```

**3. Maps:**
```cpp
map<string, int> m;
m["key"] = 10;       // Insert key-value pair
m.erase("key");      // Remove key-value pair
int x = m["key"];    // Access value by key
int y = m.size();    // Size of the map
```

### **Bit Manipulation**

**1. Check if a number is odd or even:**
```cpp
bool isOdd(int x) { return x & 1; }
```

**2. Check if a number is a power of 2:**
```cpp
bool isPowerOfTwo(int x) { return x && !(x & (x - 1)); }
```

**3. Count number of 1 bits in an integer:**
```cpp
int countBits(int x) {
    int count = 0;
    while (x) {
        count += x & 1;
        x >>= 1;
    }
    return count;
}
```

**4. Find the most significant bit position:**
```cpp
int msbPos(int x) {
    int pos = -1;
    while (x) {
        x >>= 1;
        pos++;
    }
    return pos;
}
```

### **Substring Functions**

**1. Find substring:**
```cpp
size_t found = str.find("substring");
if (found != string::npos)
    cout << "Found at: " << found << endl;
```

**2. Extract substring:**
```cpp
string sub = str.substr(startIndex, length);
```

**3. Reverse a string:**
```cpp
string reverseString(string s) {
    reverse(s.begin(), s.end());
    return s;
}
```

### **Other Useful Functions**

**1. GCD:**
```cpp
int gcd(int a, int b) {
    if (b == 0)
        return a;
    return gcd(b, a % b);
}
```

**2. LCM:**
```cpp
int lcm(int a, int b) {
    return (a / gcd(a, b)) * b;
}
```

**3. Prime Check:**
```cpp
bool isPrime(int n) {
    if (n <= 1) return false;
    if (n <= 3) return true;
    if (n % 2 == 0 || n % 3 == 0) return false;
    for (int i = 5; i * i <= n; i += 6)
        if (n % i == 0 || n % (i + 2) == 0)
            return false;
    return true;
}
```

### **1. Sieve of Eratosthenes (Finding all primes up to n)**
```cpp
vector<bool> sieve(int n) {
    vector<bool> is_prime(n + 1, true);
    is_prime[0] = is_prime[1] = false;
    for (int i = 2; i * i <= n; i++) {
        if (is_prime[i]) {
            for (int j = i * i; j <= n; j += i)
                is_prime[j] = false;
        }
    }
    return is_prime;
}
```

### **2. Finding the Longest Increasing Subsequence (LIS)**
```cpp
int LIS(vector<int>& nums) {
    if (nums.empty()) return 0;
    vector<int> lis;
    for (int num : nums) {
        auto it = lower_bound(lis.begin(), lis.end(), num);
        if (it == lis.end())
            lis.push_back(num);
        else
            *it = num;
    }
    return lis.size();
}
```

### **3. Union-Find / Disjoint Set Union (DSU)**
```cpp
class DSU {
    vector<int> parent, rank;
public:
    DSU(int n) : parent(n), rank(n, 0) {
        iota(parent.begin(), parent.end(), 0);
    }

    int find(int x) {
        if (x != parent[x])
            parent[x] = find(parent[x]);
        return parent[x];
    }

    void unite(int x, int y) {
        int rootX = find(x), rootY = find(y);
        if (rootX != rootY) {
            if (rank[rootX] > rank[rootY])
                parent[rootY] = rootX;
            else if (rank[rootX] < rank[rootY])
                parent[rootX] = rootY;
            else {
                parent[rootY] = rootX;
                rank[rootX]++;
            }
        }
    }
};
```

### **4. Binary Exponentiation (Power Calculation)**
```cpp
long long binpow(long long a, long long b, long long m) {
    long long res = 1;
    while (b > 0) {
        if (b & 1)
            res = res * a % m;
        a = a * a % m;
        b >>= 1;
    }
    return res;
}
```

### **5. Maximum Subarray Sum (Kadane's Algorithm)**
```cpp
int maxSubArray(vector<int>& nums) {
    int max_so_far = nums[0], max_ending_here = nums[0];
    for (int i = 1; i < nums.size(); i++) {
        max_ending_here = max(nums[i], max_ending_here + nums[i]);
        max_so_far = max(max_so_far, max_ending_here);
    }
    return max_so_far;
}
```

### **6. Prefix Sum Array**
```cpp
vector<int> prefixSum(const vector<int>& arr) {
    vector<int> prefix(arr.size());
    prefix[0] = arr[0];
    for (int i = 1; i < arr.size(); i++)
        prefix[i] = prefix[i - 1] + arr[i];
    return prefix;
}
```

### **7. Finding the Lowest Common Ancestor (LCA) using Binary Lifting**
```cpp
class LCA {
    vector<vector<int>> up;
    vector<int> depth;
    int LOG;
public:
    LCA(int n, const vector<vector<int>>& adj) {
        LOG = 0;
        while ((1 << LOG) <= n) LOG++;
        up.assign(n, vector<int>(LOG));
        depth.resize(n);

        function<void(int, int)> dfs = [&](int v, int p) {
            up[v][0] = p;
            for (int i = 1; i < LOG; i++)
                up[v][i] = up[up[v][i - 1]][i - 1];
            for (int u : adj[v]) {
                if (u != p) {
                    depth[u] = depth[v] + 1;
                    dfs(u, v);
                }
            }
        };

        dfs(0, 0);
    }

    int getLCA(int u, int v) {
        if (depth[u] < depth[v]) swap(u, v);
        for (int i = LOG - 1; i >= 0; i--)
            if (depth[u] - (1 << i) >= depth[v])
                u = up[u][i];
        if (u == v) return u;
        for (int i = LOG - 1; i >= 0; i--)
            if (up[u][i] != up[v][i]) {
                u = up[u][i];
                v = up[v][i];
            }
        return up[u][0];
    }
};
```

### **8. Dijkstra's Algorithm (Shortest Path in Weighted Graph)**
```cpp
vector<int> dijkstra(int V, vector<vector<pair<int, int>>>& adj, int src) {
    vector<int> dist(V, INT_MAX);
    dist[src] = 0;
    priority_queue<pair<int, int>, vector<pair<int, int>>, greater<pair<int, int>>> pq;
    pq.push({0, src});

    while (!pq.empty()) {
        int u = pq.top().second;
        pq.pop();
        for (auto& edge : adj[u]) {
            int v = edge.first;
            int weight = edge.second;
            if (dist[u] + weight < dist[v]) {
                dist[v] = dist[u] + weight;
                pq.push({dist[v], v});
            }
        }
    }
    return dist;
}
```

### **9. Segment Tree for Range Sum Queries**
```cpp
class SegmentTree {
    vector<int> tree, arr;
    int n;
public:
    SegmentTree(const vector<int>& input) : n(input.size()), arr(input) {
        tree.resize(4 * n);
        build(0, 0, n - 1);
    }

    void build(int node, int start, int end) {
        if (start == end) {
            tree[node] = arr[start];
        } else {
            int mid = (start + end) / 2;
            build(2 * node + 1, start, mid);
            build(2 * node + 2, mid + 1, end);
            tree[node] = tree[2 * node + 1] + tree[2 * node + 2];
        }
    }

    void update(int idx, int val, int node, int start, int end) {
        if (start == end) {
            arr[idx] = val;
            tree[node] = val;
        } else {
            int mid = (start + end) / 2;
            if (start <= idx && idx <= mid)
                update(idx, val, 2 * node + 1, start, mid);
            else
                update(idx, val, 2 * node + 2, mid + 1, end);
            tree[node] = tree[2 * node + 1] + tree[2 * node + 2];
        }
    }

    int query(int L, int R, int node, int start, int end) {
        if (R < start || end < L)
            return 0;
        if (L <= start && end <= R)
            return tree[node];
        int mid = (start + end) / 2;
        int p1 = query(L, R, 2 * node + 1, start, mid);
        int p2 = query(L, R, 2 * node + 2, mid + 1, end);
        return p1 + p2;
    }

    void update(int idx, int val) { update(idx, val, 0, 0, n - 1); }
    int query(int L, int R) { return query(L, R, 0, 0, n - 1); }
};
```

### **10. Finding All Subarrays with Sum Equal to k**
```cpp
int subarraySum(vector<int>& nums, int k) {
    unordered_map<int, int> count;
    count[0] = 1;
    int sum = 0, ans = 0;
    for (int num : nums) {
        sum += num;
        if (count.find(sum - k) != count.end())
            ans += count[sum - k];
        count[sum]++;
    }
    return ans;
}
```

### input-output file stream
```cpp
ifstream inputFile("input.txt");
    ofstream outputFile("output.txt");

    if (!inputFile) {
        cerr << "Unable to open input file" << endl;
        return 1; // Return with error code
    }

    if (!outputFile) {
        cerr << "Unable to open output file" << endl;
        return 1; // Return with error code
    }

```
