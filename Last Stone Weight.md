**Last Stone Weight💧**<br><br>

Leet code link: https://leetcode.com/problems/last-stone-weight/ <br><br>

Two different solutions with the same time complexity but one solution is using the build-in library function and in the other, i have written my own implementation of that function. 
<br>
Ps: PriorityQueue is the function we are taking here. <br><br>

**Time Complexity**<br>
//learn first about this part

<br><br>
**solution 1**<br>
**Code**<br>
```
class Solution {
    public int lastStoneWeight(int[] stones) {
        PriorityQueue<Integer> pq = new PriorityQueue<>(stones.length, (x,y) -> y-x);
        for(int x : stones) pq.offer(x);
        while(!pq.isEmpty()) {
            if(pq.size() == 1) return pq.poll();
            int top1 = pq.poll();
            int top2 = pq.poll();
            if(top1 == top2) continue;
            pq.offer(top1 - top2);
        }
        return 0;
    }
}
```
<br><br>

**Solution 2**<br>
**Code**<br>
```
class Solution {
    public int lastStoneWeight(int[] stones) {
        ArrayList<Integer> list = new ArrayList<>();
        for(int x : stones) list.add(x);
        applyMaxHeap(list, list.size()-1);
        
        while(!list.isEmpty()) {
            if(list.size() == 1) {
                return list.get(0);
            }
            int top1 = list.get(0);
            list.set(0, list.get(list.size()-1));
            list.remove(list.size()-1);
            adjectTheHeap(list, 0);
            
            int top2 = list.get(0);
            list.set(0, list.get(list.size()-1));
            list.remove(list.size()-1);
            adjectTheHeap(list, 0);
            
            if(top1 == top2) continue;
            list.add(top1 - top2);
            applyMaxHeap(list, list.size()-1);
        }
        return 0;
    }
    
    void applyMaxHeap(ArrayList<Integer> heap, int root) {
        int parent  = root / 2;
        int left    = 2 * root;
        int right   = 2 * root + 1;

    
        if(left < heap.size() && right < heap.size()) {
            if(heap.get(left) > heap.get(right) && heap.get(left) > heap.get(root)) {
                swap(heap, left, root);
                applyMaxHeap(heap, left);
            } 
            else if(heap.get(right) > heap.get(root)) {
                swap(heap, right, root);
                applyMaxHeap(heap, right);
            }
        }
        else if(left < heap.size() && heap.get(left) > heap.get(root)) {
                swap(heap, left, root);
                applyMaxHeap(heap, left);
        }
        else if(right < heap.size()) {
                swap(heap, right, root);
                applyMaxHeap(heap, right);
        }
        if(root-1 >= 0)
            applyMaxHeap(heap, root-1);
    }
    
    void swap(ArrayList<Integer> list, int i, int j) {
        int temp = list.get(i);
        list.set(i, list.get(j));
        list.set(j, temp);
    }
    
    void adjectTheHeap(ArrayList<Integer> heap, int root) {
        int left;
        int right;
        if(root == 0) {
            left = 1;
            right = 2;
        }
        else {
            left = 2*root;
            right = 2*root+1;
        }
        
        if(left < heap.size() && right < heap.size()) {
            if(heap.get(left) > heap.get(right) && heap.get(left) > heap.get(root)) {
                swap(heap, left, root);
                adjectTheHeap(heap, left);
            }
            else if(heap.get(right) > heap.get(root)) {
                swap(heap, right, root);
                adjectTheHeap(heap, right);
            }
        }
        else if(left < heap.size() && heap.get(left) > heap.get(root)) {
                swap(heap, left, root);
                adjectTheHeap(heap, left);
        }
        else if(right <heap.size() && heap.get(right) > heap.get(root)) {
                swap(heap, right, root);
                adjectTheHeap(heap, right);
        }
    }
}
```
