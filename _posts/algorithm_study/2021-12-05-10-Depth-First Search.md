---

title: "10_깊이 우선 탐색(Depth-First Search)"  
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

last_modified_at: 2020-01-05
---

## 깊이 우선 탐색(Depth-First Search)

- - -

### 그래프란

그래프에서 탐색은 크게 DFS와 BFS 두 가지로 나뉜다. 그 중 DFS는 깊이 우선 탐색(Depth First Search)은 말 그대로 깊이를 우선으로 탐색해준다.  
조금 더 다루기 전에 그래프(Graph)라는 자료구조에 대해 알아보자면, 그래프의 정의는 정점(vertex)와 간선(edge)의 집합이다.  
간선은 두 정점을 이어주는 역활을 하며, 자기자신을 이을 수도 있고, 간선에 방향이 있기도 하고 없기도 하며, 가중치가 있기도하고 없기도 하는등 다양한 형태의 그래프가 있다.  

`그래프` : 정점 + 간선  
`차수(degree)` : 정점과 이어진 간선의 갯수  
`노드(node)` : 정점의 다른 말

#### 그래프의 종류  

- **무방향 그래프와 방향 그래프**
간선에 방향이 있고 없고의 차이, `사이클`(간선을 따라가다 시작한 정점으로 돌아오는 경로)

- **가중치 그래프**  
간선들에 가중치가 있는 것, 가중치로서는 비용, 거리, 대역폭등 다양함  

- **멀티 그래프**  
똑같은 정점 쌍(A,B) 사이에 간선이 여러개 일 수 있는 것.

### DFS란

그래프 순회 : 모든 정점을 한 번 씩만 방문해 보는 것  
DFS는 이름에 걸맞게 한 우물만 깊게 파다가 막히면 그제서야 돌아가서 다른 우물을 파는 성향이 있다. 그리고 이는 정반대 성질을 가진 BFS와의 차이점으로 이루어진다.  
DFS는 만약 어떤 정점에서 더 이상 방문할 노드가 없다면 자신을 불렀던 정점으로 돌아가는 데, 이를 구현하기 위해서 **스택**을 사용한다.  
방문하는 순서대로 정점을 스택에 쌓고, 방문이 끝나면 스택에서 pop하는 형태로 구현가능 하다. 그리고 밑의 기본구조는 재귀함수로 이루어져 있는데, 재귀함수가 대표적인 스택 메모리 공간에 쌓아 올려지는 구조이므로 재귀함수를 이용해 이것을 구현했다.  

일단 DFS의 과정과 해당 스택을 보면  

![1](https://user-images.githubusercontent.com/42687768/71779663-6ec62e80-2ffb-11ea-87ba-78512cb5a915.JPG)  

![1](https://user-images.githubusercontent.com/42687768/72894756-58400700-3d5f-11ea-9bfa-d0ecd7af68b8.JPG)  
0을 push 해주고

![2](https://user-images.githubusercontent.com/42687768/71779666-71c11f00-2ffb-11ea-80aa-e41371bb449f.JPG)  

![2](https://user-images.githubusercontent.com/42687768/72894757-58400700-3d5f-11ea-9a17-30c0a1d7efa9.JPG)  
이어서 1을 push  

![3](https://user-images.githubusercontent.com/42687768/71779667-71c11f00-2ffb-11ea-9b91-a794231776d5.JPG)

![3](https://user-images.githubusercontent.com/42687768/72894758-58d89d80-3d5f-11ea-836b-faa85f449219.JPG)  
마찬가지로 연결되있는 노드인 3을 push해준다.  

![4](https://user-images.githubusercontent.com/42687768/71779668-71c11f00-2ffb-11ea-9e99-50354f298273.JPG)

![4](https://user-images.githubusercontent.com/42687768/72894759-58d89d80-3d5f-11ea-90cf-3b2d5f8619e9.JPG)  
이어서 4번 push

![5](https://user-images.githubusercontent.com/42687768/71779669-7259b580-2ffb-11ea-9db4-b18ae5319709.JPG)

![5](https://user-images.githubusercontent.com/42687768/72894760-58d89d80-3d5f-11ea-9cda-f987d2a8e0cf.JPG)

5번 node까지 push해주면 더이상 갈수 있는 길이 없으므로

![6-1](https://user-images.githubusercontent.com/42687768/71779671-72f24c00-2ffb-11ea-9970-68962fcb961d.JPG)

![6-1](https://user-images.githubusercontent.com/42687768/72894761-59713400-3d5f-11ea-9ea0-b6ce37f012ce.JPG)
![6-2](https://user-images.githubusercontent.com/42687768/72894763-59713400-3d5f-11ea-874e-81a5bec60ac1.JPG)
![6-3](https://user-images.githubusercontent.com/42687768/72894765-59713400-3d5f-11ea-976c-8de59a0b9562.JPG)
![6-4](https://user-images.githubusercontent.com/42687768/72894766-5a09ca80-3d5f-11ea-9397-f778b79812da.JPG)
![6-5](https://user-images.githubusercontent.com/42687768/72894767-5a09ca80-3d5f-11ea-830d-7c233618a4b3.JPG)

탐색을 안한 2번 노드에 연결된 0번 까지 스택을 pop해준뒤 (이 과정에서 계속 방문하지 않은 노드가 있는지 검색한다.) 2번 노드를 push해준다.  

![6](https://user-images.githubusercontent.com/42687768/71779670-7259b580-2ffb-11ea-99fa-23e1123e796f.JPG)

![7](https://user-images.githubusercontent.com/42687768/72894769-5a09ca80-3d5f-11ea-9270-a3162350bcbb.JPG)

마찬가지로 6번 push

![8](https://user-images.githubusercontent.com/42687768/71779672-72f24c00-2ffb-11ea-82a6-98d3e77e964f.JPG)

![8](https://user-images.githubusercontent.com/42687768/72894770-5a09ca80-3d5f-11ea-9f4b-86e8638eed22.JPG)  

7번 push를 해준뒤 다음 연결된 노드가 없으므로

![9](https://user-images.githubusercontent.com/42687768/71779665-71c11f00-2ffb-11ea-9c26-5bfa95a1b4ee.JPG)

![9-1](https://user-images.githubusercontent.com/42687768/72894771-5aa26100-3d5f-11ea-98e2-b221f6dcb846.JPG)

7번을 pop해주고

![9-2](https://user-images.githubusercontent.com/42687768/72894773-5aa26100-3d5f-11ea-90db-0ab1977e86ef.JPG)

6과 연결된 8을 푸쉬해준다.  

![9-3](https://user-images.githubusercontent.com/42687768/72894774-5aa26100-3d5f-11ea-9197-48b5edb6df22.JPG)
![9-4](https://user-images.githubusercontent.com/42687768/72894776-5aa26100-3d5f-11ea-8cbe-57c79e2b952f.JPG)
![9-5](https://user-images.githubusercontent.com/42687768/72894777-5b3af780-3d5f-11ea-9c40-abb65f978ea1.JPG)
![9-6](https://user-images.githubusercontent.com/42687768/72894778-5bd38e00-3d5f-11ea-99f0-376c6150a4e2.JPG)

나머지는 전부 pop

이처럼 간선을 따라 깊이 우선으로 계속 탐색하다 막히면 다시 돌아와서 같은 방식으로 탐색해준다. 특히 마지막에 7번 노드의 탐색이 끝나고 6번 노드로 돌아와 8번 노드를 탐색해주는 것을 보면 이해가 쉽다.  

### 기본 그래프(DFS) 클래스  

```cpp
#include <vector>
#include <algorithm>
using namespace std;
 
class Graph{
public:
    int N; // 정점의 개수
    vector<vector<int>> adj; // 인접 리스트
    vector<bool> visited; // 방문 여부를 저장하는 배열
 
    // 생성자
    Graph(): N(0){}
    Graph(int n): N(n){ 
        adj.resize(N);
        visited.resize(N);
    }
 
    // 간선 추가 함수 (무방향)
    void addEdge(int u, int v){
        adj[u].push_back(v);
        adj[v].push_back(u);
    }
 
    // 모든 리스트의 인접한 정점 번호 정렬
    void sortList(){
        for(int i=0; i<N; i++)
            sort(adj[i].begin(), adj[i].end());
    }
 
    // 깊이 우선 탐색
    void dfsStart(){
        fill(visited.begin(), visited.end(), false);
        dfs(0);
    }
 
private:
    void dfs(int curr){
        visited[curr] = true;
        cout << "node " << curr << " visited" << endl;
        for(int next: adj[curr])
            if(!visited[next]) dfs(next);
    }
};
```

### 추가 그래프 클래스

- 컴포넌트 갯수 추가 (dfsStart() 변화)

```cpp
// 모든 정점을 깊이 우선 탐색하고 컴포넌트 개수 반환
    int dfsAll(){
        int components = 0;
        fill(visited.begin(), visited.end(), false);
        for(int i=0; i<N; i++){
            if(!visited[i]){
                cout << "-- new DFS begins --" << endl;
                dfs(i);
                components++;
            }
        }
        return components;
    }

```

- 각 컴포넌트의 크기(정점의 개수)  

```cpp
    // 모든 정점을 깊이 우선 탐색하고 컴포넌트 개수 반환
    int dfsAll(){
        int components = 0;
        fill(visited.begin(), visited.end(), false);
        for(int i=0; i<N; i++){
            if(!visited[i]){
                cout << "-- new DFS begins --" << endl;
                int nodes = dfs(i);
                components++;
                cout << "size: " << nodes << endl << endl;
            }
        }
        return components;
    }
 
    // curr부터 방문한 정점 개수를 반환
    int dfs(int curr){
        int nodes = 1;
        visited[curr] = true;
        cout << "node " << curr << " visited" << endl;
        for(int next: adj[curr])
            if(!visited[next]) nodes += dfs(next);
        return nodes;
    }
```

dfs()함수를 보면, 방문하지 않은 노드에 들어갈때마다 1씩 증가가되는 재귀함수를 사용해서 표현한 것이다.  

그리고 이러한 DFS의 시간 복잡도는 O(V+E) 즉, 정점 + 간선의 시간 복잡도를 가진다.  

### 추천 문제

[11724번: 연결 요소의 개수]({{ site.url }}{{ site.baseurl }}/algorithm_solving/BOJ-11724)  
[1012번: 유기농 배추]({{ site.url }}{{ site.baseurl }}/algorithm_solving/BOJ-1012)  
[1743번: 음식물 피하기]({{ site.url }}{{ site.baseurl }}/algorithm_solving/BOJ-1743)  
[2667번: 단지번호붙이기]({{ site.url }}{{ site.baseurl }}/algorithm_solving/BOJ-2667)  
[2583번: 영역 구하기]  
[10026번: 적록색약]  
[11403번: 경로 찾기 (★)]({{ site.url }}{{ site.baseurl }}/algorithm_solving/BOJ-11403)  
[2468번: 안전 영역 (★)]  
[10552번: DOM]  
[9466번: 텀 프로젝트]({{ site.url }}{{ site.baseurl }}/algorithm_solving/BOJ-9466)  
[10265번: MT (★)]  
