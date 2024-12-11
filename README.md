# TCS_UNITE_SH

This is an example implementation of the [Taxon Concept Standard](https://github.com/tdwg/tcs2/tree/master/docs/tcs-terms) (TCS) applied to UNITE](https://unite.ut.ee) Taxon Hypotheses — a unified system for the DNA based fungal species linked to the classification.


## Example (JSON-LD)

GBIF record link - https://www.gbif.org/species/227690399/verbatim

[[example-1.jsonld]](https://github.com/kessya/TCS_UNITE_SH/blob/main/examples/example-1.jsonld) SH0089686.10FU (3.0%) => SH0867949.10FU (1.5%) => SH1220176.10FU (1.0%)

```json
{
  "@context": [
    "https://raw.githubusercontent.com/tdwg/tcs2/master/examples/context.jsonld",
    {
      "skosxl": "http://www.w3.org/2008/05/skos-xl#"
    },
    {
      "verbatimTaxonRank": "https://unite.ut.ee/terms/0.1/distance"
    }
  ],
  "@graph": [
       {
      "id": "https://dx.doi.org/10.15156/BIO/SH0089686.10FU",
      "type": "TaxonConcept",
      "dcterms:title": "SH0089686.10FU",
      "taxonName": {
        "type": "skosxl:Label",
        "skosxl:literalForm": "SH0089686.10FU"
      },
      "taxonRank": "genus",
      "accordingTo": {
        "@id": "https://unite.ut.ee"
      },
      "verbatimTaxonRank": "3.0",
      "isIncludedIn": {
        "@id": "https://doi.plutof.ut.ee/doi/10.15156/BIO/TH100177",
        "accordingTo": {
          "@id": "https://unite.ut.ee"
        }
      },
      "children": [
        {
          "@id": "https://dx.doi.org/10.15156/BIO/SH0867949.10FU",
          "accordingTo": {
            "@id": "https://unite.ut.ee"
          }
        }
      ]
    },
    {
      "id": "https://dx.doi.org/10.15156/BIO/SH0867949.10FU",
      "type": "TaxonConcept",
      "dcterms:title": "SH0867949.10FU",
      "taxonName": {
        "type": "skosxl:Label",
        "skosxl:literalForm": "SH0867949.10FU"
      },
      "taxonRank": "genus",
      "accordingTo": {
        "@id": "https://unite.ut.ee"
      },
      "verbatimTaxonRank": "1.5",
      "isIncludedIn": {
        "@id": "https://doi.plutof.ut.ee/doi/10.15156/BIO/TH100177",
        "accordingTo": {
          "@id": "https://unite.ut.ee"
        }
      },
      "parent": {
        "@id": "https://dx.doi.org/10.15156/BIO/SH0089686.10FU",
        "accordingTo": {
          "@id": "https://unite.ut.ee"
        }
      },
      "children": [
        {
          "@id": "https://dx.doi.org/10.15156/BIO/SH1220176.10FU",
          "accordingTo": {
            "@id": "https://unite.ut.ee"
          }
        }
      ]
    },
    {
      "id": "https://dx.doi.org/10.15156/BIO/SH1220176.10FU",
      "type": "TaxonConcept",
      "dcterms:title": "SH1220176.10FU",
      "taxonName": {
        "type": "skosxl:Label",
        "skosxl:literalForm": "SH1220176.10FU"
      },
      "taxonRank": "genus",
      "accordingTo": {
        "@id": "https://unite.ut.ee"
      },
      "verbatimTaxonRank": "1.0",
      "isIncludedIn": {
        "@id": "https://doi.plutof.ut.ee/doi/10.15156/BIO/TH100177",
        "accordingTo": {
          "@id": "https://unite.ut.ee"
        }
      },
      "parent": {
        "@id": "https://dx.doi.org/10.15156/BIO/SH0867949.10FU",
        "accordingTo": {
          "@id": "https://unite.ut.ee"
        }
      }
    },
    {
      "id": "https://doi.plutof.ut.ee/doi/10.15156/BIO/TH100177",
      "taxonName": {
        "id": "https://www.indexfungorum.org/names/NamesRecord.asp?RecordID=17175",
        "type": "TaxonName",
        "taxonNameString": "Boletus",
        "dwc:scientificNameAuthorship": "L",
        "dwc:namePublishedIn": "Sp. pl. 2: 1176",
        "dwc:namePublishedInYear": "1753",
        "dwc:taxonRank": "genus"
      }
    },
    {
      "@id": "https://unite.ut.ee",
      "@type": "bibo:Website",
      "dcterms:title": "UNITE: rDNA ITS based identification of Eukaryotes and their communication via DOIs",
      "bibo:uri": "https://unite.ut.ee"
    }
  ]
}
```


## Issues

**tcs:taxonRank**

According to [TCS 2](https://github.com/tdwg/tcs2/tree/master/docs/tcs-terms), the comments for the *taxonRank* term state that:

*"This property takes an object or IRI and it is recommended to use a value from an existing controlled vocabulary. While there is no TDWG vocabulary yet, the GBIF Taxonomic Rank Vocabulary (https://rs.gbif.org/vocabulary/gbif/rank.xml) is recommended.*

*A TaxonName takes its taxonRank from the taxonConcept it is applied to, so this property can also be used on a (stand-alone) TaxonName object."*

DarwinCore *verbatimTaxonRank* term allows to use taxonomic rank designations that are not in the controlled vocabulary which is used for *taxonRank* attribute:

*The taxonomic rank of the most specific name in the dwc:scientificName as it appears in the original record.*

From the UNITE perspective, for the DNA-based taxon hypotheses, we would like the option of using taxon ranks that reflect the methodology used to calculate these species hypotheses — in our case, the genetic distance between the two closest species hypotheses (e.g., 0.5%, 1.0%, 1.5%, 2.0%, 2.5%, or 3.0%). This issue could be addressed by incorporating distance values into the *verbatimTaxonRank* (as demonstrated in the example JSON-LD object), referring to the UNITE-associated metric.

**Taxonomic circumscriptions**

Taken from [TCS 2 feature report](https://github.com/tdwg/tcs2/tree/master/docs/feature-report):

*"The most significant thing that has been left out of TCS 2 for now is the circumscription or definition of taxa. TCS 1 has the CharacterCircumscription and SpecimenCircumscription elements, translated to DescribedBy and CircumscribedBy, respectively, in the TDWG Ontology. These have been left out of the initial release of TCS 2, because we are not aware of any systems using them and because it is not immediately apparent how they should be used, especially for CharacterCircumscription, or that they are the only and best way to express circumscription in TCS. Just because it is not included yet does not mean circumscription is not important. The TCS Maintenance Group has every intention of adding circumscription to TCS at a later stage in a separate effort. If we are to include circumscription in TCS, it should be done in a way that it is operational and computer-tractable. Lists of characters (or descriptions) and lists of specimens are better accommodated in other TDWG standards, like Plinian Core and SDD."*

The UNITE team is particularly interested in expressing the contents of taxon and species hypotheses - including specimen and sequence identifiers - as taxonomic circumscriptions that form part of taxon concepts. In the TCS XML schema, there are specific fields for circumscription based on a set of taxonomic descriptions (*CharacterCircumscription*) and for circumscription based on a set of specimens (*SpecimenCircumscription*), with individual records defined under *CircumscribedBy* element. We propose the following initial structure for specimen-based and sequence-based circumscriptions - 

**digitalSpecimenID**: New term to DwC proposed by the DiSSCo technical team - Digital Specimen Identifier: A persistent, FAIR Digital Object compliant, identifier for a Digital Specimen digital object on the internet.

```json
{
  "@context": [
    {
      "dwc": "http://rs.tdwg.org/dwc/terms/"
    }
  ],
  "@graph": [
    {
      "specimenCircumscription": [
        {
          "dwc:digitalSpecimenID": "https://doi.org/10.3535/M42-Z4P-DRD",
          "dwc:catalogNumber": "RMNH.ARA.18260"
        }
      ]
    },
    {
      "sequenceCircumscription": [
        {
          "dwc:associatedSequences": [
            {
              "url": "https://www.ncbi.nlm.nih.gov/nuccore/KY774023",
              "accessionNumber": "KY774023"
            },
            {
              "url": "https://unite.ut.ee/bl_forw.php?id=4671378",
              "accessionNumber": "UDB01535148"
            }
          ]
        }
      ]
    }
  ]
}
```
