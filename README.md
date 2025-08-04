# OOD-diffusion <!-- project title shown as big header -->

## Opis projektu
Niniejszy projekt poświęcony jest **badaniu eksperymentalnych metod estymacji logarytmu gęstości prawdopodobieństwa danych** `log g(x)` oraz związanej z nim funkcji score `∇ log g(x)` przy użyciu sieci neuronowych, w szczególności w kontekście **modeli dyfuzyjnych**.

Analizowane są dwa główne podejścia:

| Metoda | Krótki opis |
| ------ | ----------- |
| **Metoda 1 – Dystylacja** | Gradient wyjścia uczonej sieci **U-Net** stara się aproksymować wyjście zamrożonej, wytrenowanej sieci U-Net. |
| **Metoda 2 – Bezpośrednie przyspieszone uczenie** | Uczona jest sieć `h_t`, będąca kopią architektury oryginalnego U-Netu z Metody 1, z niewielką skalarną głowicą konwolucyjną dodaną zamiast warstw *Up-Blocks*, aby przyspieszyć proces uczenia, tak by gradient bezpośrednio aproksymował szum w standardowej funkcji kosztu modelu dyfuzyjnego. |

> **Zbiór danych:** wszystkie eksperymenty przeprowadzono na **CIFAR-10**.

## Eksperymenty i wyniki
* Porównano uzyskane proxy dla `log g(x)` z innymi modelami generatywnymi, takimi jak **Normalizujące Przepływy (Glow)** oraz **Modele Oparte o Energię (EBM)**, a także z podejściem analizującym odpowiedź oryginalnego U-Netu na dane wejściowe z dodanym niewielkim szumem.  
* Oceniano zdolność metod do **detekcji próbek spoza rozkładu (OOD)** oraz korelację oszacowań gęstości.

### Kluczowe obserwacje
* **Niska korelacja** metryki *V0* z Metody 1 z modelami Glow oraz EBM.  
* **Wysoka wartość funkcji kosztu** w etapach uczenia Metody 2 wskazuje na złożoność zadania i obszary do dalszych badań nad stabilnością i efektywnością.  
* **Duża korelacja** wyjścia wytrenowanego modelu z Metody 1 do metryki opartej na odpowiedzi oryginalnego U-Netu po dodaniu szumu wymaga głębszej analizy i teoretycznego uzasadnienia.

