# SEF - Laboratory 1 Exercise
In an information storage pseudo-system the following class hierarchies are considered:

Class Document has an attribute which is a sequence of strings (modelled either as an array, or as a list), and which corresponds to the whole text stored in the document. It also has a method suitable for displaying this text. The class also has a method analyze which returns a new sequence of strings, and whose implementation depends on the concrete type of document. The documents can be of two types:


1. XML. In this document, the information is represented as tags, each string in the sequence is either an opening tag (ex. "<name_tag>"), either a string, or an end tag  (ex. "</name_tag>"). The analyze method returns a sequence of strings obtained by removing the beginning and end tags. The method suitable for displaying the text will return “XML” followed by the whole text of the document (including the tags). Example, assume a document with the follwoing content: <tag1> value1 </tag1> <tag2> </tag2> <tag3> value2 </tag3>
   The _analyze()_ method will return for this document the sequence: value1, value2
   It is taken as a given that the initial string sequence of the document will always correspond to the described format.

2. JSON. In this document, the elements of the string sequence are either names (like “name”), or a string value. The _analyze()_ method returns a sequence of strings obtained by removing all the names from the initial sequence. The method suitable for displaying the text will return “JSON” followed by the whole text of the document (including the names). Example, assume a document with this content: name1: value1 name2: value2. After the name elements there is a ‘:’ character, and for the given example the analyze method returns: value1, value2.
   It is taken as a given that the initial string sequence of the document will always correspond to the described format.

In this system any document can be processed using a Processor. The following types of processors are considered:

1. SearchProcessor. This processor has a string attribute which is initialized via the constructor, and which corresponds to the text that will be searched for. The process method receives as parameter a sequence of documents and works in the following way: for each text obtained by analyzing a document (so with no tags or names considered)  all occurences of the search query (the searched for string) are counted. The method returns the total number of occurences of the search query in all documents from the processed document sequence.

2. CompositeProcessor. This processor contains a sequence of processors (search processors or other composed processors). The process method receives as parameter a sequence of documents and works in the following way: it returns the sum of the results obtained by applying each processor from its processor sequence on all documents received as parameter by the process method.

Whenever it is needed, the sequences are initialized and/or populated either via the constructor or by using a suitable add element method.


## Requirements:

- Implement the classes described above together with any other needed classes, by working in IntelliJ IDEA (mandatory). The code will be split in the following packages:
  * loose.oose.sef.documents for the classes in the document class hierarchy;
  * loose.oose.sef.processors for the classes in the processor class hierarchy;
  * loose.oose.sef (the root package for this project) will contain the Main class.

- Generate automatically the setter/getter method pairs for the attributes of class Document and the display method (toString)

- Test the correct functionality of the above system by implementing a Main class which:
  1)	Instantiates at least 2 documents (one of each type) based on the texts received as model
  2)	Instantiates at least 3 search processors, 1 composed processor that contains the first 2 search processor and 1 composed processor that contain the previous composed processor and the third search processor
  3)	Calls the process method on the last composed processor with a sequence of documents containing the objects instantiated at 1)
  4)	Debug the call to the process method.


- Refactor automatically the name of the string attribute of class SearchProcessor
