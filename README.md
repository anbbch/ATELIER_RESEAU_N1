------------------------------------------------------------------------------------------------------
🎯Comprendre les bases du réseau (OSI, DHCP, NAT)
------------------------------------------------------------------------------------------------------
Cet atelier propose une exploration pratique des fondamentaux des réseaux informatiques à travers trois mécanismes essentiels : le modèle OSI, le protocole DHCP et la traduction d’adresses NAT.  
  
L’objectif est de visualiser concrètement le fonctionnement du réseau, depuis la structure des communications jusqu’à l’attribution des adresses IP et la communication avec Internet. Dans un premier temps, nous allons découvrir le modèle OSI (Open Systems Interconnection) et son rôle comme cadre conceptuel pour organiser les communications réseau en 7 couches. Ensuite, notre atelier reviendra sur le protocole DHCP, qui permet d’attribuer automatiquement une configuration réseau (adresse IP, passerelle, DNS). Et enfin, l’atelier abordera le NAT (Network Address Translation), un mécanisme clé permettant à plusieurs machines d’un réseau privé de partager une même adresse IP publique pour accéder à Internet.  
  
**Notre atelier**  

![Screenshot Actions](Architecture_cible_Reseau.png)  

-------------------------------------------------------------------------------------------------------
🧩 Séquence 1 : GitHUB
-------------------------------------------------------------------------------------------------------
Objectif : Création d'un Repository GitHUB pour travailler avec son projet  
Difficulté : Très facile (~10 minutes)
-------------------------------------------------------------------------------------------------------
**Faites un Fork de ce projet**. Si besoin, voici une vidéo d'accompagnement pour vous aider à "Forker" un Repository Github : [Forker ce projet](https://youtu.be/p33-7XQ29zQ)  

---------------------------------------------------
🧩 Séquence 2 : Création d'un site chez Pythonanywhere
---------------------------------------------------
Objectif : Créer un hébergement sur Pythonanywhere  
Difficulté : Faible (~10 minutes)
---------------------------------------------------

Rendez-vous sur **https://www.pythonanywhere.com/** et créez vous un compte. Puis créez un serveur Web **Flask 3.15**.  
  
---------------------------------------------------------------------------------------------
🧩 Séquence 3 : Les Actions GitHUB (Industrialisation Continue)
---------------------------------------------------------------------------------------------
Objectif : Automatiser la mise à jour de votre hébergement Pythonanywhere  
Difficulté : Moyenne (~15 minutes)
---------------------------------------------------------------------------------------------
Dans le Repository GitHUB que vous venez de créer précédemment lors de la séquence 1, vous avez un fichier intitulé deploy-pythonanywhere.yml et qui est déposé dans le répertoire .github/workflows. Ce fichier a pour objectif d'automatiser le déploiement de votre code sur votre site Pythonanywhere. Pour information, c'est ce que l'on appel des Actions GitHUB. Ce sont des scripts qui s'exécutent automatiquement lors de chaque Commit dans votre projet (C'est à dire à chaque modification de votre code). Ces scripts (appelés actions) sont au format yml qui est un format structuré proche de celui d'XML.  

Pour utiliser cette Action (deploy-pythonanywhere.yml), **vous avez besoin de créer des secrets dans GitHUB** afin de ne pas divulguer des informations sensibles aux internautes de passage dans votre Repository comme vos login et password par exemple.  

Pour cet atelier, **vous avez 4 secrets à créer** dans votre Repository GitHUB : **Settings → Secrets and variables → Actions → New repository secret**  
  
**PA_USERNAME** = votre username PythonAnywhere.  
**PA_TOKEN** = votre API token. Token à créer dans pythonanywhere (Acount → API Token).  
**PA_TARGET_DIR** = Web → Source code (ex: /home/monuser/myapp).  
**PA_WEBAPP_DOMAIN** = votre site (ex: monuser.pythonanywhere.com).  
  
**Dernière étape :** Pour engager l'automatisation de votre première Action, vous devez cliquer sur le gros boutton vert dans l'onglet supérieur [Actions] dans votre Repository Github. Le boutton s'intitule "I understand my workflows, go ahead and enable them"   

Notions acquises de cette séquence :  
Vous avez vu dans cette séquence comment créer des secrets GiHUB afin de mettre en place de l'industrialisation continue.   

---------------------------------------------------
🗺️ Séquence 4 : OSI (Open Systems Interconnection)
---------------------------------------------------
Vous pouvez observez les différentes couches OSI sur votre site **{site}.pythonanywhere.com/osi**  
  
**Exercice 1 : Définissez les termes suivants (Répondre directement dans GitHub)**    
* Un protocole,
  
Un protocole de niveau N est un ensemble de règles associé à une couche N qui permet de supporter un service N, par exemple acheminer des informations entre deux hôtes. Un protocole de niveau N peut supporter la mise en oeuvre éventuelle de plusieurs services. Ces règles s'enchaînent de façon précise, définissent des états dont l'occurrence dépend d'états antérieurs et d'événements, et qui génère d'autres événements.

Exemple : HTTP, TCP, IP.

* Une entité protocolaire,

Une entité protocolaire de niveau N correspond au programme qui exécute un protocole de niveau N sur un hôte. C'est souvent matérialisé par un automate (machine à états - modèle formel qui décrit les différents états possibles). On utilise dans ce cas l'expression automate protocolaire.

Exemple : l’implémentation de TCP dans le système d’exploitation.

* Un service,

Un service est une fonctionnalité fournie par une couche du modèle OSI à la couche supérieure.
Il définit ce que la couche offre, sans préciser comment cela est réalisé.

Exemple : la couche transport fournit un service de communication fiable aux applications.

* Une primitive de service,

Une primitive de service : Une primitive de service est une opération qui invoque un service réalisé par une entité protocolaire. Pour un service, elles sont au nombre de 4 : 
- REQ (Request)
- IND (Indication)
- RESP (Response)
- CONF (Confirmation)
Parfois REQ et IND sont les seules définies. Par exemple T-CON-REQ, est une primitive de service de demande d'ouverture de connexion de la couche Session ou au-dessus à la couche Transport.

Les primitives classiques sont par exemple :

- REQUEST
- INDICATION
- RESPONSE
- CONFIRM

* Une Service Data Unit (SDU) par rapport à une PDU

SDU vs PDU : Une SDU correspond aux informations qui sont passées à l'aide d'une primitive de service, Les PDU pour émission sont formées par une SDU de la couche supérieure à laquelle on a ajouté des informations de contrôle (adresse destination, adresse  source, numérotation de message, taille de fenêtre glissante…) pour la transmettre.
<img width="552" height="204" alt="image" src="https://github.com/user-attachments/assets/cd464564-c28f-43bd-9588-bb753ba277ce" />

* Un point d'accès à un service SAP (Service Access Point)

SAP (Service Access Point) : Un point d'accès à un service SAP (Service Access Point) est un point de traversée de l'interface entre 2 couches adjacentes. C'est aussi l'identification ou l'adresse, unique, d'un accès à un service..



---------------------------------------------------
🗺️ Séquence 5 : Retour sur le protocole DHCP
---------------------------------------------------
Vous pouvez observez le protocole DHCP sur votre site **{site}.pythonanywhere.com/dhcp**  
  
**Exercice 2 : Créer une image montrant l’encapsulation des couches suivantes**    
<img width="2816" height="1536" alt="image" src="https://github.com/user-attachments/assets/a1443350-6884-4954-912f-c4ad76a1c5d6" />

  
--------------------------------------------------------------------
🧠 Troubleshooting :
---------------------------------------------------
Objectif : Visualiser ses logs et découvrir ses erreurs
---------------------------------------------------
Lors de vos développements, vous serez peut-être confronté à des erreurs systèmes car vous avez faits des erreurs de syntaxes dans votre code, faits de mauvaises déclarations de fonctions, appelez des modules inexistants, mal renseigner vos secrets, etc…  
Les causes d'erreurs sont quasi illimitées. **Vous devez donc vous tourner vers les logs de votre système pour comprendre d'où vient le problème** :  

Vos log sont accéssible via les URL suivantes :  
* Access log : {site}.pythonanywhere.com.access.log
* Error log : {site}.pythonanywhere.com.error.log
* Server log: {site}.pythonanywhere.com.server.log
