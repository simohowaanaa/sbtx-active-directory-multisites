# Note — DC-OUJDA

`DC-OUJDA` est préparé pour devenir le second contrôleur de domaine de la forêt unique `ad.sbtx.lab`. Il ne crée ni domaine ni forêt supplémentaire.

Son adresse fixe est `192.168.20.10`, sur le réseau Oujda `192.168.20.0/24`. Le DNS préféré pointe temporairement vers `DC-CASA` (`192.168.10.10`) afin de trouver le domaine existant lors de la future promotion.

La promotion est volontairement reportée : elle exige une communication réseau fiable entre Casablanca et Oujda. Les instantanés VirtualBox permettent de revenir à l'état préparé en cas de problème. Aucun mot de passe n'est enregistré dans ce dépôt.
