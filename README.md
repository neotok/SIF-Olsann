# Personnaliser SIF-Olsann

Ces fichiers sont la **reference** : ils contiennent les valeurs que le mod
utilise aujourd'hui, en version 7.6.2. Copiez ce dont vous avez besoin dans :

    Zomboid/Lua/SIF-Olsann/

```
Zomboid/Lua/SIF-Olsann/
├── config.json              reglages
├── traductions/*.json       textes et repliques
└── images/sif_<nom>.png     portraits et icones
```

Rien ne vous oblige a tout copier : **seules les cles que vous declarez sont
surchargees**, tout le reste continue de venir du mod. Une mise a jour du mod
n'ecrase donc jamais vos fichiers.

## config.json

| Section | Effet |
|---------|-------|
| `tag` | `"olsann"` garde la tenue et la musique de fin de vague. Tout autre tag ne laisse que la replique et le son. |
| `actions` | Valeurs par defaut de chaque action. Une commande envoyee par un viewer garde toujours le dernier mot. |
| `loot` | Listes de butin. Une liste declaree **remplace** celle du mod : c'est le seul moyen d'en retirer un objet. |
| `randomEvents.actions` | Declenchements automatiques une fois par vie. Une liste declaree remplace celle du mod. |

Le panneau en jeu (clic droit > Configurer SIF-Olsann) ecrit dans ce meme
fichier : vous pouvez cliquer ou editer a la main, c'est la meme chose.

## traductions/

Un ou plusieurs `.json`, appliques par ordre alphabetique. Le format est celui
du mod :

```json
{
  "UI_KAO_godMode_SAY_01": "Ma replique a moi",
  "UI_KAO_godMode_SAY_02": "Une autre"
}
```

Trois choses a savoir :

- Les variantes numerotees doivent **se suivre sans trou**. Le jeu s'arrete a la
  premiere manquante, donc un `03` absent rend `04` et `05` muettes.
- Une valeur **vide** est acceptee : elle fait taire cette replique-la sans
  casser les suivantes. Vider toutes les variantes rend l'action silencieuse.
- Le JSON **n'accepte aucun commentaire**. `//` ou `/* */` font echouer le
  fichier entier.

Le role se lit dans le nom de la cle : `SAY` pour les repliques tirees au hasard,
`MSG` pour un texte dit a un moment precis, `ERR` quand l'action n'a rien pu
faire, `NAME` pour le libelle affiche dans le panneau et le bandeau d'effets.

Les cles commencant par `UI_KAO_SYSTEM_` sont des textes techniques : mieux vaut
ne pas y toucher.

## images/

Nommees `sif_<identifiant>.png`. L'identifiant est celui du credit ou du groupe,
et il sert aussi a retrouver le nom affiche.

Le prefixe `sif_` n'est pas decoratif : sans lui, une image portant le nom d'une
texture du jeu serait eclipsee par celle-ci.

**Les images demandent un redemarrage** pour etre prises en compte : le moteur
met ses textures en cache. Les textes, eux, se rechargent en cours de partie.
