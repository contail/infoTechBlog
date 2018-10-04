+++
date = "2018-10-04T03:14:45+00:00"
draft = true
title = "Union find 알고리즘"

+++
disjoint set 이라고도 불리며 서로소 집합이라고도 한다.

우선 서로소 집합이라는 표현부터 알아봐야 한다.

![](https://app.forestry.io/sites/sxhm9iwjz9tswq/body-media//uploads/union.jpeg)

노드를 트리구조로 만들기

    int parent[100];
    int size[100]
    for(int i=0; i<100; i++){
        parent[i] = i;
        size[i] = 1;    
    }
    
    //편의상 자기 자신의 부모는 자기 자신이 되도록 초기화 하기 

간단하게 Union(x , y)를 하게 되면 x 자식에 y가 붙여지게 된다. Find(x)를 하게 되면 x를 포함한 트리의 루트를 알 수 있게 한다.

이러한 유니온 파인드는 두가지 연산을 지원한다

* Find 연산

        void find(int x){
          if(x == parent[x])
              return x;
          else
              return parent[x] = find(parent[x]);
        }
* Union 연산

       void union(int p, int q){
      
          //해당 p의 루트를 찾아준다.
          p = find(p);
      
          //해당 q의 루트를 찾아준다.
          q = find(q);
      
          if(p == q)
          return;
          parent[q] = p;
       }

위에 방법은 union을 하는 일반적인 방법이다. 하지만 이렇게 할 경우 트리가 편중되는 현상이 발생 할 수 있다. 편중되는 현상을 막기 위해 **rank\[index\] 배열을 도입** 할 것이다.

    int parent[100];
    int size[100]
    //rank 추가
    int rank[100];
    for(int i=0; i<100; i++){
        parent[i] = i;
        size[i] = 1;
        // 0으로 초기화
        rank[i] = 0;    
    }
    
    void union(int p, int q){
    
        //해당 p의 루트를 찾아준다.
        p = find(p);
    
        //해당 q의 루트를 찾아준다.
        q = find(q);
    
        if(p == q)
            return;
    
        if(rank[p] < rank[q]){
            parent[p] = q;
        }
        else{
            parent[q] = p;
        }
        
        if(rank[p] == rank[q])
            rank[p]++;
    
    }

두 개의 트리를 합칠 때 높이가 같으면 어떻게 합치더라도 높이가 1이라는 것은 자명합니다.

하지만 두 개의 트리의 높이가 다를 때 큰쪽에 붙이면 높이의 변화는 일어나지 않지만,

작은 쪽에 붙일 때는 트리의 높이가 변하게 됩니다.

따라서 저희는 트리의 높이를 최소화 할 필요가 있습니다.

그 방법은 **트리의 높이를 비교해서, 큰쪽에다가 작은쪽을 붙이는 방법**입니다.

위에 코드를 살펴보면 **rank를 만들어 트리의 깊이가 작은 애들을 큰 애들로 옮겨주는 작업**입니다.

### 최종코드

    void find(int x){
        
        if(x == parent[x])
            return x;
        else
            return parent[x] = find(parent[x]);
    }
    
    void union(int p, int q){
    
        //해당 p의 루트를 찾아준다.
        p = find(p);
    
        //해당 q의 루트를 찾아준다.
        q = find(q);
    
        if(p == q)
            return;
    
        if(rank[p] < rank[q]){
            parent[p] = q;
        }
        else{
            parent[q] = p;
        }
        
        if(rank[p] == rank[q])
            rank[p]++;
    
    }