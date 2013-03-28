---
layout: page
title: SMART Genomics Data Model
includenav: smartnav.markdown
---
{% include JB/setup %}

{% include example_format_tabs_top.html %}

<div id='toc'></div>



# Genomics Data Types
<div class="simple_box">
Each Genomics data type can have an optional element called <code>partOf</code>. The function of <code>partOf</code> is opposite to that of <code>contained</code> in general FHIR resources; it tells what resources are using it. As shown below, the format of <code>partOf</code> is similar to that of <conde>contained</code>.
	<div>{% highlight xml %}
<partOf>
	<type value="[code]"/><!--1..1 Type of resource-->
	<url value="[uri]"/><!--1..1 Link to the resource-->
</partOf>
	{% endhighlight %}</div>
</div>

<h2 id='Sequence'><code>Sequence</code></h2>
<li>A Sequence contains following information:</li>
1. Type of the sequence(DNA, RNA, or amino acid sequence)<br>
2. Coordinate of the region in the genome that the sequence matches to<br>
3. Read of the sequence<br>
4. Quality of the sequencing<br>
5. Source tissue from which the sequence is extracted<br><br>

<div id='Sequence_example'>
<div class='format_tabs'>
  <ul class="nav nav-tabs" data-tabs="tabs">
    <li style="margin-left: 0px;">Resource Profile:</li>
  </ul>
</div>
<div class='profile'>{% highlight xml %}
<Sequence>
	<partOf><!--0..* Resource User of this resource--></partOf>
	<identifier><!--1..1 ID for sequence--></identifier>
	<patient><!--1..1 Resource(patient) Owner of this sequence--></patient>
	<isMapped value="[boolean]"/><!--1..1 Tells whether this sequence is mapped-->
	<type value="[code]"/><!--1..1 Type of this sequence, one of DNA, RNA, or amino acid sequence-->
	<coordinate><!--0..1 Coordinate of genome that matched to this sequence-->
		<chromosome value="[code]"/><!--1..1 Chromosome of this coordiante-->
		<startPosition value="[integer]"/><!--1..1 Start position of this coordinate-->
		<endPosition value="[integer]"/><!--1..1 End position of this coordinate-->
	</coordinate>
	<read value="[string]"/><!--1..1 read of this sequence(e.g. AGGTCGACG...ATCGG)-->
	<quality value="[integer]"/><!--0..1 Phred score of this sequence (if it's a DNA sequence)-->
	<sourceTissue><!--1..1 CodeableConcept Tissue from which this sequence is extracted--></sourceTissue>
</Sequence>
{% endhighlight %}</div>
<br>

<div class='format_tabs'>
  <ul class="nav nav-tabs" data-tabs="tabs">
    <li style="margin-left: 0px;">SHOW EXAMPLE IN:</li>
    <li class="active"><a href="" data-target="#Sequence_example > div.rdf_xml" data-toggle="tab">XML</a></li>
    <li class="">      <a href="" data-target="#Sequence_example > div.json_ld" data-toggle="tab">JSON</a></li>
  </ul>
</div>
<div class='rdf_xml active'>{% highlight xml %}
<?xml version="1.0" encoding="UTF-8"?>
<Sequence>
	<text>
		<status value="generated"/>
		<div xmlns="http://www.w3.org/1999/xhtml">
			<p>DNA Sequence at chr11:150-21850 for patient 123</p>
		</div>
	</text>
	<contained>
		<type value="Patient"/>
		<url value="../patient/123"/>
		<display value="John Doe"/>
	</contained>
	<identifier>
		<use value="official"/>
		<label value="ID for sequence"/>
		<system value="http://genomics.smartplatformgs.org/terms"/>
		<id value="213"/>
		<period>
 			<start value="2013-03-16"/>
		</period>
 		<assigner>
			<display value="SMART Genomics"/>
		</assigner>
	</identifier>
	<patient>
		<type value="Patient"/>
		<url value="../patient/123"/>
		<display value="John Doe"/>
	</patient>	
	<isMapped value="true"/>
	<type value="DNA"/>
	<coorinate>
		<chromosome value="11"/>
		<startPosition value="150"/>
		<endPosition value="21850"/>
	</coordinate>
	<read value="AGGTCGACG...ATCGG"/>
	<quality value="10"/>
	<sourceTissue>
		<coding>
			<system value="http://sig.uw.edu/fma"/>
      			<code value="Skin_of_buccal_part_of_mouth"/>
    		</coding>
		<text value="skin of buccal part of mouth"/>
	</sourceTissue>
</Sequence>
{% endhighlight %}</div>
 
<div class='json_ld'>{% highlight javascript %}
   {
        "text": {
            "status": {
                "value": "generated"
            },
	    "div" : "<div xmlns='http://www.w3.org/1999/xhtml'><p>DNA Sequence at chr11:150-21850 for patient 123</p></div>"
        }, 
        "contained": {
            "url": {
                "value": "../patient/123"
            }, 
            "type": {
                "value": "Patient"
            }, 
            "display": {
                "value": "John Doe"
            }
        }, 
        "isMapped": {
            "value": "true"
        }, 
        "sourceTissue": {
            "text": {
                "value": "skin of buccal part of mouth"
            }, 
            "coding": {
                "code": {
                    "value": "Skin_of_buccal_part_of_mouth"
                }, 
                "system": {
                    "value": "http://sig.uw.edu/fma"
                }
            }
        }, 
        "patient": {
            "url": {
                "value": "../patient/123"
            }, 
            "type": {
                "value": "Patient"
            }, 
            "display": {
                "value": "John Doe"
            }
        }, 
        "quality": {
            "value": "10"
        }, 
        "read": {
            "value": "AGGTCGACG...ATCGG"
        }, 
        "coordinate": {
            "startPosition": {
                "value": "150"
            }, 
            "endPosition": {
                "value": "21850"
            }, 
            "chromosome": {
                "value": "11"
            }
        }, 
        "identifier": {
            "use": {
                "value": "official"
            }, 
            "assigner": {
                "display": {
                    "value": "SMART Genomics"
                }
            }, 
            "period": {
                "start": {
                    "value": "2013-03-16"
                }
            }, 
            "system": {
                "value": "http://genomics.smartplatformgs.org/terms"
            }, 
            "label": {
                "value": "ID for sequence"
            }, 
            "id": {
                "value": "213"
            }
        }, 
        "type": {
            "value": "DNA"
        }
    }
{% endhighlight %}</div>
</div>




<h2 id='DNASequence'><code>DNASequence</code></h2>
<li>DNASequence is a resource derived from Sequence, and contains 1) the basic info of the sequence 2) the gene that the sequence relates to(if any)</li><br>
<div id='DNASequence_example'>

<div class='format_tabs'>
  <ul class="nav nav-tabs" data-tabs="tabs">
    <li style="margin-left: 0px;">Resource Profile:</li>
  </ul>
</div>

<div class='resource_profile active'>{% highlight xml %}
<DNASequence>
	<partOf><!--0..* Resource User of this resource--></partOf>
	<identifier><!--1..1 Identifier Coordinate ID for DNAsequence--></identifier>
	<patient><!--1..1 Resource(patient) Owner of this DNASequence--></patient>
	<sequence><!--1..1 Resource(sequence) Details about this DNASequence--></sequence>
	<relatedGene><!--0..1 Resource(gene) Gene that this DNASequence relates to--></relatedGene>
</DNASequence>
{% endhighlight %}</div>
<br>

<div class='format_tabs'>
  <ul class="nav nav-tabs" data-tabs="tabs">
    <li style="margin-left: 0px;">SHOW EXAMPLE IN:</li>
    <li class="active"><a href="" data-target="#DNASequence_example > div.rdf_xml" data-toggle="tab">XML</a></li>
    <li class="">      <a href="" data-target="#DNASequence_example > div.json_ld" data-toggle="tab">JSON</a></li>
  </ul>
</div>

<div class='rdf_xml active'>{% highlight xml %}
<?xml version="1.0" encoding="UTF-8"?>
<DNASequence>
	<text>
		<status value="generated"/>
		<div xmlns="http://www.w3.org/1999/xhtml">
			<p>DNA sequence at chr17:134-214357 for patient 123</p>
		</div>
	</text>
	<contained>
		<type value="Patient"/>
		<url value="../patient/123"/>
		<display value="John Doe"/>
	</contained>
	<contained>
		<type value="Sequence"/>
		<url value="../sequence/231"/>
	</contained>
	<contained>
		<type value="Gene"/>
		<url value="../gene/chr17_124_214357"/>
		<display value="BRCA1"/>
	</contained>
	<identifier>
		<use value="official"/>
		<label value="Coordinate for DNA sequence"/>
		<system value="http://genomics.smartplatformgs.org/terms"/>
		<id value="chr17_134_214357"/>
		<period>
 			<start value="2013-03-16"/>
		</period>
 		<assigner>
			<display value="SMART Genomics"/>
		</assigner>
	</identifier>
	<patient>
		<type value="Patient"/>
		<url value="../patient/123"/>
	</patient>
	<sequence>
		<type value="Sequence"/>
		<url value="../sequence/231"/>
	</sequence>
	<relatedGene>
		<type value="Gene"/>
		<url value="../gene/478"/>
		<display value="BRCA1"/>
	</relatedGene>	
</DNASequence>
{% endhighlight %}</div>

<div class='json_ld'>{% highlight javascript %}
    {
        "text": {
            "status": {
                "value": "generated"
            }
	"div" : "<div xmlns='http://www.w3.org/1999/xhtml'><p>DNA sequence at chr17:134-214357 for patient 123</p></div>"
        },
        "contained": [
            {
                "url": {
                    "value": "../patient/123"
                }, 
                "type": {
                    "value": "Patient"
                }, 
                "display": {
                    "value": "John Doe"
                }
            }, 
            {
                "url": {
                    "value": "../sequence/231"
                }, 
                "type": {
                    "value": "Sequence"
                }
            }, 
            {
                "url": {
                    "value": "../gene/chr17_124_214357"
                }, 
                "type": {
                    "value": "Gene"
                }, 
                "display": {
                    "value": "BRCA1"
                }
            }
        ], 
        "patient": {
            "url": {
                "value": "../patient/123"
            }, 
            "type": {
                "value": "Patient"
            }
        }, 
        "sequence": {
            "url": {
                "value": "../sequence/231"
            }, 
            "type": {
                "value": "Sequence"
            }
        },  
        "relatedGene": {
            "url": {
                "value": "../gene/478"
            }, 
            "type": {
                "value": "Gene"
            }, 
            "display": {
                "value": "BRCA1"
            }
        }, 
        "identifier": {
            "use": {
                "value": "official"
            }, 
            "assigner": {
                "display": {
                    "value": "SMART Genomics"
                }
            }, 
            "period": {
                "start": {
                    "value": "2013-03-16"
                }
            }, 
            "system": {
                "value": "http://genomics.smartplatformgs.org/terms"
            }, 
            "label": {
                "value": "Coordinate for DNA sequence"
            }, 
            "id": {
                "value": "chr17_134_214357"
            }
        }
    }
{% endhighlight %}</div>
</div>

<h2 id='RNASequence'><code>RNASequence</code></h2>

<li>RNASequence is a resource derived from Sequence,and contains 1) the basic info of the sequence 2) the gene that the sequence relates to(if any)</li>
<br>
<div id='RNASequence_example'>

<div class='format_tabs'>
  <ul class="nav nav-tabs" data-tabs="tabs">
    <li style="margin-left: 0px;">Resource Profile:</li>
  </ul>
</div>

<div class='resource_profile active'>{% highlight xml %}
<RNASequence>
	<partOf><!--0..* Resource User of this resource--></partOf>
	<identifier><!--1..1 Coordinate ID for mapped sequence or ID for unmapped--></identifier>
	<patient><!--1..1 Resource(patient) Owner of this RNASequence--></patient>
	<sequence><!--1..1 Resource(sequence) Detail about this RNASequence--></sequence>
	<relatedGene><!--0..1 Resource(gene) Gene that this RNASequence transcribed from--></relatedGene>
</RNASequence>
{% endhighlight %}</div>
<br>

<div class='format_tabs'>
  <ul class="nav nav-tabs" data-tabs="tabs">
    <li style="margin-left: 0px;">SHOW EXAMPLE IN:</li>
    <li class="active"><a href="" data-target="#RNASequence_example > div.rdf_xml" data-toggle="tab">XML</a></li>
    <li class="">      <a href="" data-target="#RNASequence_example > div.json_ld" data-toggle="tab">JSON</a></li>
  </ul>
</div>

<div class='rdf_xml active'>{% highlight xml %}
<?xml version="1.0" encoding="UTF-8"?>
<RNASequence>
	<text>
		<status value="generated"/>
		<div xmlns="http://www.w3.org/1999/xhtml">
			<p>RNA seuqence transcribed from region chr12:12456-214357 for patient 123</p>
		</div>
	</text>
	<contained>
		<type value="Patient"/>
		<url value="../patient/123"/>
		<display value="John Doe"/>
	</contained>
	<contained>
		<type value="Sequence"/>
		<url value="../sequence/231"/>
	</contained>
	<contained>
		<type value="Gene"/>
		<url value="../gene/chr12_12456_214357"/>
		<display value="GBA"/>
	</contained>
	<identifier>
		<use value="official"/>
		<label value="Coordinate of transcriped region for the RNASequence"/>
		<system value="http://genomics.smartplatformgs.org/terms"/>
		<id value="chr12_12456_214357"/>
		<period>
 			<start value="2013-03-16"/>
		</period>
 		<assigner>
			<display value="SMART Genomics"/>
		</assigner>
	</identifier>
	<patient>
		<type value="Patient"/>
		<url value="../patient/123"/>
	</patient>
	<sequence>
		<type value="Sequence"/>
		<url value="../sequence/231"/>
	</sequence>
	<relatedGene>
		<type value="Gene"/>
		<url value="../gene/478"/>
		<display value="GBA"/>
	</relatedGene>	
</RNASequence>
{% endhighlight %}</div>

<div class='json_ld'>{% highlight javascript %}
    {
	    "text": {
            "status": {
                "value": "generated"
            },
	    "div" : "<div xmlns='http://www.w3.org/1999/xhtml'><p>RNA seuqence transcribed from region chr12:12456-214357 for patient 123</p></div>"
        }, 
        "contained": [
            {
                "url": {
                    "value": "../patient/123"
                }, 
                "type": {
                    "value": "Patient"
                }, 
                "display": {
                    "value": "John Doe"
                }
            }, 
            {
                "url": {
                    "value": "../sequence/231"
                }, 
                "type": {
                    "value": "Sequence"
                }
            }, 
            {
                "url": {
                    "value": "../gene/chr12_12456_214357"
                }, 
                "type": {
                    "value": "Gene"
                }, 
                "display": {
                    "value": "GBA"
                }
            }
        ], 
        "patient": {
            "url": {
                "value": "../patient/123"
            }, 
            "type": {
                "value": "Patient"
            }
        }, 
        "sequence": {
            "url": {
                "value": "../sequence/231"
            }, 
            "type": {
                "value": "Sequence"
            }
        }, 
        "relatedGene": {
            "url": {
                "value": "../gene/478"
            }, 
            "type": {
                "value": "Gene"
            }, 
            "display": {
                "value": "GBA"
            }
        }, 
        "identifier": {
            "use": {
                "value": "official"
            }, 
            "assigner": {
                "display": {
                    "value": "SMART Genomics"
                }
            }, 
            "period": {
                "start": {
                    "value": "2013-03-16"
                }
            }, 
            "system": {
                "value": "http://genomics.smartplatformgs.org/terms"
            }, 
            "label": {
                "value": "Coordinate of transcriped region for the RNASequence"
            }, 
            "id": {
                "value": "chr12_12456_214357"
            }
        }
    }
{% endhighlight %}</div>
</div>

<h2 id='AminoAcidSequence'><code>AminoAcidSequence</code></h2>
<li>AminoAcidSequence is a resource derived from Sequence, and contains following information:</li>
1. Basic info of the sequence<br>
2. Gene that the sequence relates to<br>
3. Trait resulted from having the sequence<br><br>
<div id='AminoAcidSequence_example'>


<div class='format_tabs'>
  <ul class="nav nav-tabs" data-tabs="tabs">
    <li style="margin-left: 0px;">Resource Profile:</li>
  </ul>
</div>

<div class='resource_profile active'>{% highlight xml %}
<AminoAcidSequence>
	<partOf><!--0..* Resource User of this resource--></partOf>
	<identifier><!--1..1 Identifier Coordinate ID for AminoAcidSeuqence--></identifier>
	<patient><!--1..1 Resource(patient) Owner of this AminoAcidSequence--></patient>
	<sequence><!--1..1 Resource(sequence) Amino acid read of this sequence--></sequence>
	<relatedGene><!--0..1 Resource(gene) Gene that this sequence translated from--></relatedGene>
	<relatedTrait><!--0..1 CodeableConcept Trait resulted from having this protein-->
		<hasTrait value="[boolean]"/><!--1..1 Effect that this sequence has for the trait(positive/negative)-->
		<trait><!--1..1 CodeableConcept Ontology for this trait--></trait>
	</relatedTrait>
</AminoAcidSequence>
{% endhighlight %}</div>
<br>

<div class='format_tabs'>
  <ul class="nav nav-tabs" data-tabs="tabs">
    <li style="margin-left: 0px;">SHOW EXAMPLE IN:</li>
    <li class="active"><a href="" data-target="#AminoAcidSequence_example > div.rdf_xml" data-toggle="tab">XML</a></li>
    <li class="">      <a href="" data-target="#AminoAcidSequence_example > div.json_ld" data-toggle="tab">JSON</a></li>
  </ul>
</div>
<div class='rdf_xml active'>{% highlight xml %}
<?xml version="1.0" encoding="UTF-8"?>
<AminoAcidSequence>
	<text>
		<status value="generated"/>
		<div xmlns="http://www.w3.org/1999/xhtml">
			<p>Amino acid seqeunce stranslated from region chr11:150-23450 for patient 123</p>
		</div>
	</text>
	<contained>
		<type value="Patient"/>
		<url value="../patient/123"/>
		<display value="John Doe"/>
	</contained>
	<contained>
		<type value="Sequence"/>
		<url value="../sequence/256"/>
	</contained>
	<contained>
		<type value="Gene"/>
		<url value="../gene/chr11_150_23450"/>
		<display value="HBB"/>
	</contained>
	<identifier>
		<use value="official"/>
		<label value="Coordinate of transcriped region for the RNASequence"/>
		<system value="http://genomics.smartplatformgs.org/terms"/>
		<id value="chr11_150_23450"/>
		<period>
 			<start value="2013-03-16"/>
		</period>
 		<assigner>
			<display value="SMART Genomics"/>
		</assigner>
	</identifier>
	<patient>
		<type value="Patient"/>
		<url value="../patient/123"/>
	</patient>
	<sequence>
		<type value="Sequence"/>
		<url value="../sequence/231"/>
	</sequence>
	<relatedGene>
		<type value="Gene"/>
		<url value="../gene/478"/>
		<display value="HBB"/>
	</relatedGene>		
	<relatedTrait>
		<hasTrait value="true"/>
		<ontology>
			<coding>
				<system value="http://purl.bioportal.org/ontologies/SNOMEDCT" />
      				<code value="35434009"/>
    			</coding>
			<text value="Sickle cell-hemoglobin C disease"/>
		</ontology>
	</relatedTrait>
</AminoAcidSequence>
{% endhighlight %}</div>
<div class='json_ld'>{% highlight javascript %}
    {
        "text": {
            "status": {
                "value": "generated"
            },
	    "div" : "<div xmlns='http://www.w3.org/1999/xhtml'><p>Amino acid seqeunce stranslated from region chr11:150-23450 for patient 123</p></div"
        },
        "contained": [
            {
                "url": {
                    "value": "../patient/123"
                }, 
                "type": {
                    "value": "Patient"
                }, 
                "display": {
                    "value": "John Doe"
                }
            }, 
            {
                "url": {
                    "value": "../sequence/256"
                }, 
                "type": {
                    "value": "Sequence"
                }
            }, 
            {
                "url": {
                    "value": "../gene/chr11_150_23450"
                }, 
                "type": {
                    "value": "Gene"
                }, 
                "display": {
                    "value": "HBB"
                }
            }
        ], 
        "patient": {
            "url": {
                "value": "../patient/123"
            }, 
            "type": {
                "value": "Patient"
            }
        }, 
        "sequence": {
            "url": {
                "value": "../sequence/231"
            }, 
            "type": {
                "value": "Sequence"
            }
        },  
        "relatedTrait": {
            "ontology": {
                "text": {
                    "value": "Sickle cell-hemoglobin C disease"
                }, 
                "coding": {
                    "code": {
                        "value": "35434009"
                    }, 
                    "system": {
                        "value": "http://purl.bioportal.org/ontologies/SNOMEDCT"
                    }
                }
            }, 
            "hasTrait": {
                "value": "true"
            }
        }, 
        "relatedGene": {
            "url": {
                "value": "../gene/478"
            }, 
            "type": {
                "value": "Gene"
            }, 
            "display": {
                "value": "HBB"
            }
        }, 
        "identifier": {
            "use": {
                "value": "official"
            }, 
            "assigner": {
                "display": {
                    "value": "SMART Genomics"
                }
            }, 
            "period": {
                "start": {
                    "value": "2013-03-16"
                }
            }, 
            "system": {
                "value": "http://genomics.smartplatformgs.org/terms"
            }, 
            "label": {
                "value": "Coordinate of transcriped region for the RNATranscript"
            }, 
            "id": {
                "value": "chr11_150_23450"
            }
        }
    }
{% endhighlight %}</div>
</div>


<h2 id='Gene'><code>Gene</code></h2>
<li>A Gene contains following information:</li>
1. Genotype of the patient<br>
2. Phenotype of the patient<br>
3. Sequences that relates to the gene<br><br>
<div id='Gene_example'>

<div class='format_tabs'>
  <ul class="nav nav-tabs" data-tabs="tabs">
    <li style="margin-left: 0px;">Resource Profile:</li>
  </ul>
</div>


<div class='resource_profile active'>{% highlight xml %}
<Gene>
	<partOf><!--0..* Resource User of this resource--></partOf>
	<identifier><!--Identifier Coordinate ID for gene--></identifier>
	<patient><!--1..1 Resource(patient) Owner of this gene--></patient>
	<genotype><!--0..1 Resource(DNASequence) DNA sequence of this gene--></genotype>
	<phenotype><!--0..1 CodeableConcept Phenotype resulted from having this protein-->
		<hasTrait value="[boolean]"/><!--1..1 Effect of this gene on a trait(positive/negative)-->
		<trait><!--1..1 CodeableConcept Ontology for this trait--></trait>
	</phenotype>
	<relatedSequence><!--0..* Resource(Sequence) Sequence that this gene contains--></relatedSequence>
</Gene>
{% endhighlight %}</div>
<br>

<div class='format_tabs'>
  <ul class="nav nav-tabs" data-tabs="tabs">
    <li style="margin-left: 0px;">SHOW EXAMPLE IN:</li>
    <li class="active"><a href="" data-target="#Gene_example > div.rdf_xml" data-toggle="tab">XML</a></li>
    <li class="">      <a href="" data-target="#Gene_example > div.json_ld" data-toggle="tab">JSON</a></li>
  </ul>
</div>
<div class='rdf_xml active'>{% highlight xml %}
<?xml version="1.0" encoding="UTF-8"?>
<Gene>
	<text>
		<status value="generated"/>
		<div xmlns="http://www.w3.org/1999/xhtml">
			<p>Gene from region chr11:150~23450 for patient 123</p>
		</div>
	</text>
	<contained>
		<type value="Patient"/>
		<url value="../patient/123"/>
		<display value="John Doe"/>
	</contained>
	<contained>
		<type value="DNASequence"/>
		<url value="../sequence/chr11:150~23450"/>
	</contained>
	<identifier>
		<use value="official"/>
		<label value="Coordinate of the gene"/>
		<system value="http://genomics.smartplatformgs.org/terms"/>
		<id value="chr11_150_23450"/>
		<period>
 			<start value="2013-03-16"/>
		</period>
 		<assigner>
			<display value="SMART Genomics"/>
		</assigner>
	</identifier>
	<patient>
		<type value="Patient"/>
		<url value="../patient/123"/>
	</patient>
	<sequence>
		<type value="DNASequence"/>
		<url value="../sequence/chr11_150_23450"/>
	</sequence>
	<phenotype>
		<hasTrait value="true"/>
		<ontology>
			<coding>
				<system value="http://purl.bioportal.org/ontologies/SNOMEDCT" />
      				<code value="35434009"/>
    			</coding>
			<text value="Sickle cell-hemoglobin C disease"/>
		</ontology>
	</phenotype>	
</Gene>
{% endhighlight %}</div>
<div class='json_ld'>{% highlight javascript %}
    {
        "text": {
            "status": {
                "value": "generated"
            },
	    "div" : "<div xmlns='http://www.w3.org/1999/xhtml'><p>Gene from region chr11:150~23450 for patient 123</p></div>"
        },
        "contained": [
            {
                "url": {
                    "value": "../patient/123"
                }, 
                "type": {
                    "value": "Patient"
                }, 
                "display": {
                    "value": "John Doe"
                }
            }, 
            {
                "url": {
                    "value": "../sequence/chr11:150~23450"
                }, 
                "type": {
                    "value": "DNASequence"
                }
            }
        ],  
        "patient": {
            "url": {
                "value": "../patient/123"
            }, 
            "type": {
                "value": "Patient"
            }
        }, 
        "sequence": {
            "url": {
                "value": "../sequence/chr11_150_23450"
            }, 
            "type": {
                "value": "DNASequence"
            }
        }, 
        "phenotype": {
            "ontology": {
                "text": {
                    "value": "Sickle cell-hemoglobin C disease"
                }, 
                "coding": {
                    "code": {
                        "value": "35434009"
                    }, 
                    "system": {
                        "value": "http://purl.bioportal.org/ontologies/SNOMEDCT"
                    }
                }
            }, 
            "hasTrait": {
                "value": "true"
            }
        }, 
        "identifier": {
            "use": {
                "value": "official"
            }, 
            "assigner": {
                "display": {
                    "value": "SMART Genomics"
                }
            }, 
            "period": {
                "start": {
                    "value": "2013-03-16"
                }
            }, 
            "system": {
                "value": "http://genomics.smartplatformgs.org/terms"
            }, 
            "label": {
                "value": "Coordinate of the gene"
            }, 
            "id": {
                "value": "chr11_150_23450"
            }
        }
    }
{% endhighlight %}</div>
</div>


<h2 id='Variant'><code>Variant</code></h2>
<li>A Variant contains basic data in a VCF file, including:</li>
1. Basic info about the reference sequence<br>
2. Basic info about the sample sequence<br>
3. Optional information in VCF format<br>
4. URI linked to the raw VCF file that contains the variant<br><br>
<div id='Variant_example'>

<div class='format_tabs'>
  <ul class="nav nav-tabs" data-tabs="tabs">
    <li style="margin-left: 0px;">Resource Profile:</li>
  </ul>
</div>

<div class='profile active'>{% highlight xml %}
<Variant>
	<partOf><!--0..* Resource User of this resource--></partOf>
	<patient><!--1..1 Resource(Patient) Owner of this Variant--></patient>
	<rawFile value="[uri]"/><!--1..1 Link of raw VCF file for this Variant-->
	<reference><!--1..1 Resource(Sequence) Reference sequence--></reference>
	<ALT value="[string]"/><!--1..* Alternative genotype-->
	<FILTER><!--1..* Same function as that in a VCF file-->
		<name value="[string]"/><!--1..1 Value of the FILTER-->
		<definition value="[string]"/><!--0..1 Definition from the header section of VCF file-->
	</FILTER>
	<attribute><!--1..* Attribute of the reference sequence; an element that combines both the header, INFO, and values that correspond to INFO in VCF file -->
		<name value="[code]"/><!--1..1 Name of the attribute, corresponds to a single slot in INFO of VCF file-->
		<description value="[string]"/><!--1..1 Definition of the attribute, corresponds to the definition in header section-->
		<value value="[string]"/><!--1..1 Value of the attribute-->
	<attribute>
	<sample><!--1..* Sample sequence of the alignment-->
		<genotype><!--1..1 Resource(Sequence) Sample sequence--></genotype>
		<attribute><!--1..* Attribute of the sample sequence, an element that combines both the header, FORMAT, and values that correspond to Fromat in VCF file-->
			<name value="[code]"/><!--1..1 Name of the attribute, corresponds to a single slot in FORMAT of VCF file-->
			<description value="[string]"/><!--1..1 Definition of the attribute, corresponds to the definition in header section-->
			<value value="[string]"/><!--1..1 Value of the attribute-->
		<attribute>	
	</sample>
</Variant>
{% endhighlight %}</div>
<br>

<div class='format_tabs'>
  <ul class="nav nav-tabs" data-tabs="tabs">
    <li style="margin-left: 0px;">SHOW EXAMPLE IN:</li>
    <li class="active"><a href="" data-target="#Variant_example > div.rdf_xml" data-toggle="tab">XML</a></li>
    <li class="">      <a href="" data-target="#Variant_example > div.json_ld" data-toggle="tab">JSON</a></li>
  </ul>
</div>
<div class='rdf_xml active'>{% highlight xml %}
<?xml version="1.0" encoding="UTF-8"?>
<Variant>
	<text>
		<status value="generated"/>
		<div xmlns="http://www.w3.org/1999/xhtml">
			<h>Variant</h>
			<p>DNA sequence at region chr20:14000-14321 compare to sequence at region chr20:12000-12321</p>
		</div>
	</text>
	<contained>
		<type value="Patient"/>
		<url value="../patient/456"/>
		<display value="John Doe"/>
	</contained>
	<contained>
		<type value="DNASequence"/>
		<url value="../DNASequence/chr20_14000_14321"/>
	</contained>
	<contained>
		<type value="DNASequence"/>
		<url value="../DNASequence/chr20_12000_12321"/>
	</contained>
	<patient>
		<type value="Patient"/>
		<url value="../patient/456"/>
	</patient>
	<rawFile value="http://genomics.smartplatforms.org/record/123/vcf/1"/>
	<reference>
		<type value="DNASequence"/>
		<url value="../DNASequence/chr20_14000_14321"/>
	</reference>
	<ALT value="G"/>
	<FILTER>
		<name value="PASS"/>
	</FILTER>
	<attribute>
		<name value="DP"/>
		<definition value="Read depth"/>
		<value value="9"/>
	</attribute>
	<sample>
		<genotype>
			<type value="DNASequence"/>
			<url value="../DNASequence/chr20:12000-12321"/>
		</genotype>
		<attribute>
			<name value="DP"/>
			<definition value="Read depth"/>
			<value value="13"/>
		</attribute>
	</sample>
</Variant>
{% endhighlight %}</div>
<div class='json_ld'>{% highlight javascript %}
{
    "text": {
        "status": {
            "value": "generated"
        },
	"div" : "<div xmlns='http://www.w3.org/1999/xhtml'><h>Variant</h><p>DNA sequence at region chr20:14000-14321 compare to sequence at region chr20:12000-12321</p></div>"
    }
    "contained": [
        {
            "url": {
                "value": "../patient/456"
            }, 
            "type": {
                "value": "Patient"
            }, 
            "display": {
                "value": "John Doe"
            }
        }, 
        {
            "url": {
                "value": "../DNASequence/chr20_14000_14321"
            }, 
            "type": {
                "value": "DNASequence"
            }
        }, 
        {
            "url": {
                "value": "../DNASequence/chr20_12000_12321"
            }, 
            "type": {
                "value": "DNASequence"
            }
        }
    ],
    "attribute": {
        "definition": {
            "value": "Read depth"
        }, 
        "name": {
            "value": "DP"
        }, 
        "value": {
            "value": "9"
        }
    }, 
    "sample": {
        "attribute": {
            "definition": {
                "value": "Read depth"
            }, 
            "name": {
                "value": "DP"
            }, 
            "value": {
                "value": "13"
            }
        }, 
        "genotype": {
            "url": {
                "value": "../DNASequence/chr20:12000-12321"
            }, 
            "type": {
                "value": "DNASequence"
            }
        }
    }, 
    "patient": {
        "url": {
            "value": "../patient/456"
        }, 
        "type": {
            "value": "Patient"
        }
    }, 
    "reference": {
        "url": {
            "value": "../DNASequence/chr20_14000_14321"
        }, 
        "type": {
            "value": "DNASequence"
        }
    }, 
    "ALT": {
        "value": "G"
    }, 
    "FILTER": {
        "name": {
            "value": "PASS"
        }
    },  
    "rawFile": {
        "value": "http://genomics.smartplatforms.org/record/123/vcf/1"
    }
}
{% endhighlight %}</div>
</div>

<h2 id='Alignment'><code>Alignment</code></h2>
<li>An Alignment contains basic information in a blast/SAM file, including:</li>
1. Basic info about the sequence being queried<br>
2. Basic info about the reference sequence<br>
3. Type of raw file of this Alignment(blast/SAM)<br>
4. Link of the raw file<br>
5. Type of alignment(local/global/short-read)<br>
6. Score of the alignment<br><br>
<div id='Alignment_example'>

<div class='format_tabs'>
  <ul class="nav nav-tabs" data-tabs="tabs">
    <li style="margin-left: 0px;">Resource Profile:</li>
  </ul>
</div>

<div class='profile active'>{% highlight xml %}
<Alignment>
	<partOf><!--0..* Resource User of this resource--></partOf>
	<patient><!--1..1 Resource(Patient)Owner of the subject Sequence--></patient>
	<query><!--1..1 Resource(Sequence) Queried(subject) sequence of alignment--></query>
	<reference><!--1..1 Resource(Sequence) Reference sequence of alignment--></reference>
	<fileType value="[code]"><!--1..1 Format of raw file of this alignment [blast/SAM]-->
	<rawFile value="[uri]"><!--1..1 Link of raw file of this alignment-->
	<score value="[integer]"><!--1..1 Confidence of this alignment-->
	<type value="[code]"><!--1..1 Type of alignment [local/global/short-read]-->
</Alignment> 
{% endhighlight %}</div>
<br>

<div class='format_tabs'>
  <ul class="nav nav-tabs" data-tabs="tabs">
    <li style="margin-left: 0px;">SHOW EXAMPLE IN:</li>
    <li class="active"><a href="" data-target="#Alignment_example > div.rdf_xml" data-toggle="tab">XML</a></li>
    <li class="">      <a href="" data-target="#Alignment_example > div.json_ld" data-toggle="tab">JSON</a></li>
  </ul>
</div>
<div class='rdf_xml active'>{% highlight xml %}
<?xml version="1.0" encoding="UTF-8"?>
<Alignment>
	<text>
		<status value="generated"/>
		<div xmlns="http://www.w3.org/1999/xhtml">
			<p>Alignment of sequence123(http://genomics.smartplatforms.org/records/456/alignments/123) against sequence234(http://genomics.smartplatforms.org/records/456/alignments/234)</p>
		</div>
	</text>
	<contained>
		<type value="Patient"/>
		<url value="../patient/456"/>
		<display value="John Doe"/>
	</contained>
	<contained>
		<type value="Sequence"/>
		<url value="../sequence/123"/>
	</contained>
	<contained>
		<type value="Sequence"/>
		<url value="../sequence/234"/>
	</contained>
	<patient>
		<type value="Patient"/>
		<url value="../patient/456"/>
	</patient>
	<query>
		<type value="Sequence"/>
		<url value="../sequence/123"/>
	</query>
	<reference>
		<type value="Sequence"/>
		<url value="../sequence/234"/>
	</reference>
	<fileType value="SAM"/>
	<rawFile value="http://genomics.smartplatforms.org/file/alignments/sam/1"/>
	<score value="0.5"/>
	<type value="global"/>
</Alignment>
{% endhighlight %}</div>
<div class='json_ld'>{% highlight javascript %}
    {
        "text": {
            "status": {
                "value": "generated"
            }
	    "div" : "<div xmlns='http://www.w3.org/1999/xhtml'><p>Alignment of sequence123(http://genomics.smartplatforms.org/records/456/alignments/123) against sequence234(http://genomics.smartplatforms.org/records/456/alignments/234)</p></div>"
        },
        "contained": [
            {
                "url": {
                    "value": "../patient/456"
                }, 
                "type": {
                    "value": "Patient"
                }, 
                "display": {
                    "value": "John Doe"
                }
            }, 
            {
                "url": {
                    "value": "../sequence/123"
                }, 
                "type": {
                    "value": "Sequence"
                }
            }, 
            {
                "url": {
                    "value": "../sequence/234"
                }, 
                "type": {
                    "value": "Sequence"
                }
            }
        ],
        "patient": {
            "url": {
                "value": "../patient/456"
            }, 
            "type": {
                "value": "Patient"
            }
        }, 
        "reference": {
            "url": {
                "value": "../sequence/234"
            }, 
            "type": {
                "value": "Sequence"
            }
        },  
        "fileType": {
            "value": "SAM"
        },  
        "score": {
            "value": "0.5"
        }, 
        "rawFile": {
            "value": "http://genomics.smartplatforms.org/file/alignments/sam/1"
        }, 
        "query": {
            "url": {
                "value": "../sequence/123"
            }, 
            "type": {
                "value": "Sequence"
            }
        }, 
        "type": {
            "value": "global"
        }
    }
{% endhighlight %}</div>
</div>

<h2 id='UncategorizedData'><code>UncategorizedData</code></h2>

<li>An UncategorizedData displays any data that don't fit into resources defined above as well as data that linked to them; data within an UncategorizedData is either displayed as table or graph. </li><br>

<div id='TableFormat_example'>
<li>Tables in <code>UncategorizedData</code>are described with following format</li><div class='format_tabs'>
  <ul class="nav nav-tabs" data-tabs="tabs">
    <li style="margin-left: 0px;">SHOW FORMAT IN:</li>
    <li class="active"><a href="" data-target="#TableFormat_example > div.rdf_xml" data-toggle="tab">XML</a></li>
    <li class="">      <a href="" data-target="#TableFormat_example > div.json_ld" data-toggle="tab">JSON</a></li>
  </ul>
</div>

<div class='rdf_xml active'>{% highlight xml %}
<table>
	<column value='[string]'/><!--1..* Names of the columns-->
	<entry><!--1..* Entry of the table-->
		<name value="[string]"/><!--0..1 Name of entry-->
		<description value="[string]"/><!--0..1 Description of the function of the entry-->
		<content><!--1..* Content corresponds each column-->
			<column value="[string]"/><!--1..1 Column to which this data corresponds-->
			<data><!--1..1-->
				<isCategorized value="[boolean]"/><!--1..1 Whether this data belongs to any defined SMART Genomics data model-->
				<url value="[uri]"/><!--1..1 Llink to the data source-->
			</data>
		</content>
	</entry>
</table>
{% endhighlight %}</div>

<div class='json_ld'>{% highlight javascript %}
{
	"column" : [
		{"value" : "column1"},
		{"value" : "column2"},
		...other columns...
	],
	"entry" : [
		{
			"name" : {
				"value" : "entry1"
			},
			"description" : {
				"value" : "demontstration",
			},
			"content" : [
				{
					"column" : {
						"value" : "column1"
					},
					"isCategorized" : {
						"value" : "true"
					},
					"uri" : {
						"value" : "http://genomics.smartplatforms.org/records/123/sequences/1"
					}
				},
				...other columns within entry1...
			]
		},
		...other entries...
	]
}
{% endhighlight %}</div>
</div>

<li>Graphs in <code>UncategorizedData</code>are described with following format:</li>
<div id='GraphFormat_example'>

<div class='format_tabs'>
  <ul class="nav nav-tabs" data-tabs="tabs">
    <li style="margin-left: 0px;">SHOW FORMAT IN:</li>
    <li class="active"><a href="" data-target="#TableFormat_example > div.rdf_xml" data-toggle="tab">XML</a></li>
    <li class="">      <a href="" data-target="#TableFormat_example > div.json_ld" data-toggle="tab">JSON</a></li>
  </ul>
</div>

<div class='rdf_xml active'>{% highlight xml %}
<graph>
	<node id="[string]"><!--1..* Definition for a node-->
		<descripton value="[string]"/><!--0..1 Description of the node-->
		<content><!--1..1 Content of the node-->
			<isCategorized value="[boolean]"/><!--1..1 Whether this data belongs to any defined SMART Genomics data model-->
			<url value="[uri]"/><!--1..1 Link to the data source-->
		</content>
	</node>
	<vector id="[string]"><!--1..* Vector that describe the relationship between two nodes-->
		<description value="[string]"><!--0..1 Description of the relationships between the two nodes-->
		<from value="[id]"/><!--ID of the start node-->
		<to value="[id]"/><!--ID of the end node-->
	</vetor>
</graph>
{% endhighlight %}</div>

<div class='json_ld'>{% highlight javascript %}
{
	"node" : [
		{
			"_id" : "node1",
			"description" : {
				"value" : "node for demonstration"
			},
			"content" : {
				"isCategorized" : {
					"value" : "false"
				},
				"uri" : {
					"value" : "http://genomics.smartplatforms.org/records/123/file/3"
				}
			}
		},
		...other nodes...
	],
	"vector" : [
		{
			"_id" : "123",
			"description" : {
				"value" : "vector for demonstration"
			},
			"from" : {
				"value" : "node1"
			},
			"to" : {
				"value" : "node2"
			}
		},
		... other vectors...
	]
}
{% endhighlight %}</div>
</div>

<div id='UncategorizedData_example'>

<li>Resource profile of <code>UncategorizedData</code></li>

<div class='profile active'>{% highlight xml %}
<UncategorizedData>
	<partOf><!--0..* Resource User of this resource--></partOf>
	<identifier><!--1..1 Identifier ID of this UncategorizedData--></identifier>
	<patient><!--1..1 Resource(Patient) Owner of the data--></patient>	
	<structure value="[code]"/><!--1..1 Structure of the data (table/graph)-->
	<subjectType value="[code]"/><!--1..1 Type of the subject described by the datad (e.g experiment)-->
	<description value="string"/><!--1..1 Description of the subject-->
	<content><!--1..1 Content of the data--></content>
</UncategorizedData>
{% endhighlight %}</div>
<br>

<li>Example <code>UncategorizedData</code></li>

<div class='format_tabs'>
  <ul class="nav nav-tabs" data-tabs="tabs">
    <li style="margin-left: 0px;">SHOW EXAMPLE IN:</li>
    <li class="active"><a href="" data-target="#UncategorizedData_example > div.rdf_xml" data-toggle="tab">XML</a></li>
    <li class="">      <a href="" data-target="#UncategorizedData_example > div.json_ld" data-toggle="tab">JSON</a></li>
  </ul>
</div>

<div class='rdf_xml active'>{% highlight xml %}
<?xml version="1.0" encoding="UTF-8"?>
<UncategorizedData>
	<text>
		<status value="generated"/>
		<div xmlns="http://www.w3.org/1999/xhtml">
			<p>Data of sequencing results for patient </p>
		</div>
	</text>
	<contained>
		<type value="Patient"/>
		<url value="../patient/456"/>
		<display value="John Doe"/>
	</contained>
	<identifier>
		<use value="official"/>
		<label value="ID for UncategorizedData"/>
		<system value="http://genomics.smartplatformgs.org/terms"/>
		<id value="123"/>
		<period>
 			<start value="2013-03-16"/>
		</period>
 		<assigner>
			<display value="SMART Genomics"/>
		</assigner>
	</identifier>	
	<patient>
		<type value="Patient"/>
		<url value="../patient/456"/>
		<display value="John Doe"/>
	</patient>
	<structure value="graph"/>
	<subjectsType value="LabReport"/>
	<description value="Sequencing results"/>
	<content><!--Content of the graph--></content>
</UncategorizedData>
{% endhighlight %}</div>

<div class='json_ld'>{% highlight javascript %}
    {
	"text": {
            "status": {
                "value": "generated"
            },
	    "div" : "<div xmlns='http://www.w3.org/1999/xhtml'><p>Data of sequencing results for patient </p></div>",
        },
        "contained": {
            "url": {
                "value": "../patient/456"
            }, 
            "type": {
                "value": "Patient"
            }, 
            "display": {
                "value": "John Doe"
            }
        }, 
        "patient": {
            "url": {
                "value": "../patient/456"
            }, 
            "type": {
                "value": "Patient"
            }, 
            "display": {
                "value": "John Doe"
            }
        }, 
        "description": {
            "value": "Sequencing results"
        },  
        "identifier": {
            "use": {
                "value": "official"
            }, 
            "assigner": {
                "display": {
                    "value": "SMART Genomics"
                }
            }, 
            "period": {
                "start": {
                    "value": "2013-03-16"
                }
            }, 
            "system": {
                "value": "http://genomics.smartplatformgs.org/terms"
            }, 
            "label": {
                "value": "ID for UncategorizedData"
            }, 
            "id": {
                "value": "123"
            }
        }, 
        "structure": {
            "value": "graph"
        }, 
        "subjectsType": {
            "value": "LabReport"
        }
	"content" : {
			...content of the graph...
		}
    }
{% endhighlight %}</div>
</div>

# Utility API Response

<h2 id='Sequence Info'><code>Sequence Info</code></h2>
<li>Utility API response that returns the coordinate for given gene</li>

<div id='Sequence_Info_example'>

<div class='format_tabs'>
  <ul class="nav nav-tabs" data-tabs="tabs">
    <li style="margin-left: 0px;">Example in JSON</li>
    <li class="active"><a href="" data-target="#Lab_Result_examples > div.json" data-toggle="tab"></a></li>
  </ul>
</div>
<div class='json active'>{% highlight javascript %}
{
	"name": "GBA"
	"coordinate": "chr1_155204239_155214253"
}
{% endhighlight %}</div>
</div>

<h2 id='UncategorizedData Info'><code>UncategorizedData Info</code></h2>

<li>API response that shows available Uncategorized Infos' descriptions and identifiers</li>
<div id='UncategorizedData_Info_example'>

<div class='format_tabs'>
  <ul class="nav nav-tabs" data-tabs="tabs">
    <li style="margin-left: 0px;">Example in JSON:</li>
    <li class="active"><a href="" data-target="#UncategorizedData_Info_examples > div.json" data-toggle="tab"></a></li>
  </ul>
</div>
<div class='json active'>{% highlight javascript %}
{	
	"Identifiers" : [
		{
			"description" : "sequencing results",
			"identifier" : "123"
		}
	...Information about other UncategorizedDta...
	]
}
{% endhighlight %}</div>

# CCDA Data Types

<h2 id='Genetic Test Report'><code>Genetic Test Report</code></h2>
<li>A CCDA file is returned; the Results section of the file is filled with data extracted from the patient's genotypic information, while the other sections are left empty</li>

<div class='format_tabs'>
  <ul class="nav nav-tabs" data-tabs="tabs">
    <li style="margin-left: 0px;">CCDA Genetic Test Report in XML:</li>
    <li class="active"><a href="" data-target="#Lab_Result_examples > div.xml" data-toggle="tab"></a></li>
  </ul>
</div>
<div class='xml active'>{% highlight xml %}
<clinicaldocument xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="urn:hl7-org:v3" xsi:schemalocation="urn:hl7-org:v3 CDA.xsd">
 <typeid root="2.16.840.1.113883.1.3" extension="POCD_HD000040">
	<!--Other sections of CCDA-->	
	<!--Results section of CCDA-->
	<component>
            <section>
               <templateId
                  root="2.16.840.1.113883.10.20.22.2.3.1"/>
               <code
                  code="30954-2"
                  codeSystem="2.16.840.1.113883.6.1"
                  codeSystemName="LOINC"
                  displayName="RESULTS"/>
               <title>RESULTS</title>
               <text>
                  <table>
                     <tbody>
                        <tr>
                           <td
                              colspan="2">LABORATORY INFORMATION</td>
                        </tr>
                        <tr>
                           <td
                              colspan="2">Genetic Test Report</td>
                        </tr>
                        <tr>
                           <td>
                           <td>Mutation of G84GG is detected in GBA gene(chr1:155204239~155214653); the mutation has been reported to be associated with Gaucher's Disease</td>
                        </tr>
                     </tbody>
                  </table>
               </text>
               <entry
                  typeCode="DRIV">
                  <organizer
                     classCode="BATTERY"
                     moodCode="EVN">
                     <templateId
                        root="2.16.840.1.113883.10.20.22.4.1"/>
                     <id
                        root="7d5a02b0-67a4-11db-bd13-0800200c9a66"/>
                     <code xsi:type="CE"
                        code="LP28723-2"
                        displayName="Genotyping"
                        codeSystem="2.16.840.1.113883.6.96"
                        codeSystemName="LOINIC"/>
                     <statusCode
                        code="completed"/>
                     <component>
                        <observation
                           classCode="OBS"
                           moodCode="EVN">
                           <templateId
                              root="2.16.840.1.113883.10.20.22.4.2"/>
                           <id
                              root="107c2dc0-67a5-11db-bd13-0800200c9a66"/>
                           <code xsi:type="CE"
                              code="22073-1"
                              displayName="Gauchers disease type 1 gene mutation analysis:Presence or Identity:Point in time:Whole blood/Tissue, unspecified:Nominal:Molecular Genetics"
                              codeSystem="2.16.840.1.113883.6.1"
                              codeSystemName="LOINC"> </code>
                           <statusCode
                              code="completed"/>
                           <effectiveTime
                              value="22073-1"/>
                           <value
                              xsi:type="CD"
                              code="35689-9"
			      displayName="GBA gene.g.G84GG:Arbitrary:Point in time:Whole blood/Tissue, unspecified:Ordinal:Molecular Genetics"
                              codesystem="2.16.840.1.113883.6.1"
			      codsystemName="LOINIC"/>
                           <interpretationCode
                              code="N"
                              codeSystem="2.16.840.1.113883.5.83"/>
                           <methodCode/>
                           <targetSiteCode/>
                           <author>
                              <time/>
                              <assignedAuthor>
                                 <id
                                    root="2a620155-9d11-439e-92b3-5d9816ff4de8"/>
                              </assignedAuthor>
                           </author>>
                        </observation>
                     </component>	
                 </organizer>
               </entry>
            </section>
         </component>
	<!--Other sections of CCDA-->
</clinicaldocument>

{% endhighlight %}</div>






<div class="red_box">
Sequence is intended to be used as base resource for DNASequence, RNASequence, and AminoAcidSequence; direct access is not encouraged.
</div>
