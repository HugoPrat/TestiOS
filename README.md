# TestiOS

Le but est de juste load le model ChainSawMobile dans le constructeur du Processor
pour ça on utilise la fonction torch::jit::_load_for_mobile qui ce trouve dans Pytorch pour Mobile

Avec cocoapods
    -exporter le projet avec le Jucer
    -Bouger le Podfile dans Build/iOS/
    -aller dans ce répertoire faire 'pod install'
    -cela crée un NewProject.xcworkspace à ouvrir avec xcode (c'est le projet avec les pods)
    -utiliser les headers cocoapods dans PluginProcessor.h et tenter de lancer le projet
    ## Comportement atteint => Build success mais le lancement ce stop immédiatement

Sans cocoapods
    -Suivre les instruction sur https://pytorch.org/mobile/ios/ pour rebuild les library partagé pour iOS de pytorch
    -Rajouter les librairies de la même manière qu'un projet JUCE
    -Exporter puis utiliser les header manuel dans PluginProcessor.h et tenter de lancer le projet
    ## Comportement atteint => Crash au torch::jit::_load_for_mobile(is);
    Sans doute un lien avec la version des librairies recompilé et ajouter par rapport au modèle

Pour passer un modèle en mobile ou changer la version de torch utilisé ave cle modèle : https://pytorch.org/mobile/home/
Avec Cocoapods attention à installer la bonne version de LibTorch-Lite en fonction du modèle

version de torch utilisé pour le model movileChainsaw 1.1O.1