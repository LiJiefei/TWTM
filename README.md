Tag-Weighted Topic Model for Mining Semi-Structured Documents
============================================================
The code of http://dl.acm.org/citation.cfm?id=2540540 <br/>
Author: Shuangyin Li, Jiefei Li, Rong Pan <br/>
<br/>
Any question about code please contact us by email lijiefei@mail2.sysu.edu.cn.<br/>

Source Code
------------------------------------------------------------
src/ <br/>
<br/>

Install
-------------------------------------------------------------
cd src/ && make <br/>


Usage
-------------------------------------------------------------
###Input file format: <br/>
DocNumLabels label1 label2 ... @ DocNumWords word1 word2 ...<br/>
DocNumLabels label1 label2 ... @ DocNumWords word1 word2 ...<br/>
DocNumLabels label1 label2 ... @ DocNumWords word1 word2 ...<br/>

Each row represent one document with labels. DocNumLables means the number labels of document. DocNumWords means the number words of document. Each label is integer and represent one label. Each word is integer and represent one word.<br/>
<br/>
demo/twtm.demo.input is a simple demo input file.<br/>
demo/label.txt is the label dictionary file. The word in row 1 means the label0.<br/>
demo/words.dic is the word dictionary file.<br/>
<br/>
<br/>
###Training:<br/>
```
./twtm est <input data file> <setting.txt> <num_topics> <model save dir>
```
Example: <br/>
```
./src/twtm est demo/twtm.demo.input src/setting.txt 10 demo/model
```

###Inference:<br/>
There are two methods to inference a new document's topic distribution. <br/>
One is still using the labels of new document to inference.<br/>
```
./twtm inf <input data file> <setting.txt> <model dir> <prefix> <output dir>
```
Example:  <br/>
```
./src/twtm inf demo/twtm/demo.input src/setting.txt demo/model/ final demo/output/
```

One is just using the words of new document. So with the TWTM model, we can inference some new document without any label just like LDA model. <br/>

```
./twtm lda-inf <input data file> <setting.txt> <model dir> <prefix> <output dir>
```

Example: <br/>
```
./src/twtm lda-inf demo/twtm/demo.input src/setting.txt demo/model/ final demo/output/
```


