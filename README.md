TP04 - Design Patterns State et Command
Description du projet

Ce projet fait partie du cours Approche Objet (UE 4TIN706U) de l'Université de Bordeaux. L'objectif de ce TP est d'implémenter deux Design Patterns : State et Command. Le TP vise à simuler une machine à états qui change de comportement en fonction des commandes reçues et de son état actuel.
Objectifs pédagogiques

    Design Pattern State : Modéliser les différents états d'une machine (lecture, pause, arrêt, avance rapide, retour en arrière) en utilisant le pattern State.
    Design Pattern Command : Encapsuler les actions de la machine dans des commandes, séparant ainsi l'invocation de l'exécution des actions.
    Design Pattern Observer (bonus) : Observer les changements d'état de la machine et les notifier à plusieurs observateurs.

Fonctionnalités

    Gestion des États avec le Design Pattern State :
        Implémentation de différents états : PlayingState, PauseState, StopState, ForwardingState, RewindingState.
        Chaque état implémente l'interface State et gère les actions spécifiques (lecture, pause, arrêt, etc.).
        Le contexte Automata gère la transition entre les états.

    Gestion des Commandes avec le Design Pattern Command :
        Chaque commande (lecture, pause, stop, etc.) implémente l'interface Command.
        Les commandes sont exécutées via la classe BagOfCommands qui permet de stocker et d'exécuter plusieurs commandes séquentiellement.

    Observateurs (Optionnel) :
        Implémentation du pattern Observer pour observer les changements d'état et enregistrer les événements.

Structure du projet

Le projet est structuré de la manière suivante :

    Automata : Classe représentant la machine à états.
    State : Interface des états de la machine.
    PlayingState, PauseState, StopState, etc. : Différentes implémentations de l'interface State.
    Command : Interface des commandes.
    PlayCommand, StopCommand, etc. : Implémentations des différentes commandes.
    BagOfCommands : Classe permettant de gérer et d'exécuter plusieurs commandes.
    Observer (optionnel) : Interface pour observer les changements d'état.
    Main : Classe principale de test.

Exécution
Compilation

Pour compiler le projet, utilisez la commande suivante :

bash

javac -d bin src/**/*.java

Exécution

Pour exécuter le programme principal :

bash

java -cp bin fr.ubordeaux.ufinfo.master.ao.td4.Main

Exemple d'utilisation

Voici un exemple d'exécution où la machine reçoit plusieurs commandes :

java

Automata automata = new Automata();
automata.setState(new StopState(automata));

Command playCommand = new PlayCommand(automata);
Command stopCommand = new StopCommand(automata);
Command rewindCommand = new RewindCommand(automata);
Command forwardCommand = new ForwardCommand(automata);

BagOfCommands bag = new BagOfCommands();
bag.addCommand(playCommand);
bag.addCommand(stopCommand);
bag.addCommand(rewindCommand);
bag.addCommand(forwardCommand);

bag.executeAll();

Auteurs

    Monir Chelh
    Université de Bordeaux
    Master 4TIN706U Approche Objet

Licence

Ce projet est sous licence MIT.