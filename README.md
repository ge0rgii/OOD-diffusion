# OOD-diffusion

Niniejszy projekt poświęcony jest badaniu eksperymentalnych metod estymacji logarytmu gęstości prawdopodobieństwa danych (log g(x)) oraz związanej z nim funkcji score (∇ log g(x)) przy użyciu sieci neuronowych, w szczególności w kontekście modeli dyfuzyjnych. Analizowane są dwa główne podejścia: ”Metoda 1 - Dystylacja”, gdzie gradient wyjścia uczonej sieci U-Net
stara się aproksymować wyjście zamrożonej, wytrenowanej sieci
U-Net, oraz ”Metoda 2 - Bezpośrednie przyspieszone uczenie”, gdzie uczona jest sieć ht, będąca kopią architektury oryginalnego U-Netu z ”Metody 1”, z niewielką skalarną głowicą konwolucyjną dodaną do sieci zamiast
warstw Up-Blocks, w celu przyspieszenia procesu uczenia, tak aby gradient
dla tak określonego wyjścia bezpośrednio aproksymował szum w standardowej funkcji kosztu modelu dyfuzyjnego. Przeprowadzono eksperymenty na
zbiorze danych CIFAR-10, porównując uzyskane proxy dla logarytmu gęstości z innymi modelami generatywnymi, takimi jak Normalizujące Przepływy
(Glow) oraz Modele Oparte O Energię (EBM), oraz z podejściem opartym na
analizie odpowiedzi oryginalnej sieci U-Net na dane wejściowe z dodanym
niewielkim szumem. Oceniano zdolność metod do detekcji próbek spoza rozkładu (OOD) oraz korelację oszacowań gęstości. Wstępne wyniki, w tym
niska korelacja metryki V0 z Metody 1 z modelami Glow oraz EBM, oraz
wysoka wartość funkcji kosztu w etapach uczenia Metody 2, wskazują na
złożoność zadania i sugerują obszary dla dalszych badań nad stabilnością
i efektywnością proponowanych metod. Duża korelacja wyjścia wytrenowanego modelu z ”Metody 1” do metryki wykorzystującej wyjscie oryginalnego
U-Netu po dodaniu niewielkiej ilości szumu również wymaga głębszej analizy oraz teoretycznego uzasadnienia.
