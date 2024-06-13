# Proyecto-Jair-Montes

# Proyecto sobre la creación de un grafo de las interacciones de los personajes en la saga Maze Runner

### NetworkX:

"""
Qué es: NetworkX es una biblioteca de Python para la creación, manipulación y estudio de la estructura, dinámica y funciones de complejas redes de grafos.

Qué hace: Permite trabajar con grafos (redes) de una manera muy flexible y poderosa. Puedes crear grafos, agregar y eliminar nodos y aristas, calcular propiedades de grafos, encontrar caminos y realizar muchas otras operaciones relacionadas con la teoría de grafos.
"""
### Matplotlib:

"""
Qué es: Matplotlib es una biblioteca de Python para la creación de visualizaciones estáticas, animadas e interactivas.

Qué hace: Proporciona una forma muy flexible y robusta de crear una amplia gama de gráficos y visualizaciones, incluyendo gráficos de líneas, gráficos de dispersión, histogramas, mapas de calor, y mucho más. Es especialmente útil para la visualización de datos científicos y de ingeniería.
"""

# Primero instala las librerías desde la terminal:
# pip install networkx matplotlib

# Después importamos las librerías:
import networkx as nx
import matplotlib.pyplot as plt


# Crear un grafo vacío
"""
Para crear un grafo vacío ejecutamos la siguiente línea e código:
"""
G = nx.Graph()

# Lista de personajes principales y secundarios de "Maze Runner: Correr o Morir"
"""
Definimos una lista llamada Personajes donde ingresamos cada nombre de los personajes como cadenas:
"""
personajes = [
    "Thomas", "Teresa", "Minho", "Newt", "Jeff", "Ben", "Clint", "Marcus", "AvaPaige",
    "DraCrowford", "Ponytail", "DrUno", "MamaDeThomas",
    "Carl", "Zart", "Sonya", "Janson", "Brenda", "Vince", "Jorge", "Harriet",
    "MaryCooper", "Aris", "David", "Riley", "Sarten", "Winston", "Lawrence", "Chuck",
    "Gally", "Alby", "Shai", "FionaRamsey", "PetterButtler", "JansonAsistente",
    "Alex", "JefeEstacion"
]

# Añadir nodos (personajes)
"""
Ejecutamos la siguiente línea de código:
"""
for personaje in personajes:
    G.add_node(personaje)

# Lista de conversaciones/interacciones entre personajes
"""
Definimos la lista llamada "interacciones" en tuplas la cual es una colección ordenada e inmutable de elementos en Python. Las tuplas se utilizan a menudo para agrupar datos relacionados.
"""

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

# Añadir aristas (conversaciones entre personajes)

for interaccion in interacciones:
    G.add_edge(*interaccion)

"""
La línea de código anterior es un bucle for que itera sobre una lista de tuplas llamada interacciones y agrega cada tupla como una arista (edge) en un grafo G utilizando la biblioteca NetworkX.
"""

# Crear una nueva figura de matplotlib con el tamaño especificado

plt.figure(figsize=(12, 10))

"""
La línea de código anterior es parte de la biblioteca Matplotlib y se utiliza para crear una nueva figura para la visualización de gráficos.
"""

# Asignar posiciones a los nodos en el grafo 
"""
Para esto utilizamos el algoritmo de disposición Spring Layout, esto asegura una disposición adecuada de los nodos en el espacio.
"""
pos = nx.spring_layout(G, seed=42)  

# Con la siguiente línea de código lo que se hace es dibujar el grafo G con las posiciones asignadas, incluyendo etiquetas en los nodos, personaliza la apariencia del grafo, como el color de los nodos, el tamaño de los nodos, el tamaño de la fuente de las etiquetas, el grosor de los bordes y el color de los bordes.

nx.draw(G, pos, with_labels=True, node_color='lightblue', node_size=3000, font_size=12, font_weight='bold', edge_color='gray')

# Agregar un título a la figura:
plt.title("Grafo de conversaciones en 'Maze Runner: Correr o Morir'")

# Mostrar la figura en la ventana de salida:
plt.show()


# Utilizamos G.nodes que devuelve una vista que proporciona acceso a los nodos en el grafo:
print("Nodos:", G.nodes)

# Con G.edges devolvemos una vista que proporciona acceso a las aristas en el grafo:
print("Aristas:", G.edges)

# Para devolver un diccionario que mapea los nodos a los vecinos de cada nodo utilizamos G.adj: 
print("Vecinos de cada nodo:", G.adj)

# La línea de código siguiente devuelve un iterador que produce los vecinos de un nodo dado:
print("Vecinos de cada nodo:")
for node in G.nodes:
    print(f"{node}: {list(G.neighbors(node))}")

# Para finalizar utilizamos el siguiente código que devuelve un diccionario que mapea los nodos a sus grados.
print("Grado de cada nodo:")
print(G.degree)
