#include <bits/stdc++.h>
using namespace std;

class Graph {
public:
	map<int, bool> visited;
	map<int, list<int> > adj;

	void addEdge(int v, int w);


	void DFS(int v);
};

void Graph::addEdge(int v, int w)
{

	adj[v].push_back(w);
}

void Graph::DFS(int v)
{
	visited[v] = true;
	cout << v << " ";

	list<int>::iterator i;
	for (i = adj[v].begin(); i != adj[v].end(); ++i)
		if (!visited[*i])
			DFS(*i);
}


int main()
{
	Graph g;
	g.addEdge(1, 2);
	g.addEdge(2, 4);
	g.addEdge(2, 5);
	g.addEdge(1, 3);

	cout << "Following is Depth First Traversal"
			" (starting from vertex 2) \n";

	g.DFS(1);

	return 0;
}
