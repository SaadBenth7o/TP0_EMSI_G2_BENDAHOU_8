==========================================================
TP 0 – Introduction à Jakarta EE (CDI + JSF)
Auteur : Bendahou Saad

Serveur : Payara 6.2025.10
Java 
==========================================================

OBJECTIFS
----------------------------------------------------------
Prendre en main Maven, Git/GitHub et les spécifications Jakarta EE (CDI et JSF)
à travers une mini-application Web simulant un mini chatbot local.
Ce TP prépare la suite (intégration d’un LLM).

----------------------------------------------------------
PRESENTATION RAPIDE DE JAKARTA EE
----------------------------------------------------------
• Successeur de Java EE (transmis par Oracle à la fondation Eclipse).
• Spécifications clés : CDI (injection de dépendances), JSF (interface utilisateur serveur).
• Déploiement sous forme WAR sur un serveur d’application (Payara).
• Principe “convention plutôt que configuration”.

----------------------------------------------------------
STRUCTURE DU PROJET
----------------------------------------------------------
pom.xml                     → configuration Maven
src/main/java/.../Bb.java   → backing bean (classe CDI @Named, @ViewScoped)
src/main/webapp/index.xhtml → page JSF principale
src/main/webapp/WEB-INF/web.xml → configuration accueil et filtres

----------------------------------------------------------
LANCEMENT
----------------------------------------------------------
1. Démarrer Payara :
   asadmin start-domain

2. Compiler et packager :
   mvn clean package

3. Déployer le fichier .war dans :
   payara/domains/domain1/autodeploy/

4. Accéder à l’application :
   http://localhost:8080/TP0_Bendahou/
   (remplacer selon le nom de ton projet)

5. Console d’administration Payara :
   http://localhost:4848
----------------------------------------------------------
TRAITEMENT PERSONNEL (BONUS)
----------------------------------------------------------
Méthode concernée : envoyer()

Traitement choisi : ANALYSE DE TEXTE
  - Normalisation (trim + espaces)
  - Comptage du nombre total de mots
  - Comptage du nombre de mots uniques
  - Détection si le texte est un palindrome (en ignorant espaces, accents, ponctuation)
  - Lors du premier envoi, affichage du rôle système choisi et verrouillage du changement

Exemple :
  Entrée : "Élu par cette crapule"
  Sortie :
  === RÔLE SYSTÈME ===
  You are a helpful assistant. You help the user to find the information they need.
  If the user type a question, you answer it.

  === ANALYSE DE VOTRE TEXTE ===
  Texte normalisé : Élu par cette crapule
  Mots : 4 | Mots uniques : 4
  Palindrome (ignorant espaces/accents/ponctuation) : OUI