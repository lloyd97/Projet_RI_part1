# Projet RI partie 1
Ce repertoire contient les packages partie 1 du projet.

### part_one_urdf
Ce package contient l'urdf pour la jambe du robot et launch file approprier.

### udm_project_moveitconfig
Ce package a été généré avec moveit assistant

### udm_project_control
Ce package contient les noeuds correspondant a l'urdf, les services et les launch file nécéssaire 
pour controler la jambe à travers la cinématique directe et inverse

## Installation
Pour installer ce noeud il faut le cloner dans le dossier src de votre catkin workspace (catkin_ws).

```
cd catkin_ws/src
git clone https://github.com/lloyd97/PROJET_ROS/Projet_RI_part1.git
catkin build
cd ..
source devel/setup.bash
```
## Execution 

### Visualiser la jambe
Pour visualiser, il suffit d'executer le code suivant dans le terminal:

```
source devel/setup.bash
roslaunch part_one_urdf simulate.launch
```
### Controler la jambe à l'aide de la cinématique directe

Dans le premier terminal de votre catkin workspace:
```
source devel/setup.bash
roslaunch udm_project_moveitconfig demo.launch
```

Ouvrez un autre terminal dans le deuxième terminal 
de votre catkin workspace:
```
source devel/setup.bash
roslaunch udm_project_control direct.launch
```

Ouvrez un troisieme terminal et executez les commandes
suivante:
```
source devel/setup.bash
rosservice call /direct_kin_service_legmr "joint1:
 data: -0.3
joint2:
 data: -0.4
joint3:
 data: 0.1
joint4:
 data: -0.2"
```
NOTE: Vous pouvez selectionner d'autre valeur. 

### Controler la jambe à l'aide de la cinématique inverse

Dans le premier terminal de votre catkin workspace:
```
source devel/setup.bash
roslaunch udm_project_moveitconfig demo.launch
```

Ouvrez un autre terminal dans le deuxième terminal 
de votre catkin workspace:
```
source devel/setup.bash
roslaunch udm_project_control indirect.launch
```

Ouvrez un troisieme terminal et executez les commandes
suivante:
```
source devel/setup.bash
rosservice call /indirect_kin_service_legmr "pose:
 orientation:
  w: 1
 position:
  x: 0.3
 position:
  y: 0.3
 position:
  z: -0.1"
```
NOTE: Vous pouvez selectionner d'autre valeur. 