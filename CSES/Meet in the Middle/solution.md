### Metacognition: 
We first were confused by how to actually form all the different sequences of sums. One approach we thought of was to simply use a brute force recursive solution however this would naturally produce duplicate subsets hence we would need to keep track of the "active" subsets. Another solution hinted by a fellow member in ACPC was to use a bitset. If we used a bitset we could map each set value to a index in the bitmap. This made it clear on how to find all the combinations, we would simply generate all the different binary numbers with n bits. However this will TME since O(2^40) was too slow. But what if we instead looked at half of the numbers. Why would we need to find all the combinations for all the n bits at once, this helped influence a merge algorithm between sets. Next all that was left was to think about how to actually implement this solution.


```c++

#include <iostream>
#include <vector>
#include <unordered_map>
using namespace std;



vector<long long> get_bit_subsets(int n, int start, vector<long long>& bit_map){
    vector<long long> subsets;
    for(int i = 0; i < (1<<n); i++){
        long long s = 0;
        for(int j = 0; j < n; j++){
            if (i & (1 << j)){
                s += bit_map[j+start];
            }
        }
        subsets.push_back(s);
    }
    return subsets;
}

int main(){
    /*
        Input Processing:
    */
    int x,n;
    cin >> n;
    cin >> x;
    vector<long long> bit_map(n);
    for(int i = 0; i < n; i++){
        cin>>bit_map[i];
    }
    /* 
        Algorithm: 
    */ 
    // split bit_map into two arrays "left" and "right"
    vector<long long> left = get_bit_subsets(n/2, 0, bit_map);
    vector<long long> right = get_bit_subsets(n-n/2, n/2, bit_map);
    // hash the sum to its frequency from "right"
    unordered_map<long long, long long> right_cnt;
    for(long long i = 0; i < static_cast<long long>((right.size())); i++){
        if(right_cnt.count(right[i]) != 0){
            right_cnt[right[i]]++;
        }else{
            right_cnt[right[i]] = 1;
        }
    }
    // "merge" the two subsets and count the ways
    long long cnt = 0;
    for(long long i = 0; i < static_cast<long long>((left.size())); i++){

        if(right_cnt.count(x - left[i]) != 0){
            cnt += right_cnt[x-left[i]];
        }
    }
    
    cout<<cnt<<endl;
    return 0;
}





```
