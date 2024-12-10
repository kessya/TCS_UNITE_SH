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
