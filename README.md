# Laboratorio 4
Técnicas de Simulación en Computadoras: Cuarta práctica de laboratorio 

## Contenido

<p align="center"> Método de los Elementos Finitos para el problema de dinámica de fluidos en una dimensión 
con funciones de forma lineales y con peso de Galerkin </p>

### Cambios en classes.h

```cpp
//Se actualiza esta enumeracion para tomar en cuenta los nuevos parametros
enum parameters {ELEMENT_LENGTH,ADJECTIVE_VELOCITY,DYNAMIC_VISCOSITY,DENSITY,EXTERNAL_FORCE};

//Esta enumeracion ya no necesita el valor de Neumann
enum sizes {NODES,ELEMENTS,DIRICHLET};
```

```cpp
class item{
    protected:
        int id;
        float x;
        int node1;
        int node2;
        float value;
    public:
    //Se añaden setters para los atributos
        void setId(int identifier) {
            id = identifier;
        }

        void setX(float x_coord) {
            x = x_coord;
        }

        void setNode1(int node_1) {
            node1 = node_1;
        }

        void setNode2(int node_2) {
            node2 = node_2;
        }

        void setValue(float value_to_assign) {
            value = value_to_assign;
        }
```

```cpp
class mesh{
        //Se modifican los tamaños de los arreglos para adecuarse a las nuevas circumstancias
        float parameters[5];
        int sizes[3];
        //Se elimina el arreglo para las condiciones de Neumann
        node *node_list;
        element *element_list;
        condition *dirichlet_list;
    public:
        //Se actualizan los metodos para reflejar la nueva cantidad de parametros
        //y de arreglos
        void setParameters(float l,float u_bar,float nu,float rho,float f){
            parameters[ELEMENT_LENGTH]=l;
            parameters[ADJECTIVE_VELOCITY]=u_bar;
            parameters[DYNAMIC_VISCOSITY]=nu;
            parameters[DENSITY]=rho;
            parameters[EXTERNAL_FORCE]=f;
        }
   }   
```

### Cambios en problem.msh

La primera línea corresponde a respectivamente

```
0.3 1.4 0.5 1000 10
10 9 2 1
Coordinates
```

Adicionalmente, tenemos condiciones para cada variable en cada nodo

```
DirichletU
1	15
10  3
EndDirichletU

DirichletP
10  0
EndDirichletP
```



<hr>
<p align="center">Para servirles, <strong>Equipo de Instructores</strong> </p>
