---
layout: page
title: SMART Genomics API Calls
includenav: smartnav.markdown
---
{% include JB/setup %}

<div id="toc"></div>




# coordinte_id
<ul>
SMART Genomics API uses identifiers of format below to identify with a region within the genome:<br><br>
<code>Chromosome_startpos_endpos</code><br><br>
For example, <code>chr7_123_456</code> identifies with a region within chromosome 7 that starts from position 123 to 456.
</ul>
# Record Calls

## Sequence
<ul>
<li>URI:<code> GET /records/{record__id}/sequence </code></li>
</ul>
<ul>
<li>Get specified <code>Sequence</code> with following parameters:</li><br>
<code>sequence : ID__list</code><br>
<code>isMapped : [true/false]</code><br><br>
</ul>
<ul>
<code>ID__list</code> is a space delimited list of Sequence ID (<code>Sequence</code> is intended to be used as base resource for <code>DNASequence</code>, <code>RNASequence</code>,and <code>AminoAcidSequence</code>; each <code>Sequence</code> is identified with an internal ID instead of with a <code>coordinate_id</code>).<br>
<code>isMapped</code> is an optional filter that filers out all unmapped <code>Sequence</code> (sequences that mapped to a region within the genome) when it's <code>true</code>, and filters out all mapped <code>Sequence</code> when it's <code>false</code>; when not specified, all sequences linked to <code>ID__list</code> will be returned.<br>
</ul>
Look up <code>Sequence</code> ID with [Sequence Info](#section4.1)<br><br>
[Details about Sequence](../data_model/#Sequence)

## DNASequence
<ul>
<li>URI:<code> GET /records/{record__id}/dnasequence </code></li>
</ul>
<ul>
<li>Get specified <code>DNASequence</code> with following parameter:</li><br>
<code>coordinates : coordinate__list</code><br><br>
</ul>
<ul>
<code>coordinate__list</code> is a space delimited list of <code>coordinate_id</code>
</ul>
[Details about DNASequence](../data_model/#DNASequence)

## RNASequence
<ul>
<li>URI:<code> GET /records/{record__id}/rnasequence </code></li>
</ul>
<ul>
<li>Get specified <code>RNASequence</code> with following parameter:</li><br>
<code>coordinates : coordinate_list</code><br><br>
</ul>
<ul>
<code>coordinate__list</code> is a space delimited list of <code>coordinate_id</code>, which identifies the region from which the RNA sequence is transcribed from.
</ul>
[Details about RNASequence](../data_model/#RNASequence)

## AminoAcidSequence
<ul>
<li>URI:<code> GET /records/{record_id}/protein/ </code></li>
</ul>
<ul>
<li>Get specified <code>AminoAcidSequence</code> for a patient with following parameter:</li><br>
<code>coordinates : coordinate__list</code><br><br>
</ul>
<ul>
<code>coordinate__list</code> is a space delimited list of <code>coordinate_id</code>, which identifies the region from which the animo sequence is translated from.
</ul>
[Details about AminoAcidSequence](../data_model/#AminoAcidSequence)

## Gene
<ul>
<li>URI:<code> GET /records/{record_id}/gene/ </code></li>
</ul>
<ul>
<li>Get specified Gene for a patient with following parameter:</li><br>
<code>coordinates : coordinate__list</code><br><br>
</ul>
<ul>
<code>coordinate__list</code> is a space delimited list of <code>coordinate_id</code>, which identifies the region where the gene is located.
</ul>
[Details about Gene](../data_model/#Gene)

## Variant
<ul>
<li>URI:<code> GET /records/{record_id}/variant </code></li>
</ul>
<ul>
<li>Get specified Variant with following parameters:</li><br>
<code>reference : coordinate__list</code><br><br>
</ul>
<ul>
<code>coordinate__list</code> is a space delimited list of <code>coordinate_id</code>, which identifies the reference sequence of a variant.<br> 
</ul>
[Details about Variant](../data_model/#Variant)
<br><br>

## Alignment
<ul>
<li>URI:<code> GET /records/{record_id}/alignment </code></li>
</ul>
<ul>
<li>Get specified <code>Alignment</code> with following parameters:</li><br>
<code>reference : coordinate__id</code><br>
<code>query : coordiante__id</code><br><br>
</ul>
<ul>
<li><code>reference</code> and <code>query</code> are the <code>coordinate__id</code> of the reference sequence and query sequence for an <code>Alignment</code></li>
</ul>
[Details about Alignment](../data_model/#Alignment)
<br><br>

## UncategorizedData
<ul>
<li>URI:<code> GET /records/{record_id}/uncategorizeddata </code></li>
</ul>
<ul>
<li>Get specified UncategorizedData with following parameter:</li><br>
<code>data : data__list</code><br><br>
</ul>
<ul>
<code>data__list</code> is a space delimited list of <code>data_id</code><br>
</ul>
Look up <code>data_id</code> with [UncategorizedData Info](#section4.2)<br><br>
[Details about UncategorizedData](../data_model/#UncategorizedData)
<br><br>


# Utility API
## Sequence Info
<ul>
<li>URI:<code> GET /records/{record_id}/sequence_info </code></li>
</ul>
<ul>
<li>Get ID for specified Sequence with following parameters:</li><br>
<code>type : type of sequence</code>(dna/rna/amino_acid)<br>
<code>coordinates : coordinate__list</code><br><br>
</ul>
[Details about Sequence Info](../data_model/#Sequence Info)
<br><br>

## UncategorizedData Info
<ul>
<li>URI:<code> GET /records/{record_id}/uncategorizeddata_info </code></li>
</ul>
Get IDs for all UncategorizedData<br><br>
[Details about UncategorizedData Info](../data_model/#UncategorizedData Info)
<br><br>

# CCDA API
## Genetic Test Report
<ul>
<li>URI:<code> GET /records/{record_id}/genetic__test_report/ </code></li>
</ul>
[Show Example CCDA file for Genetic Test Report](../data_model/#Genetic Test Report)
<br><br>



<div class="red_box">
If an API is not called with any parameters, all data from the directory will be returned.
</div>





