---
published: true
title: Organizing my first ML project
collection: ml
layout: single
author_profile: true
read_time: true
categories: [machinelearning]
excerpt : "Writing"
header :
    #overlay_image: "https://maelfabien.github.io/assets/images/wolf.jpg"
    #teaser : "https://maelfabien.github.io/assets/images/wolf.jpg"
comments : true
toc: true
toc_sticky: true
sidebar:
    nav: sidebar-sample
---

<!--src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script> -->

Here are some words about how I wrote and organized my first project.

# I. Context

Completing my data science bootcamp, I wanted to realize a great interesting project allowing me to develop new skills and deeply apply the majort part of what I learned. And, for me, what could be better than Deep Learning ? Based on my knowledge on some possible machine learning applications around us, in my project I wanted to analyze video streaming in order to detect and predict emotions. It could be interesting for many applications like security cameras, job interviews, improving the quality of customer service...

Because emotions may be expressed on faces and via voice tones, a priori, this can be done by simultaneously processing video streaming, audio and (transcripted) text. I was wondering if this sort of project could be achieved in the time we had (less than a month). Basically, I have a good scientific backgroung, and I can quickly learn a lot of things. But, I didn't know if it was enough since I never managed this kind of project, in addition it was not my main scientific topic (so, many things to learn from scratch).

I was even wondering where to find data to feed to my machine learning algorithms, and how to train them ? I meant what kind of models could be applied in order to have great performances. In addition, could I locally train my models ? or I must use cloud infrastructures and online notebooks and frameworks ? Another point was to getting started and to learn the main concepts to master and manage my project. On of my supervisor suggests to me to simply start with audio and text processing since it might be quite tricky with the three channels.


# Hier c’est un peu le projet idéal que j’avais en tête pour les étudiants de Vivadata et je demande la parole, du traitement du texte, et créer une application Web, ou déployer le tout avec une API et que ça mélange énormément de concepts. Départ, je te conseille de regarder toutes les librairies de HuggingFace qui mettent à disposition de nombreux modèles prés-entrainés, aussi bien en NLP qu’en traitement de la parole et de nombreux notebook qui te permettent de fine-tuner beaucoup d’algorithmes sur des données complémentaires. Si tu souhaites travailler sur des langages avec peu de ressources (hors anglais, français, allemand, espagnol...), c’est aussi totalement faisable! Et HuggingFace organise un challenge cette semaine pour créer les meilleures modèles de traitement de la parole sur Colab, dans 60 langages. Si tu peux y participer, ça serait génial! Et tu peux déployer ton modèle sur HuggingFace à la fin, et le rendre accessible à tous.

#Bonjour Maël,
#J’espère que ton week-end se passe bien
#Merci pour ton retour et ton orientation
#J’ai commencé à regarder des trucs sur HuggingFace, et je suis tombé essentiellement sur le concept de Transformers où il y a pas mal de modèles pré-entraînés...
#Il s’agit essentiellement pour l’instant de traitements textuels, une sorte d’état de l’art, je ne suis encore pas tombé sur du traitement audio.
#J’aimerais savoir comment trouver les autres librairies de HuggingFace

#Salut Maël,
#J’espère que ton week-end s’est bien passé
#J’ai commencé à créer mon bloghttps://will007-max.github.io
#La prise en main de l’outil n’est pas toujours évidente
#J’ai regardé quelques transformers qui travaillent sur du texte, et comme tu me l’avais fait remarqué ce sont essentiellement de modèles pré-entrainés qu’il faut fine-tuner en accord avec le problème et les données à disposition
#J’ai également regardé quelques preprocessings sur le traitement audio
#Je n’ai pas encore testé de modèle car tout n’est pas encore claire dans ma tête

#Salut William, top pour ton blog, c'est cool!

#Salut Maël,
#Concernant la reconnaissances des émotions dans l’audio et le texte, comment approcher le truc ? L’idée serait-t-elle de partir sur deux canaux au choix (dès le début, l’utilisateur choisit soit l’audio soit le texte), ou bien il faudra à l’avance transcrire l’audio en texte, et entraîner chaque canal (audio, texte) pour à la suite faire une sorte de moyenne des prédictions ?

#Je te conseille de l'aborder de la 2ème manière. Tu fais la transcription vocale, et tu fais une "fusion" des scores de tes prédictions
#Si tu regardes sur mon github, j'ai un projet un peu similaire
#C'est vieux, mais c'est une piste de départ


#Bonjour Maël,
#J’espère que ta semaine s’est bien passée.
#Je suis en train de compléter au fur et à mesure mon blog, en fonction de mon niveau actuel de compréhension. Concernant le fonctionnement de l’outil, please j’aimerais avoir des astuces sur comment publier les articles. Je sais que ce sont des fichiers HTML ou MD, seulement je ne sais dans quel dossier ranger mes futurs articles, et comment faire en sorte qu’ils s’affichent bien sur le blog.
#Je continue de rajouter des informations sur mon blog, il faut dire que je m’inspire pas mal de ce que tu as fait... J’ai prévu de faire une présentation de mon futur projet final au niveau de l’onglet My Projects.
#Parlant du projet, j’ai trouvé pas mal de datasets sur Kaggle. J’aimerais avoir ton avis sur la configuration requise pour entraîner mes modèles. Dois-je prévoir de le faire sur le cloud ou bien je peux le faire en local ?
#Ce week-end, je vais continuer d’explorer les transformers, et je commencerai à implémenter les trucs sur des modèles pré-entrainés de HuggingFace.
#J’avais consulter ton GitHub, mais je n’ai pas réussi à utiliser l’app que tu as eu à développer dans tes projets précédents car j’avais des messages d’erreur en local.
#Merci pour tes conseils
#A bientôt, Maël !

#Pour tes modèles, Colab devrait faire l'affaire, HuggingFace on plein de notebooks colab déjà faits pour fine-tuner des algos :slightly_smiling_face:
