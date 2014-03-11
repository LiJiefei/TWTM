Tag-Weighted Topic Model for Mining Semi-Structured Documents
============================================================
The code of http://dl.acm.org/citation.cfm?id=2540540
Author: Shuangyin Li, Jiefei Li, Rong Pan

Any question about code please contact us by email lijiefei@mail2.sysu.edu.cn.

Source Code
------------------------------------------------------------
src/


Install
-------------------------------------------------------------
cd src/ && make


Usage
-------------------------------------------------------------
Input file format:
DocNumLabels label1 label2 ... @ DocNumWords word1 word2 ...
DocNumLabels label1 label2 ... @ DocNumWords word1 word2 ...
DocNumLabels label1 label2 ... @ DocNumWords word1 word2 ...

Each row represent one document with labels. DocNumLables means the number labels of document. DocNumWords means the number words of document. Each label is integer and represent one label. Each word is integer and represent one word.

demo/twtm.demo.input is a simple demo input file.
demo/label.txt is the label dictionary file. The word in row 1 means the label0.
demo/words.dic is the word dictionary file.


Training:
./twtm est <input data file> <setting.txt> <num_topics> <model save dir>
Example: ./src/twtm est demo/twtm.demo.input src/setting.txt 10 demo/model

Inference:
There are two methods to inference a new document's topic distribution.
One is still using the labels of new document to inference.

./twtm inf <input data file> <setting.txt> <model dir> <prefix> <output dir>
Example: ./src/twtm inf demo/twtm/demo.input src/setting.txt demo/model/ final demo/output/

One is just using the words of new document. So with the TWTM model, we can inference some new document without any label just like LDA model.

./twtm lda-inf <input data file> <setting.txt> <model dir> <prefix> <output dir>
Example: ./src/twtm lda-inf demo/twtm/demo.input src/setting.txt demo/model/ final demo/output/


