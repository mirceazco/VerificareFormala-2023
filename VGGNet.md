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

Exista cinci configuratii ale retelei VGG, de la A la E. Adancimea configuratiei creste de la A la B, fiecare cu mai multe straturi adaugate. Tabelul urmator descrie toate arhitecturile posibile ale retelei.

<div align="center">
    <img height="350" width="400" src="https://github.com/mirceazco/VerificareFormala-2023/blob/main/LaTeX/config.png">
</div>

Fiecare configuratie urmeaza un model arhitectural comun, diferind doar in adancime. Reteaua A are 11 straturi de greutate (8 straturi de convolutie si 3 straturi complet conectate), in timp ce reteaua E are 19 straturi de greutate (16 straturi de convolutie si 3 straturi complet conectate).

Exista cateva canale de straturi de convolutie - numarul variaza de la 64 de canale in primul strat la 512 in ultimul strat (creste cu un factor de doi pentru fiecare strat de max-pooling). 

In figura de mai jos putem vedea numarul total de parametri in milioane.

<div align="center">
    <img height="77" width="724" src="https://github.com/mirceazco/VerificareFormala-2023/blob/main/LaTeX/parameters.png">
</div>

<p align="justify">Procesul de antrenare al VGG este similar cu cel al lui AlexNet (Krizhevsky et al.). Ambele implica optimizarea unei functii de regresie logistica multinomiala pentru a realiza backpropagation. VGG utilizeaza mini-loturi pentru a evita gradientul care dispare, fenomen generat de adancimea rețelei.
In timpul antrenamentului, dimensiunea lotului a fost setata la 256, in timp ce momentum a fost setat la 0,9. Modelul VGG a introdus regularizarea dropout in doua dintre straturile complet conectate, cu o rata dropout setata la 0,5. Rata de invatare initiala a retelei a fost de 0,001. Cand acuratetea setului de validare a incetat sa se imbunatateasca, rata de invatare a scazut cu un factor de 10. Rata de invatare a scazut de trei ori, iar antrenamentul s-a incheiat dupa 74 de epoci (370.000 de iteratii).

Arhitectura VGG16 a obtinut cele mai bune rezultate in ceea ce priveste performanta retelei unice (eroare de testare de 7,0%). Tabelul de mai jos prezinta ratele de eroare.

<div align="center">
    <img height="92" width="726" src="https://github.com/mirceazco/VerificareFormala-2023/blob/main/LaTeX/rates.png">
</div>

Arhitecturile moderne folosesc conexiuni de salt si inceptii pentru a reduce numarul de parametri de antrenare, imbunatatind atat precizia, cat si timpul de antrenare.


# Training :

<p align="justify">  - <strong> Metoda de optimizare </strong> este o coborare a gradientului stocastica (SGD) + momentum (0,9) cu momentum. Dimensiunea lotului este de 256.

- <strong> Regularizare: </strong> Se utilizeaza regularizarea L2, iar descompunerea ponderilor este de 5e-4. Dropout se aplica dupa primele doua straturi complet conectate, p = 0,5.

 - Desi este mai profund si are mai multi parametri decat reteaua AlexNet, speculăm ca VGGNet poate converge in mai putine cicluri din doua motive: in primul rand, adancimea mai mare si convolutiile mai mici aduc o regularizare implicita; in al doilea rand, unele straturi de pre-antrenament.




