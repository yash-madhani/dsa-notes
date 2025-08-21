# Problems on BFS/DFS

## Number of provinces (leetcode)
https://leetcode.com/problems/number-of-provinces/description/

Approach: visit all the nodes in each province once via dfs, and keep updating visited array. Th number of times dfs is called is the number of province.
```
class Solution {

    public void dfs(int node, ArrayList<ArrayList<Integer>> adj ,int[] vis)
    {
        vis[node] = 1;
        for(Integer it: adj.get(node))
        {
            if(vis[it] == 0)
            {
                dfs(it, adj, vis);
            }
        }
    }

    public int findCircleNum(int[][] isConnected) {
        ArrayList<ArrayList<Integer>> adj = new ArrayList<ArrayList<Integer>>();
        int n = isConnected.length;

        // Changing matrix to list
        for(int i=0;i<n;i++)
            adj.add(new ArrayList<Integer>());
        for(int i=0;i<n;i++)
        {
            for(int j=0;j<n;j++)
            {
                if(isConnected[i][j] == 1 && i != j)
                {
                    adj.get(i).add(j);
                    adj.get(j).add(i);
                }
            }
        }

        int[] vis = new int[n];
        int count = 0;

        for(int i=0;i<n;i++)
        {
            if(vis[i] == 0)
            {
                count++;
                dfs(i,adj,vis);
            }
        }

        return count;
    }
}
```

## Rotten Oranges
https://leetcode.com/problems/rotting-oranges/description/

WATCH VIDEO
```
class Pair {
    int row;
    int col;
    int tm;
    Pair(int _row, int _col, int _tm)
    {
        this.row = _row;
        this.col = _col;
        this.tm = _tm;
    }
}

class Solution {
    public int orangesRotting(int[][] grid) {
        int n = grid.length;
        int m = grid[0].length;
        int[][] vis = new int[n][m];
        int cntfresh = 0;
        Queue<Pair> q = new LinkedList<>();

        for(int i=0;i<n;i++)
        {
            for(int j=0;j<m;j++)
            {
                if(grid[i][j] == 2)
                {
                    q.add(new Pair(i,j,0));
                    vis[i][j] = 2;
                }
                else
                    vis[i][j] = 0;

                if(grid[i][j] == 1)
                    cntfresh++;
            }
        }

        int tmax=0;
        int cnt=0;
        int[] drow = {1,0,-1,0};
        int[] dcol = {0,1,0,-1};
        while(!q.isEmpty())
        {
            int t = q.peek().tm;
            int row = q.peek().row;
            int col = q.peek().col;
            q.poll();
            tmax = Math.max(t,tmax);
            for(int i=0;i<4;i++)
            {
                int nrow = row + drow[i];
                int ncol = col + dcol[i];
                if(nrow>=0 && nrow<n && ncol>=0 && ncol<m && vis[nrow][ncol] != 2 && grid[nrow][ncol] == 1)
                {
                    q.add(new Pair(nrow,ncol,t+1));
                    vis[nrow][ncol] = 2;
                    cnt++;
                }
            }
        }

        if(cnt != cntfresh) return -1;

        return tmax;
    }
}
```

## Flood fill
https://leetcode.com/problems/flood-fill/description/

use dfs
```
class Solution {
    public void dfs(int row, int col, int[][] ans, int[][] image, int inicolor, int finalcolor)
    {
        ans[row][col] = finalcolor;
        int n = ans.length;
        int m = ans[0].length;
        int[] drow = {-1,0,1,0};
        int[] dcol = {0,1,0,-1};
        for(int i=0;i<4;i++)
        {
            int nrow = drow[i] + row;
            int ncol = dcol[i] + col;
            if(nrow>=0 && nrow<n && ncol>=0 && ncol<m && image[nrow][ncol] == inicolor && ans[nrow][ncol] != finalcolor)
            {
                dfs(nrow,ncol,ans,image,inicolor,finalcolor);
            }
        }
    }
    public int[][] floodFill(int[][] image, int sr, int sc, int color) {
        int[][] ans = image;
        int inicolor = image[sr][sc];
        dfs(sr,sc,ans,image,inicolor,color);
        return ans;
    }
}
```

## Cycle Detection in unirected Graph (bfs)
https://youtu.be/BPlrALf1LDU?si=f2om-2IGqbBvN4In

```
import java.util.*;

class Solution
{
   static boolean checkForCycle(ArrayList<ArrayList<Integer>> adj, int s,
            boolean vis[], int parent[])
    {
       Queue<Node> q =  new LinkedList<>(); //BFS
       q.add(new Node(s, -1));
       vis[s] =true;
       
       // until the queue is empty
       while(!q.isEmpty())
       {
           // source node and its parent node
           int node = q.peek().first;
           int par = q.peek().second;
           q.remove(); 
           
           // go to all the adjacent nodes
           for(Integer it: adj.get(node))
           {
               if(vis[it]==false)  
               {
                   q.add(new Node(it, node));
                   vis[it] = true; 
               }
        
                // if adjacent node is visited and is not its own parent node
               else if(par != it) return true;
           }
       }
       
       return false;
    }
    
    // function to detect cycle in an undirected graph
    public boolean isCycle(int V, ArrayList<ArrayList<Integer>> adj)
    {
        boolean vis[] = new boolean[V];
        Arrays.fill(vis,false);
        int parent[] = new int[V];
        Arrays.fill(parent,-1);  
        
        for(int i=0;i<V;i++)
            if(vis[i]==false) 
                if(checkForCycle(adj, i,vis, parent)) 
                    return true;
    
        return false;
    }
    
    public static void main(String[] args)
    {
        ArrayList<ArrayList<Integer>> adj = new ArrayList<>();
        for (int i = 0; i < 4; i++) {
            adj.add(new ArrayList < > ());
        }
        adj.get(1).add(2);
        adj.get(2).add(1);
        adj.get(2).add(3);
        adj.get(3).add(2);
                
        Solution obj = new Solution();
        boolean ans = obj.isCycle(4, adj);
        if (ans)
            System.out.println("1");    
        else
            System.out.println("0");
    }
}

class Node {
    int first;
    int second;
    public Node(int first, int second) {
        this.first = first;
        this.second = second; 
    }
}
```
## Cycle Detection in undirected Graph (dfs)
https://youtu.be/zQ3zgFypzX4?si=4dWUxo9sOZwbsEV7

```
import java.util.*;

class Solution {
    private boolean dfs(int node, int parent, int vis[], ArrayList<ArrayList<Integer>> 
    adj) {
        vis[node] = 1; 
        // go to all adjacent nodes
        for(int adjacentNode: adj.get(node)) {
            if(vis[adjacentNode]==0) {
                if(dfs(adjacentNode, node, vis, adj) == true) 
                    return true; 
            }
            // if adjacent node is visited and is not its own parent node
            else if(adjacentNode != parent) return true; 
        }
        return false; 
    }
    // Function to detect cycle in an undirected graph.
    public boolean isCycle(int V, ArrayList<ArrayList<Integer>> adj) {
       int vis[] = new int[V]; 
       for(int i = 0;i<V;i++) {
           if(vis[i] == 0) {
               if(dfs(i, -1, vis, adj) == true) return true; 
           }
       }
       return false; 
    }
    public static void main(String[] args)
    {
        ArrayList<ArrayList<Integer>> adj = new ArrayList<>();
        for (int i = 0; i < 4; i++) {
            adj.add(new ArrayList < > ());
        }
        adj.get(1).add(2);
        adj.get(2).add(1);
        adj.get(2).add(3);
        adj.get(3).add(2);
                
        Solution obj = new Solution();
        boolean ans = obj.isCycle(4, adj);
        if (ans)
            System.out.println("1");    
        else
            System.out.println("0");
    }

}

```

## 0/1 Matrix 
https://leetcode.com/problems/01-matrix/

use BFS, watch start of the video for intuition if needed
```
class Pair {
    int row;
    int col;
    int level;
    Pair(int _row, int _col, int _level)
    {
        this.row = _row;
        this.col = _col;
        this.level = _level;
    }
}
class Solution {
    public int[][] updateMatrix(int[][] mat) {
        int n = mat.length;
        int m = mat[0].length;
        int[][] vis = new int[n][m];
        int[][] ans = mat;
        Queue<Pair> q = new LinkedList<>();

        for(int i=0;i<n;i++)
        {
            for(int j=0;j<m;j++)
            {
                if(mat[i][j] == 0)
                {
                    q.add(new Pair(i,j,0));
                    vis[i][j] = 1;
                }
                else
                    vis[i][j] = 0;
            }
        }

        int[] drow = {1,0,-1,0};
        int[] dcol = {0,1,0,-1};
        while(!q.isEmpty())
        {
            int row = q.peek().row;
            int col = q.peek().col;
            int level = q.peek().level;
            q.poll();
            for(int i=0;i<4;i++)
            {
                int nrow = drow[i] + row;
                int ncol = dcol[i] + col;
                if(nrow>=0 && nrow<n && ncol>=0 && ncol<m && vis[nrow][ncol] == 0)
                {
                    ans[nrow][ncol] = level+1;
                    vis[nrow][ncol] = 1;
                    q.add(new Pair(nrow,ncol,level+1));
                }
            }
        }
        return ans;
    }
}
```

## Surrounded Regions

Approach: use dfs for border 'O's
```
class Solution {
    public void dfs(int[][] vis, char[][] board, int row, int col)
    {
        int n = board.length;
        int m = board[0].length;
        vis[row][col] = 1;
        int[] drow = {1,0,-1,0};
        int[] dcol = {0,1,0,-1};
        for(int i=0;i<4;i++)
        {
            int nrow = row + drow[i];
            int ncol = col + dcol[i];
            if(nrow>=0 && nrow<n && ncol>=0 && ncol<m && board[nrow][ncol] == 'O' && vis[nrow][ncol]==0)
            {
                dfs(vis, board, nrow, ncol);
            }
        }
    }
    public void solve(char[][] board) {
        int n = board.length;
        int m = board[0].length;
        int[][] vis = new int[n][m];

        //for first and last row
        for(int i=0;i<m;i++)
        {
            if(board[0][i] == 'O' && vis[0][i] == 0)
            {
                dfs(vis,board,0,i);
            }

            if(board[n-1][i] == 'O' && vis[n-1][i] == 0)
            {
                dfs(vis,board,n-1,i);
            }
        }
        
        // for first and last column
        for(int i=0;i<n;i++)
        {
            if(board[i][0] == 'O' && vis[i][0] == 0)
            {
                dfs(vis,board,i,0);
            }

            if(board[i][m-1] == 'O' && vis[i][m-1] == 0)
            {
                dfs(vis,board,i,m-1);
            }
        }

        for(int i=0;i<n;i++)
        {
            for(int j=0;j<m;j++)
            {
                if(vis[i][j] == 0)
                {
                    board[i][j] = 'X';
                }
            }
        }
    }
}
```

## Number of Enclaves
https://leetcode.com/problems/number-of-enclaves/description/

Approach: dfs/bfs from the boundary and mark them, count the remaining and return
```
class Solution {
    public void dfs(int row, int col, int[][] vis, int[][] grid)
    {
        vis[row][col] = 1;
        int n = grid.length;
        int m = grid[0].length;
        int[] drow = {1,0,-1,0};
        int[] dcol = {0,1,0,-1};
        for(int i=0;i<4;i++)
        {
            int nrow = drow[i] + row;
            int ncol = dcol[i] + col;
            if(nrow>=0 && nrow<n && ncol>=0 && ncol<m && grid[nrow][ncol]==1 && vis[nrow][ncol]==0)
            {
                dfs(nrow,ncol,vis,grid);
            }
        }
    }
    public int numEnclaves(int[][] grid) {
        int n = grid.length;
        int m = grid[0].length;
        int[][] vis = new int[n][m];

        for(int i=0;i<n;i++)
        {
            // for first column
            if(grid[i][0] == 1 && vis[i][0] == 0)
            {
                dfs(i,0,vis,grid);
            }

            // for last column
            if(grid[i][m-1] == 1 && vis[i][m-1] == 0)
            {
                dfs(i,m-1,vis,grid);
            }
        }

        for(int i=0;i<m;i++)
        {
            // for first row
            if(grid[0][i] == 1 && vis[0][i] == 0)
                dfs(0,i,vis,grid);
            
            // for last row
            if(grid[n-1][i] == 1 && vis[n-1][i] == 0)
                dfs(n-1,i,vis,grid);
        }

        int count = 0;
        for(int i=0;i<n;i++)
            for(int j=0;j<m;j++)
            {
                if(grid[i][j] == 1 && vis[i][j] == 0)
                    count++;
            }
        
        return count;
    }
}
```

## Bipartite Graph
https://leetcode.com/problems/is-graph-bipartite/description/

Watch Video, it is easy
```
class Solution {
    public boolean dfs(int[] color, int node, int val, int[][] graph)
    {
        color[node] = val;
        int m = graph[node].length;

        for(int i=0;i<m;i++)
        {
            if(color[graph[node][i]] == -1)
            {
                if(dfs(color, graph[node][i], 1-val, graph) == false) return false;
            }
            else if (color[graph[node][i]] == val) {
                return false;
            }
        }
        return true;

    }
    public boolean isBipartite(int[][] graph) {
        int n = graph.length;
        int[] color = new int[n];

        for(int i=0;i<n;i++) color[i] = -1;

        for(int i=0;i<n;i++)
        {
            if(color[i] == -1)
                if(dfs(color,i,0,graph) == false) return false;
        }

        return true;
        
    }
}
```


# Topo Sort and Problems

## Watch Topo Sort Video
https://youtu.be/5lZ0iJMrUMk

## Course Schedule - I
https://leetcode.com/problems/course-schedule/description/

Approach: Basic topo sort
```
class Solution {
    public boolean canFinish(int numCourses, int[][] prerequisites) {
        ArrayList<ArrayList<Integer>> adj = new ArrayList<>();

        for(int i=0;i<numCourses;i++)
            adj.add(new ArrayList<Integer>());

        int m = prerequisites.length;
        for(int i=0;i<m;i++)
        {
            adj.get(prerequisites[i][0]).add(prerequisites[i][1]);
        }

        int indegree[] = new int[numCourses];
        for(int i=0;i<numCourses;i++)
        {
            for(int it : adj.get(i))
                indegree[it]++;
        }

        Queue<Integer> q = new LinkedList<Integer>();
        for(int i=0;i<numCourses;i++)
        {
            if(indegree[i] == 0)
                q.add(i);
        }

        List<Integer> topo = new ArrayList<Integer>();
        while(!q.isEmpty())
        {
            int node = q.peek();
            q.poll();
            topo.add(node);

            for(int it : adj.get(node))
            {
                indegree[it]--;
                if(indegree[it] == 0) q.add(it);
            }
        }

        if(topo.size() == numCourses) return true;
        return false;
    }
}
```

## Find eventual safe states
https://leetcode.com/problems/find-eventual-safe-states/description/

Reverse then apply Topo Sort, can be solved using DFS as well.
```
class Solution {
    public List<Integer> eventualSafeNodes(int[][] graph) {
        List<List<Integer>> adjRev = new ArrayList<>();
        for(int i=0;i<graph.length;i++)
            adjRev.add(new ArrayList<Integer>());

        int[] indegree = new int[graph.length];

        for(int i = 0; i < graph.length; i++) {
            for(int j = 0; j < graph[i].length; j++) {
                adjRev.get(graph[i][j]).add(i); 
                indegree[i]++; 
            }
        }

        Queue<Integer> q = new LinkedList<Integer>();

        for(int i=0;i<indegree.length;i++)
        {
            System.out.println(indegree[i]);
            if(indegree[i] == 0) q.add(i);
        }
        System.out.println(indegree);
        List<Integer> topo = new ArrayList<>();

        while(!q.isEmpty())
        {
            int node = q.peek();
            q.poll();
            topo.add(node);

            for(int it : adjRev.get(node))
            {
                indegree[it]--;
                if(indegree[it] == 0) q.add(it);
            }
        }

        Collections.sort(topo);
        return topo;
    }
}
```

# Shortest Path Algorithms and Problems

## Shortest path in a binary maze
https://leetcode.com/problems/shortest-path-in-binary-matrix/description/

Approach: Djisktra's Algorithm without priority queue since weights = 1.
```
class Tuple {
    int dist;
    int row;
    int col;
    Tuple(int _dist, int _row, int _col)
    {
        this.row = _row;
        this.col = _col;
        this.dist = _dist;
    }
}
class Solution {
    public int shortestPathBinaryMatrix(int[][] grid) {
        int n = grid.length;
        int m = grid[0].length;

        if(n==1 && m==1 && grid[0][0] == 0) return 1;
        if(n==1 && m==1 && grid[0][0] == 1) return -1;
        if (grid[0][0] == 1 || grid[n-1][m-1] == 1) return -1;

        int[][] d = new int[n][m];
        for(int i=0;i<n;i++)
            for(int j=0;j<m;j++)
                d[i][j] = Integer.MAX_VALUE;
        d[0][0] = 0;

        Queue<Tuple> q = new LinkedList<>();
        q.add(new Tuple(1,0,0));
        int[] drow = {-1,-1,-1,0,0,1,1,1};
        int[] dcol = {-1,0,1,-1,1,-1,0,1};
        
        while(!q.isEmpty())
        {
            Tuple temp = q.peek();
            q.poll();
            int dist = temp.dist;
            int row = temp.row;
            int col = temp.col;

            for(int i=0;i<8;i++)
            {
                int nrow = row + drow[i];
                int ncol = col + dcol[i];
                if(nrow>=0 && nrow<n && ncol>=0 && ncol<m && grid[nrow][ncol]==0 && dist+1<d[nrow][ncol])
                {
                    d[nrow][ncol] = dist+1;
                    q.add(new Tuple(dist+1,nrow,ncol));
                    if(nrow == n-1 && ncol == m-1) return dist+1;
                }
            }
        }

        return -1;
    }
}
```

## Path with minimum effort
https://leetcode.com/problems/path-with-minimum-effort/description/

Use Djisktra's
```
class Tuple {
    int dist;
    int row;
    int col;
    Tuple(int _dist, int _row, int _col)
    {
        this.dist = _dist;
        this.row = _row;
        this.col = _col;
    }
}
class Solution {
    public int minimumEffortPath(int[][] heights) {
        int n = heights.length;
        int m = heights[0].length;
        int[][] effort = new int[n][m];

        for(int i=0;i<n;i++)
            for(int j=0;j<m;j++)
                effort[i][j] = Integer.MAX_VALUE;
        effort[0][0] = 0;

        PriorityQueue<Tuple> pq = new PriorityQueue<Tuple>((x,y) -> Integer.compare(x.dist,y.dist));
        pq.add(new Tuple(0,0,0));

        int[] drow = {0,1,0,-1};
        int[] dcol = {1,0,-1,0};
        
        while(!pq.isEmpty())
        {
            Tuple temp = pq.peek();
            int dist = temp.dist;
            int row = temp.row;
            int col = temp.col;
            pq.poll();

            for(int i=0;i<4;i++)
            {
                int nrow = row+drow[i];
                int ncol = col+dcol[i];

                if(nrow<n && nrow>=0 && ncol<m && ncol>=0)
                {
                    int neweffort = Math.max(dist, Math.abs(heights[row][col] - heights[nrow][ncol]));
                    if(neweffort < effort[nrow][ncol])
                    {
                        effort[nrow][ncol] = neweffort;
                        pq.add(new Tuple(neweffort,nrow,ncol));
                    }

                }
            }
        }

        return effort[n-1][m-1];
    }
}
```

## Cheapest flights within k stops
https://leetcode.com/problems/cheapest-flights-within-k-stops/description/

Use Djikstra's Algo for stops and not distance.
```
class Pair {
    int node;
    int weight;
    Pair(int _node, int _weight)
    {
        this.node = _node;
        this.weight = _weight;
    }
}

class Tuple {
    int stops;
    int node;
    int dist;
    Tuple(int _stops, int _node, int _dist) {
        this.stops = _stops;
        this.node = _node;
        this.dist = _dist;
    }
}

class Solution {
    public int findCheapestPrice(int n, int[][] flights, int src, int dst, int k) {
        ArrayList<ArrayList<Pair>> adj = new ArrayList<>();
        for(int i=0;i<n;i++)
            adj.add(new ArrayList<>());

        for(int i=0;i<flights.length;i++)
        {
            adj.get(flights[i][0]).add(new Pair(flights[i][1],flights[i][2]));
        }

        int[] d = new int[n];
        for(int i=0;i<n;i++)
            d[i] = Integer.MAX_VALUE;

        Queue<Tuple> q = new LinkedList<>();
        q.add(new Tuple(0,src,0));

        while(!q.isEmpty())
        {
            Tuple temp = q.peek();
            int stops = temp.stops;
            int node = temp.node;
            int dist = temp.dist;
            q.poll();

            if(stops>k) continue;

            for(Pair it : adj.get(node))
            {
                int adjNode = it.node;
                int cost = it.weight;

                if(cost+dist<d[adjNode])
                {
                    d[adjNode] = cost+dist;
                    q.add(new Tuple(stops+1,adjNode,cost+dist));
                }
            }
        }

        if(d[dst] == Integer.MAX_VALUE) return -1;

        return d[dst];

    }
}
```

## Network Delay time
https://leetcode.com/problems/network-delay-time/description/

Use Simple Djikstra's Allgorithm
```
class Pair {
    int node;
    int weight;
    Pair(int _node, int _weight)
    {
        this.node = _node;
        this.weight = _weight;
    }
}

class Tuple {
    int node;
    int dist;
    Tuple(int _node, int _dist) {
        this.node = _node;
        this.dist = _dist;
    }
}

class Solution {
    public int networkDelayTime(int[][] times, int n, int k) {
        ArrayList<ArrayList<Pair>> adj = new ArrayList<>();
        for(int i=0;i<=n;i++)
            adj.add(new ArrayList<>());
        
        for(int i=0;i<times.length;i++)
            adj.get(times[i][0]).add(new Pair(times[i][1],times[i][2]));

        int[] d = new int[n+1];
        for(int i=1;i<=n;i++)
            d[i] = Integer.MAX_VALUE;
        d[k] = 0;

        PriorityQueue<Tuple> pq = new PriorityQueue<>((x,y) -> Integer.compare(x.dist,y.dist));
        pq.add(new Tuple(k,0));

        while(!pq.isEmpty())
        {
            Tuple temp = pq.peek();
            int currnode = temp.node;
            int currcost = temp.dist;
            pq.poll();

            for(Pair it : adj.get(currnode))
            {
                int nextnode = it.node;
                int nextcost = it.weight;

                if(currcost+nextcost < d[nextnode])
                {
                    d[nextnode] = currcost+nextcost;
                    pq.add(new Tuple(nextnode, currcost+nextcost));
                }
            }
        }

        for(int i=1;i<=n;i++)
        {
            if(d[i] == Integer.MAX_VALUE)
                return -1;
        }

        int max = 0;

        for(int i=1;i<=n;i++)
            max = Math.max(d[i],max);
        
        return max;
    }
}
```

# 