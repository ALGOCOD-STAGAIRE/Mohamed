# Installation et Configuration de Votre Environment ROS
## 1. Installation de ROS
Avant de commencer ce tutoriel assurez-vous que vous avez terminé le tutorielTutoriel d'installation de ROS Groovy sur Ubuntu (fr) ou Tutoriel d'installation de ROS sur Ubuntu (en). 
## 2. Gérer son Environment
Lors de l'installation de ROS, vous verrez que vous serez invité à sourcer un des nombreux fichiers de configuration *.sh, voire ajouter cette commande «source» au script de démarrage du shell. Ceci est nécessaire car ROS repose sur la notion de combinaisons des espaces en utilisant l'environnement du shell. Cela rend le développement des différentes versions de ROS ou des différents packages plus facile. 
Si vous avez des problèmes pour trouver où utiliser vos packages, assurez-vous que votre environnement est correctement configuré. Un bon moyen de vérifier est de s'assurer que les environment variables comme ROS_ROOT et ROS_PACKAGE_PATH sont configurées:
```
export | grep ROS
```
Si elles n'étaient pas configurées, il vous faudrait 'sourcer' les bons fichiers setup.*sh .
Ces fichiers d'environnement ont déjà été créés pour vous, mais peuvent avoir plusieurs origines:
- Les packages ROS installés via les package managers fournissent des fichiers setup.*sh
- rosbuild workspaces fournit des fichiers setup.*sh utilisant des outils tels que rosws
- Des fichiers setup.*sh sont créés automatiquement par les packages catkin building ou installing

Si vous avez juste installé ROS depuis apt sur Ubuntu alors vous aurez des fichiers setup.*sh dans '/opt/ros/<distro>/', et vous pouvez le 'sourcer' par la commande suivante : 
  
Utilisez le nom court de votre distribution à la place de <distro>

Par exemple, si vous avez installé la version Hydro de ROS, la commande serait :

```
  source /opt/ros/melodic/setup.bash
```
Vous devrez lancer cette commande dans chaque nouveau shell que vous ouvrirez pour avoir accès aux commandes ROS, à moins que vous n'ajoutiez cette ligne à votre fichier .bashrc. Cette méthode vous permet d'installer plusieurs distributions ROS (e.g. fuerte and groovy) sur le même ordinateur et de basculer de l'une à l'autre.

Sur d'autres plateformes, vous pourrez trouver les fichiers setup.*sh dans le répertoire ROS où ROS est installé. 
## 3. Créer un Workspace ROS
```
   mkdir -p ~/catkin_ws/src 
   cd ~/catkin_ws/src
   catkin_init_workspace
```
Même si l'espace de travail est vide (il n'y a pas de paquets dans le dossier 'src', juste un lien unique CMakeLists.txt), vous pouvez quand même "construire" l'espace de travail: 
```
cd ~/catkin_ws/
catkin_make
```
  
La commande catkin_make est un outil qui facilite le travail avec catkin workspaces. Si vous regardez dans le dossier courrant vous verrez les dossiers 'build' et 'devel'. A l'interieur du dossier 'devel' vous pouvez voir maintenant qu'il y a plusieurs fichiers setup.*sh. "Sourcer" un de ces fichiers va positionner ce workspace en tête de votre environment. Pour en savoir plus il faut se réferrer à la documentation générale de catkin. Avant de continuer "sourcez" votre nouveau fichier setup.*sh : 
  ``` 
  source devel/setup.bash 
  ```
  Maintenant que votre environnement est configuré, continuez avec le tutoriel ROS file system tutorial. 
