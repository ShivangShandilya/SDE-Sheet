Problem - [Detect a Cycle in Directed Graph](https://leetcode.com/problems/course-schedule/)

- Given a Directed Graph with V vertices and E edges, check whether it contains any cycle or not.

Example 1:

    Input Format: V = 5, E = 5

![image](https://user-images.githubusercontent.com/101946115/215888205-9aaa5f70-300a-4fa9-bc0d-0ab84ad65f89.png)

    Result: True

Explanation: 2->3->4->2 is a cycle.

- SOLUTION

```
import java.util.*;

class Solution {
    public boolean isCyclic(int N, ArrayList<ArrayList<Integer>> adj) {
        // int topo[] = new int[N];
        int indegree[] = new int[N];
        for (int i = 0; i < N; i++) {
            for (Integer it : adj.get(i)) {
                indegree[it]++;
            }
        }

        Queue<Integer> q = new LinkedList<Integer>();
        for (int i = 0; i < N; i++) {
            if (indegree[i] == 0) {
                q.add(i);
            }
        }
        int cnt = 0;
        while (!q.isEmpty()) {
            Integer node = q.poll();
            cnt++;
            for (Integer it : adj.get(node)) {
                indegree[it]--;
                if (indegree[it] == 0) {
                    q.add(it);
                }
            }
        }
        if (cnt == N)
            return false;
        return true;
    }
}

public class tUf {
    public static void main(String[] args) {
        int V = 6;
        ArrayList<ArrayList<Integer>> adj = new ArrayList<>();
        for (int i = 0; i < V; i++) {
            adj.add(new ArrayList<>());
        }
        adj.get(1).add(2);
        adj.get(2).add(3);
        adj.get(3).add(4);
        adj.get(3).add(5);
        adj.get(4).add(2);

        Solution obj = new Solution();
        boolean ans = obj.isCyclic(V, adj);
        if (ans)
            System.out.println("True");
        else
            System.out.println("False");
    }
}
```
