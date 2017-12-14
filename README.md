Author: Marie Dubremetz
**Description**
This script has been written because currently stanford coreNLP do not support lemmatization for the french language. Thus it takes the output file of stanford coreNLP (in XML) and pass each words through tree-tagger individually.

**Input/output**

(File).xml->(file).lem.xml

**Preriquisites**

You need to install and be able to use Tree-Tagger and stanford coreNLP

**Purpose:**

Given a xmlfile parsed by stanford, the script replace all the words under the tag "\<lemma\>" by the lemmatized version

First run your stanford parser on your french text with output xml (with the annotator lemma, which will not do anything except from adding the "lemma" tag with the word in it.
For me the command was:

		java -mx3g -cp "*" edu.stanford.nlp.pipeline.StanfordCoreNLP -props StanfordCoreNLP-french.properties -annotators tokenize,ssplit,pos,lemma,parse -file myfile -outputFormat xml
		
**Usage:**

		$bash baseline.sh myfile.xml
		
**old output:**

		 <token id="1">
		 <word>les</word>
		 <lemma>les</lemma>
		 <CharacterOffsetBegin>0</CharacterOffsetBegin>
		 <CharacterOffsetEnd>7</CharacterOffsetEnd>
		 <POS>V</POS>
		 
**Example of desired output:**

		 <token id="1">
		 <word>les</word>
		 <lemma>le</lemma>
		 <CharacterOffsetBegin>0</CharacterOffsetBegin>
		 <CharacterOffsetEnd>7</CharacterOffsetEnd>
		 <POS>V</POS>
		 
**Disclamer**

This is a totally unofficial patch that overcomes the lack of lemmatization of Stanford coreNLP. It works only on the XML version with the annotators in the java command that I gave above!
Since it lemmatizes words one by one the performance might be lower than usual and the process is very slow!

**Contact**

Marie Dubremetz. firstname.lastname@lingfil.uu.se

**Licence**


You may cite the papers related to the version of the parser you use (Stanford CoreNLP) and TreeTagger
