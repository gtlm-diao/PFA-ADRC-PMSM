# Fonctionnement du bloc ADRC

### ✅ Ce que tu dis est vrai et voici le fil logique bien résumé :

1. **On part d’un état estimé précédent** :

   $$
   \hat{x}(t)
   $$

   C’est ce qu’on connaissait de l’état à l’instant précédent.

2. **À partir de cet état et de l’entrée $u(t)$**, on **calcule une variation** (ou dérivée) attendue :

   $$
   \dot{\hat{x}}_{\text{préd}}(t) = A\hat{x}(t) + Bu(t)
   $$

3. **Mais on sait que ce modèle n’est pas parfait**, alors on compare ce qu’on aurait dû voir à la sortie :

   $$
   \hat{y}(t) = C\hat{x}(t)
   $$

   avec la vraie mesure :

   $$
   y(t)
   $$

4. **On fait la différence (l’erreur)** :

   $$
   e(t) = y(t) - \hat{y}(t)
   $$

   C’est ce que tu appelles la différence entre $y(t)$ et $y^\wedge(t)$. Bravo.

5. **On corrige la variation estimée des états internes avec cette erreur** :

   $$
   \dot{\hat{x}}(t) = A\hat{x}(t) + Bu(t) + L\,e(t)
   $$

6. **Maintenant qu’on a la variation complète (avec correction)**, on **met à jour** les états internes estimés :

   $$
   \hat{x}(t+\Delta t) = \hat{x}(t) + \dot{\hat{x}}(t) \cdot \Delta t
   $$

7. Ensuite on **recommence la boucle** à l’instant suivant avec la nouvelle estimation $\hat{x}(t+\Delta t)$.

---

### 🧠 Ce que tu décris est **le principe fondamental d’un observateur** :

* Prédire (simulateur),
* Corriger (boucle de rétroaction sur l’erreur),
* Répéter (itération).

Et dans le cas de l’**ESO**, on estime aussi une perturbation **comme un état supplémentaire**.
Par exemple, si le système est affecté par une force extérieure $f(t)$, on la traite comme un état à part entière :

$$
x = \begin{bmatrix}
\text{état physique} \\
\text{perturbation totale}
\end{bmatrix}
$$

---

### 📌 Résumé de ton raisonnement, bien clarifié

| Étape | Action                                           |
| ----- | ------------------------------------------------ |
| 1     | Tu as $\hat{x}(t)$, l’état estimé au temps t     |
| 2     | Tu calcules $\hat{y}(t) = C\hat{x}(t)$           |
| 3     | Tu compares avec $y(t)$, la mesure réelle        |
| 4     | Tu en déduis l’erreur $e(t) = y(t) - \hat{y}(t)$ |
| 5     | Tu ajustes $\dot{\hat{x}}(t)$ avec $L\,e(t)$     |
| 6     | Tu avances vers $\hat{x}(t+\Delta t)$            |
| 7     | Tu recommences à la prochaine itération          |
