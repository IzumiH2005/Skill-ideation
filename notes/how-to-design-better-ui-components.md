# How to Design Better UI Components 3.0 — Adrian Kuleszo (@uiadrian) — Notes complètes

> Source : e-book 197 pages (A4). Lu page par page (texte OCR + analyse visuelle de chaque illustration).
> Structure du livre : 1. Design Basics (Figma setup, Layouts/Grids/Box model) · 2. Foundations (Colors, Shadows, Gradients) · 3. Lingo (UI/UX terms) · 4. Interface (Buttons, Forms, Pricing, Dropdowns, Navigation, Search, Modals, Hero, Cards, Style guides) · 5. Practice (Good vs Bad UI, Practicing UI).

## Pages d'intro (p.1–5)
- Auteur : Adrian Kuleszo, agence DesignMe ; 500k+ followers ; 9 000+ ebooks vendus. Version 3.0 = refonte complète du 1er ebook gratuit (fév. 2022), désormais 9 $.
- Public : designers d'interface, web designers, devs, managers, graphistes. Conseil : garder Figma/carnet à côté, « design is best learned by doing ».
- Légende des encadrés : travail d'agence DesignMe / astuce courte actionnable (vert) / ressource d'un autre produit / avis subjectif de l'auteur.

---
# CHAPITRE 1 — THE DESIGN BASICS

## 1.1 Figma setup
### p.7 (06) — Mobile vs web
- Différence principale : espace disponible + **axe d'empilement**. Desktop : contenu en colonnes et rangées horizontales ; colonnes → sections ; sections empilées verticalement → page. Mobile : presque tout empilé verticalement, section sous section.
- Illustration : même landing (app cashback, 3 étapes « Register / Select a shop / Receive cashback ») en desktop (3 colonnes côte à côte) vs mobile (les 3 cartes empilées).
### p.8 (07) — Choisir la frame mobile
- Prendre la frame du **plus petit appareil courant** : iOS iPhone 13 Mini **375×812**, Android Small/Large **360×800**.
- Si tout tient dans la plus petite frame → OK. Commencer grand = problèmes de responsive refilés aux devs.
- Astuce : **toujours plus facile de scaler un design vers le haut que vers le bas.**
### p.9 (08) — Frame web
- Démarrer en **1440×1024** ; pour du no-code Framer : **1200×1024** ; visualiser aussi **1920×1024** (changement d'échelle). Concevoir pour les principaux breakpoints desktop.
- Piège Framer/Webflow : base 1440 → à 1439px bascule au breakpoint Tablet. Solution : dans une frame 1440 Figma, zone de travail de **1200px** avec **marges 20–40px**, design placé dedans.

## 1.2 Layouts, grids, box model
### p.11 (10) — Intro grid systems
- Illustration : écran Settings mobile avec annotations Auto Layout (direction verticale, gap 10, padding 36/24), propriétés Fill / Hug / Fixed sur les éléments.
- Méthode perso de l'auteur (Figma, Framer, Webflow). Objectif : designs clairs et bien structurés → traduction dev efficace, moins d'aller-retours.
### p.12–13 (11–12) — Termes de base
- Illustration annotée (Settings zave.it) : gutters, column grid (colonnes violettes translucides), side margins, columns.
- **Column grid** : cadre divisant l'écran en colonnes verticales pour aligner/organiser.
- **Baseline grid** : lignes horizontales définissant un rythme vertical ; rare, utile pour icônes, logos, dashboards complexes.
- **Columns** : sections verticales de la grille. **Side margin** : espace gauche/droite, cadre le contenu, évite qu'il s'étale sur toute la largeur. **Gutter** : espace entre colonnes.
- **Réglages grille mobile (capture Figma)** : Count **4**, couleur #5315FD à 10 %, Type **Stretch**, Width Auto, **Margin 16**, **Gutter 8**.
### p.14 (13) — Grille 8-pt
- Multiples de 8 pour espacements, marges ET dimensions des composants (8,16,24,32,40,48,56,64). Aligne avec la densité de pixels → scale bien.
- **4-pt** pour petits éléments / détails fins, surtout en mobile. **5px** seulement avec des grilles Bootstrap (sites non codés par lui).
### p.15 (14) — 8px vs 5px
- 5px : Bootstrap, colonnes fixes, espacement compact. 8px : layouts fluides, plus d'air.
- Illustration : hero « PartnerUp » avec cotes ambiguës (96 or 100? 16 or 20? 240 or 250? 10 or 8? 32 or 30?) → choisir un système et s'y tenir.
- **Setup recommandé : Fluid grid 12 colonnes, marges 100px, gutters 20px** → largeur 1240px → 3 colonnes de 400px ou 4 de 295px (gutters 20).
### p.16 (15) — Desktop grid
- Frame 1440×1024, **100px de marge partout → safe zone 1240px**, 12 colonnes, gutters 20px.
- En Framer : +20px de marge latérale supplémentaire pour respirer au bord du breakpoint (contenu 1160–1200px ; pas de marge < 1200px).
- Astuce : concevoir pour **deux largeurs de box : min 1200px, max 1920px+**.
### p.17 (16) — Containers / Box model
- Penser chaque section/élément comme placé dans des conteneurs (divs/boxes) imbriqués = **Box Model**. Pas de layout trop « créatif » : les devs vous détesteront.
- Illustration annotée (hero PartnerUp) : hero section → 2 columns → text container + image container ; l'illustration déborde avec **overflow = visible**.
- Pour chaque nouvel élément : penser bounding box + position dans le layout. Images → conteneurs → conteneurs plus grands → colonnes → sections. Ne pas oublier padding et margins.
### p.18–19 (17–18) — Scaler au-delà de 1440px
- Les débutants oublient ce qui se passe au-delà de 1920×1080. Exemple : site prêt immobilier « A Home Loan Experience That Makes Sense ».
- 1440×1024 : marges 100 / box 1240 / 100. En 2580×1440 avec box fixe 1240 → marges **660px** de chaque côté → déséquilibré (pire en 4K/ultra-wide).
- Côté dev : unités relatives **VW** ou **EM** (relatif à la taille de police de base, généralement **16px**).
- En no-code : réglage **max width**. Ex. arrêter de scaler à 1920 : en 2580×1440 → box 1920 avec marges 320. Faire un écran pour visualiser ça pour les devs.
### p.20 (19) — Fixed vs full width
- Option A : marges en % (**5–10 %**) → design sur **80–90 %** de l'espace. Option B : largeur fixe (1240px). Préférence perso.
- Largeur fixe ⇒ penser au plus petit breakpoint : sous 1240px (petit écran, split screen) ajouter du **padding latéral** (illustration : contenu collé au bord sans padding = mauvais).
### p.21 (20) — Mobile grid
- « Every pixel counts » ; mobile = contenu essentiel, choisir quoi garder pour grands écrans.
- Démarrer sur le plus petit iPhone récent (**375px**) ; **marges min 16px**, **gutters 8px**, **grille 4 colonnes** → contenu **335px+**. Android : Android Small, même grille.
- Exemple Figma Mastery : marges 20px sur iPhone 13 Mini.
### p.22 (21) — Row grid
- Utile pour dashboards web/mobile complexes. Réglages Figma montrés : **type: top, 8px offset, 8px height, 8px gutter, count: 800** (nombre élevé si l'artboard est haut).
- Les devs n'ont pas de « row grid » : ils utilisent frameworks, CSS Grid, Flexbox. (Le Fintech UI Kit du Design Manual a été fait sans baseline rows.)
### p.23 (22) — Soft vs hard grid
- Il utilise rarement les baseline grids. Règle : colonnes verticales + éléments et distances sur incréments **4–8px**.
- Avec l'expérience : designer **sans grille**, avec incréments 4–8px + **auto-layout comme source de vérité** ; allumer la grille ponctuellement pour un placement difficile. Illustration : « columns only » vs « columns + rows » (app zave.it, faite grilles éteintes).

## 1.3 Alignment
### p.25 (24) — Container alignment
- Les conteneurs internes s'alignent sur les largeurs de colonnes, **gutters = marges entre eux**. Illustration : grille 3×2 de cartes features (site Design Manual, 12 colonnes + grille 8px).
- Pas besoin de s'inquiéter de l'alignement à l'intérieur du conteneur : nombres ronds + **padding interne 20–40px** si besoin. Aligner la rangée sur la largeur de la nav header pour ancrer le contenu aux deux bords (scan plus facile).
### p.26 (25) — Rythme vertical & alignement horizontal
- Illustration carte « Companion Care » : version gauche espacements 24/24/12/24/24 ; version droite (en conteneur) 24/12/16/16/40.
- **Règle d'espacement par proximité : titre ↔ description 8–20px+ ; groupes de texte ↔ icônes/boutons 20–40px+ ; padding autour des conteneurs 12–20px+.**
- Alignement horizontal : composants similaires dans des boîtes de **hauteur fixe**, sur la même ligne (3 cartes services : icône / titre / description alignés).
### p.27 (26) — Layout consistency
- Cohérence = mêmes apparences/comportements partout → prévisibilité → confiance. La grille donne à l'équipe des tailles, espacements et patterns communs (produit durable, mis à jour par plusieurs personnes).
- Nommer les calques, process, auto-layout : négligeable en solo, **obligatoire en équipe** ; apprendre tôt, libre de s'en passer en perso.
- Illustration : 3 cartes d'investissement uniformes (Low risk / Balanced / High yield) — même structure (icône+titre, description, Returns 4,5%–6,5%, Risk ±6,5%, bouton outline « Choose … package »), la carte centrale mise en avant par un bandeau vert « Our recommendation for you » + bordure verte.
### p.28 (27) — White space
- Espace négatif : évite l'encombrement, améliore la lisibilité, crée un point focal, guide l'œil dans la hiérarchie.
- Illustration : formulaire Register avant/après — après : plus d'espace entre champs, entre indicateur de force du mot de passe et checklist, bouton et texte légal.
- **Au moins 16–20px de marge** ; espacer les éléments interactifs pour éviter les miss-clicks (padding interne ET marge externe).
### p.29 (28) — Less is more
- Chercher ce qu'on peut **retirer** plutôt qu'ajouter ; chaque élément ajoute de la **charge cognitive**.
- Illustration : section produit « How To Design Better UI » surchargée (badge avis, encart remise, 4 checks, 2 « + », bouton, paiements, mention) → version épurée (rating déplacé en badge sur l'image, encart supprimé).
- Méthode : concevoir la vue mobile pour tester la simplicité ; sinon retirer encore.

---
# CHAPITRE 2 — MASTER THE FOUNDATIONS
## 2.1 Colors in UI
### p.31 (30) — Bases + contraste
- Couleurs = accentuer, donner le ton, guider subconsciemment le comportement ; fonctionnelles (attention, utilisabilité, lisibilité), conversions, identité de marque.
- Accessibilité minimale = exigence de la plupart des projets commerciaux. Exemple : bouton « Get started » texte blanc sur lavande **2:1 → échoue AA & AAA** ; texte noir sur même lavande **7.25:1 → passe AA & AAA**.
- **Ratios cibles : grand texte (>24px) 3:1 ; petit texte (<18px) 4.5:1 ; boutons et inputs 3:1.** (le livre écrit « WCAG 3.0 AA »)
- Outils : plugins **A11Y Contrast Checker**, **Stark** — vérifier pendant la conception, pas au handoff.
### p.32 (31) — Psychologie des couleurs
- Roue chromatique 12 teintes : yellow, amber, orange, vermillion, red, magenta, purple, violet, blue, teal, green, chartreuse.
- **Bleu** : calme, confiance, fiabilité → finance, santé. **Vert** : croissance, harmonie → durabilité, bien-être. **Rouge** : urgence, excitation → alertes, CTA, avec parcimonie (anxiété).
### p.33 (32) — Suite psychologie
- **Jaune** : bonheur, vitalité, capte l'attention, optimisme → mettre en avant des features ; attention luminosité/contraste. **Orange** : convivial, enthousiaste → CTA engageants sans l'intensité du rouge (le livre s'achète via un bouton orange). **Violet** : luxe, créativité, innovation — mais galvaudé par la tech (dark modes violets) → tendance à diversifier les palettes pour une identité unique. **Noir** : élégance, haut de gamme, dark mode (visibilité, moins de fatigue). **Blanc** : pureté, simplicité, minimalisme ; s'accorde avec noir et n'importe quel accent.
- Les couleurs ont des significations **différentes selon les cultures** → rechercher le marché cible.
### p.34 (33) — Tints & shades
- **Tint** = couleur pure + blanc (pastel, moins saturé). **Shade** = + noir. Illustration : violet #6600FF-ish décliné en 6 tints quasi blancs et 6 shades jusqu'au quasi noir.
- Tints → fonds, éléments secondaires (bouton secondaire). Shades → emphase des éléments essentiels. Exemple : « Cancel » (fond tint lavande, texte violet) + « Save changes » (fond shade violet très foncé, texte blanc).
### p.35 (34) — Chaud vs froid
- Chaud (rouge→jaune) : accueillant, convivial. Bleus : calme, ordre, design sobre/minimal.
- Illustration app « Influencer 1:1 Chat » : même écran Inbox en froid (fond gris-bleu, bouton bleu nuit, sans-serif) vs chaud (fond crème/beige, bouton brun foncé, typo serif). Astuce : de **subtils changements de teinte + typographie + rayons d'angle** changent tout le ressenti.
### p.36 (35) — Combinaisons à fort contraste
- Couleurs vives sur fond sombre → focus, énergie, dynamisme. Exemple : landing Prototyping Masterclass, fond noir, palette noir/gris/blanc + accent **vert-jaune vif** (CTA « Join the Waitlist », titres surlignés, carte prix).
### p.37 (36) — Monochromatique
- Nuances d'une seule couleur → harmonie, flux visuel doux, design « propre », simplifie les choix.
- Palette Fintech app (Design Manual) : **Dark BG (bleu nuit quasi noir) / Primary (bleu-pétrole foncé) / Accent (bleu ciel) / Light (bleu très pâle) / White BG** ; + vert vif en accent ponctuel.
### p.38 (37) — Contraste et lisibilité
- Priorité n°1 : lisibilité du texte sur fond ; le contraste sert aussi à souligner CTA, distinguer éléments, attirer l'attention.
- Illustration : Settings zave.it MVP en dark mode — haut contraste (texte blanc) 😎 vs bas contraste (texte gris sur gris) 😡.
- Bas contraste = difficile pour malvoyants, seniors, faible éclairage. **Lisibilité/accessibilité > esthétique.**
### p.39 (38) — Branding cohérent & usage émotionnel
- Couleurs de marque identiques partout (site, pubs) → mémorisation, confiance (Coca-Cola = rouge/blanc/noir ; Facebook = bleu). Illustration : Fintech App SmartBank (bleu pétrole + jaune-vert accent) cohérente sur tous les écrans.
- Couleurs émotionnelles : exemple iOS natif — actions destructrices en **rouge** (« Remove » dans menu contextuel, « Delete Draft » dans action sheet), actions neutres en bleu/noir.
### p.40 (39) — Couleurs depuis les images & simplifier
- Vieux truc de branding : **prélever la palette dans l'imagerie existante** (photo livre/bougie → blanc cassé, vert feuille, noir verdâtre, beige rosé, taupe).
- **Une couleur primaire** qui génère tints clairs et shades foncés ; + un accent optionnel. **Règle 60-30-10 : 60 % primaire (tints/shades), 30 % neutre, 10 % accent.** Illustration : Primary bleu vif + tints ; Neutral du quasi-noir au gris clair ; Accent orange + gris.
### p.41 (40) — Tonalité des images ; teinter gris/noirs
- Ajuster température, saturation, exposition des photos pour coller à la palette (même portrait en version neutre/grise, froide/bleutée, chaude/beige).
- **Ne pas utiliser gris/blanc/noir purs** : y injecter la primaire. Astuce sans plugin : poser la primaire par-dessus le gris (ou noir/blanc), **opacité 5–15 %**, pipeter le résultat (gris → gris bleuté ; noir → bleu nuit).
### p.42 (41) — Feedback, interactivité, statuts système
- Couleur pour l'interactivité (hover) et le feedback (succès vert, erreur rouge). Exemple CRM DesignMe : badge « Complete » vert, bandeau orange d'info, coches vertes.
- **Minimum 3 couleurs système : erreur rouge, warning orange, succès vert.** Contraste min **4.5:1, idéalement 7:1**. Illustration : badges pâles à 1.65:1 (illisibles) vs badges texte foncé à 7:1.
### p.43 (42) — Designer en niveaux de gris
- D'abord layout, structure, fonctionnalité ; la couleur ensuite (sinon distraction + révisions coûteuses). La couleur vient compléter un layout déjà solide.
- Questions à se poser (wireframe NFT gris) : Quels éléments UI inclure ? Dans quel ordre ? L'info suit-elle un flux logique ? L'UI est-elle trop distrayante ? Les utilisateurs sauront-ils quoi faire ? **Chaque élément a-t-il un but ?**
### p.44 (43) — Repérer les problèmes d'accessibilité
- Le gris force à se concentrer sur hiérarchie, contraste, lisibilité. Plugin **A11y – Color Contrast Checker** (« AAAMAZING – all texts meet AAA »).
- Barème affiché : **polices normales (<19px) AA 4.5:1 / AAA 7:1 ; grandes (19px+) AA 3:1 / AAA 4.5:1.**
- Itérations plus rapides : 3 variantes d'écran NFT en gris (ordre des sections Best Seller / Top Collections / Best Authors) avant la couleur.
### p.45 (44) — Transition vers la couleur
- Une fois le gris validé, appliquer le schéma couleur sans toucher layout/structure. Illustration : palette gris (noir, blancs, gris) → même palette + **un seul accent jaune-vert** ; images en couleur.
- La couleur peut créer du bruit ; la retirer temporairement force à prioriser structure, fonctionnalité, utilisabilité.

## 2.2 Shadows
### p.47 (46) — Intro
- Les ombres imitent la lumière réelle → profondeur, réalisme ; surtout **utilisabilité** : différencier les couches, établir la hiérarchie, guider l'interaction.
### p.48 (47) — Élévation & douceur
- Élévation = l'ombre dépend de la distance à la surface. Illustration : 6 boutons « Login » d'élévation croissante (ombre nette proche → ombre diffuse lointaine).
- Comparatif : **#000 opacité 10 %, x0 y15 blur20** (plus contrasté, lumière juste au-dessus, plus 2D) vs **#000 opacité 4 %, x0 y10 blur15** (plus doux/naturel). Plus doux = source lumineuse lointaine = plus naturel.
### p.49 (48) — Direction & reflet matière
- **Une seule direction d'ombre / une seule source de lumière** dans une composition (cartes côte à côte : même ombre).
- **Material reflection** : ombre teintée de la couleur du bouton. Bouton violet **bg #7949FF, ombre #7949FF opacité 20 %, x0 y15 blur20** vs bouton blanc ombre noire 4 % x0 y10 blur15.
### p.50 (49) — Style & ombres multiples
- **Ombre dure façon stroke (néo-brutalisme)** : carte stroke **2px #000** + ombre **#000 100 % x4 y4 blur0** → pas besoin de dupliquer des calques, handoff plus simple.
- **Ombres multiples superposées** = plus réaliste : **#000 4 % x0 y10 blur15 + #000 15 % x0 y2 blur4** (ombre diffuse + ombre de contact).
### p.51 (50) — Strokes à opacité réduite & inner shadows
- Stroke subtil : **1px, #898989, opacité 20 %** sur bouton blanc + ombre « Beautiful Shadows » → le bouton ressort et se fond naturellement avec l'ombre.
- Inner shadows (effet bouton « skeuo » brillant) : bouton **#EDEDED**, **stroke 1px inside dégradé #FFFFFF → #BDBDBD → #FFFFFF**, **inner shadow #FFFFFF 100 % x-4 y2 blur10**.
- Avis : pas nécessaire partout ; **rester sur les standards** donne les meilleurs résultats — les boutons fancy impressionnent les designers, pas les utilisateurs.
### p.52 (51) — Plugin Beautiful Shadows
- Génère plusieurs couches de drop shadow (5 dans l'exemple) d'opacités variées → ombre réaliste. On règle la direction (en déplaçant l'ellipse/lumière dans l'aperçu), la couleur et l'intensité.
### p.53 (52) — Ombres sur fond sombre
- Sur fond sombre, l'ombre se voit peu : utiliser un **halo/surbrillance plus clair** pour créer l'élévation et attirer l'attention.
- Ou « vraies » ombres : **empiler plusieurs ombres à forte opacité** ; avec Beautiful Shadows, monter l'opacité à ~100.

## 2.3 Gradients
### p.55 (54) — Intro
- Ajoutent profondeur, dimension, modernité ; transforment un design plat. Exemple : dégradés subtils (blanc → gris-bleu très pâle) sur la page Design Manual.
- **Modération** : abus ou mauvais mélange = design cheap et non poli. Ligne fine entre intéressant et inutile.
### p.56 (55) — Linéaire
- Transition le long d'une droite entre 2+ couleurs ; la plus courante ; idéale fonds et boutons (illustr. : violet vertical, violet→lavande horizontal, bleu→rose diagonal).
- **Boutons** : dégradé subtil = plus cliquable, surtout CTA primaire (exemples Login : violet, noir→gris, bleu, pastel lavande→bleu ciel).
- **Fonds** : casser la monotonie ou améliorer la lisibilité sur fonds chargés (overlay violet foncé sur captures).
### p.57 (56) — Radial
- 2 stops (centre / bord). Pour mieux fondre : **glisser un stop vers l'intérieur de la forme**. Exemple : halo vert olive sur fond noir (landing Prototyping Masterclass).
- **Overlay radial** : rectangle par-dessus un motif (grille), fill radial avec stops **100 % → 0 % d'opacité** → révèle progressivement motif/image dessous.
### p.58 (57) — Angular & diamond
- **Angular** : stops autour du cercle ; plus dur à maîtriser, compositions superbes (ex. landing « Clokk – Clock is ticking. » avec plan gris en dégradé angulaire).
- **Diamond** : peu courant, forme nette en losange, comme un rayon de lumière (ex. « Explore the depths », bleu sur noir).
### p.59 (58) — Mesh & choix des couleurs
- **Mesh** : multi-couleurs abstraites sans chemin linéaire/radial ; à la main via formes floutées, ou générateurs en ligne / plugins Figma gratuits.
- **Choisir des teintes voisines sur le spectre** pour éviter les transitions abruptes : lavande → bleu ciel 😎 vs brun → violet (couleurs éloignées, transition boueuse) 😡.
### p.60 (59) — Plus de points & position
- Dégradé multicolore fluide : ajouter des stops intermédiaires de teintes voisines entre les 3 points principaux (ex. 5 stops : noir, bleu nuit, violet, bleu clair, vert-jaune).
- **Resserrer les points vers une extrémité** (espaces décroissants vers la fin). S'applique à tous les types de dégradés.
### p.61 (60) — Bruit/texture & dégradé comme source de lumière
- **Grain/noise par-dessus le dégradé** (plugin Noise & Texture ; calque Image 15 % sur Linear 100 %) → profondeur ; « textures et bruit font passer du bon à l'exceptionnel ».
- **Layer blur sur une forme en dégradé** (ex. ellipse blanche, blur 80) = halo/« godly rays » pour guider l'attention vers un bouton, mockup, carte (« Established in 2020 »).

---
# CHAPITRE 3 — MASTER THE LINGO (UI/UX terms)
### p.63 (62) — Intro
- Connaître le vocabulaire = penser dans un paradigme commun. Termes en nuage : user journey, Material Design, brand guidelines, sitemap, user flows, Human Interface Guidelines. Le domaine est interdisciplinaire (psycho, tech, art, business… « et l'industrie alimentaire » — blague annonçant les termes « food »).
## Glossaire UX (process & livrables)
### p.64 (63)
- **User journey** : récit pour se mettre dans la peau de l'utilisateur, par cas d'usage et persona. Template : persona (Kristen Roberts, F, étudiante, 24, Londres) + **Scenario** (découvre l'app via l'influenceur favori…) + **Expectations** (réservation facile, proximité avec ses idoles, insights). Lignes : **STAGES** Awareness → Consideration → Conversion → Exploration → Retention ; **STEPS** IG Story/TikTok → Website → Payment → In-app navigation → Active use ; **THINKING** / **DOING** par étape.
- **User journey map** : cartographie de bout en bout pour les stakeholders ; repère problèmes et quick wins, aligne l'équipe. Template : « Web onboarding — Total journey 4–6 minutes », étapes avec durées et émojis d'humeur, branche optionnelle ; ligne « App onboarding ».
### p.65 (64)
- **User persona** : personnage semi-fictif basé sur de vrais utilisateurs. Template : nom, photo, 3 adjectifs (Fun – Dedicated – Compassionate), citation, Goals/Interests, Pain points/Concerns, Motivations (barres), Personality (Introvert↔Extrovert, Low↔High confidence), Demographics, Scenario.
- **Sitemap** : hiérarchie exacte des pages et leurs relations ; indispensable avant toute refonte majeure (ex. client Supply Chain Finance).
### p.66 (65)
- **User flows** : chemin/étapes pour atteindre un but ; séquence + options (flowchart avec décisions en losange, étapes colorées).
- **Information architecture (IA)** : organisation et étiquetage de l'information pour trouver facilement (arbre : Dashboard → Offer / Users / Submissions / Media / Pages / Globals / Reports → Manage…).
### p.67 (66)
- **Wireframes** : plan de structure/layout, low ou mid fidelity (progression low-fi gris → mid-fi avec texte → hi-fi « Order a card »).
- **Low-fidelity** : early-stage, souvent dessiné à la main, fonction et structure avant style.
### p.68 (67)
- **High-fidelity** : pixel-perfect, interactif, look final (SmartBank « Stress less about your money », badges stores, note 4.9/5 sur 1923 avis).
- **Prototype** : modèle cliquable pour tests, feedback, validation (banking app avec nombreux liens de prototypage).
### p.69 (68)
- **Inspiration board** : collecte d'inspirations en ligne pour l'exploration visuelle, à montrer aux stakeholders.
- **Moodboard** : images, couleurs, textures → ambiance, style ; ex. « Direction 2 : Light / Gray + Pastel accents », concept, mots-clés Modern, Clean, Fun, Bright, Fresh, Clever.
### p.70 (69)
- **Brand guidelines** : logo, palette, typo, ton (SmartBank : violet nuit, jaune-vert, lavande, noir/blanc).
- **Style guide** : couleurs & text styles, patterns, iconographie, imagerie → cohérence multi-plateformes. Exemple d'échelle typo (Avenir Next) : **display/d1 72 SemiBold, d2 64, headline/h1 56, h2 48, h3 40, h4 32…** ; palettes tonales primaire/secondaire/dark/light ; grilles desktop/mobile.
### p.71 (70)
- **Component library** : collection de composants réutilisables (boutons, cartes, menus, navbars…) — sections : container cards, tab bars & navigation bars, lists & badges, icons & images, account cards.
- **Design system** : guidelines + composants + patterns pour la cohérence multi-produits. « Atoms » montrés : rampes tonales (neutres, Primary bleu-pétrole, Secondary jaune-vert, noir/blanc), **System colors** (Success verts, Error rouges), blurs, icônes, avatars, drapeaux.
### p.72 (71)
- **Material Design** (Google, m3.material.io) : interactions responsives, layouts en grille, effets de profondeur ; Android + très utilisé en web. Material Theming pour personnaliser.
- **Human Interface Guidelines** (Apple, developer.apple.com/design/human-interface-guidelines) : principes, bonnes pratiques, éléments d'interface pour une UX cohérente et accessible.
### p.73 (72)
- **Product roadmap** : vision, direction, progrès dans le temps, jalons et timelines (vue Gantt : Onboarding, New Logo, Web app wireframes, Mobile app…).
- **Project backlog** : liste priorisée de tâches/features/fixes (Trello client Kingdom Advisors : Your Assets / Task Backlog / Active Tasks / In Review / Completed).
### p.74 (73)
- **Design iterations** : réviser/affiner selon feedback et tests (3 versions d'un écran « Community » : feed de posts → onglets Questions/Answers → version compacte avec badges « Check profile »).
- **MVP** : produit dans sa forme la plus simple déployable ; tester en marché réel avec les features minimales mais essentielles (zave.it MVP : profil créateur, deals, cashback).

## UI elements (glossaire composants)
### p.76 (75)
- Les éléments UI sont les parties tangibles avec lesquelles l'utilisateur interagit ; connaître **fonction, placement et nom** de chacun est essentiel pour communiquer. Exemples zave.it : toast/notification cashback, bannière « Add your bank account », notification support, demande de feedback.
### p.77 (76)
- **Navigation bar** : barre horizontale vers les sections principales, évite les clics inutiles ; peut être **sticky** (ex. designme : Start here, Services, Pricing, FAQs, About, Happy Clients + CTA « Hire us! »).
- **Hero section** : premier visuel ; imagerie engageante + **CTA clair + preuve sociale** (Figma Mastery : titre fort, sous-titre, CTA « Enroll in Figma Mastery Today » + secondaire « View Curriculum », « Trusted by 25,000+ designers on Gumroad (5.0/5.0) », avatars de témoins).
### p.78 (77)
- **CTA buttons** : attirent l'attention, guident l'action (« Sign Up », « Buy Now »). Ex. zave.it : champ Email, bouton primaire noir « Continue », séparateur « or », boutons secondaires outline « Sign in with Apple / Google ».
- **Footer** : liens secondaires, pages légales, contact, réseaux sociaux, newsletter, courte description ; **indispensable** sur tout site. Ex. Relume : bandeau communauté + CTA, colonnes Product / Community / Power ups / Resources, badge Product Hunt, copyright.
### p.79 (78)
- **Modal windows** : petites boîtes/overlays d'info sans changer de page (acceptation, confirmation, annonces, pubs) ; importantes pour signaler des changements de statut sur mobile (ex. « Congrats! Your class is ready. » + « Copy invite link »).
- **Forms** : de la newsletter au paiement ; champs + CTA de soumission (paiement : Name on card, Card number, MM/YY, CVC, « Pay $29.95 » ; contact : First name, Email, Message (optional), checkbox privacy policy, « Send message » ; variante avec cases à cocher Services).
### p.80 (79)
- **Sliders/Carousels** : faire tourner du contenu dans un conteneur, économiser de l'espace (carrousel créateurs zave.it avec flèches).
- **Search bars** : essentielles en e-commerce et sites riches en contenu (« Search bank… », recherche « Brit » → British Pound + Cancel).
### p.81 (80)
- **Breadcrumbs** : navigation secondaire montrant la position (Home / Category / Subcategory) ou **stepper** cliquable (1 Your interests > 2 Support a Creator > 3 Confirm your choice).
- **Dialog boxes (alerts)** : petites fenêtres exigeant une réponse avant de continuer (iOS : « Delete this list » Cancel / Delete rouge ; Android : CANCEL / DELETE en texte).
### p.82 (81)
- **Tab bar** : nav horizontale en bas des apps mobiles ; icônes ± labels ; section active mise en évidence (zave.it : Home / Deals / Profile, actif en vert).
- **Thumb-friendly zone** : placer les éléments importants dans la zone facile (vert, bas/centre de l'écran), et **les boutons d'interruption de flux (back, delete, close) hors de portée** (zone haute rouge/orange). Ex. bouton « Add new activity » en bas.
### p.83 (82)
- **Toasts** : souvent pleine largeur, signalent activité/mise à jour ; natifs ou custom. 4 variantes : succès vert (Congratulations!), info bleu (Did you know?), warning jaune, erreur rouge (Something went wrong!) — icône ronde colorée + titre + texte + ✕.
- **Tabs** : diviser le contenu en panneaux sur le même écran (iOS segmented 13/14/16-inch ; Android onglets Chat/Expenses soulignés).
### p.84 (83)
- **Snackbars** : natifs Android, apparaissent au-dessus de la bottom app bar ; confirmer ou **annuler** une action (« Message deleted — Undo »).
- **Tooltip** : popup contextuelle au survol/tap, clarifie le rôle (« Available extensions: .mov, .mp4, .mve » ; termes soulignés en pointillés dans une table de pricing).
### p.85 (84)
- **Accordions** : déplier/replier, gagner de la place (FAQ designme « What the FAQ?! », ✕ pour fermer, + pour ouvrir ; ex. landing page 3–5 jours ouvrés, dev Framer jusqu'à 5 jours, identité de marque jusqu'à 3 jours).
- **Notifications d'app** : envoyées même app fermée (Wallet « SmartBank Card is ready for Apple Pay »).
### p.86 (85)
- **Chips/tags** : compacts, input/attribut/action, filtres/catégories/mots-clés ; **colorés** pour des indices visuels (Full Time orange pâle, Senior Level rose, Part-Time vert).
- **FAB** : action principale/la plus fréquente, élevée au-dessus du reste (Material 3 : « Compose » avec icône crayon).
### p.87 (86) — Pub Design Manual
- Le Design Manual couvre **100+ écrans mobiles issus des 16 flows les plus courants** (iOS/Android). Mise à jour Fintech UI kit prévue (nouveaux composants iOS, chapitres UX). Page promotionnelle.

---
# CHAPITRE 4 — MASTER THE USER INTERFACE
## 4.1 Buttons
### p.89 (88) — Intro
- Boutons : changer de page, acheter, confirmer ; libellé = **copy CTA clair** ; une action en un tap. Illustration Enabled (gris foncé + ombre) → Pressed (noir, sans ombre).
- Principes Material : **Identifiable** (crie « click me! », promet que quelque chose se passe), **Findable** (pas de cache-cache, ressort), **Clear** (icônes descriptives ou labels concis ; pas de copy vague).
### p.90 (89) — Anatomie
- Éléments : **label, padding, corner radius**.
- **Label 14–20px**. **Padding horizontal ≈ 2× vertical** (souvent). **Hauteur 32–60px**. Material : **≥ 48px** ; Apple : **≥ 44px** ; desktop (souris plus précise) : **32–40px**.
- Radius selon langage de marque : **arrondi = accueillant, ludique, moins sérieux ; angles vifs = sophistiqué**.
- Exemple chiffré : **texte 14–17px, line-height 22px+, padding vertical 10px+, padding horizontal 16px+, hauteur 40px+**.
### p.91 (90) — Types
- **Filled (primaire/CTA)** : ressortent le plus ; texte d'action convaincant (« Get started today », « Get a free trial », « Shop now » — angles vifs, légèrement arrondis, pilule).
- **Ghost (outline, secondaire)** : actions importantes non primaires, souvent « en savoir plus » (learn more, watch a video, contact support).
- **Link (tertiaire)** : style texte, emphase réduite ; **souligner** pour l'accessibilité (malvoyants) ; peut être coloré (« See pricing » souligné, « read more → » bleu, « more features »).
### p.92 (91) — États & padding invisible
- États : **normal, hover, active, disabled, focused, progress (loading…)**. Chacun distinguable mais **sans changements drastiques** (bruit visuel). Illustr. : normal gris foncé ; hover noir ; active fond clair + bordure/texte verts ; disabled gris clair texte pâle ; focused anneau bleu ; progress « loading… ».
- **Zone tappable min 40–44px** même pour liens tertiaires et items de liste (menu Home/About/Pricing/Contact dans des boîtes **44px+**).
### p.93 (92) — Hiérarchie de style & alignement
- Primary (filled) = CTA principal ; Secondary (outline) = moyenne ; Tertiary (texte) = faible.
- Boutons en ligne : **du plus au moins important** (gauche→droite) : « Apply changes » (filled) / « Save Draft » (outline) / « Cancel » (lien souligné). Plus loin = moins proéminent.
### p.94 (93) — Taille & contraste
- **Mobile min 48×48px** (≈ bout de doigt moyen). **Desktop min ≈164×48px+** (« Let's rock! » avec icône). Partir de ces minima puis ajuster ; le bouton est souvent l'élément le plus important de la page → proéminent.
- Contraste fond/label : bleu clair + texte blanc 😡, gris moyen + blanc 😡, noir + blanc 😎. Texte lisible en toutes circonstances.
### p.95 (94) — Centrage du texte & icônes
- Bouton 32pt + texte 17pt = centrage parfait impossible → **ajuster pour des nombres ronds/pairs** (illustration : texte décalé 😡 vs centré 😎).
- **Icône + texte** = indice visuel supplémentaire ; règle générale : **icône avant le label** (« ▶ Play video »).
- Nuance de l'auteur : dépend du contexte. Icône à gauche = aide au scan/communique l'action (comme une liste à icônes). Icône à droite = indique **où mène l'action** (« Log out » + porte ouverte, « Send message » + avion en papier, « Download PDF » + flèche).
### p.96 (95) — Style & CTA fort
- Adapter le style à la marque (pilule dégradée noire avec ombre, rectangle noir carré, outline arrondi). **Arrondi = doux, accueillant, friendly ; carré = structuré, minimaliste.**
- Libellé qui annonce le résultat, sans devinette (« ▶ Play the Video », « Download PDF ⬇ »). **Bannir « click here »** (mobile/clavier : on ne clique pas).
### p.97 (96) — Nommage & cohérence
- Verbes d'action décrivant le résultat : boîte « Are you sure you want to delete? » → **« Cancel / Delete »** plutôt que « No / Yes ».
- Cohérence (Jakob Nielsen : un des principes d'utilisabilité les plus puissants) : couleurs, formes, tailles communes → **design system**. Illustr. : Send Message (filled + icône), Submit (disabled), Cancel (outline), bouton icône seul, « Use AI » (tertiaire avec icône), pagination 1/2/3/>.
### p.98 (97) — Dégradés, strokes, inner shadows sur boutons
- Dégradé linéaire + stroke linéaire (violet clair→violet, stroke blanc→violet) → profondeur, hiérarchie, focus sur le texte.
- **Inner shadow** pour un effet 3D : **X0 Y6 Blur19 Spread0, couleur #B43AFF à 48 %** sur bouton violet « Use AI ».
### p.99 (98) — Placement mobile
- **CTA dans la zone du pouce** (bas de l'écran), surtout navigation (« Continue » en bas 😎 vs juste sous le champ en haut 😡). **Boutons destructifs/secondaires hors de portée.**
- S'adapter à la façon dont on tient le téléphone → moins de frustration et d'erreurs.

## 4.2 Forms
### p.101 (100) — Intro & anatomie
- Équilibre commodité utilisateur ↔ besoin d'information.
- Anatomie (wireframe annoté) : **labels, input field, placeholder text, input type** (téléphone avec drapeau/indicatif ; textarea « Message (optional) »), **acceptance text** (case « You agree to our privacy policy » avec lien violet), **call to action** (« Send message », bouton noir pleine largeur).
### p.102 (101) — Labels
- **Labels visibles en permanence** (formulaire avec placeholders seuls → confusion sur le champ rempli). Faciliter la validation de la saisie.
- Alternative compacte : **floating label** (le placeholder « Your first name » remonte en petit label violet au-dessus/sur la bordure quand on saisit).
### p.103 (102) — Optionnel vs requis
- Pas d'encombrement. Les études UX : l'**astérisque n'est plus une bonne pratique** (voire une erreur) — les points rouges mettent mal à l'aise. **Marquer les champs optionnels « (optional) »** plutôt que les requis (il y a généralement plus de requis) → moins de bruit, formulaire moins intimidant.
### p.104 (103) — CTA actionnable & erreurs
- CTA primaire **proéminent** (outline pâle → bouton noir rempli) + bouton secondaire pour annuler ; doit avoir l'air cliquable.
- **Messages d'erreur** : champ bordé/teinté rouge + **icône** + texte **descriptif** sous le champ (« Please choose the right email format. ») pour corriger vite.
### p.105 (104) — Checkbox vs radio vs dropdown
- **Plusieurs choix → checkboxes ; un seul → radio ou select.** Empiler **verticalement** (pas horizontalement) pour éviter les miss-clicks. Illustr. : dropdown « Services » remplacé par 3 checkboxes empilées (Website design, Branding ✔, Mobile design ✔).
- Bon UX de formulaire = **réduire la friction** ; saisie pénible → hausse du taux d'abandon.
### p.106 (105) — Longueur des champs & placeholders
- **Largeur du champ ≈ longueur attendue de la saisie** ; **placeholders descriptifs du format** : « Name on Card », « XXXX - XXXX - XXXX - XXXX », MM / YY, « *** » (CVC court à côté de la date).
- Formulaires compacts : regrouper des champs côte à côte, **supprimer l'inutile** (« a-t-on besoin du téléphone pour facturer un abonnement ? Non → supprimer »). Illustr. : 6 champs empilés (dont téléphone, MM et YY séparés) → 4 lignes compactes.
### p.107 (106) — Types d'input
- Champs dédiés : email, téléphone (sélecteur pays + drapeau), carte bancaire, upload… (Illustr. : email en textarea et message en champ simple 😡 → email champ simple, téléphone avec drapeau, message en textarea).
- Facilite aussi l'export des données (sheets). **Ne pas réinventer la roue**, se concentrer sur les vrais problèmes.
### p.108 (107) — Découper en étapes
- Beaucoup de champs → **multi-étapes** + indicateur de progression (« Step 2 of 3 », barre ou %).
- **Validation immédiate** par champ (coche verte), confirmation avant de continuer : case de confirmation, input surligné d'une autre couleur, ou **bouton Continue désactivé temporairement** (contraste suffisant + toast/snackbar d'instructions, ex. « Please, complete the form first. »).
- **États de succès** obligatoires (« You're all set! » + illustration + « Take me to the app! »).
### p.109 (108) — Accessibilité des formulaires
- Fond en dégradé + champs semi-translucides = « flex de designer » mais mauvais choix. **On ne design pas pour soi** : lunettes, malvoyance, troubles temporaires, manque de concentration.
- Illustr. login « Welcome back » : version claire lisible (bouton Login bleu plein, champs nets) vs version glassmorphism sombre peu lisible.
- Les utilisateurs ne remarquent pas vos effets ; ils peuvent même les distraire et **faire abandonner** inscription, achat, réservation.

## 4.3 Pricing
### p.111 (110) — Intro
- Une section pricing efficace exige tactiques marketing + **copywriting persuasif** : communiquer la valeur, construire la confiance, guider vers l'achat. Layout, hiérarchie, mots : tout a un sens.
- Exemple DesignMe : 2 cartes « AGENCY — Perfect if you need a senior designer — $6500/m » et « STARTUP+ [2x FASTER] — Perfect if you need a design team — $10450/m » ; CTA « Book a 20-min call » ; features avec icônes (violet = différenciantes) puis coches ; toggle add-on « No-code development +$1000 » vs « No-code included FREE » ; rareté : « Unavailable this month » / « 1 Spot left this month ».
- Ces pratiques relèvent du **CRO (conversion-rate optimization)**.
### p.112 (111) — Doubler les bénéfices / offrir un bonus
- On choisit toujours le plan le plus rentable ; offrir un essai d'un service plus cher pour fixer les attentes ; inclure gratuitement un add-on dans le plan haut (« No-code included FREE » vs « +$1000 »).
- Bannière sous les plans : « Interested in a One-Time Project only? Let's talk! » + « Book an intro call » (dégradé violet). **Résultat : +100 k$ de projets, tous transformés ensuite en retainers.**
- Essai gratuit/offre sans risque réduit la friction, mais **la valeur doit motiver l'achat, pas le prix**. Si des concurrents plus chers vendent plus → problème de valeur ; travailler le produit d'abord, puis réduire friction/objections.
### p.113 (112) — Mettre en avant le plan populaire
- Plusieurs plans = confusion → orienter vers le plan optimal (badge **POPULAR**, carte en **fond sombre inversé** + bouton violet) ; dire (en amont ou en FAQ) qu'on peut monter/descendre de plan.
- **Rareté** (disponibilité limitée) rend l'offre plus désirable — sans abus : les gens sentent le faux.
### p.114 (113) — Preuve sociale
- « Si tu as de la preuve sociale, utilise-la. Point. » (« si ça marche pour eux… »). Ex. : « Rated 5.0/5.0 by 14,439 readers from » + logos netguru, Panasonic, Nestlé, Toptal, Wix ; avatars.
- Logos d'entreprises réputées = message fort de qualité. Aussi : avis clients, trust badges, étoiles, notes — visibles et significatifs.
- Sans preuve sociale : **badges de paiement sécurisé** (Mastercard, PayPal, Apple Pay, « Lemon Squeezy & Stripe ») ou **logos de la stack « powered by »** (crédibilité par association).
### p.115 (114) — Sticky headers
- Long tableau comparatif → **en-tête de prix sticky** (Professional $300 / Enterprise $1250 / Enterprise-Elite $5000, toggle Monthly/Annually, fond vert pâle). Moins de scroll et de clics ; garder l'info importante au premier plan ; minimiser les étapes vers l'objectif.
### p.116 (115) — Psychologie des prix
- **Charm pricing** : $9.95, $9.99, $9 au lieu de $10.
- **< 100 $ : remise en %** (50 % sur 50 $ > « 25 $ off »). **Prix élevés (≈1000 $) : remise en montant** (« $200 OFF » > « 20 % OFF »). Illustr. : $999 barré → $799 vert.
- **Prix précis** ($245 plutôt que $250) = paraît calculé, plus crédible. Ex. @MrNick_Buzz : $4179 et $6317 — intrigue.
### p.117 (116) — Tooltips
- Réponses immédiates via tooltip (termes soulignés en pointillés dans le tableau) ; **flèche** pointant l'élément exact (tableaux denses) ; **au survol plutôt qu'au clic** (ex. « Tx Status : Increase a transaction's fee to increase its chances of being mined sooner. »).
### p.118 (117) — Mettre en avant le plan visé
- Colonnes séparées suffisent à distinguer, mais pour orienter : **carte plus grande, CTA différent (plein vs outline), bordure, tag** (« MOST POPULAR » vert). Ex. sur fond bleu nuit : $0 Free Version / **$99 PRO Version + Guide Bundle** / $199 PRO Bundle (Unlimited) ; features grisées pour ce qui n'est pas inclus.
- **Ne pas exagérer** au point d'éclipser les autres options et les rendre non pertinentes. Version 2 « Choose your bundle! As easy as 1, 2, 3… » : carte centrale surélevée, plus claire, seul CTA plein blanc ; autres CTA en outline.

## 4.4 Dropdowns
### p.120 (119) — Intro
- Dropdowns, FAQ, accordéons organisent le contenu. **Règle : plus de 5 choix → dropdown.** Compact sans casser le flux ; indispensable en formulaires et dashboards. Ex. « Filters ▾ / Sort by ▴ » : New Arrivals (surligné bleu pâle), Recommended, Price low→high, high→low, Highest rating.
- Économise l'espace en regroupant des options ; à utiliser quand les choix sont **prévisibles et listables**.
### p.121 (120) — Dropdown standard
- Un seul choix ; en-tête affichant la sélection ou un prompt (« Select an item ▾ ») ; s'étend au clic/tap ; chevron s'inverse ; item survolé surligné ; séparateurs possibles entre groupes.
- **Listes longues : conteneur scrollable** — afficher une **scrollbar** et **atténuer/couper le dernier item visible** pour signaler la suite.
### p.122 (121) — Multi-select
- Plusieurs choix (filtres, catégories, attributs). En-tête avec **compteur** (« Pizza toppings (3) », chiffre en bleu) ; checkboxes ; items cochés sur fond gris.
- Bonnes pratiques : **feedback visuel clair** des sélections, **moyen simple d'effacer**, **navigation clavier** (accessibilité).
### p.123 (122) — États
- **Default, Hover (bordure plus foncée), Open (chevron ▴ + liste), Selected (texte bleu + ✓ dans la liste), Disabled (grisé)** ; aussi active. Différencier par couleur, ombrage, icônes ; transitions fluides.
### p.124 (123) — Ombres et strokes subtils
- Sur fond blanc/clair, dropdown sans ombre ni bordure se confond 😡 → **ombre légère + stroke fin** 😎. Crucial en design minimaliste à faible contraste.
- Header de nav chargé : **un coin vif** (côté déclencheur) ou un **pointeur/flèche** pour montrer d'où sort le menu.
### p.125 (124) — Environnement focalisé
- Longue liste (ex. pays) sur mobile : le dropdown s'ouvre en **modal sheet plein écran avec barre de recherche** en haut (« Search » + « Cancel »), liste avec drapeaux, sélection encadrée. Idéal quand l'espace est limité.
### p.126 (125) — Raccourcis clavier
- Pour power users (mains sur le clavier). Ex. menu Figma multi-niveaux (File/Edit/View… → Pixel grid ⇧', Layout grids ⇧G, Rulers ⇧R…). Afficher le **raccourci aligné à droite** de chaque item (Undo ⌘Z, Redo ⇧⌘Z, Paste over selection ⇧⌘V, Paste to replace ⇧⌘R).
### p.127 (126) — Dropdowns imbriqués
- Hiérarchie pour options complexes sans submerger ; catégorie → sous-catégories (« Copy as ▸ » → Copy as text (désactivé), CSS, Copy as SVG, Copy as PNG ⇧⌘C).
- Chemin de navigation clair : **flèches ▸ ou indentation** signalent un niveau plus profond.

## 4.5 Navigation
### p.129 (128) — Intro & logo
- La nav = « ancre » de la page ; impacte temps passé, taux de rebond, conversions.
- **Logo en haut à gauche, cliquable → retour à l'accueil** (pattern connu) ; permet de retirer le lien « Home » redondant (illustr. : nav avec « Home » → sans, logo cliquable). Nav : liens + « Log in » (secondaire) + « Sign up » (noir plein).
### p.130 (129) — Contraste des liens
- Liens lisibles sur le fond de la nav (gris pâle illisible → noir lisible ; CTA grisé → noir plein). Respecter l'accessibilité.
- Fond **semi-transparent flouté** : utiliser un **blending mode** ou des **variantes de header** (clair/sombre) selon la section traversée (ex. header qui passe en version sombre sur la section noire « The guy behind designme »).
### p.131 (130) — Noms courts & CTA
- Liens **courts et simples** : « What we do / How expensive is this / What the FAQ? / About DesignMe / What others are saying » → « Services / Pricing / FAQs / About / Happy Clients ».
- CTA de nav distinct : **bouton**, ou séparateur, contraste ou graisse plus forte (« Contact / Start here » en liens → « Get started now! » en bouton noir, éloigné des liens).
### p.132 (131) — Trop de liens & hover
- Penser au plus petit écran desktop : **dropdowns, mega-menu, ou déplacer les liens secondaires dans le footer** (Legal, Terms and Conditions, Careers, Support, Become an affiliate).
- **Hover states** sur les liens : changement de couleur, soulignement, fond → indiquent l'interactivité.
### p.133 (132) — Active state & sticky
- Toujours montrer la position : **active state** (soulignement coloré sous « FAQs ») distinct du hover et du regular state.
- **Nav sticky** : accessible quel que soit le scroll ; surtout utile pour les **landing pages one-page** (zave.it).
### p.134 (133) — Profondeur pour header sticky
- Ombre légère ou flou pour l'élévation ; ou **stroke inférieur 0,5–1px** à peine contrasté ; ou **fond à 60 % d'opacité + blur 24** ; règle générale : **background blur 20–32 et fill du header 50–80 %**.

## 4.6 Search
### p.136 (135) — Intro & accessibilité
- Recherche efficace = critique (attention courte ; ex. chercher un réglage iPhone).
- Si l'app dépend de la recherche : **bien visible, en haut**, sans scroll. **Recherche globale** dans le header d'un dashboard = très utile (Kingdom Advisors : champ « Search » à côté des notifications et de l'avatar).
### p.137 (136) — Recherches récentes
- Anatomie annotée : **champ de recherche proéminent**, **bouton ⓧ pour effacer la requête**, **« Cancel » pour revenir au flux d'origine**, section « Featured Influencers », **« Recent searches »** avec **« Clear all »** (réinitialiser l'historique) et **« × » par requête**.
- Réduit la ressaisie et la **charge cognitive** ; personnalisation (le système se souvient des intérêts).
### p.138 (137) — Style des inputs
- Refléter l'esthétique : rayons libres (arrondis/carrés), strokes ou ombres subtils ; **bordures et fonds clairs** ; cohérence = identité de marque.
- Astuce : **coins arrondis parfaits pour chips et grilles** (amical, compact, attention sur le contenu). Chips de recherches récentes (UIUX, UI Design, User Experience).
- **Champs tappables ≥ 44px de haut**, bordures ou fonds définis pour se distinguer.
### p.139 (138) — Espace blanc & placeholder
- Plus d'espace autour du champ de recherche → ressort, moins de bruit (champ avec stroke + plus d'air avant « recent searches »).
- Placeholder **avec exemples/termes populaires** : « Search » → « Search guides, ebooks, and more… » (guide les nouveaux visiteurs).
### p.140 (139) — Autocomplete & page sans résultats
- **Autocomplétion** pendant la frappe, avec la partie complétée en gras (« UI design **for beginners** / **for advanced** / **handbook** ») → plus rapide, moins de frappe.
- **Page « no results » utile** : pas juste « We're sorry… » ; proposer suggestions, astuces, recherches populaires, résultats liés (« See 21 related search results for "design" and "advanced users" » + cartes).

## 4.7 Modals
### p.142 (141) — Intro & échappatoires
- Info au bon moment, guider les actions, réduire la complexité de navigation. **Réservés aux interactions critiques** (ou contexte utile) ; l'abus agace et casse le flux.
- **Contrôle utilisateur** : bouton **✕** bien visible, CTA clairs, **clic à l'extérieur pour fermer**. Anatomie : close button, illustration, titre + modal copy (« Welcome to our App! … free for the next 14 days »), action buttons (« View App » secondaire gris / « Open Guide » primaire noir).
### p.143 (142) — Responsive & progression
- Modal responsive : version desktop (horizontale, compacte) vs mobile (plus haute, illustration au-dessus, boutons « Learn more » / « Sounds great! »).
- **Indicateurs de progression** pendant les longues opérations (gère les attentes). Ex. iOS Face ID : modal de scan puis « Try Face ID Again / Cancel ».
### p.144 (143) — Erreurs & actions irréversibles
- Pas toutes les erreurs en modal : **inline ou notifications** souvent mieux.
- Modal de confirmation pour actions lourdes (supprimer compte/données, gros achat) : « Deactivate account — Are you sure…? » **Cancel (outline) / Deactivate (rouge plein)**.
- **Éviter les doubles négations** (« Are you sure you don't want to keep your account? » → « No » = confus) ; labels **Yes/No = confus** → verbes liés à l'action.
### p.145 (144) — Tâches complexes
- Modal multi-étapes sans quitter la page (« Import Orders » : onglets Upload CSV → Check data → Confirm import ; zone drag & drop « Drag and drop file here or Choose file — Only certain file types are allowed » ; Cancel / Continue désactivé) ; étape de confirmation explicite = contrôle.
- **Indicateurs de progression dans les modals** = sentiment d'avancement. Mais si le modal ajoute beaucoup d'étapes, chercher à collecter l'info **sans casser le flux**.

## 4.8 Hero sections
### p.147 (146) — Intro & above the fold
- Hero = susciter assez d'intérêt pour rester, collecter des leads, vendre ; donne le ton, message central, 1re impression.
- **Above the fold doit contenir : 1) proposition de valeur unique ; 2) raison de faire confiance ; 3) principaux bénéfices produit/service ; 4) l'action à faire.**
- Exemple SmartBank : titre « Improve the way you pay, with one click », 3 bénéfices à puces cochées, CTA « Learn more » / « Get started », avatars + « Rated 5.0/5.0 by 1,500+ users ★★★★★ », mockups iPhone à droite.
### p.148 (147) — Hiérarchie : F vs Z
- **F-pattern** : heroes riches en texte, infos/CTA alignés à gauche. **Z-pattern** : mix visuels forts + texte, éléments centrés.
- **Aligné à gauche** : scanné plus facilement (lecture gauche→droite), on lit plus de texte → infos détaillées, storytelling.
- **Centré** : plus équilibré, esthétique, point focal → message court et fort/CTA ; bon pour scan rapide, pas pour lecture intensive ; impact visuel. (En centré, les bénéfices passent en ligne sous le mockup.)
### p.149 (148) — Titres clairs et accrocheurs
- Compréhensible **en quelques secondes**, pas de jargon, langage simple ; jouer sur l'émotion (excitation, curiosité, confiance).
- « Improve the way you pay, with one click » = **pas clair** → « **Simplify Your Savings, Secure Your Future.** » (= « cette app m'aide à simplifier l'épargne pour un futur plus sûr ») : bénéfice immédiat + long terme → connexion émotionnelle.
### p.150 (149) — CTA
- Visuellement distinct ; langage orienté action, urgence ou bénéfice : « Start A Free Trial », « Get started now », « Become a member » ≫ « Click Here » / « Submit ». Ex. « Get Started Free ».
- Astuce : ajouter **« Now » / « Today »** pour l'urgence.
- Placement là où l'utilisateur navigue naturellement ; taille visible sans écraser ; accessible ; **ne pas multiplier** les CTA principaux (un seul action la plus désirable).
### p.151 (150) — CTA secondaires
- Chemins alternatifs moins dominants, placés près du primaire (« ▶ Watch Demo » fond gris clair à côté de « Get Started Free » noir).
- Style distinct : couleurs plus subtiles ou **bordure fine sans fond**. Le **CTA de la nav** (« Get the App », outline) doit aussi se distinguer des CTA primaire et secondaire du contenu → hiérarchie claire : primaire (noir) → secondaire (gris) → nav (outline).
### p.152 (151) — Visuels pertinents
- Mockup produit, image, composition, vidéo : fixent le ton et les attentes ; mockup mid-fi pour illustrer la transformation/les bénéfices. Ex. : **logo agrandi en fond (« blown-out logo »)** + mockups produit.
- Visuels alignés sur l'identité (couleurs, typo, imagerie) et **responsive** (version mobile : mockup au-dessus, texte centré, CTA pleine largeur empilés).
### p.153 (152) — Preuve sociale dans le hero
- **Nombre d'utilisateurs, notes, nombre d'avis** (« Rated 5.0/5.0 by 1,500+ users ★★★★★ » + rangée d'avatars ; « Trusted by 5,000+ designers »).
- **Logos de partenaires/clients connus** (« students from » Coca-Cola, Intel, Apollo.io, netguru, Panasonic, Nestlé, Toptal) → crédibilité empruntée.
- **Garanties** (satisfait ou remboursé, essai gratuit) → moins de risque perçu.
- Preuve sociale **pertinente et authentique**, sinon effet inverse.
### p.154 (153) — Suggérer la suite (teasing continuation)
- Indiquer qu'il y a plus sous la ligne de flottaison : flèche vers le bas, **section qui dépasse du bas de l'écran** (bloc sombre « What is this section about? »), image/titre coupé à mi-hauteur → curiosité.
- Exemple annoté Figma Mastery : « Master Figma in hours » — **titre clair + callout**, **plus de preuve sociale** en haut (« from the creator of… »), **hiérarchie de boutons** (Enroll primaire / View Curriculum secondaire), **preuve sociale** (avatars + note), **vidéo coupée en bas** (« Should I click to play? »), surlignage (« What is this highlight? »).
### p.155 (154) — Récapitulatif above the fold
- Titre accrocheur, simple, direct · visuels reflétant la marque · **CTA principal proéminent, persuasif, fort contraste** · **CTA secondaire pour visiteurs moins engagés** · **preuve sociale forte** · patterns **F ou Z** pour guider l'œil, alignement stratégique.
- « On n'a qu'une chance de faire une première impression. » Beau ET fonctionnel.

## 4.9 UI Cards
### p.157 (156) — Intro & anatomie
- Cartes = aperçu compact et digestible (produits, articles, profils).
- **Anatomie : card container, thumbnail, card title, supporting text, action button(s)** ; en général header (titre/icône), zone de contenu (texte/image), footer (boutons/liens). Composant universel, layout selon la catégorie de contenu.
### p.158 (157) — Longueur idéale
- Équilibre : trop = surcharge, trop peu = pas assez de valeur. Titres courts et percutants, descriptions brèves (on scanne les cartes).
- Grille multi-colonnes → contenu plus court ; une colonne (mobile) → plus long acceptable. Contenu dynamique → **tronquer avec « … »** (description de 6 lignes → 2 lignes + « Read more → »).
### p.159 (158) — Cohérence entre cartes
- Plusieurs cartes = longueurs cohérentes (titres de 3, 1, 2 lignes = désordre). **Tronquer titres/descriptions avec « … »** + **tooltip au survol** pour le texte complet, ou **fill height** sur tous les conteneurs.
- Hauteurs **min/max fixes** pour le contenu → layout prévisible, facile en CSS.
### p.160 (159) — Hiérarchie visuelle
- Typo + espacement : **titre proéminent (gras, foncé)** puis description plus claire, lien « Read more → » coloré (avant : tout de même graisse/gris → après : titre bold, lien bleu).
- Espace blanc **cohérent dans et entre** les cartes (grille 3×2 propre).
- Images : **qualité, style et dimensions cohérents** ; recadrer au même format/ratio.
### p.161 (160) — CTA de cartes
- Clairs, visibles, distincts : « Read more → » (lien), « Add to Cart » (bouton bleu pleine largeur sous prix « Sport Shoes 2.0 $49.90 » + ♡), « Decline » (rouge) / « Accept » (bleu) sur carte de demande d'ami.
- Taille tappable sans écraser le contenu ; **en bas de la carte** (fin naturelle de lecture). **Desktop : états hover et active** (ex. image assombrie/teintée + curseur main au survol).
### p.162 (161) — Layout & style
- Orientation **horizontale (grilles)** ou **verticale (listes, image à gauche)**.
- Style : **bordure** (définit les bords), **coins arrondis** (plus doux, moderne), **ombre** (pop sur fonds clairs) ; avec modération. Comparatif : no effects / + border / + shadow.
### p.163 (162) — Espacements des cartes (chiffres clés)
- **Padding interne 16–24px** ; **horizontal 12–20px**, **vertical 4–8px de plus** pour l'équilibre optique (schéma : 16 latéral, 24 haut/bas, 16 entre image et titre, 24 avant le bas).
- **16–40px entre cartes** ; **64–96px** de padding haut/bas de la section de cartes.
- Schéma desktop : marges **100** / cartes **300** / gutters **20** / 300 / 20 / 300 / 100.
### p.164 (163) — Types : blog & produit
- **Blog posts** : résumé d'article incitant au clic (image, titre, extrait, Read more).
- **Product cards** : e-commerce, image, prix, notes (« Generic Hand Cream Bottle $24.90 » + description).
### p.165 (164) — Information & status cards
- **Information cards** : infos bite-size pour dashboards (Bounce rate 61,6 %, Session duration 2:42 min, Total revenue $3,421 +4.58 % en badge vert, Total expenses $1,121 −5.29 % rouge, Traffic score 86.42 avec jauge, sparklines, « see details »).
- **Status cards** : processus longs (« Payment processing — Please wait… » + barre de progression ; succès « Congratulations! You've been paid by a Client » + « Go to Payments »).
### p.166 (165) — Avis & pricing cards
- **Reviews/testimonials** : photo, nom, citation (note 4.95/5 sur 120 évaluations avec histogramme 5★ 95 %, 4★ 3 %… ; avis avec étoiles ; carrousel de témoignages avec guillemets, nom, rôle).
- **Pricing cards** : options claires et comparables (Advanced Plan 10000 unique visitors/mo $49.95 ; Pro Plan Unlimited $59.95 ; « Choose package! » + « Learn more »).

## 4.10 Style guides
### p.168 (167) — Intro
- Style guide UI = référence pour l'équipe à chaque sprint ; esthétique globale ; montrer au moins les composants importants en usage ; définit typo, couleurs, layout.
- Exemple SmartBank LP : **Color palette** (Primary violet, Secondary vert-jaune, Dark BG, Light BG, White, Black) ; **Tonal palette** (Primary / Second / Dark, du 50 au 900) ; **Layout** (« SM desktop = 1440×1024 », Desktop grid 12 colonnes, marges latérales…).
### p.169 (168) — Typographie
- Polices de **Fontshare** (gratuites usage perso et commercial). Paire : **Satoshi → display & headlines ; Inter → callouts & body text**.
- **Type scale** = clé de la hiérarchie ; références : **HIG (iOS), Material Design (Android/mobile), Tailwind CSS (desktop)**.
- Échelle exemple (Avenir Next + Inter) : **display/d1 72 SemiBold · d2 64 · headline/h1 56 · h2 48 · h3 40 · h4 32 · h6 20 SemiBold · sub headline 20 Regular · title 18 SemiBold · menu 16 SemiBold · body large 16 Medium · body small 14 Medium · button large 16 Bold · button small 14 Bold**.
### p.170 (169) — Où trouver les échelles
- Web/Android : **générateur de type scale Material** (m3.material.io/styles/typography/type-scale-tokens) — redimensionne n'importe quelle police selon les règles de lisibilité Material.
- iOS : **HIG Dynamic Type** (xSmall → xxxLarge). Taille par défaut **Large** : Large Title 34/41 Regular · Title 1 28/34 · Title 2 22/28 · Title 3 20/25 · **Headline 17/22 Semibold** · **Body 17/22** · Callout 16/21 · Subhead 15/20 · Footnote 13/18 · Caption 1 12/16 · Caption 2 11/13 (taille/leading en points).
### p.171 (170) — Espacements & UI kits
- Valeurs prédéfinies : **min 8px puis multiples** selon poids visuel et proximité : **8, 16, 24, 32, 48, 64, 80**.
- UI kits : longtemps contre, mais vitesse/efficacité (petites équipes, freelance). Favoris : **Relume Library** (Figma/Webflow), **Untitled UI** (Jordan Hughes, kit Figma préféré), **AlignUI** (dashboards), **UI8** (assets), **Freepik** (icônes, images, vecteurs), **Craftwork** (templates Framer, fonts, 3D).
### p.172 (171) — Couleurs principales & documentation
- Base : **≥1 primaire, parfois une secondaire, des gris, noir et blanc**. Palettes tonales via plugins **Foundation: Color Generator** ou **Material Theme Builder** (rampes 50→900 : neutres, Primary bleu-pétrole, Secondary jaune-vert ; + shadows, blurs).
- **Tout documenter** : couleurs, typo, imagerie, iconographie, grilles, ombres, blurs, graphismes. **Nommer** couleurs et text styles (conventions Material pour Android/Web, HIG pour iOS).
### p.173 (172) — Composants réutilisables
- Cohérence + dev simplifié. Bouton Primary (violet) : Default / Hover / Disabled / Pressed ; Secondary (outline) mêmes états.
- **Atomic design** : atomes → molécules → templates, sections, pages (image + titre + prix + bouton → carte produit → section « Shop latest collection »). Réutiliser boutons, titres, cartes, formulaires, sections CTA.
### p.174 (173) — Component library
- Un composant par élément dans une bibliothèque : modifier le composant principal = mise à jour partout. Optionnel mais accélère et aligne l'équipe ; travail initial rentabilisé.
- Ex. Fintech UI Kit : « Organisms » → Containers (Method of verification, Transaction is being processed, Account, Informational text, List of banks, Bank details, Privacy toggles, Requirements, Card, Help issue, Transaction status, Transactions…), Insights (Charts, Earnings breakdown, Calendar), Account cards, Lists.
- iOS/Android : **partir des composants système** et les modifier (kits iOS / Material gratuits de la Figma Community) → devs reproduisent plus facilement.

---
# CHAPITRE 5 — PRACTICE MAKES PROGRESS
## 5.1 Bad vs Good UI (analyse des premiers designs de l'auteur)
### p.176 (175) — Intro
- Comparaison : app « Adventure » (ses débuts : fond photo sombre, serif, éléments flottants) « why this is not good? » vs app zave.it (« and this is acceptable? »).
- Citation (Michael Filipiuk) : on sait reconnaître un bon design sans savoir le reproduire parce que **le goût est plus développé que les compétences**.
### p.177 (176) — Erreur 1 : pas d'alignement
- Sans grille ni incréments : éléments « flottants », largeurs et marges latérales différentes (lignes de guides irrégulières vs marges nettes et constantes sur zave.it).
- Aligner = **ancres visuelles**, scan facile, moins de charge cognitive. La grille apporte équilibre et ordre ; les humains aiment symétrie et équilibre (apaisant).
### p.178 (177) — Erreur 2 : espacements aléatoires
- Mauvais : 28 / 18 / 21 / 14 / 20 pt (non divisibles par 4) → encombré, inégal, sans hiérarchie. Bon (zave.it) : 16 / 20 / 16 / 20 / 20 / 16 pt.
- **Plus d'espace autour des éléments importants**, moins autour des secondaires → repérage rapide. **8px = plus petit incrément**, augmenter pour distinguer l'important. Crucial sur mobile.
### p.179 (178) — Erreur 3 : pas d'échelle typographique
- Texte = avec espace et couleur, l'outil n°1 de hiérarchie. Ex. tailles relevées : 12, 13, 13, 18, 20, 20, 18, 13, 14, 13, 14px → trop de tailles proches. Consulter **HIG (iOS)**, **Material/Tailwind (Android/Web)**.
- L'échelle garantit cohérence (aspect pro), tient compte de la lisibilité selon taille/distance, et **accélère les décisions**.
### p.180 (179) — Erreur 4 : trop créatif
- Débutant = tout montrer sur un écran → encombré. Critique annotée de « Adventure » : « what's the hamburger for? », « waste of space above », « is heading really needed here? », « why add search here and not on tab bar? », « uneven spacing », « text is way too small », « profile page and an avatar — why both? » (redondances).
- **Le grand design UI : combien on peut retirer sans perdre de fonctionnalité.** Identifier les features cœur ; le reste est secondaire et peut nuire.
### p.181 (180) — Erreur 5 : manque de cohérence
- Sans approche unifiée → décousu, non professionnel. Solution : **style guide** (couleurs, texte, imagerie) appliqué aux composants.
- Exemple app influenceur (3 écrans) annoté : **tailles de police cohérentes, palette unifiée (noir/blanc), espacements cohérents, boutons cohérents (pilule noire), composants système (clavier iOS)**.
- Démarche : quelques polices alignées sur la personnalité de marque → palette adaptée à la cible → standardiser boutons, formulaires, composants → documenter → créer des composants réutilisables.
### p.182 (181) — Erreur 6 : contraste ignoré
- « Adventure » : contraste trop faible, texte illisible 😡 ; « The app » : **contraste min 4.5:1** 😎. Ne rien supposer, suivre les standards.
- Checklist accessibilité : **AA suffit pour le digital** ; **cibles 44×44px iOS, 48×48px Android & web** ; plugin **A11y Contrast Checker** ; **formulaires et navigation utilisables au clavier** + **états focus** dessinés.
- Les designers sous-estiment le contraste, surtout dans les dark modes « fancy » partagés en ligne.
### p.183 (182) — Erreur 7 : suivre de mauvais exemples
- Beaucoup d'« experts » autoproclamés ; vérifier **portfolio et expérience réelle** de ceux qu'on écoute (l'auteur a perdu argent et temps).
- Crédentials de l'auteur : designs livrés à **30M+ utilisateurs**, refonte de la plus grande app d'investissement UK, app shopping n°1 en Allemagne (plus gros lancement de l'histoire du pays, **4.9 par 5500+ utilisateurs**). Ne pas dépendre d'une seule source. Design Manual : 6 mois de travail avec sa femme.
### p.184 (183) — Design Manual & alternatives gratuites
- Design Manual : **770+ pages** (iOS/Android), app Fintech complète, templates de framework, Practice File pour répliquer l'app ; flows mobiles populaires ; orienté pratique.
- **Alternatives gratuites pour s'entraîner : mobbin.com, land-book.com, refero.design.**

## 5.2 Practicing UI
### p.186 (185) — Théorie vs pratique
- La théorie donne les règles ; la pratique apprend à les appliquer (forme/fonction, œil du détail, interaction). Maîtrise = créer, expérimenter, itérer.
- Illustration : écran « Transfer » avec cotes : **24px** (header→segmented), **36px**, **80px** (bloc compte), **56px** (champ destinataire), **16px** entre champs, **48px** (bouton Continue), **40px** (marge bas).
### p.187 (186) — Tracer des designs
- Capturer des écrans d'apps/sites admirés (gratuit, simples screenshots), les poser sur l'artboard, **opacité ~20 %, verrouiller le calque, retracer composant par composant**.
- Développe l'œil pour typo, couleurs, flux ; comprendre comment les pros résolvent les problèmes courants.
### p.188 (187) — Défi : répliquer à côté
- Screenshot **à côté** de l'artboard (pas dessous) + guides horizontaux → décider soi-même espacements, tailles, alignements ; plus proche de la création originale.
- Grille d'analyse critique annotée (écran « Order a card ») : « Why is the title below the navigation? », « Tabs are iOS segmented buttons », « Label has stronger contrast », « Descriptions are greyed out », « Cards have arrows to indicate action », « Is this an ad I can turn off? », « Close button has low contrast — dark UX? », « Where will this button take me? ».
### p.189 (188) — Analyse approfondie
- Comment le design résout le problème utilisateur ; **ordre de lecture** (1er, 2e, 3e…) ; rôle de taille, couleur, contraste, placement. Ex. onboarding SmartBank numéroté : 1 titre « Spend smarter every day, all from one app. », 2 visuel/graph, 3 CTA « Sign up » / « Log in » ; écran email : 1 titre, 2 champ, 3 clavier, 4 mention légale + Continue.
- Étudier espacements et marges → apprendre la grille de 8px.
### p.190 (189) — Copywriting & volume
- Analyser le **copywriting** (clarté, ton, cohérence avec le visuel) — « plus tôt on apprend à écrire, mieux c'est ».
- **Répliquer 10, 20, 100 écrans** → bibliothèque mentale de patterns ; vitesse, raccourcis, maîtrise des outils, adaptabilité aux styles, confiance.
### p.191 (190) — Où trouver de bons exemples
- Les mauvais conseils et les visuels « flashy » (style > substance) faussent la compréhension. Tendance à surcharger de visuels → noie le message ; le contenu et sa communication priment.
- **Twitter/Instagram** valorisent des designs faits pour plaire aux designers, pas utilisables. « Good design is not just about how things look; it's about how they work. » Chaque élément doit avoir un but.
- Sources réalistes : **Mobbin, Refero, Land-book, Onepagelove, Saaslandingpages**.
### p.192 (191) — Design Manual (promo)
- Extrait de tutoriel : champs d'input espacés **24px** du texte, auto-layout (Shift+A), dupliquer (Cmd/Ctrl+D), champs 56px, 16px entre champs ; bouton Continue variante Disabled, **40px** au-dessus (grille 4pt) et **16px** au-dessus du clavier iOS. 400+ pages iOS/Android, 100 écrans Fintech expliqués, plan de 100 jours.
### p.193–197 — Promo & fin
- Ultimate Guide to Web Design : 340 pages, 6 parties, 33 chapitres (freelance, bases, web, process, no-code, handoff ; process de site à 10 000 $). Agence relancée : 100 k$ en 6 mois ; 80 k$/mois avec 7 clients et 5 designers ($30k MRR mentionné ailleurs).
- Figma Mastery : ~11 h, jusqu'à une landing responsive ; mise à jour (variables, logique conditionnelle, Figma→Framer).
- Ebook « ever-evolving », chapitres ajoutés régulièrement ; pas de chevauchement avec les autres produits (1100+ pages). Contact hello@uiadrian.com.

---
# SYNTHÈSE — RÈGLES ET CHIFFRES CLÉS (aide-mémoire)

## Frames & grilles
| Contexte | Valeur |
|---|---|
| Frame mobile de départ | iPhone 13 Mini 375×812 / Android Small 360×800 (toujours partir du plus petit) |
| Grille mobile | 4 colonnes, marges ≥16px (souvent 20), gutters 8px |
| Frame web | 1440×1024 (Framer : 1200×1024) ; tester 1920 |
| Grille desktop | 12 colonnes, marges 100px, gutters 20px → safe zone 1240px (3×400 ou 4×295) |
| Box widths | min 1200px, max 1920px+ ; au-delà → max-width (ex. 1920) |
| Fluide | marges 5–10 %, contenu 80–90 % |
| Système d'espacement | multiples de 8 (4 pour détails fins ; 5 seulement avec Bootstrap) : 8,16,24,32,48,64,80 |

## Espacements de référence
- Titre↔description 8–20px ; groupes texte↔icônes/boutons 20–40px ; padding conteneur 12–20px+ (sections 20–40px) ; marges min 16–20px.
- Cartes : padding 16–24px (horizontal 12–20, vertical +4–8), 16–40px entre cartes, 64–96px autour des rangées de cartes.
- Header sticky : stroke bas 0,5–1px, ou fill 50–80 % + background blur 20–32 (ex. 60 % + 24).

## Accessibilité & cibles tactiles
- Contraste : petit texte 4.5:1 (AA) / 7:1 (AAA) ; grand texte (≥19–24px) 3:1 (AA) / 4.5:1 (AAA) ; boutons & inputs 3:1 ; couleurs système idéalement 7:1. AA suffit pour le digital.
- Cibles : 44×44 iOS, 48×48 Android/web ; zone tappable invisible ≥40–44px même pour liens et items de liste ; champs ≥44px de haut.
- Clavier : formulaires/nav navigables, états focus visibles.

## Boutons
- Label 14–20px (ex. 14–17px, line-height 22px+) ; padding H ≈ 2× V (16px+ / 10px+) ; hauteur 32–60px (mobile ≥44–48, desktop 32–40) ; mobile min 48×48, desktop ≈164×48.
- Hiérarchie : primaire plein → secondaire outline (ghost) → tertiaire lien (souligné). Ordonner du plus au moins important.
- États : normal, hover, active/pressed, focused, disabled, loading — distincts mais subtils.
- Libellés verbe+résultat (« Cancel / Delete », pas « No / Yes » ; jamais « Click here ») ; « Now/Today » pour l'urgence.
- Icône à gauche = aide au scan ; à droite = destination de l'action.
- Mobile : CTA dans la zone du pouce, actions destructrices/interruptions hors de portée.
- Arrondi = friendly/ludique ; carré = sophistiqué/minimaliste/structuré.

## Ombres (recettes Figma)
- Douce : #000 4 % x0 y10 b15 ; plus marquée : #000 10 % x0 y15 b20 ; contact : + #000 15 % x0 y2 b4.
- Teintée : couleur du bouton à 20 % x0 y15 b20. Brutaliste : stroke 2px #000 + ombre 100 % x4 y4 b0.
- Stroke subtil : 1px #898989 à 20 %. Inner shadow : #FFF 100 % x−4 y2 b10 ; ou couleur 48 % x0 y6 b19.
- Une seule source de lumière ; sur fond sombre : halo clair ou ombres empilées à forte opacité. Plugin Beautiful Shadows.

## Couleurs
- 1 primaire (+ tints/shades), neutres, 1 accent ; règle 60-30-10. Teinter gris/noirs/blancs avec la primaire (overlay 5–15 %).
- 3 couleurs système min : rouge erreur, orange warning, vert succès.
- Concevoir d'abord en niveaux de gris. Palette tirable des images. Adapter la tonalité des photos. Attention aux significations culturelles.
- Psychologie : bleu confiance (finance/santé), vert croissance (bien-être), rouge urgence (alertes, parcimonie), jaune optimisme, orange convivialité CTA, violet luxe/créativité (galvaudé), noir élégance, blanc simplicité.

## Dégradés
- Teintes voisines sur le spectre ; ajouter des stops intermédiaires ; resserrer les stops vers une extrémité ; radial : stop glissé vers l'intérieur ; overlay radial 100→0 % ; ajouter du grain ; layer blur = source de lumière.

## Formulaires
- Labels toujours visibles (ou floating labels) ; marquer « (optional) » plutôt que des astérisques ; largeur de champ = longueur attendue ; placeholders de format ; bons types d'input ; checkboxes (multi) vs radio/select (unique), empilés verticalement ; erreurs inline rouges + icône + texte explicite ; multi-étapes avec progression ; validation immédiate ; état de succès ; supprimer les champs inutiles ; pas de glassmorphism illisible.

## Dropdowns
- >5 choix → dropdown ; listes longues scrollables (scrollbar + dernier item coupé) ; multi-select avec compteur, clear, clavier ; états default/hover/open/selected/disabled ; ombre + stroke sur fond clair ; coin vif/pointeur depuis la nav ; mobile : modal sheet avec recherche ; raccourcis clavier ; sous-menus avec ▸.

## Navigation
- Logo cliquable en haut à gauche ; liens courts ; CTA en bouton distinct ; contraste (variantes sur fonds sombres) ; trop de liens → dropdown/mega-menu/footer ; hover + active states ; sticky (landing one-page) avec ombre/stroke/blur.

## Search
- Visible en haut (recherche globale) ; recherches récentes (Clear all, × par item) ; bouton effacer + Cancel ; placeholder avec exemples ; autocomplétion (complément en gras) ; page « aucun résultat » avec alternatives ; champs ≥44px, coins arrondis pour chips.

## Modals
- Réservés au critique ; ✕ visible + clic extérieur + CTA clairs ; responsive ; indicateurs de progression ; confirmation des actions destructrices (bouton rouge, verbe d'action, pas de double négation) ; erreurs mineures inline ; multi-étapes avec progression sans casser le flux.

## Hero / above the fold
- Contient : proposition de valeur, raison de confiance, bénéfices, action attendue.
- F-pattern (gauche, texte) vs Z-pattern (centré, visuel). Titre compris en secondes, émotionnel, bénéfice présent + futur.
- 1 CTA primaire contrasté + 1 secondaire subtil (+ CTA nav encore distinct). Preuve sociale (note, nb d'utilisateurs, logos, garanties). Visuels de marque responsive. Suggérer la suite (section qui dépasse, flèche, image coupée).

## Pricing (CRO)
- Mettre en avant le plan visé (taille, badge POPULAR, fond inversé, CTA plein) sans écraser les autres ; rareté honnête ; bonus/add-on offert ; offre one-shot ou essai ; preuve sociale, badges paiement, logos « powered by » ; header sticky dans les comparatifs ; tooltips au survol ; charm pricing ($9.99), % sous 100 $, montant au-dessus, prix précis ($245) ; la valeur prime sur le prix.

## Cartes
- Anatomie : conteneur, thumbnail, titre, texte, actions. Contenu concis, troncature « … » + tooltip, hauteurs min/max ; hiérarchie typo ; images au même ratio ; CTA en bas, hover/active sur desktop ; grille ou liste ; bordure/ombre/rayon avec modération. Types : blog, produit, info (dashboard), statut, avis, pricing.

## Style guide / design system
- Fontshare (Satoshi titres + Inter texte) ; échelles HIG / Material / Tailwind ; HIG Large : Body 17/22, Headline 17/22 Semibold, Large Title 34/41… ; palette primaire/secondaire/gris/noir/blanc en rampes 50–900 (Foundation Color Generator, Material Theme Builder) ; tout documenter et nommer ; composants réutilisables et atomic design ; bibliothèque de composants ; partir des kits système iOS/Material. UI kits : Relume, Untitled UI, AlignUI, UI8, Freepik, Craftwork.

## Process & apprentissage
- Grayscale d'abord, puis couleur. « Less is more » : retirer tant que la fonction reste ; tester la simplicité en vue mobile.
- 7 erreurs de débutant : pas d'alignement, espacements aléatoires, pas d'échelle typo, trop de créativité, incohérence, contraste ignoré, mauvais mentors.
- Pratique : tracer (screenshot à 20 %, verrouillé) → répliquer à côté avec guides → analyser hiérarchie, espacements, copywriting → répéter 10/20/100 écrans. Sources : Mobbin, Refero, Land-book, Onepagelove, Saaslandingpages (pas Instagram/Twitter).
