# VGGNet16
<p align="justify"> VGG16 se refera la modelul VGG, numit si VGGNet. Este un model de retea neurala convolutionala (CNN) cu suport pentru 16 straturi. Modelul VGG16 poate atinge o precizie de testare de 92,7% in ImageNet, un set de date care contine peste 14 milioane de imagini de antrenament din 1000 de clase de obiecte. Este unul dintre modelele de top din competitia ILSVRC-2014.
VGG16 aduce imbunatatiri fata de AlexNet si inlocuieste filtrele mari cu secvente de filtre mai mici de 3×3. In AlexNet, dimensiunea kernelului este de 11 pentru primul strat convoluzional si 5 pentru al doilea strat. Cercetatorii au antrenat modelul VGG timp de cateva saptamani folosind unitati de procesare grafica (GPU) NVIDIA Titan Black.


# Motivatia din spatele modelului VGG :

<p align="justify">Acest model e diferit de modelele performante anterioare in mai multe moduri. In primul rand, a folosit un mic camp receptiv de 3x3 cu o defazare de 1 pixel - pentru comparatie, AlexNet a folosit un camp receptiv 
de 11x11 cu o defazare de 4 pixeli. Filtrele de 3x3 se combina pentru a oferi functia unui camp receptiv mai mare.

<p align="justify">Ca si beneficii de utilizare avem utilizarea unor straturi mai mici in locul unui singur strat mare, mia multe straturi active non-liniarea insotesc straturi de convolutie imbunatating functiile de decizie si permitand retelei sa converga mai repede.
Un alt beneficiu ar fi acela ca VGG foloseste un filtru de convolutie mai mic ceea ce reduce tendinta retelei de a face overfitting in timpul exercitiilor de antrenament. Un filtru de **3x3** este de dimensiune optima deoarece o dimensiune mai mica nu poate captura informatii de la stanga la dreapta si de sus in jos. Astfel, VGG este cel mai mic model posibil pentru a intelege caracteristicile spatiale ale unei imagini.
Convolutiile constante de 3x3 fac reteaua usor de gestionat.



# Arhitectura VGG16 :

<p align="justify">VGG16 este o retea neurala adanca cu 16 straturi avand un total de 138 milioane de parametri. Cu toate acestea, simplitatea arhitecturii VGGNet16 reprezinta principala sa atractie.
Arhitectura VGGNet integreaza cele mai importante caracteristici ale retelelor neurale de convolutie.

<div align="center">
    <img height="350" width="400" src="https://github.com/mirceazco/VerificareFormala-2023/blob/main/LaTeX/vggnet.png.png">
</div>


O retea VGG consta in filtre de convolutie mici. VGG16 are trei straturi complet conectate si 13 straturi de convolutie.
Scurta prezentare a arhitecturii:


- <strong> Input </strong> — VGGNet primeste o intrare de imagine de 224×224 pixeli. In competitia ImageNet, creatorii modelului au mentinut dimensiunea constanta a imaginii prin decuparea unei sectiuni de 224×224 de la centrul fiecarei imagini.

- <strong> Straturi de convolutie </strong> - filtrele de convolutie ale VGG folosesc campul receptiv cel mai mic posibil de 3x3. VGG utilizeaza, de asemenea, un filtru de convolutie de 1x1 pentru transformarea liniara a intrarii. 

- <strong> ReLu activation </strong> — urmeaza componenta Functiei de Activare Liniara Rectificata (ReLU), o inovatie majora a lui AlexNet pentru reducerea timpului de antrenament. ReLU este o functie liniara care 
furnizeaza o iesire potrivita pentru intrarile pozitive si furnizeaza zero pentru intrarile negative. VGG are o valoare de pas a convolutiei setata la 1 pixel pentru a pastra rezolutia spatiala dupa convolutie.

- <strong> Hidden Layers </strong> - toate straturile ascunse ale retelei VGG folosesc ReLU in loc de Normalizarea Locala a Raspunsului, asa cum se intampla in AlexNet. Aceasta din urma creste timpul de antrenament si consumul de memorie cu o imbunatatire redusa a preciziei generale.

- <strong> Pooling layers </strong> – un strat de pooling urmeaza mai multe straturi de convolutie, ajutand la reducerea dimensionalitatii si a numarului de parametri ai hartilor de caracteristici create de fiecare pas de convolutie. Pooling-ul este crucial data fiind cresterea rapida a numarului de filtre disponibile de la 64 la 128, 256 si in cele din urma 512 in straturile finale.

- <strong> Fully connected layers </strong> — VGGNet include trei straturi complet conectate. Primele doua straturi au fiecare 4096 de canale, iar al treilea strat are 1000 de canale, unul pentru fiecare clasa.


# VGG Configuration, Training, and Results



