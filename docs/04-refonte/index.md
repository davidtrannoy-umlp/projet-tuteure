# Cadre technique (Elementor)

Cette page sera complétée à mesure que les choix techniques se précisent, mais voici le cadre de départ connu.

## Outil de refonte : Elementor

La refonte se fera avec **Elementor**, un page builder pour WordPress.

!!! note "Pourquoi Elementor"
    Elementor est un outil largement utilisé professionnellement, avec une importante communauté et documentation, ce qui en fait un bon choix pédagogique pour une équipe d'étudiant·es qui le découvre. Il permet une construction de page « visuelle » (drag and drop) sans nécessairement écrire de code.

## Points de vigilance techniques

### Responsive

!!! warning "Le responsive ne se fait pas « tout seul »"
    Elementor propose des réglages spécifiques par appareil (desktop / tablette / mobile) pour chaque élément (marges, tailles de police, visibilité). Il faudra systématiquement vérifier l'affichage sur les 3 tailles pour chaque page créée, et pas seulement sur desktop.

Bonnes pratiques à appliquer :

- Concevoir « mobile first » autant que possible : penser d'abord à l'affichage mobile, puis enrichir pour desktop
- Tester réellement sur un téléphone, pas seulement avec l'aperçu responsive du navigateur
- Faire attention au poids des images (Elementor permet d'optimiser/redimensionner les images importées)

### Cohérence graphique

- Définir une charte de styles globale dans Elementor (Réglages du site : couleurs, typographies) plutôt que de régler chaque élément manuellement page par page
- Réutiliser des blocs/templates Elementor pour les éléments récurrents (en-tête, pied de page, blocs d'appel à l'action)

### Performance

- Limiter le nombre de plugins additionnels
- Optimiser les images (poids, format) avant import

## À documenter au fil du projet

- [ ] Version d'Elementor utilisée (Free / Pro)
- [ ] Plugins complémentaires nécessaires (formulaires, SEO, etc.)
- [ ] Accès et environnement de test (site de préproduction si disponible, ou directement en production ?)

Voir aussi la page [Livrables attendus](livrables-attendus.md) pour le détail des éléments à produire pendant cette phase.
