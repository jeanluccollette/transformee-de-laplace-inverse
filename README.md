# Transformée de Laplace inverse

## Introduction

La résolution d'équations différentielles linéaires peut s'effectuer en s'aidant de la transformée de Laplace. Via cette méthode, on accède dans un premier temps à la transformée de Laplace de la solution, qui se présente pour l'essentiel sous la forme d'une fraction rationnelle d'une variable complexe $p$.

Pour revenir à l'expression temporelle de la solution, il faut procéder à la **décomposition en éléments simples** de la fraction rationnelle en $p$, de sorte qu'apparaissent des termes élémentaires de la forme $\dfrac{K}{(p-a)^n}$ (dans le corps des complexes) pour lesquels l'expression temporelle associée $K\dfrac{t^{n-1}e^{at}\theta(t)}{(n-1)!}$ est connue.

L'idée ici est d'illustrer les méthodes de calcul via le package **sympy** de calcul symbolique. Mais il reste préférable de pouvoir **mener ces calculs avec un crayon et un papier**.

La validation s'effectuera avec la fonction **impulse** du package **scipy.signal**.

## Méthodes de calcul

### Méthode 1

* Cas d'un pôle $p_0$ simple

$$F(p)=\dfrac{P(p)}{Q(p)}=\dfrac{P(p)}{B(p)(p-p_0)}=K(p)+\dfrac{a_1}{(p-p_0)}$$

$$a_1=\dfrac{P(p_0)}{B(p_0)}=F(p)(p-p_0)|_{p=p_0}$$

* Cas d'un pôle $p_0$ d'ordre de multiplicité N supérieur à 1

Première étape pour récupérer le terme de plus haut degré :

$$F(p)=\dfrac{P(p)}{Q(p)}=\dfrac{P(p)}{B(p)(p-p_0)^N}=K(p)+\Sigma_{n=1}^N\dfrac{a_n}{(p-p_0)^n}$$

$$a_N=\dfrac{P(p_0)}{B(p_0)}=F(p)(p-p_0)^N|_{p=p_0}$$

Par récurrence sur N étapes incluant la première étape :

    Initialisation

$$F_n(p)=F(p)$$

    Pour $n$ variant de $N$ à $1$ :

$$a_n=F_n(p)(p-p_0)^n|_{p=p_0}$$

$$F_n(p)=F_n(p)-\dfrac{a_n}{(p-p_0)^n}$$

## Le Notebook

[Version sur ce dépôt](transformee-de-laplace-inverse.ipynb)

[Version sur Google Colab](https://colab.research.google.com/drive/1QFP2hEKg-0lrkFroXCtD9xHtFhaUhLSr?usp=sharing)


