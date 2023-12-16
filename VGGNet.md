# VGGNet16
<p align="justify"> VGG16 se refera la modelul VGG, numit si VGGNet. Este un model de retea neurala convolutionala (CNN) cu suport pentru 16 straturi. Modelul VGG16 poate atinge o precizie de testare de 92,7% in ImageNet, un set de date care contine peste 14 milioane de imagini de antrenament din 1000 de clase de obiecte. Este unul dintre modelele de top din competitia ILSVRC-2014.
VGG16 aduce imbunatatiri fata de AlexNet si inlocuieste filtrele mari cu secvente de filtre mai mici de 3×3. In AlexNet, dimensiunea kernelului este de 11 pentru primul strat convoluzional si 5 pentru al doilea strat. Cercetatorii au antrenat modelul VGG timp de cateva saptamani folosind unitati de procesare grafica (GPU) NVIDIA Titan Black.


# Motivatia din spatele modelului VGG :

<p align="justify">Acest model e diferit de modelele performante anterioare in mai multe moduri. In primul rand, a folosit un mic camp receptiv de 3x3 cu o defazare de 1 pixel - pentru comparatie, AlexNet a folosit un camp receptiv 
de 11x11 cu o defazare de 4 pixeli. Filtrele de 3x3 se combina pentru a oferi functia unui camp receptiv mai mare.

<p align="justify">Ca si **beneficii de utilizare ** avem utilizarea unor straturi mai mici in locul unui singur strat mare, mia multe straturi active non-liniarea insotesc straturi de convolutie imbunatating functiile de decizie si permitand retelei sa converga mai repede.
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


- Input— VGGNet primeste o intrare de imagine de 224×224 pixeli. In competitia ImageNet, creatorii modelului au mentinut dimensiunea constanta a imaginii prin decuparea unei sectiuni de 224×224 de la centrul fiecarei imagini.

Convolutional layers—the convolutional filters of VGG use the smallest possible receptive field of 3×3. VGG also uses a 1×1 convolution filter as the input’s linear transformation. 

ReLu activation—next is the Rectified Linear Unit Activation Function (ReLU) component, AlexNet’s major innovation for reducing training time. ReLU is a linear function that provides a matching output for positive inputs and outputs zero for negative inputs. VGG has a set convolution stride of 1 pixel to preserve the spatial resolution after convolution (the stride value reflects how many pixels the filter “moves” to cover the entire space of the image).

Hidden layers—all the VGG network’s hidden layers use ReLU instead of Local Response Normalization like AlexNet. The latter increases training time and memory consumption with little improvement to overall accuracy.

Pooling layers–A pooling layer follows several convolutional layers—this helps reduce the dimensionality and the number of parameters of the feature maps created by each convolution step. Pooling is crucial given the rapid growth of the number of available filters from 64 to 128, 256, and eventually 512 in the final layers.

Fully connected layers—VGGNet includes three fully connected layers. The first two layers each have 4096 channels, and the third layer has 1000 channels, one for every class.
