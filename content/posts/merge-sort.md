+++
date = "2018-10-04T03:05:38+00:00"
draft = true
title = "Merge Sort"

+++
최악일때도 (nlogn) 인 정렬 알고리즘이다.

N개를 정렬하는 알고리즘이다.

n개를  n/2로 나눈다.

그리고 왼쪽 n/2개와 오른쪽 n/2를 정렬한다.

정렬한 결과를 합친다.

    void sort(int start, int end){
        
        if (start == end){
            return;
        }
        
        int mid = (start+end)/2;
        
        sort(start, mid);
        sort(mid+1,end);
        merge(start,end);
    
    
    }
    
    void merge(int start, int end){
        
        int mid = (start+end)/2;
        int s = start;
        int j = mid+1;
        int k = 0;
    
        //위에서 정해진 구간에 맞게끔 값 넣어주기
        while( s <= mid && j <=end){
            
            //앞에꺼 그대로 저장
            if(a[s] <= a[j]{
                b[k++] = a[s++];
            }
            //뒤에 값 저장
            else{
                b[k++] = a[j++];
            }
        }
        
        //나머지 부분 채워주기
        while (s<=mid) b[k++] = a[s++];
        while (j<=end) b[k++] = a[j++];
        
        //원래 배열에 다시 넣어주기
        for(int i=start; i<=end; i++){
            a[i] = b[i-start];
        }
    
    }