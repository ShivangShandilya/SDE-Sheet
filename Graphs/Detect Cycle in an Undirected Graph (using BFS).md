Problem - [Detect Cycle in an Undirected Graph (using BFS)](https://leetcode.com/problems/course-schedule/)

- Given an undirected graph with V vertices and E edges, check whether it contains any cycle or not. 

- Example 1:

      Input:
      V = 8, E = 7
      
<img src = "https://user-images.githubusercontent.com/101946115/215887651-1182702e-434a-4fad-8b8e-7892a554d39f.png" height = 200 width = 400 />

      Output:  0

Explanation: No cycle in the given graph.

- SOLUTION

```
class Solution {
    public boolean canFinish(int numCourses, int[][] prerequisites) {
        List<Integer>[] graph = new ArrayList[numCourses];
        int[] degree = new int[numCourses];
        
        // point
        int count = 0;
        
        Queue<Integer> queue = new LinkedList<>();
        
        for(int i = 0; i < numCourses; i++) graph[i] = new ArrayList<>();
        
        for(int[] c : prerequisites){
            graph[c[1]].add(c[0]);
            degree[c[0]]++;
        }
        
        for(int i = 0; i < numCourses; i++){
            if(degree[i] == 0){
                queue.add(i);
                count++;
            }
        }
        
        while(!queue.isEmpty()){
            int course = queue.poll();
            for(int c : graph[course]){
                if(--degree[c] == 0){
                    count++;
                    queue.add(c);
                }
            }
        }
        return (count == numCourses);
    }
}
```
