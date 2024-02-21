# Vecteurs

## Vocabulaire

### Vecteur

$$n$$-**uplet** de $$n$$ nombres réels appelés *composantes*, noté $$\vec{v} =
\begin{pmatrix} x_1 \\ \vdots \\ x_n \end{pmatrix}$$.

### Échelonnement

Opérations élémentaires sur les lignes d'une matrice :

- Permutation de deux lignes;
- Multiplication d'une ligne par un scalaire non nul;
- Addition d'un multiple d'une ligne à une autre.

### Scalaire

Nombre réel ou complexe, multiplié à un vecteur.

### Combinaison Linéaire

Expression formée de la somme de vecteurs multipliés par des scalaires, notée :

$$
\sum_{i=1}^{p} \alpha_i \vec{u}_i = \alpha_1 \vec{u}_1 + \ldots + \alpha_p
\vec{u}_p
$$

## Famille de Vecteurs

### Famille liée

Ensemble de vecteurs où au moins un vecteur est nul après échelonnement.
Au moins un des vecteurs est combinaison linéaire des autres.
On dit aussi que les vecteurs sont **linéairement dépendants**.

### Famille libre

Ensemble de vecteurs où aucun vecteur n'est nul après échelonnement.
Aucun des vecteurs n'est combinaison linéaire des autres.
On dit aussi que les vecteurs sont **linéairement indépendants**.

### Famille génératrice

Ensemble de vecteurs où tout vecteur est combinaison linéaire des autres.

### Base

Famille libre et génératrice.

## Norme et Produit Scalaire

### Norme

Aussi appelée **norme usuelle** ou **norme euclidienne**, mesure de la longueur
d'un vecteur, notée :

$$
\| \vec{v} \| = \sqrt{x_1^2 + \ldots + x_n^2} = \sqrt{\vec{v} \cdot \vec{v}}
$$

### Produit Scalaire

Somme des produits des composantes de deux vecteurs de même dimension,
notée :

$$
\vec{u} \cdot \vec{v} = \sum_{i=1}^n u_i v_i
$$
où $$n$$ est la dimension des vecteurs.
