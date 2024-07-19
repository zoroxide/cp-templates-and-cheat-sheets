### Graph Algorithms
**1. Depth First Search (DFS):**
```cpp
void dfs(int node, const std::vector<std::vector<int>>& adj, std::vector<bool>& visited)
{
    visited[node] = true;
    for (int neighbor : adj[node])
    {
        if (!visited[neighbor])
        {
            dfs(neighbor, adj, visited);
        }
    }

    // Usage example
    // std::vector<std::vector<int>> adj(n); // adjacency list of graph
    // std::vector<bool> visited(n, false);
    // dfs(start_node, adj, visited);
}
 ```
***2. Breadth First Search (BFS):***
```cpp
void bfs(int start, const std::vector<std::vector<int>>& adj, std::vector<bool>& visited)
{
    std::queue<int> q;
    q.push(start);
    visited[start] = true;
    while (!q.empty())
    {
        int node = q.front();
        q.pop();
        for (int neighbor : adj[node])
        {
            if (!visited[neighbor])
            {
                q.push(neighbor);
                visited[neighbor] = true;
            }
        }
    }

    // Usage example
    // std::vector<std::vector<int>> adj(n); // adjacency list of graph
    // std::vector<bool> visited(n, false);
    // bfs(start_node, adj, visited);
}
```
### Bit Manipulation
***1. Check if a number is odd or even:***
```cpp
bool isOdd(int x) { return x & 1; }
2. Check if a number is a power of 2:
bool isPowerOfTwo(int x) { return x && !(x & (x - 1)); }
3. Count number of 1 bits in an integer:
int countBits(int x) {
 int count = 0;
 while (x) {
 count += x & 1;
 x >>= 1;
 }
 return count;
}
```
***4. Find the most significant bit position:***
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
## Other Useful Functions

***1. frequency of elements***
```cpp
unordered_map<int, int> freq;
for (auto &x : vec) freq[x]++;
```
***3. Prime Check:***
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
***2. Finding the Longest Increasing Subsequence (LIS)***
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
***10. Finding All Subarrays with Sum Equal to k***
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

***11. Two Sum***
```cpp
// Function to find two numbers that add up to a target
bool twoSum(const std::vector<int>& arr, int target)
{
    int left = 0, right = arr.size() - 1;
    while (left < right)
    {
        int sum = arr[left] + arr[right];
        if (sum == target)
        {
            return true;
        }
        else if (sum < target)
        {
            ++left;
        }
        else
        {
            --right;
        }
    }
    return false;
}
```

***12. prefixsum***
```cpp
// Function to compute prefix sums of an array
std::vector<int> prefixSum(const std::vector<int>& arr)
{
    int n = arr.size();
    std::vector<int> prefix(n);
    prefix[0] = arr[0];
    for (int i = 1; i < n; ++i)
    {
        prefix[i] = prefix[i-1] + arr[i];
    }
    return prefix;
}
```

### Dynamic Programming
***1. Longest Common Subsequence (LCS):***
```cpp
int LCS(string X, string Y)
{
    int m = X.size(), n = Y.size();
    vector<vector<int>> L(m + 1, vector<int>(n + 1));
    for (int i = 0; i <= m; i++)
    {
        for (int j = 0; j <= n; j++)
        {
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
### ***input-output file stream***
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
