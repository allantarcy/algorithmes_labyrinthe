# Contexte des algorithmes

Avant de se déplacer dans le labyrinthe, le robot reçoit son orientation initiale **N - E - S - O**.

N = 0 , E = 1, S = 2, O = 3 

Pour avancer le robot cherche la fonction **F (forward)**.

Pour tourner à droite le robot cherche la fonction **R (right)**.

Pour tourner à gauche le robot cherche la fonction **L (left)**.

Pour faire demi-tour, le robot cherche la fonction **B (back)**.

## Données en entrée

Labyrinthe : (Matrice carrée)

$$\begin{array}{ccccc}
{0}&{1}&{2}&{3}&{4}\\
{5}&{6}&{7}&{8}&{9}\\
{10}&{11}&{12}&{13}&{14}\\
{15}&{16}&{17}&{18}&{19}\\
{20}&{21}&{22}&{23}&{24}\\
\end{array}$$

Numéro de la case courante (CC)

Numéro de la case d'arrivée (CA)

Vecteur de murs (1,4) : (M)

## Fonctions nécessaires pour l'implémentation en environnement réel

```fortran
procedure get_murs()

    MF = 0, MR = 1, MB = 2, ML = 3
    M = (0,0,0,0)

    if capteur_gauche == 1 then !Mur à droite du robot
        M(ML) = 1
    end if

    if capteur_median == 1 then !Mur à droite du robot
        M(MF) = 1
    end if

    if capteur_droit == 1 then !Mur à droite du robot
        M(MR) = 1
    end if

    return M

end procedure
```

---

```fortran
procedure case_courante()

    if O == 0 then !Avancer vers le nord
        CC = CC - taille_matrice
    else if O == 1 then !Avancer vers l'est
        CC = CC + 1
    else if O == 2 then !Avancer vers le sud
        CC = CC + taille_matrice
    else if O == 3 then !Avancer vers l'ouest
        CC = CC - 1
    end if

    return CC

end procedure
```

---

fonction F():

Faire avancer les deux moteurs en suivant la ligne médiane.

S'arrêter lorsque les deux capteurs de lignes latéraux ont passé deux lignes.

Mettre à jour la case courante avec la fonction `case_courante()`.

---

fonction R():

Faire reculer le moteur droit et avancer le moteur gauche.

S'arrêter lorsque le capteur de ligne médian détecte une nouvelle ligne noire.

Incrémenter l'orientation de 1 modulo 4 ( `o = (o + 1) mod 4` )

---

fonction L():

Faire reculer le moteur gauche et avancer le moteur droit.

S'arrêter lorsque le capteur de ligne médian détecte une nouvelle ligne noire.

Décrémenter l'orientation de 1 modulo 4 ( `o = (o - 1) mod 4` )

---

fonction B():

Faire reculer le moteur droit et avancer le moteur gauche.

S'arrêter lorsque le capteur de ligne médian détecte deux lignes noires.

Incrémenter l'orientation de 2 modulo 4 ( `o = (o + 2) mod 4` )