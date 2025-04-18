# Informations générales
vidéo explicative sur la position de l'angle du rotor 

## COMMANDE FOC (Vectoorielle)
### Rôle Clé de l'Onduleur  et sa complicité avec theta (la position du rotor pour créer un champ magnétique maximal
-Il convertit la tension continue (batterie) en tensions alternatives synchronisées avec θ.

-Technique courante : Modulation PWM pour ajuster finement amplitude et phase.

[Link vidéo  explivcative interaction des champs statoriques et rotoriques et problématique du FOC](https://youtu.be/2ICU2bi4KeQ?si=6X5m7smUAL9vT6yg)


### Key Factors Influencing Mass Adoption of Electric Vehicles 
[Vidéo](https://youtu.be/2-20N4ly93E?si=QI_657oBsGWdPCbA "Vidéo explicatire")

The high upfront cost and limited range of electric vehicles (EVs) are the primary barriers to mass adoption. However, EV manufacturers are actively addressing these challenges in next-generation designs.  

### Efficiency Improvements in EVs
EVs already represent a significant leap in efficiency compared to internal combustion engines (ICEs), increasing from 20-30% efficiency (ICE) to over 90% for electric motors.  

### Tesla’s Motor Innovation
Tesla boosted the efficiency of the Model 3 motor by switching from an AC induction motor to a **permanent magnet switched reluctance (PMSR) motor**. This change alone increased the Model 3’s range by **30-40%** compared to the Model S.  

### The Next Big Leap: Axial Flux Motors  
A promising technology for further efficiency gains is the axial flux motor.  

### How Axial Flux Motors Work 
The key difference between conventional radial flux motors and axial flux motors lies in the **direction of magnetic flux**:  
- Radial Flux Motors**: Magnetic flux is *perpendicular* (90°) to the axis of rotation.  
- **Axial Flux Motors**: Magnetic flux runs *parallel* to the axis of rotation.  

### Advantages of Axial Flux Motors 
1. *Higher Electromagnetic Efficiency* – More torque is generated per unit of electromagnetic flux.  
2. *Better Torque Production* – Torque in axial flux motors scales with the **cube** of the motor diameter (vs. the **square** in radial flux motors).  
3. *Superior Power-to-Weight Ratio* – Lighter and more compact.  
4. *Easier Cooling* – The coil design allows for better thermal management.  
5. *Material Efficiency* – Uses fewer rare-earth magnets and copper, reducing costs.  

### Comparison to Disc vs. Drum Brakes  
Axial flux motors are like **disc brakes**, making better use of space for torque generation, whereas radial flux motors resemble **drum brakes**—bulkier and less efficient.  

### **Potential Range Increase**  
Axial flux motors could improve EV range by **up to 20%** (e.g., in a Tesla Model 3).  

### **Challenges of Axial Flux Motors**  
1. **Higher Rotor Inertia** – Larger diameters increase rotational inertia.  
2. **Manufacturing Complexity** – More difficult to produce than radial flux motors.  
   - Companies like **Infinitum Electric** are solving this by using **PCB-based stators**, making production easier.  

### **Innovative Hybrid Approach: Koenigsegg’s Quark Motor**  
Koenigsegg, the hypercar manufacturer, combined **axial and radial flux motors** into a single unit called the **Quark motor**, achieving class-leading **power-to-weight ratio** and torque efficiency.  

### **Conclusion**  
Axial flux motors represent a major advancement in EV technology, offering greater efficiency and range. While manufacturing challenges remain, companies are rapidly innovating to bring this technology to mainstream EVs.  

Thanks for reading—hope you found this informative!  

---

 ### Key Improvements: 
✅ **Removed timestamps** for cleaner readability.  
✅ **Restructured for logical flow** (problem → current solutions → next-gen tech).  
✅ **Simplified technical explanations** while keeping key details.  
✅ **Added headings** for better organization.  


# NECESSITE DE COMPENSATION
Le découplage dans les machines électriques (comme la MS) a deux objectifs clés :

Linéariser le système (éliminer les couplages non linéaires entre axes d-q).

Rendre le système plus rapide (en supprimant les retards induits par les interactions entre variables).

Voici comment cela fonctionne, avec une comparaison MCC vs MS :

1. Problème des Couplages en Machine Synchrone (MS)
En MS, les équations de tension dans le repère tournant (d-q) font apparaître des termes croisés dus à la rotation du champ magnétique :

{
vd=Rid+Lddiddt−ωLqiqvq=Riq+Lqdiqdt+ω(Ldid+ψf)
où :

ωLqiqωL q​ i q​  et ωLdidωL ​ i d​  sont des termes de couplage non linéaires.

Ils créent des interactions entre les axes d et q, ce qui :

Ralentit la dynamique (car les actions sur un axe perturbent l'autre).

Rend le contrôle plus complexe (PID classique inefficace).

2. Stratégie de Découplage
Pour éliminer ces couplages et améliorer la rapidité, on utilise une compensation feedforward :

a. Injection de termes opposés
On ajoute aux tensions de commande 
v d  et vq
les termes perturbateurs, mais de signe opposé :

{vd∗=vd+ωLqiqvq∗=vq−ωLdid
Résultat :

Les équations deviennent linéaires et découplées :

{
vd∗=Rid+Lddiddtvq∗=Riq+qdiqdt+ωψf{ v d∗ =Ri d +L d​  dtdi d
v q∗​ =Ri q​ +L q​  dtdi q​ ​ +ωψ f
​
On peut maintenant régler id et iq indépendamment, comme deux systèmes du 1er ordre.

b. Gain en Rapidité
Sans découplage :
La dynamique est ralentie par les interactions entre axes (il faut attendre que les transitoires se stabilisent).

Avec découplage :
Les constantes de temps résiduelles sont uniquement 
Ld/R et Lq/R → Réponse plus rapide.

3. Pourquoi la MCC n'a pas ce problème ?
En MCC, le couple est directement proportionnel au courant d'induit 
T=K⋅I :

Pas de décomposition en axes d-q.

Pas de termes de couplage liés à ωω.

La seule limitation de rapidité vient de l'inertie mécanique (déjà discutée).

→ Le système est naturellement découplé et linéaire en courant/tension.

4. Analogie avec l'Automatique
MCC : Système SISO (Single Input Single Output) → Un PID suffit.

MS : Système MIMO (Multi Input Multi Output) couplé → Nécessite un découplage pour :

Transformer le système en deux boucles indépendantes (d et q).

Appliquer des correcteurs plus agressifs (car plus de marges de stabilité).

5. Exemple Pratique : Commande Vectorielle
Dans une MS, le découplage permet :

Contrôler 
id=0 ;id=0 (pour minimiser les pertes).

Piloter le couple via 
iqiq avec une dynamique rapide.
→ La performance est comparable à celle d'une MCC, malgré la complexité supérieure de la MS.

Conclusion
Le découplage sert bien à :

Linéariser le système (supprimer les interactions d-q).

Accélérer la réponse (en réduisant les retards induits par les couplages).

C'est la clé pour obtenir des performances équivalentes à une MCC dans des machines plus complexes (MS, asynchrones).
