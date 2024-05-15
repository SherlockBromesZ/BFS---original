# BFS - imprimir ordem dos elementos visitados
```cpp
#include <iostream>
#include <vector>
#include <queue>
using namespace std;

void bfs(int start, vector<vector<int>>& grafo) {
    int num_nos = grafo.size();
    vector<bool> visitado(num_nos, false);
    queue<int> q;

    // Inicializa o BFS
    visitado[start] = true;
    q.push(start);

    while (!q.empty()) {
        int no = q.front();
        q.pop();

        // Processa o nó no
        cout << "Visitando nó: " << no << endl;

        // Itera sobre todos os vizinhos do nó no
        for (int vizinho : grafo[no]) {
            if (!visitado[vizinho]) {
                visitado[vizinho] = true;
                q.push(vizinho);
            }
        }
    }
}

int main() {
    // Número de nós e arestas
    int num_nos, num_arestas;
    cin >> num_nos >> num_arestas;

    vector<vector<int>> grafo(num_nos);

    // Lê as arestas
    for (int i = 0; i < num_arestas; i++) {
        int u, v;
        cin >> u >> v;
        grafo[u].push_back(v);
        grafo[v].push_back(u); // Remova esta linha se o grafo for direcionado
    }

    // Executa BFS a partir do nó 0
    bfs(0, grafo);

    return 0;
}
```
