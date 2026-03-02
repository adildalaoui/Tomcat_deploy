### Apache Tomcat : Vue d’ensemble et utilisation

#### Qu’est-ce qu’Apache Tomcat ?

Apache Tomcat est un serveur web open source et un conteneur de servlets développé par la Apache Software Foundation. Il est principalement utilisé pour déployer des servlets Java, des JavaServer Pages (JSP) et des applications WebSocket. Tomcat fournit un environnement de serveur web HTTP « 100 % Java » dans lequel le code Java peut s’exécuter, ce qui en fait un choix idéal pour les applications web basées sur Java.

#### Fonctionnalités clés d’Apache Tomcat :
- **Java Servlet & JSP Support : Tomcat est spécialement conçu pour exécuter des servlets Java et des JSP, permettant aux développeurs de créer du contenu web dynamique en Java.
- **Support de WebSocket : Tomcat prend en charge le protocole WebSocket, ce qui permet une communication en temps réel entre le serveur et les clients.
- **Haute compatibilité : Tomcat est compatible avec divers frameworks Java tels que Spring, Struts et Hibernate.
- **Léger : Comparé à des serveurs d’applications complets comme JBoss ou WebLogic, Tomcat est léger et plus facile à configurer et à gérer.
- **Extensible et modulaire : Tomcat permet l’intégration de composants supplémentaires, offrant un haut degré de personnalisation et d’extensibilité.

### Quelle est la différence entre Tomcat et Nginx ?

**Objectif et cas d’utilisation :**

- **Apache** Tomcat est principalement utilisé comme serveur d’applications Java. Il est conçu pour héberger des servlets Java, des JSP et des applications basées sur WebSocket. Si votre projet implique l’exécution d’applications web basées sur Java, Tomcat est un excellent choix.

- **Nginx** est un serveur web, serveur proxy inverse, répartiteur de charge et cache HTTP. Nginx excelle dans la diffusion de contenu statique (HTML, CSS, JS, images) et dans le rôle de proxy inverse pour le contenu dynamique généré par d’autres serveurs (par exemple Tomcat, Node.js, Django). Nginx est reconnu pour ses performances élevées, sa scalabilité et sa faible consommation de ressources.

**Gestion des requêtes :**

- **Tomcat** est conçu pour gérer les requêtes et réponses HTTP des applications Java. Il est équipé pour gérer les servlets Java, les JSP et les technologies associées, ce qui implique le traitement du code Java côté serveur.
- **Nginx** est conçu pour gérer efficacement un grand nombre de connexions simultanées, ce qui le rend idéal pour servir du contenu statique et pour l’équilibrage de charge. Il utilise une architecture événementielle et non bloquante, capable de traiter plusieurs requêtes dans un seul thread, contrairement au modèle classique « un thread par requête » utilisé par les serveurs web traditionnels.

**Performance:**

- **Tomcat** est optimisé pour servir du contenu dynamique généré par des applications Java. Cependant, il peut être moins performant que Nginx pour servir du contenu statique ou gérer un grand nombre de connexions simultanées.

-**Nginx** est optimisé pour la performance, en particulier pour servir du contenu statique et gérer une forte concurrence. Il est souvent utilisé comme proxy inverse devant des serveurs d’applications comme Tomcat, afin de servir le contenu statique et d’équilibrer la charge.

### Quand utiliser Nginx, Tomcat ou Apache HTTP Server ?

**1. Quand utiliser Apache Tomcat ?:**

-**Applications web basées sur Java** : Si votre application est écrite en Java et utilise des Servlets, JSP ou WebSocket, Tomcat est le meilleur choix.
-**Frameworks Java** : Pour les applications développées avec des frameworks Java comme Spring ou Struts, Tomcat offre un environnement serveur compatible et robuste.
-**Serveur d’applications autonome** : Si votre application n’a pas besoin de toutes les fonctionnalités d’un serveur Java EE complet, Tomcat constitue une alternative légère et efficace.

**2.Quand utiliser Nginx :**
-**Distribution de contenu statique** : Nginx excelle dans la diffusion de fichiers statiques (HTML, CSS, JavaScript, images) avec une grande efficacité.
-**Proxy inverse et répartition de charge** : Nginx est souvent utilisé comme proxy inverse pour distribuer le trafic entrant vers différents serveurs d’applications, y compris Tomcat, améliorant ainsi les performances et la disponibilité.
-**Applications à forte concurrence** : Pour les applications nécessitant la gestion de milliers de connexions simultanées, l’architecture événementielle de Nginx en fait un choix idéal.
-**Passerelle API (API Gateway)** : Nginx peut être utilisé comme passerelle API, gérant et routant le trafic vers différents services backend.

**3.Quand utiliser Apache HTTP Server :**
-**Hébergement web général** : Apache HTTP Server est un serveur web polyvalent capable de servir du contenu statique et dynamique. Il est flexible et prend en charge une large gamme de modules pour différentes fonctionnalités.
PHP ou autre contenu dynamique : Apache est un bon choix si vous servez du contenu dynamique généré par des langages comme PHP, Python (via mod_wsgi) ou Perl.
-**Compatibilité et flexibilité** : Apache est très configurable et supporte de nombreux modules, ce qui le rend adapté à une grande variété d’environnements.

**Scénarios de déploiement courants**
-**Nginx + Tomcat** : Nginx peut être utilisé comme proxy inverse devant Tomcat. Dans cette configuration, Nginx gère toutes les requêtes HTTP entrantes, sert directement le contenu statique et transmet les requêtes dynamiques à Tomcat. Ce montage combine la performance de Nginx pour les fichiers statiques avec les capacités Java de Tomcat.
-**Nginx + Apache HTTP Server** : Nginx peut agir comme proxy inverse pour Apache, gérant le contenu statique et la terminaison SSL, tandis qu’Apache traite le contenu dynamique via ses différents modules.
-**Tomcat autonome** : Pour les applications purement basées sur Java, Tomcat peut être utilisé comme serveur autonome, surtout lorsque l’application ne nécessite pas de gérer une grande quantité de contenu statique.

### Résumé

Le choix entre Tomcat, Nginx et Apache HTTP Server dépend des besoins spécifiques de votre application :
Utilisez **Tomcat** pour les applications basées sur Java nécessitant un conteneur de servlets.
Utilisez **Nginx** pour la diffusion de contenu statique haute performance et à forte concurrence, ou comme proxy inverse / répartiteur de charge.
Utilisez **Apache HTTP Server** pour un hébergement web généraliste offrant flexibilité et support de modules pour différents langages et environnements.



# Guide d’installation et de configuration d’Apache Tomcat 9.0.65

Ce guide fournit des instructions étape par étape pour installer Apache Tomcat 9.0.65 sur un système Linux, configurer le serveur et mettre en place l’accès administratif.

## Table of Contents

1. [Prerequisites](#prerequisites)
2. [Installation Steps](#installation-steps)
   - [1. Download and Extract Tomcat](#1-download-and-extract-tomcat)
   - [2. Configure Tomcat Users](#2-configure-tomcat-users)
   - [3. Create Start and Stop Scripts](#3-create-start-and-stop-scripts)
   - [4. Modify Access Restrictions](#4-modify-access-restrictions)
3. [Starting and Stopping Tomcat](#starting-and-stopping-tomcat)


## Prerequis

-Un système d’exploitation Linux avec des privilèges sudo.
-Une connaissance de base des commandes Linux.
-installation de JAVA et Maven

## Étapes d’installation :

### 1.Télécharger et extraire Tomcat

1. **Passer en utilisateur root :**

   ```bash
   sudo su
   ```

2. **Se déplacer dans le répertoire /opt :**

   ```bash
   cd /opt
   ```

3. **Télécharger l’archive tarball d’Apache Tomcat 9.0.65:**

   ```bash
   sudo wget https://archive.apache.org/dist/tomcat/tomcat-9/v9.0.65/bin/apache-tomcat-9.0.65.tar.gz
   ```

4. **Extraire l’archive téléchargée:**

   ```bash
   sudo tar -xvf apache-tomcat-9.0.65.tar.gz
   ```

### 2. Configurer les utilisateurs Tomcat

1. **Se déplacer dans le répertoire de configuration de Tomcat :**

   ```bash
   cd /opt/apache-tomcat-9.0.65/conf
   ```

2. **Éditer le fichier tomcat-users.xml pour ajouter un utilisateur admin :**

   ```bash
   sudo vi tomcat-users.xml
   ```

3. **Ajouter la ligne suivante avant la balise de fermeture </tomcat-users> :**

   ```xml
   <user username="admin" password="admin1234" roles="admin-gui,manager-gui,manager-script"/>
   ```

 Cela crée un utilisateur administrateur avec le nom d’utilisateur admin et le mot de passe admin1234. L’utilisateur se voit attribuer des rôles permettant d’accéder aux interfaces administratives et de gestion de Tomcat.

### 3. Créer les scripts de démarrage et d’arrêt de Tomcat

1. **Créer des liens symboliques pour les scripts de démarrage et d’arrêt de Tomcat**

   ```bash
   sudo ln -s /opt/apache-tomcat-9.0.65/bin/startup.sh /usr/bin/startTomcat
   sudo ln -s /opt/apache-tomcat-9.0.65/bin/shutdown.sh /usr/bin/stopTomcat
   ```
Ces liens permettent de démarrer et d’arrêter Tomcat en utilisant les commandes tomcat-start et tomcat-stop depuis n’importe quel répertoire.

### 4. Modifier les restrictions d’accès dans Tomcat

1. **Éditer le fichier context.xml pour l’application Manager**

   ```bash
   sudo vi /opt/apache-tomcat-9.0.65/webapps/manager/META-INF/context.xml
   ```

2. **Commenter la configuration RemoteAddrValve**


   ```xml
   <!--
   <Valve className="org.apache.catalina.valves.RemoteAddrValve"
   allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" />
   -->
   ```
Ce changement supprime la restriction qui limitait l’accès à l’application Manager uniquement depuis le localhost.

3. **le fichier context.xml pour l’application Host Manager**

   ```bash
   sudo vi /opt/apache-tomcat-9.0.65/webapps/host-manager/META-INF/context.xml
   ```

4. **Commenter la configuration RemoteAddrValve pour Host Manager**

   ```xml
   <!--
   <Valve className="org.apache.catalina.valves.RemoteAddrValve"
   allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" />
   -->
   ```

   Ce changement supprime la restriction qui limitait l’accès à l’application Host Manager uniquement depuis le localhost.

## Démarrage et arrêt de Tomcat

- **Pour arreter Tomcat:**

  ```bash
  sudo stopTomcat
  ```

- **Pour lancer Tomcat:**

  ```bash
  sudo startTomcat
  ```

Ces commandes permettent de contrôler le fonctionnement du serveur Tomcat, en le démarrant ou en l’arrêtant selon les besoins.

-**Créer un build de son application**
 En utilisant
 
'''bash
mvn package
'''

- **Copier le war dans le dossier webapps**

- Pour acceder a l'application, il faut saisir l'url:8080/nom_de_l'application




