# Transformée de Laplace inverse

## Introduction

La résolution d'équations différentielles linéaires peut s'effectuer en s'aidant de la transformée de Laplace. Via cette méthode, on accède dans un premier temps à la transformée de Laplace de la solution, qui se présente pour l'essentiel sous la forme d'une fraction rationnelle d'une variable complexe $p$.

Pour revenir à l'expression temporelle de la solution, il faut procéder à la **décomposition en éléments simples** de la fraction rationnelle en $p$ (degré du numérateur strictement inférieur à celui du dénominateur), de sorte qu'apparaissent des termes élémentaires de la forme $\dfrac{K}{(p-a)^n}$ (dans le corps des complexes) pour lesquels l'expression temporelle associée $K\dfrac{t^{n-1}e^{at}\theta(t)}{(n-1)!}$ est connue.

L'idée ici est d'illustrer les méthodes de calcul via le package **sympy** de calcul symbolique. Mais il reste préférable de pouvoir **mener ces calculs avec un crayon et un papier**.

La validation s'effectuera avec la fonction **impulse** du package **scipy.signal**.

## Méthodes de calcul

### Introduction

Pour les deux méthodes présentées ci-dessous, la transformée de Laplace se présente sous la forme d'une fraction rationnelle dont on connaît les pôles et les zéros, ainsi que leur ordre de multiplicité.

La **méthode 1** réalise les calculs de façon littérale, et les applications numériques s'effectuent a posteriori. Cependant, la "lourdeur" des expressions littérales dans les calculs finit par ne plus donner de résultats cohérents pour des degrés du dénominateur trop élevés.

La **méthode 2** réalise les calculs de façon numérique, avec l'apparition parfois de monômes à coefficient non nul dans le polynôme $R(y)$ alors qu'ils devraient l'être lors de la division de polynôme, à cause des erreurs arithmétiques en cours de calcul. Malgré ces erreurs desquels résultent des coefficients néanmoins très faibles au lieu d'être nuls, la méthode réalise correctement la décomposition quel que soit le degré du dénominateur.

En conclusion, cette seconde méthode fonctionne toujours correctement, dans des conditions qui, en revanche, aboutissent parfois à de mauvais résultats avec les méthodes **apart** ou **inverse_laplace_transform** de **sympy**.

### Méthode 1

* Cas d'un pôle $p_0$ simple

$$F(p)=\dfrac{P(p)}{Q(p)}=\dfrac{P(p)}{B(p)(p-p_0)}=K(p)+\dfrac{a_1}{(p-p_0)}$$

$$a_1=\dfrac{P(p_0)}{B(p_0)}=F(p)(p-p_0)|_{p=p_0}$$

* Cas d'un pôle $p_0$ d'ordre de multiplicité N supérieur à 1

Première étape pour récupérer le terme de plus haut degré :

$$F(p)=\dfrac{P(p)}{Q(p)}=\dfrac{P(p)}{B(p)(p-p_0)^N}=K(p)+\Sigma_{n=1}^N\dfrac{a_n}{(p-p_0)^n}$$

$$a_N=\dfrac{P(p_0)}{B(p_0)}=F(p)(p-p_0)^N|_{p=p_0}$$

Par récurrence sur N étapes incluant la première étape :

---

Initialisation

$$F_n(p)=F(p)$$

---

Pour $n$ variant de $N$ à $1$ :

$$a_n=F_n(p)(p-p_0)^n|_{p=p_0}$$

$$F_n(p)=F_n(p)-\dfrac{a_n}{(p-p_0)^n}$$

### Méthode 2

Voir la page Wikipédia [Décomposition en éléments simples](https://fr.wikipedia.org/wiki/D%C3%A9composition_en_%C3%A9l%C3%A9ments_simples#%C3%89l%C3%A9ments_simples_associ%C3%A9s_%C3%A0_un_p%C3%B4le_multiple) à la rubrique **Éléments simples associés à un pôle multiple**.

## Les Notebooks

### Méthode 1

[Version sur ce dépôt](tlinv_m1.ipynb)

[Version sur Google Colab](https://colab.research.google.com/drive/12iWWqLLKzbYbD0LhHG_JLTZ3FZqfgqiy?usp=drive_link)

### Méthode 2

[Version sur ce dépôt](tlinv_m2.ipynb)

[Version sur Google Colab](https://colab.research.google.com/drive/1PDHuEOMK2lnMBFB8r_vEqeuznw5TgrCv?usp=drive_link)


