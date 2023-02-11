# Algorithme 'tribord'

*Cette stratégie de résolution s'appuie sur un unique robot qui tournera toujours à droite en cas de choix.*

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

Orientation initiale : (O)

Vecteur de murs (1,4) : (M)

## Détail de l'algorithme

```fortran

procedure tribord

    O = orientation_initiale
    CC = case_initiale
    CA = case_arrivee

    MF = 0, MR = 1, MB = 2, ML = 3

    M = get_murs(CC)

    while CC ~= CA do
        
        if M(MR) == 0 then
            R()
            F(1)
        else if M(MF) == 0 then
            F(1)
        else if M(ML) == 0 then
            L()
            F(1)
        else
            B()
            F(1)
        end if

        CC = case_courante()
        M = get_murs(CC)    

    end while

end procedure

```