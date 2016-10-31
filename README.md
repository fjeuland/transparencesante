# transparencesante
pour l'analyse de la base de Transparence Santé accessible sur data.gouv.fr : https://www.data.gouv.fr/fr/datasets/transparence-sante-1/#discussion-1

un fichier pdf est présent pour décrire le contenu de l'archive mais a été d'une utilité modérée
trois tables sont présentes : Entreprise, Avantage & Convention

# Préparation de la base de donnée avec PostgreSQL

##Entreprise
--Créer la table tentreprises
--(fait manuellement dans ce cas)

--Importer le contenu du fichier
COPY tentreprise FROM '/share/MD0_DATA/.qpkg/PostgreSQL/web/TransparenceSante/entreprise_2016_10_24_04_00.csv' CSV HEADER DELIMITER ',';

##Convention
--Créer la table tconventions
CREATE TABLE tconventions (	
entreprise_identifiant	varchar,
denomination_sociale	varchar,
ligne_identifiant	varchar,
ligne_rectification	varchar,
benef_categorie_code	varchar,
categorie	varchar,
benef_nom	varchar,
benef_prenom	varchar,
benef_qualite_code	varchar,
qualite	varchar,
benef_adresse1	varchar,
benef_adresse2	varchar,
benef_adresse3	varchar,
benef_adresse4	varchar,
benef_codepostal	varchar,
benef_ville	varchar,
benef_pays_code	varchar,
pays	varchar,
benef_titre_code	varchar,
benef_titre_libelle	varchar,
benef_specialite_code	varchar,
benef_speicalite_libelle	varchar,
benef_qualification	varchar,
benef_identifiant_type_code	varchar,
identifiant_type	varchar,
benef_identifiant_valeur	varchar,
benef_etablissement	varchar,
benef_etablissement_codepostal	varchar,
benef_etablissement_ville	varchar,
benef_denomination_sociale	varchar,
benef_objet_social	varchar,
ligne_type	varchar,
conv_date_signature	varchar,
conv_objet	varchar,
conv_date_debut	varchar,
conv_date_fin	varchar,
conv_manifestation_date	varchar,
conv_manifestation_nom	varchar,
conv_manifestation_lieu	varchar,
conv_manifestation_organisateur	varchar
);

-- Importer le contenu du fichier convention
COPY tconventions (entreprise_identifiant,denomination_sociale,ligne_identifiant,ligne_rectification,benef_categorie_code,categorie,benef_nom,benef_prenom,benef_qualite_code,qualite,benef_adresse1,benef_adresse2,benef_adresse3,benef_adresse4,benef_codepostal,benef_ville,benef_pays_code,pays,benef_titre_code,benef_titre_libelle,benef_specialite_code,benef_speicalite_libelle,benef_qualification,benef_identifiant_type_code,identifiant_type,benef_identifiant_valeur,benef_etablissement,benef_etablissement_codepostal,benef_etablissement_ville,benef_denomination_sociale,benef_objet_social,ligne_type,conv_date_signature,conv_objet,conv_date_debut,conv_date_fin,conv_manifestation_date,conv_manifestation_nom,conv_manifestation_lieu,conv_manifestation_organisateur) FROM '/share/MD0_DATA/.qpkg/PostgreSQL/web/TransparenceSante/declaration_convention_2016_10_24_04_00.csv' CSV HEADER DELIMITER ';';

##Avantage
--Créer la table tavantages
CREATE TABLE tavantages (	
entreprise_identifiant	varchar,
denomination_sociale	varchar,
ligne_identifiant	varchar,
ligne_rectification	varchar,
benef_categorie_code	varchar,
categorie	varchar,
benef_nom	varchar,
benef_prenom	varchar,
benef_qualite_code	varchar,
qualite	varchar,
benef_adresse1	varchar,
benef_adresse2	varchar,
benef_adresse3	varchar,
benef_adresse4	varchar,
benef_codepostal	varchar,
benef_ville	varchar,
benef_pays_code	varchar,
pays	varchar,
benef_titre_code	varchar,
benef_titre_libelle	varchar,
benef_specialite_code	varchar,
benef_speicalite_libelle	varchar,
benef_qualification	varchar,
benef_identifiant_type_code	varchar,
identifiant_type	varchar,
benef_identifiant_valeur	varchar,
benef_etablissement	varchar,
benef_etablissement_codepostal	varchar,
benef_etablissement_ville	varchar,
benef_denomination_sociale	varchar,
benef_objet_social	varchar,
ligne_type	varchar,
avant_date_signature	varchar,
avant_montant_ttc	integer, --était varchar
avant_nature	varchar,
avant_convention_lie	varchar,
avant_conv_semestre	varchar
);	

-- Importer le contenu du fichier avantage
COPY tavantages (entreprise_identifiant,denomination_sociale,ligne_identifiant,ligne_rectification,benef_categorie_code,categorie,benef_nom,benef_prenom,benef_qualite_code,qualite,benef_adresse1,benef_adresse2,benef_adresse3,benef_adresse4,benef_codepostal,benef_ville,benef_pays_code,pays,benef_titre_code,benef_titre_libelle,benef_specialite_code,benef_speicalite_libelle,benef_qualification,benef_identifiant_type_code,identifiant_type,benef_identifiant_valeur,benef_etablissement,benef_etablissement_codepostal,benef_etablissement_ville,benef_denomination_sociale,benef_objet_social,ligne_type,avant_date_signature,avant_montant_ttc,avant_nature,avant_convention_lie,avant_conv_semestre) FROM '/share/MD0_DATA/.qpkg/PostgreSQL/web/TransparenceSante/declaration_avantage_2016_10_24_04_00.csv' CSV HEADER DELIMITER ';';
