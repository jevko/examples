# XML

A [phyloXML](http://www.phyloxml.org/examples_syntax/phyloxml_syntax_example_1.html) tree encoded with Jevko:

```
phyloxml[xmlns:xsi=[http://www.w3.org/2001/XMLSchema-instance] xmlns=[http://www.phyloxml.org] xsi:schemaLocation=[http://www.phyloxml.org http://www.phyloxml.org/1.10/phyloxml.xsd]
  phylogeny[rooted=[true]
    name[Alcohol dehydrogenases]
    description[contains examples of commonly used elements]
    clade[
      events[
        speciations[1]
      ]
      clade[
        taxonomy[
          id[provider=[ncbi]6645]
          scientific_name[Octopus vulgaris]
        ]
        sequence[
          accession[source=[UniProtKB]P81431]
          name[Alcohol dehydrogenase class-3]
        ]
      ]
      clade[
        confidence[type=[bootstrap]100]
        events[
          speciations[1]
        ]
        clade[
          taxonomy[
            id[provider=[ncbi]1423]
            scientific_name[Bacillus subtilis]
          ]
          sequence[
            accession[source=[UniProtKB]P71017]
            name[Alcohol dehydrogenase]
          ]
        ]
        clade[
          taxonomy[
            id[provider=[ncbi]562]
            scientific_name[Escherichia coli]
          ]
          sequence[
            accession[source=[UniProtKB]Q46856]
            name[Alcohol dehydrogenase]
          ]
        ]
      ]
    ]
  ]
]
```

original:

```
<phyloxml
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xmlns="http://www.phyloxml.org" 
  xsi:schemaLocation="http://www.phyloxml.org http://www.phyloxml.org/1.10/phyloxml.xsd"
>
  <phylogeny rooted="true">
    <name>Alcohol dehydrogenases</name>
    <description>contains examples of commonly used elements</description>
    <clade>
      <events>
        <speciations>1</speciations>
      </events>
      <clade>
        <taxonomy>
          <id provider="ncbi">6645</id>
          <scientific_name>Octopus vulgaris</scientific_name>
        </taxonomy>
        <sequence>
          <accession source="UniProtKB">P81431</accession>
          <name>Alcohol dehydrogenase class-3</name>
        </sequence>
      </clade>
      <clade>
        <confidence type="bootstrap">100</confidence>
        <events>
          <speciations>1</speciations>
        </events>
        <clade>
          <taxonomy>
            <id provider="ncbi">1423</id>
            <scientific_name>Bacillus subtilis</scientific_name>
          </taxonomy>
          <sequence>
            <accession source="UniProtKB">P71017</accession>
            <name>Alcohol dehydrogenase</name>
          </sequence>
        </clade>
        <clade>
          <taxonomy>
            <id provider="ncbi">562</id>
            <scientific_name>Escherichia coli</scientific_name>
          </taxonomy>
          <sequence>
            <accession source="UniProtKB">Q46856</accession>
            <name>Alcohol dehydrogenase</name>
          </sequence>
        </clade>
      </clade>
    </clade>
  </phylogeny>
</phyloxml>
```