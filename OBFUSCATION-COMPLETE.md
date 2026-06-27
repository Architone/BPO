# Build publié — niveau de protection

Ce dossier contient une version **minifiée** : tous les commentaires et l'indentation
ont été retirés, le code est compacté. C'est un **frein réel à la lecture/réutilisation**,
sans aucun renommage (donc zéro risque de casse — testé : le moteur 3D fonctionne).

## Aller plus loin : obfuscation complète (renommage des variables + chaînes encodées)
À faire **sur ta machine** (l'installation de paquets npm est bloquée dans l'environnement de génération) :

```
npm install -g javascript-obfuscator
# extrais le gros <script> de meuble.html dans engine.js, puis :
javascript-obfuscator engine.js --output engine.obf.js \
  --compact true --rename-globals false \
  --string-array true --string-array-encoding base64 \
  --string-array-rotate true --string-array-shuffle true \
  --control-flow-flattening false --self-defending false --debug-protection false
# recolle engine.obf.js à la place du <script> d'origine.
```
> Garde `--control-flow-flattening false` et `--self-defending false` : c'est ce qui
> préserve les performances du rendu et évite les bugs. Garde aussi `--rename-globals false`
> car le moteur lit des variables globales définies dans `data/*.js`.

Rappel : aucune protection n'est absolue pour du JavaScript côté navigateur — la vraie
barrière reste juridique (licence « Tous droits réservés » + CGU).
