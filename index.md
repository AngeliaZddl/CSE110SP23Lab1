---
layout: default
---

# About Me

**Name:** *Angelia Zhang*

**Current City:** *San Diego*

## Favorite

### Cat

***Love Cat But Have an Allergy to Cat Fur***

~~Too Poor To Feed One~~

[cat](/cat.jpg)

### Hotpot

***The spicier the better I like it***

[Hotpot](/Hotpot.jpg)

### Motto

> Time Is Money.

## Programming

* An exercise about from [LeetCode](https://leetcode.com/problems/reorder-routes-to-make-all-paths-lead-to-the-city-zero/description/).*

> 1466. Reorder Routes to Make All Paths Lead to the City Zero

### Solve it by Queue learned from CSE100

```
class Solution {
public:
    int minReorder(int n, vector<vector<int>>& connections) {
        int count = 0;
        vector<vector<int>> gh(n);

        for (auto pair : connections) {
            int from = pair[0];
            int to = pair[1];
            gh[from].push_back(to);
            gh[to].push_back(-from);
        }
        queue<int> q;
        q.push(0);

        vector<bool> visited(n, false);
        visited[0] = true;

        while (!q.empty()) {
            int curr = q.front();
            q.pop();
            for (int neighbor : gh[curr]) {
                if (!visited[abs(neighbor)]) {
                    if (neighbor > 0) {
                        count++;
                    }
                    visited[abs(neighbor)] = true;
                    q.push(abs(neighbor));
                }
            }
        }
        return count;
    }
};
```

### Solve it by Stack

***Using stack would be much faster and take less memory.***

```
class Solution {
public:
    int minReorder(int n, vector<vector<int>>& connections) {
        int count = 0;
        vector<vector<int>> graph(n);
        bitset<100000> visited(0);

        for (auto& connection : connections) {
            graph[connection[0]].push_back(connection[1]);
            graph[connection[1]].push_back(-connection[0]); // Reverse direction
        }

        vector<int> stack;
        stack.push_back(0);

        while (!stack.empty()) {
            int curr = stack.back();
            stack.pop_back();

            if (visited[curr + 50000]) {
                continue;
            }
            visited[curr + 50000] = true;

            for (int neighbor : graph[curr]) {
                if (!visited[abs(neighbor) + 50000]) {
                    if (neighbor > 0) {
                        count++; // Need to reverse direction
                    }
                    stack.push_back(abs(neighbor));
                }
            }
        }

        return count;
    }
};
```

## My Github Page in the Past

*I learned Github from CSE15L.*

Noted some git commands in my [lab report]((https://angeliazddl.github.io/CSE15L_Lab_Report/)).

## Traveling List in Summer Vocation

+ China
    + HongKong
    + Sichuan
    + Shaanxi
+ Japan
    + Tokyo
    + Kyoto
    + Osaka

## TODO Before Being Dead

1. Bungee jumping
2. Travel around Europe
3. Buy a house on coastal cliff
4. To be continuous...

## TODO Recently

- [ ] Rich my resume
- [ ] Find a internship
- [ ] Read two rearch papers about AI every week
- [x] Do 2 exercises on LeetCode every week