# VGGNet16
<p align="justify"> VGG16 se refera la modelul VGG, numit si VGGNet. Este un model de retea neurala convolutionala (CNN) cu suport pentru 16 straturi. Modelul VGG16 poate atinge o precizie de testare de 92,7% in ImageNet, un set de date care contine peste 14 milioane de imagini de antrenament din 1000 de clase de obiecte. Este unul dintre modelele de top din competitia ILSVRC-2014.
VGG16 aduce imbunatatiri fata de AlexNet si inlocuieste filtrele mari cu secvente de filtre mai mici de 3×3. In AlexNet, dimensiunea kernelului este de 11 pentru primul strat convoluzional si 5 pentru al doilea strat. Cercetatorii au antrenat modelul VGG timp de cateva saptamani folosind unitati de procesare grafica (GPU) NVIDIA Titan Black.


# Motivatia din spatele modelului VGG :

Acest model e diferit de modelele performante anterioare in mai multe moduri. In primul rand, a folosit un mic camp receptiv de 3x3 cu o defazare de 1 pixel - pentru comparatie, AlexNet a folosit un camp receptiv 
de 11x11 cu o defazare de 4 pixeli. Filtrele de 3x3 se combina pentru a oferi functia unui camp receptiv mai mare.

Ca si **beneficii de utilizare** avem utilizarea unor straturi mai mici in locul unui singur strat mare, mia multe straturi active non-liniarea insotesc straturi de convolutie imbunatating functiile de decizie si permitand retelei sa converga mai repede.
Un alt beneficiu ar fi acela ca VGG foloseste un filtru de convolutie mai mic ceea ce reduce tendinta retelei de a face overfitting in timpul exercitiilor de antrenament. Un filtru de **3x3** este de dimensiune optima deoarece o dimensiune mai mica nu poate captura informatii de la stanga la dreapta si de sus in jos. Astfel, VGG este cel mai mic model posibil pentru a intelege caracteristicile spatiale ale unei imagini.
Convolutiile constante de 3x3 fac reteaua usor de gestionat.



# Arhitectura VGG16 :
