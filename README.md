# Proyecto-Jair-Montes
## Proyecto sobre la creación de un grafo de las interacciones de los personajes en la saga Maze Runner

### Primero instalamos las librerías:
!pip install networkx matplotlib

import networkx as nx
import matplotlib.pyplot as plt

### Crear un grafo vacío
G = nx.Graph()

### Lista de personajes principales y secundarios de "Maze Runner: Correr o Morir"
personajes = [
    "Thomas", "Teresa", "Minho", "Newt", "Jeff", "Ben", "Clint", "Marcus", "AvaPaige",
    "DraCrowford", "Ponytail", "DrUno", "MamaDeThomas",
    "Carl", "Zart", "Sonya", "Janson", "Brenda", "Vince", "Jorge", "Harriet",
    "MaryCooper", "Aris", "David", "Riley", "Sarten", "Winston", "Lawrence", "Chuck",
    "Gally", "Alby", "Shai", "FionaRamsey", "PetterButtler", "JansonAsistente",
    "Alex", "JefeEstacion"
]

### Añadir nodos (personajes)
for personaje in personajes:
    G.add_node(personaje)

### Lista de conversaciones/interacciones entre personajes

interacciones = [
    ("Thomas", "Teresa"), ("Thomas", "Minho"), ("Thomas", "Newt"), ("Thomas", "Jeff"),
    ("Thomas", "Ben"), ("Thomas", "Clint"), ("Thomas", "Marcus"), ("Thomas", "AvaPaige"),
    ("Thomas", "DraCrowford"), ("Thomas", "Barkley"), ("Thomas", "SoldadoPelon"),
    ("Thomas", "Ponytail"), ("Thomas", "DrUno"), ("Thomas", "MamaDeThomas"),
    ("Thomas", "Carl"), ("Thomas", "Zart"), ("Thomas", "Sonya"), ("Thomas", "Janson"),
    ("Thomas", "Brenda"), ("Thomas", "Vince"), ("Thomas", "Jorge"), ("Thomas", "Harriet"),
    ("Thomas", "MaryCooper"), ("Thomas", "Aris"), ("Thomas", "David"), ("Thomas", "Riley"),
    ("Thomas", "Sarten"), ("Thomas", "Winston"), ("Thomas", "Lawrence"), ("Thomas", "Chuck"),
    ("Thomas", "Gally"), ("Thomas", "Alby"),
    ("Teresa", "Shai"), ("Teresa", "Minho"), ("Teresa", "Newt"), ("Teresa", "Jeff"),
    ("Teresa", "Clint"), ("Teresa", "AvaPaige"), ("Teresa", "DraCrowford"),
    ("Teresa", "FionaRamsey"), ("Teresa", "DrUno"), ("Teresa", "PetterButtler"),
    ("Teresa", "Janson"), ("Teresa", "Vince"), ("Teresa", "Chuck"), ("Teresa", "Gally"),
    ("Teresa", "Alby"),
    ("Minho", "Newt"), ("Minho", "Jeff"), ("Minho", "Ben"), ("Minho", "Clint"),
    ("Minho", "DrUno"), ("Minho", "Janson"), ("Minho", "Brenda"), ("Minho", "Aris"),
    ("Minho", "David"), ("Minho", "Alex"), ("Minho", "Chuck"), ("Minho", "Gally"),
    ("Minho", "Alby"),
    ("Newt", "Jeff"), ("Newt", "Ben"), ("Newt", "DraCrowford"), ("Newt", "DrUno"),
    ("Newt", "Sonya"), ("Newt", "Janson"), ("Newt", "Brenda"), ("Newt", "Jorge"),
    ("Newt", "Harriet"), ("Newt", "Aris"), ("Newt", "Sarten"), ("Newt", "Winston"),
    ("Newt", "Chuck"), ("Newt", "Gally"), ("Newt", "Alby"),
    ("Jeff", "Clint"), ("Jeff", "Gally"),
    ("Ben", "Chuck"), ("Ben", "Gally"), ("Ben", "Alby"),
    ("Marcus", "Ponytail"), ("Marcus", "Jorge"), ("Marcus", "Brenda"),
    ("AvaPaige", "FionaRamsey"), ("AvaPaige", "PetterButtler"), ("AvaPaige", "Janson"),
    ("AvaPaige", "MaryCooper"),
    ("DraCrowford", "DrUno"),
    ("Ponytail", "Brenda"),
    ("DrUno", "JansonAsistente"),
    ("Zart", "Sarten"), ("Zart", "Winston"),
    ("Sonya", "Vince"), ("Sonya", "Jorge"), ("Sonya", "Harriet"), ("Sonya", "Aris"),
    ("Janson", "JansonAsistente"), ("Janson", "Vince"), ("Janson", "JefeEstacion"),
    ("Brenda", "Jorge"), ("Brenda", "Sarten"), ("Brenda", "MaryCooper"),
    ("Vince", "Jorge"), ("Vince", "Harriet"), ("Vince", "Sarten"), ("Vince", "MaryCopper"),
    ("Jorge", "MaryCooper"), ("Jorge", "Sarten"),
    ("Harriet", "Aris"),
    ("Aris", "Sarten"), ("Aris", "Winston"),
    ("Sarten", "Winston"), ("Sarten", "Gally"),
    ("Lawrence", "Gally"),
    ("Chuck", "Alby"),
    ("Gally", "Alby"),
]

### Añadir aristas (conversaciones entre personajes)
for convo in interacciones:
    G.add_edge(*convo)

### Dibujar el grafo
plt.figure(figsize=(12, 10))
### Layout lo usé para una tener una disposición mejor ya que si no los grafos no se alcanzaban a distinguir bien
pos = nx.spring_layout(G, seed=42)  
nx.draw(G, pos, with_labels=True, node_color='lightblue', node_size=3000, font_size=12, font_weight='bold', edge_color='gray')
plt.title("Grafo de conversaciones en 'Maze Runner: Correr o Morir'")
plt.show()

### G.nodes: Devuelve una vista que proporciona acceso a los nodos en el grafo.
print("Nodos:", G.nodes)

### G.edges: Devuelve una vista que proporciona acceso a las aristas en el grafo.
print("Aristas:", G.edges)

### G.adj: Devuelve un diccionario que mapea los nodos a los vecinos de cada nodo.
print("Vecinos de cada nodo:", G.adj)

### G.neighbors: Devuelve un iterador que produce los vecinos de un nodo dado.
print("Vecinos de cada nodo:")
for node in G.nodes:
    print(f"{node}: {list(G.neighbors(node))}")

### G.degree: Devuelve un diccionario que mapea los nodos a sus grados.
print("Grado de cada nodo:")
print(G.degree)
