---

title: "11_너비 우선 탐색(Breadth-First Search)"  
excerpt: "탐색, 그래프, 간선, 정점"  
toc: true  
toc_sticky: true  
toc_label: ""  
categories:  
 - algorithm_study  
tags:  
 - study
 - cpp
 - algorithm

last_modified_at: 2020-01-22
---

## 너비 우선 탐색(Depth-First Search)

- - -

### BFS란

DFS와 마찬가지로 컴포넌트의 모든 정점을 한 번씩 순회하는 용도이다. 그러나 DFS와 대립되는 성질을 갖고 있으며, 사용되는 곳도 다르다. 다만, 공통적으로는 컴포넌트의 개수를 세거나 각 컴포넌트의 크기를 구하는데는 사용이 가능하다.  

DFS가 깊이를 중시했던 것에 반해 BFS는 넓이를 중시하므로 모든 곳을 똑같이 조금씩 파게된다. 이러한 과정을 하기위해 BFS에서는 QUEUE를 사용한다.  

DFS의 과정을 살펴보면 queue와 함께 보면,

![1](https://user-images.githubusercontent.com/42687768/72882625-443bdb80-3d46-11ea-95fb-3e8969c974a6.JPG)
![1-1](https://user-images.githubusercontent.com/42687768/72882627-44d47200-3d46-11ea-8308-e5338ab51043.JPG)

0을 push해주고,  

![2](https://user-images.githubusercontent.com/42687768/72882628-44d47200-3d46-11ea-96af-8ab8ae63c952.JPG)
![2-1](https://user-images.githubusercontent.com/42687768/72882629-44d47200-3d46-11ea-932f-e76eea6411b1.JPG)

0을 pop할 때, 0과 연결된 노드들을 전부 push해준다. 여기서 push된 노드는 1,2이다.  

![3](https://user-images.githubusercontent.com/42687768/72882630-44d47200-3d46-11ea-8a8a-2776011b4a7c.JPG)
![3-1](https://user-images.githubusercontent.com/42687768/72882631-456d0880-3d46-11ea-86c7-5c51fe36cc69.JPG)

queue에 따라 순서대로, 1,2를 pop해주면 마찬가지로 연결된 노드들을 push해주게 된다. 여기서는 1을 pop할 때, 3,5가 push, 2를 pop할 떄, 6,8이 push 되었다.  

![4](https://user-images.githubusercontent.com/42687768/72882632-456d0880-3d46-11ea-8960-4998e630e18a.JPG)
![4-1](https://user-images.githubusercontent.com/42687768/72882634-456d0880-3d46-11ea-9457-6a682d03eae6.JPG)

마찬가지로 3을 pop하게 되면, 연결된 4가 push되고, 이어서 5가 pop되면, 이어져있는 4를 push해야하지만 현재 queue에 존재하므로 push하지 않았다. 역시 같은 과정으로 6이 push 되었을 때, 7이 push되며, 연결된 8은 이미 queue에 존재하므로 push되지 않는다.  

이러한 과정을 보았을 때, BFS는 깊이를 단계별로 나눈 것을 볼 수 있다. 즉, 시작점으로부터의 단계를 구했을때, k단계의 최단거리는 k이다.  

### 기본 그래프(BFS) 클래스  

```cpp
#include <iostream>
#include <vector>
#include <queue>
#include <algorithm>
using namespace std;
 
class Graph{
public:
    int N; // 정점의 개수
    vector<vector<int>> adj; // 인접 리스트
 
    // 생성자
    Graph(): N(0){}
    Graph(int n): N(n){ adj.resize(N); }
 
    // 간선 추가 함수
    void addEdge(int u, int v){
        adj[u].push_back(v);
        adj[v].push_back(u);
    }
 
    // 모든 리스트의 인접한 정점 번호 정렬
    void sortList(){
        for(int i=0; i<N; i++)
            sort(adj[i].begin(), adj[i].end());
    }
 
    // 너비 우선 탐색
    void bfs(){
        vector<bool> visited(N, false); // 방문 여부를 저장하는 배열
        queue<int> Q;
        Q.push(0);
        visited[0] = true;
        // 탐색 시작
        while(!Q.empty()){
            int curr = Q.front();
            Q.pop();
            cout << "node " << curr << " visited" << endl;
            for(int next: adj[curr]){
                if(!visited[next]){
                    visited[next] = true;
                    Q.push(next);
                }
            }
        }
    }
};
 
int main(){
    Graph G(9);
    G.addEdge(0, 1);
    G.addEdge(0, 2);
    G.addEdge(1, 3);
    G.addEdge(1, 5);
    G.addEdge(3, 4);
    G.addEdge(4, 5);
    G.addEdge(2, 6);
    G.addEdge(2, 8);
    G.addEdge(6, 7);
    G.addEdge(6, 8);
    G.sortList();
    G.bfs();
}
```

### 추가 그래프 클래스  

- 깊이 구하기  

```cpp
  // 너비 우선 탐색
    void bfs(){
        vector<bool> visited(N, false); // 방문 여부를 저장하는 배열
        queue<int> Q;
        Q.push(0);
        visited[0] = true;
 
        // 탐색 시작
        int level = 0;
        while(!Q.empty()){
            int qSize = Q.size();
            cout << "------ level " << level << " ------" << endl;
            for(int i=0; i<qSize; i++){
                int curr = Q.front();
                Q.pop();
                cout << "node " << curr << " visited" << endl;
                for(int next: adj[curr]){
                    if(!visited[next]){
                        visited[next] = true;
                        Q.push(next);
                    }
                }
            }
            level++;
        }
    }
```

### 추천 문제

[1260번: DFS와 BFS]({{ site.url }}{{ site.baseurl }}/algorithm_solving/BOJ-1260)  
[2644번: 촌수계산]({{ site.url }}{{ site.baseurl }}/algorithm_solving/BOJ-2644)  
[2178번: 미로 탐색]({{ site.url }}{{ site.baseurl }}/algorithm_solving/BOJ-2178)  
[6593번: 상범 빌딩]
[5427번: 불 (★)]
[3055번: 탈출 (★)]
[2206번: 벽 부수고 이동하기 (★)]
[7576번: 토마토]
[7562번: 나이트의 이동]
[5014번: 스타트링크]
[1697번: 숨바꼭질]
[16397번: 탈출]
[9019번: DSLR (★)]
[1525번: 퍼즐 (★)]
[1039번: 교환 (★)]
