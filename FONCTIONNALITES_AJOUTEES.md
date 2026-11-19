# Fonctions ajoutées — parcelles, mesures et systèmes de coordonnées

## Export DXF et GeoJSON

Dans **Points** ou **Traces**, les formats généraux d’export comprennent maintenant **DXF** et **GeoJSON**. Le DXF regroupe les points, les segments de traces, les itinéraires, les mesures en cours et les polygones enregistrés. Les entités sont classées par calque. Les polygones portent aussi une annotation avec leur surface sur la grille active et leur périmètre.

Le GeoJSON est une collection complète de fonctions avec coordonnées géographiques WGS84 en longitude/latitude. Il exporte les points, traces, itinéraires, mesures et polygones. Les propriétés des polygones contiennent la surface projetée, la surface ellipsoïdale et le périmètre. Les traces et itinéraires indiquent leur longueur. Les coordonnées X/Y projetées et le CRS actif sont conservés dans les propriétés des entités.

## Surface et périmètre

Dans **Outils**, une mesure de trois points ou plus affiche la surface dans la projection active, la surface ellipsoïdale WGS84 et le périmètre. Les polygones enregistrés affichent ces mêmes métriques.

Une trace ou un itinéraire ouvert affiche toujours sa longueur. Dans son écran de détail, l’application propose également un aperçu de la surface et du périmètre si le segment entre le dernier et le premier point ferme la forme. Le bouton **Fermer / enregistrer comme polygone** enregistre cette géométrie comme parcelle; le tracé d’origine reste conservé.

## ED50, NTT et UTM

Les réglages UTM permettent de choisir une zone de 1 à 60 et l’hémisphère Nord ou Sud. Le mode **Auto** prend l’hémisphère du centre de carte ou du GPS. Pour des coordonnées manuelles ou des données éloignées de la carte courante, choisissez explicitement l’hémisphère et vérifiez la zone: une paire X/Y seule ne permet pas toujours de distinguer Nord et Sud.

ED50 reste disponible avec son ellipsoïde et ses paramètres de décalage modifiables. Les valeurs par défaut sont une approximation pour l’Europe occidentale et doivent être remplacées par les paramètres adaptés à la zone de levé.

Le choix **NTT** utilise l’ellipsoïde français Clarke 1880 et la projection officielle UTM 32N. L’Office de la Topographie et du Cadastre tunisien précise que la migration vers WGS84 repose sur des paramètres locaux associés aux feuilles 1:50 000; la publication de la FIG décrit aussi des transformations établies par feuille. L’application propose donc une translation XYZ modifiable à titre d’approximation, initialisée à zéro. Elle ne remplace pas les paramètres de transformation officiels de l’OTC et ne doit pas servir à un levé légal tant que ceux-ci ne sont pas configurés. [OTC — NTT](https://www.otc.nat.tn/geodesy/ntt) [FIG Working Week 2011 — systèmes géodésiques tunisiens](https://www.fig.net/resources/proceedings/fig_proceedings/fig2011/papers/ts04a/ts04a_benhadjsalem_5273.pdf)

## Contrôles effectués

La syntaxe JavaScript embarquée passe `node --check`. Des tests isolés vérifient les zones UTM 1, 33, 34 et 60, les deux hémisphères y compris à haute latitude, les conversions inverses ED50/NTT, les métadonnées CRS, les métriques de polygones, et la présence des géométries dans les exports DXF et GeoJSON.

L’APK n’a pas été compilé dans cet environnement, qui ne dispose pas de Gradle et de l’Android SDK. L’archive livrée contient le projet Android source, à ouvrir et compiler dans Android Studio ou un environnement Android configuré.
