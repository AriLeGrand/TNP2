# ⚡ Unreal Speedrun  (UE 5.6.1)

![Unreal Engine](https://img.shields.io/badge/Unreal_Engine-5.6.1-white?style=for-the-badge&logo=unrealengine&logoColor=white&color=0E1128)
![Status](https://img.shields.io/badge/Status-In_Development-orange?style=for-the-badge)

Un projet de mouvement et de speedrun ultra-fluide développé sous **Unreal Engine 5.6.1**.

---

## 🚀 Fonctionnalités Actuelles

### 🛠️ Core Mechanics
* **📦 Grab System** : Système d'interaction physique permettant de saisir et porter des cubes.
* **💨 Jump & Impulse Pads** : 
    * *Jump Pad* : Projection verticale fixe.
    * *Impulse Pad* : Propulsion dynamique basée sur le vecteur d'entrée du joueur.
* **⏱️ Speedrun Timer** : Un chronomètre précis affiché en HUD pour tracker les runs, avec gestion des zones d'arrivée.
* ** 🔁 Reverse Gravity** : Permet de déplacer le joueur facilement vers le haut sur une distance donné.

---

## 🚧 En cours d'implémentation (WIP)

Le projet est activement mis à jour avec des mécaniques de mouvement avancées :

> [!TIP]
> **Bhop (Bunny Hopping)** : Optimisation du `CharacterMovementComponent` pour permettre la conservation de l'inertie et le gain de vitesse via des sauts synchronisés.
>
> **Grappin (Physics Based)** : Système de balancement utilisant des *Physics Constraints* pour un mouvement organique et non scripté.



---

## 🛠️ Installation & Setup

1. **Prérequis** : Avoir installé **Unreal Engine 5.6.1**.
2. **Clonage** :
   ```bash
   git clone https://github.com/Quest-Education-Group/par-3g-gameboy-s2p2-24
   ```
---
## 🎮 Commandes (Layout Provisoire)
| action      | Touche       | Description                 |
|-------------|--------------|-----------------------------|
| Mouvement   | Z/Q/S/D      | Déplacement classique       |
| Saut        | Espace       | Saut (Hold pour Bhop WIP)   |
| Grab        | Click Gauche | Ramasser / Lâcher un cube   |
| Impulse Pad | Click Droit  | Impulse dans le sens du pad |


---
## 🧠 Pourquoi ces choix techniques ?

Ce projet ne se contente pas d'utiliser les paramètres par défaut d'Unreal Engine. Chaque mécanique est réfléchie pour offrir un feeling "arcade" et technique.

### 🏃‍♂️ Mouvement & Bunny Hopping (Bhop)
Contrairement au `CharacterMovementComponent` de base qui limite strictement la vitesse, j'implémente un système de **friction et d'accélération aérienne** basé sur l'algorithme classique des moteurs Quake/Source.

* **Référence théorique :** [Defrag & Quake Movement par Adrian Biagioli](https://adrianb.io/2015/02/14/bunnyhop.html).
* **Objectif :** Permettre au joueur de dépasser la vitesse maximale autorisée via des *strafe-jumps* précis. Le calcul repose sur la projection du vecteur de souhait de direction sur la vélocité actuelle, permettant d'ajouter de l'accélération uniquement si elle ne dépasse pas une limite définie, sans brider l'inertie déjà acquise.

### ⚓ Grappin & Physique
Plutôt que d'utiliser un grappin "sur rails" (scripté), j'ai opté pour une approche **Physics-Based** :
* Utilisation de `Physics Constraints` pour simuler une corde élastique.
* **Conservation du Momentum** : Le grappin interagit directement avec la vélocité accumulée par le Bhop, permettant des balancements réalistes et des catapultages à haute vitesse.

### 📐 Aperçu Technique
[Voir les blueprints](https://blueprintue.com/render/1wmvk2v-/)
