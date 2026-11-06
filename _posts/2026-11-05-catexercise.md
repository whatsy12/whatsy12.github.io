---
title: "고양이 운동 문제풀이 [C++]"
date: 2026-11-05 14:32:17
categories:
- JOI
tags:
- LCA
- tree
- joi
---

https://jungol.co.kr/problem/5834

장애물이 설치되어 있는 노드를 기점으로 트리를 서브트리로 분활한다면 항상 고양이가 있는 노드가 포함되어 있는 서브트리에서 최대의 높이를 가진 정점은 고양이가 현재 있는 노드다. 최소 높이부터 유파로 서브트리의 크기를 늘리는 방법으로 접근하자. 두 서브트리를 합칠 때, 각 서브트리에 포함되는 최대 높이의 정점들 사이의 거리를 스파스 테이블로 효율적으로 구한다면 AC를 받을 수 있다.

```cpp
#include<bits/stdc++.h>
using namespace std;
#define ll long long
#define pii pair<ll, ll>
#define x first
#define y second

ll n;
vector<pii> v;
vector<ll> d;
vector<vector<ll>> arr;
vector<ll> par;
vector<ll> cache;
vector<ll> depth;
vector<vector<ll>> sparse;
vector<vector<ll>> dist;
ll SZ;

ll Find(ll cur) {
    if (cur == par[cur]) return cur;
    return par[cur] = Find(par[cur]);
}

bool Union(ll a, ll b) {
    a = Find(a);
    b = Find(b);
    if (a == b) return false;
    par[a] = b;
    return true;
}

void Sparse() {
    for (ll i = 1; i <= SZ; i++) {
        for (ll j = 0; j < n; j++) {
            sparse[j][i] = sparse[sparse[j][i - 1]][i - 1];
            dist[j][i] = dist[j][i - 1] + dist[sparse[j][i - 1]][i - 1];
        }
    }
}

ll Dst(ll a, ll b) {
    if (depth[a] > depth[b]) swap(a, b);
    ll cost = 0;
    for (ll i = SZ; i >= 0; i--) {
        if (depth[sparse[b][i]] >= depth[a]) {
            cost += dist[b][i];
            b = sparse[b][i];
        }
    }
    if (a == b) return cost;
    for (ll i = SZ; i >= 0; i--) {
        if (sparse[a][i] != sparse[b][i]) {
            cost += dist[a][i];
            cost += dist[b][i];
            a = sparse[a][i];
            b = sparse[b][i];
        }
    }
    cost += 2;
    return cost;
}

int main(void) {
    cin >> n;
    for (SZ = 1; (1 << SZ) < n; SZ++);
    sparse.resize(n, vector<ll> (SZ + 1));
    dist.resize(n, vector<ll> (SZ + 1));
    v.resize(n);
    d.resize(n);
    arr.resize(n);
    par.resize(n);
    cache.resize(n, 0);
    iota(par.begin(), par.end(), 0);
    for (ll i = 0; i < n; i++) {
        cin >> v[i].x;
        v[i].y = i;
        d[i] = v[i].x;
    }
    sort(v.begin(), v.end());
    for (ll i = 0; i < n - 1; i++) {
        ll a, b;
        cin >> a >> b;
        a--;
        b--;
        arr[a].emplace_back(b);
        arr[b].emplace_back(a);
    }
    depth.resize(n);
    queue<ll> q;
    queue<ll> dpth;
    vector<bool> visited(n);
    q.emplace(0);
    dpth.emplace(0);
    sparse[0][0] = 0;
    dist[0][0] = 0;
    while (!q.empty()) {
        ll cur = q.front();
        q.pop();
        depth[cur] = dpth.front();
        dpth.pop();
        visited[cur] = true;
        for (auto i : arr[cur]) {
            if (visited[i]) continue;
            sparse[i][0] = cur;
            dist[i][0] = 1;
            visited[i] = true;
            q.emplace(i);
            dpth.emplace(depth[cur] + 1);
        }
    }
    Sparse();
    for (ll i = 0; i < n; i++) {
        ll cur = v[i].y;
        for (auto j : arr[cur]) {
            if (d[j] < d[cur]) {
                ll idx = Find(j);
                cache[cur] = max(cache[cur], cache[idx] + Dst(idx, cur));
                Union(idx, cur);
            }
        }
        if (i == n - 1) cout << cache[cur];
    }
}
```