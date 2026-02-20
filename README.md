# Transformée de Laplace inverse

## Introduction

La résolution d'équations différentielles linéaires peut s'effectuer en s'aidant de la transformée de Laplace. Via cette méthode, on accède dans un premier temps à la transformée de Laplace de la solution, qui se présente pour l'essentiel sous la forme d'une fraction rationnelle d'une variable complexe $p$.

Pour revenir à l'expression temporelle de la solution, il faut procéder à la **décomposition en éléments simples** de la fraction rationnelle en $p$ (degré du numérateur strictement inférieur à celui du dénominateur), de sorte qu'apparaissent des termes élémentaires de la forme $\dfrac{K}{(p-a)^n}$ (dans le corps des complexes) pour lesquels l'expression temporelle associée $K\dfrac{t^{n-1}e^{at}\theta(t)}{(n-1)!}$ est connue.

L'idée ici est d'illustrer les méthodes de calcul via le package **sympy** de calcul symbolique. Mais il reste préférable de pouvoir **mener ces calculs avec un crayon et un papier**.

La validation s'effectuera avec la fonction **impulse** du package **scipy.signal**.

## Méthode de calcul

Voir la page Wikipédia [Décomposition en éléments simples](https://fr.wikipedia.org/wiki/D%C3%A9composition_en_%C3%A9l%C3%A9ments_simples#%C3%89l%C3%A9ments_simples_associ%C3%A9s_%C3%A0_un_p%C3%B4le_multiple) à la rubrique **Éléments simples associés à un pôle multiple**.

La méthode réalise les calculs de façon numérique, avec l'apparition parfois de monômes à coefficient non nul dans le polynôme $R(y)$ alors qu'ils devraient l'être lors de la division de polynôme, à cause des erreurs arithmétiques en cours de calcul. Malgré ces erreurs desquels résultent des coefficients néanmoins très faibles au lieu d'être nuls, la méthode réalise correctement la décomposition quel que soit le degré du dénominateur.

En conclusion, cette seconde méthode fonctionne toujours correctement, dans des conditions qui, en revanche, aboutissent parfois à de mauvais résultats avec les méthodes **apart** ou **inverse_laplace_transform** de **sympy**.

## Le Notebook

[Version sur ce dépôt](tlinv.ipynb)

[Version sur Google Colab](https://colab.research.google.com/drive/1tRv40an9F6WMwOGtceiDpGqu-Jiq6ATj?usp=drive_link)

