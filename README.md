[README.md](https://github.com/user-attachments/files/22456651/README.md)
# 📘 Flightcase FWI – Base documentaire

Ce dépôt contient la **base documentaire textuelle** utilisée par le **Tool_Documents_Search** (via GitHub Document Loader + stockage PGVector).  
Il centralise toutes les informations nécessaires pour répondre aux questions des clients : **CGV, assurance, caution, coordonnées, infos légales, statuts, TVA, etc.**

---

## 📂 Fichiers

- `flightcase_documents_full.csv`  
  Table structurée avec les colonnes :  
  - `category` → Thématique (ex. Caution, Assurance, CGV, Coordonnées, Infos légales)  
  - `title` → Intitulé clair (ex. Franchise assurance, Montant caution standard)  
  - `content` → Texte exact issu des documents officiels (réponse exploitable)  
  - `source` → Document d’origine (ex. CGV.pdf, KBIS.pdf, Dépôt de garantie.docx)  

---

## 🔎 Exemple d’entrée

| category   | title                    | content                                                                 | source                           |
|------------|--------------------------|-------------------------------------------------------------------------|----------------------------------|
| Caution    | Montant caution standard | Un dépôt de garantie standard de 5000€ est exigé, par CB (Visa/Mastercard, pas Amex). | Dépôt de garantie.docx |
| Assurance  | Franchise assurance      | La franchise est de 15% du montant des dommages avec un minimum de 300€ HT. | Conditions Générales de Location.pdf |
| CGV        | Annulation ou report     | Toute annulation doit être notifiée 24h avant. Moins de 24h = facturation 10%. | Conditions Générales de Location.pdf |

---

## ⚙️ Utilisation

1. Le **GitHub Document Loader** lit ce fichier (`flightcase_documents_full.csv`).  
2. Chaque ligne est transformée en **document vectorisé** dans la table Postgres `documents`.  
3. Le nœud **Tool_Documents_Search** permet la recherche sémantique :  
   - Requête client → Embedding → Rerank → Retour de l’extrait exact.  

---

## ✍️ Mise à jour

- **Ajouter une info** :  
  Ajouter une nouvelle ligne dans le CSV avec les 4 champs (`category`, `title`, `content`, `source`).  
- **Modifier une info** :  
  Éditer la ligne concernée, en gardant la cohérence des champs.  
- **Supprimer une info** :  
  Supprimer la ligne correspondante.  

⚠️ Toujours utiliser le texte exact des documents Flightcase (CGV, KBIS, Statuts, etc.).  
⚠️ Ne jamais inventer d’informations.  

---

## 📌 Sources intégrées

- Conditions Générales de Location (PDF)  
- Dépôt de garantie (DOCX)  
- Extrait KBIS (PDF)  
- Avis de situation Sirene (PDF)  
- Statuts SASU Flightcase (PDF)  
- Numéro de TVA intracommunautaire (PDF)  

---
