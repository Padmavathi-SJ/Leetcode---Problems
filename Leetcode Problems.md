### 1823.Find the winner of the game

```
class Solution {
public:
    int findTheWinner(int n, int k) {
        queue <int> q;
        for(int i=1; i<=n; i++)
        q.push(i);
        int counter=k;
        while(q.size()>1){
            int rankOfFriend = q.front();
            q.pop();
            counter--;
            if(counter==0){
                counter=k;
            }
            else {
                q.push(rankOfFriend);
            }
        }
        return q.front();
    }
};

```

**In the above code, we are traversing the queue till reach the kth position.**
**Once reached pop that position, and start from the next of the popped position and repeat.**
**this performs till the size of queue will less than 1 and stop.**
**the last balanced position is the winner of the game.**
