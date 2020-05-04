---
date: 2020-05-02
title: "Lancement de Sandpiper Framework"
linkTitle: "Annonce de Sandpiper"
description: "Une nouvelle façon efficace d'échanger les données des produits et des applications de soins automatiques."
author: "The Sandpiper Authors"
resources:
- src: "compliance-levels.png"
  title: "Sandpiper Compliance Levels"
---

### Motivation

À la même époque l'année dernière, lors de son discours d'ouverture pour l'ACPN 2019, [Jason Riegel](https://www.linkedin.com/in/jasonriegel/) a mis notre industrie au défi de faire mieux.

Jason a comparé l'environnement de livraison de contenu d'aujourd'hui à une époque juste avant l'arrivée du télégraphe pour la livraison de messages transnationaux dans les années 1800.

{{% alert %}}
*"notre industrie est coincée quelque part entre le coach de scène et le pony express"* -- Jason Riegel
{{% /alert %}}

De toute évidence, nous ne voulons pas être l'équivalent d'aujourd'hui du pony express! Nous avons besoin d'une technologie "perturbatrice" dont l'impact est similaire au télégraphe.

Il a conclu sa présentation par une vision pour un "**marché secondaire connecté**":

{{% alert %}}
"We need... **REAL TIME**, seamless access to **CLEAN, MEANINGFUL CODED CONTENT**, tied to **INDUSTRY STANDARDS** designed to **ENABLE INSTANTANEOUS CONNECTIVITY** between supplier and the point of sale."
{{% /alert %}}

Sur ce défi, une graine a été plantée. Il devait y avoir un meilleur moyen d'échanger des données produit que de fournir des fichiers de données complets chaque mois!

### Le Moment de l'Ampoule {{< icon >}} 

Et si nous pouvions utiliser un identifiant unique pour identifier chaque application ... cela aiderait, n'est-ce pas? Oui, mais cela ne pouvait pas garantir que nous disposions toujours d'un "ensemble complet" d'informations. Si vous supprimez un identifiant, cela signifie-t-il que vous devez le remplacer par autre chose? Comment savoir si nous avons manqué une mise à jour?

Chaque système de «changement net» que nous avons trouvé (où les ajouts étaient associés à des suppressions) était intrinsèquement fragile. Nous devions rendre cela pare-balles. Comment garantir que les partenaires commerciaux restent toujours synchronisés sans échanger des fichiers complets, ne serait-ce que de temps en temps?

{{% alert %}}
**The answer turned out to be very simple.** It comes down to the basic idea of managing a set of syncable objects. If your set matches my set, then we are in sync. 
{{% /alert %}}

Une fois qu'un objet se voit attribuer un ID unique et placé dans un ensemble, il ne peut plus être modifié. Il peut être supprimé, mais jamais modifié.

Alors maintenant, peu nous importe ce que nous livrons, tant que nous pouvons l'identifier de manière unique! Cela signifie que nous pouvons gérer ACES, PIES, PartsPRO, TecDoc ... pratiquement *tout* ce qui peut être identifié et livré séparément.

Ce concept simple est la base de Sandpiper.

### Livraison en Temps Réel

Maintenant, nous **avions la formule** pour un mécanisme de livraison fiable. Les ingénieurs du groupe sont immédiatement passés à la "phase de dessin des serviettes".

Il est devenu clair dès le départ que nous n'avions pas besoin d'une conception centrale à moyeu et à rayons. Tout comme avec le [Web] (https://en.wikipedia.org/wiki/World_Wide_Web), nous n'avions besoin que de deux machines pour dialoguer. Si vous étiez un fournisseur, par exemple, vous mettriez en place un "abonnement" avec chacun de vos partenaires commerciaux (par exemple détaillants, ecats, WD, etc.), en supposant, bien sûr, qu'ils avaient également une machine qui comprenait la formule.

Chaque fois qu'un changement était apporté à vos données, il avertissait tout le monde abonné à ces données et exécutait une petite danse (une «synchronisation») pour s'assurer que vos informations étaient à jour.

Alors que le dessin des serviettes était impressionnant, nous avons réalisé qu'il s'agissait d'un saut assez massif par rapport à notre situation actuelle. Bien que la livraison en temps quasi réel reste l'objectif ultime, il était clair que nous devions marcher avant de courir.

### Compliance Levels & Adoption

Comme tout le monde dans notre industrie le sait, l'un des plus grands défis avec les normes de données a toujours été l'adoption. Si un client ne l'exigeait pas, cela n'était tout simplement pas considéré comme une priorité. Autant nous nous attendons à ce que les bonnes idées soient comme le film *Field of Dreams*, "si vous le construisez, elles viendront", cela ne fonctionne presque jamais de cette façon.

Nous savions que nous avions besoin d'un système super simple avec des avantages immédiats, zéro interruption et un gain de temps par rapport aux processus existants. Nous avons donc eu l'idée des «niveaux de conformité» de Sandpiper:

* **Niveau 0.** Non-compliance. Maintain the current state of data exchange.
* **Niveau 1.** Continue to exchange full-files, but automate the process.
* **Niveau 2.** Exchange smaller "grains" of information, but make them logically complete such as "pies-item" (all PIES segments for an Item) or "aces-part" (all ACES applications for a part number).
* **Niveau 3.** Near real-time delivery of atomic grains. The Holy Grail.

Voici une visualisation des trois premiers niveaux de conformité:

{{< imgproc compliance Resize "400x" />}}

La valeur réelle du **Niveau 1** est de regrouper les nombreuses exigences de livraison de l'industrie en une seule (y compris les formulaires de soumission de documents, etc.). Cela signifie que vous publieriez un fichier une seule fois, confiant qu'il serait livré à tous vos partenaires commerciaux qui l'ont demandé.

### L'état du Projet

Nous avons fait de grands progrès au cours des derniers mois, mais nous ne faisons que commencer. Nous avons résolu de nombreux problèmes difficiles (comme la version de référence et la synchronisation des données), mais nous avons encore beaucoup à faire.

Il s'agit d'un **effort purement bénévole**, avec plusieurs centaines d'heures déjà consacrées. Plusieurs entreprises ont gracieusement autorisé à consacrer des ressources à ce projet pendant les heures de travail, mais nous avons besoin de votre aide. Nous avons besoin de développeurs, de testeurs, d'écrivains, de traducteurs ... Si vous voyez un besoin, n'hésitez pas à le combler!

Veuillez vous joindre à notre [liste de diffusion](https://mailchi.mp/172fd6548eee/sandpiper). Cet acte simple montre à l'industrie que vous comprenez l'importance de cette nouvelle direction passionnante de la diffusion de contenu. Consultez également notre [Feuille de route](/blog/roadmap) pour voir ce que nous avons prévu.

{{< imgproc mascot Resize "x80" />}}
