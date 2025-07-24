---
title: "금광 세그 튜토리얼"
date: 2024-07-23 11:47:53
categories: Algorithm

tags:

- 세그먼트 트리
- 최대 부분 배열 문제
- 알고리즘
- 튜토리얼

---

## 문제

https://www.acmicpc.net/problem/16993

## 틀린 풀이

https://www.acmicpc.net/problem/10999

위 문제처럼 문제를 푸는것은 안돼요! 이것은 최대 구간합을 구하지 못해, 오히려 그냥 누적합으로 구간합을 구하는 것이 더 빨라요!

그렇다고 해서 구간합을 누적합을 사용하고 최대값 - 최소값을 하면 최소값이 최대값의 오른쪽에 있을 수 있다는 반례가 있습니다!

## 금광 세그를 이용한 풀이

그렇다면 이 문제는 어떻게 해결해야 할까요? 이 문제를 해결할 수 있는 테크닉을 금광 세그라고 합니다. 이 문제를 풀려면 마치 이분탐색을 하는 것처럼 풀어야 합니다. 

f(i, j) = A[i], A[i+1], ..., A[j]에서 가장 큰 연속합 (1 ≤ i ≤ j ≤ N)이라 정의하겠습니다! [히스토그램에서 가장 큰 직사각형](https://www.acmicpc.net/problem/6549)을 세그먼트 트리로 풀어보신 분들은 그 문제를 어떻게 풀었는지 다시 한번 생각해 봅시다. 문제를 두 작은 문제로 계속 변환하여 이분탐색처럼 해결했죠? 이 문제도 비슷합니다! 문제를 더 작은 문제 2개로 분활하여 문제를 푸는 것입니다!

mid = (i + j) / 2

f(i, j) = max(f(i, mid), f(mid + 1, j), (두 케이스를 합친 경우))

## 소스코드
```cpp
#include<bits/stdc++.h>
using namespace std;
#define ll long long int
ll n, m;
vector<ll> arr;
typedef struct Node {
    ll leftMax, rightMax, _max, psum;
};
vector<Node> tree;

Node Merge(Node left, Node right) {
    Node res;
    res.leftMax = max(left.leftMax, left.psum + right.leftMax);
    res.rightMax = max(right.rightMax, right.psum + left.rightMax);
    res._max = max({left._max, right._max, left.rightMax + right.leftMax});
    res.psum = left.psum+ right.psum;
    return res;
}

void Init(ll start, ll end, ll node) {
    if (start == end) {
        tree[node].rightMax = arr[start];
        tree[node].leftMax = arr[start];
        tree[node]._max = arr[start];
        tree[node].psum = arr[start];
        return;
    }
    ll mid = (start + end) / 2;
    Init(start, mid, node * 2);
    Init(mid + 1, end, node * 2 + 1);
    tree[node] = Merge(tree[node * 2], tree[node * 2 + 1]);
}

Node Query(ll start, ll end, ll left, ll right, ll node) {
    if ((end < left) || (right < start)) {
        Node res;
        res.rightMax = INT_MIN;
        res.leftMax = INT_MIN;
        res._max = INT_MIN;
        res.psum = INT_MIN;
        return res;
    }
    if ((left <= start) && (end <= right)) {
        return tree[node];
    }
    ll mid = (start + end) / 2;
    return Merge(Query(start, mid, left, right, node * 2), Query(mid + 1, end, left, right, node * 2 + 1));
}

int main(void) {
    ios::sync_with_stdio(0);cin.tie(0);cout.tie(0);
    cin >> n;
    arr.resize(n);
    tree.resize(n * 4);
    for (ll i = 0; i < n; i++) {
        cin >> arr[i];
    }
    Init(0, n - 1, 1);
    cin >> m;
    for (ll i = 0; i < m; i++) {
        ll a, b;
        cin >> a >> b;
        Node res = Query(0, n - 1, a - 1, b - 1, 1);
        cout << res._max << "\n";
    }
}
