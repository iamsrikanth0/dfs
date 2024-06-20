import java.util.*;
public class Dfs{
    static class Edge{
        int src;
        int dst;
      public  Edge(int s, int d){
            this.src = s;
            this.dst = d;
        }
    }

    public static void creatingAGraphs( ArrayList<Edge> graph[]){
        //Creating empty arraylist fron Null arraylist
        for(int i=0; i<graph.length; i++){
            graph[i]= new ArrayList<Edge>();
        }
        graph[0].add(new Edge(0, 1));
        graph[0].add(new Edge(0, 2));

            graph[1].add(new Edge(1, 0));
            graph[1].add(new Edge(1, 3));
    
            graph[2].add(new Edge(2, 0));
            graph[2].add(new Edge(2, 4));

            
            graph[3].add(new Edge(3, 1));
            graph[3].add(new Edge(3, 4));
            graph[3].add(new Edge(3, 5));
            
            graph[4].add(new Edge(4, 2));
            graph[4].add(new Edge(4, 3));
            graph[4].add(new Edge(4, 5));

            graph[5].add(new Edge(5, 3));
            graph[5].add(new Edge(5, 4));
            graph[5].add(new Edge(5, 6));

            graph[6].add(new Edge(6, 5));



    
    }

    public static void breadfirstsearch(ArrayList<Edge> graph[], int V, int SP){
        Queue<Integer> q = new LinkedList(); // We use Queue DS to get the immediate neighbour first
        boolean vis[] = new boolean[V]; // We use boolean to know if all the Vertices are visited
     q.add(SP);

     while(!q.isEmpty()){
        int curr = q.remove();
        if(vis[curr]== false){
            System.out.print(curr+" ");
            vis[curr] = true;
            for(int i=0; i<graph[curr].size(); i++){
                Edge e = graph[curr].get(i);
                q.add(e.dst);// Adding neighbours
            }
        }
     }
    }

    public static void depthFirstSearch(ArrayList<Edge> graph[], boolean vis[], int SP){

        int curr = SP;
        if(vis[curr]==false){//base case
            System.out.print(curr+" ");
        vis[curr]= true; // step that is helping the function move towards base case 
        for(int i=0; i<graph[curr].size(); i++){ // Recurring step
            Edge e = graph[curr].get(i);
            depthFirstSearch(graph, vis, e.dst);// step that is helping the function move towards base case 
        }
        }

    }

    public static void main(String args[]){
        int V = 7;
    ArrayList<Edge> graph[] = new ArrayList[V];
    boolean vis[] = new boolean[V];
    creatingAGraphs(graph);
    int SP = 0; //Choosing a starting point
    // If we have diconnected components, we write something like below
    // for(int i=0; i<V; i++){
    //if(vis[i] == false)}//make it a starting point
    //bfs(graph,V, vis, i)

    depthFirstSearch(graph, vis, SP);
    
    }
    
}
