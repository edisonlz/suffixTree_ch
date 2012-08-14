SuffixTree --- A Suffix Tree library for Python Chinese 

Conspirator: Danny Yoo (dyoo@hkn.eecs.berkeley.edu)

This is a SWIG wrapper around Dan Gusfield's 'strmat' suffix tree
library.

    http://www.cs.ucdavis.edu/~gusfield/strmat.html

Suffix trees allow for very powerful string matching, and are used
quite a bit in many elegant string algorithms.  Since this is a
wrapper around strmat.stree, most of the documentation in
doc/stree.doc should apply.


Here are the modules included in the SuffixTree package:

    o SuffixTree.SuffixTree -- The suffix tree structure.  This is a
      thin wrapper around strmat's stree data structure.  This isn't a
      complete wrapper yet; I need to find some time to complete this.
      The wrapper appears to be good enough for simple stuff.

      Methods of SuffixTree:

          o SuffixTree(alphabet=STREE_ASCII)

              Construct a new SuffixTree.  By default, the alphabet
              used by the SuffixTree is ASCII.  Other choices include
              STREE_DNA, STREE_RNA, and STREE_PROTEIN.

          o add(string, id)

              Adds a string to the suffix tree with an id.

          o root()

              Returns the root() SuffixNode of the tree.

          o num_nodes():

              Returns the total number of nodes held in the tree.

          o match(string)

              Given a string, traverse the suffix tree and return a
              3-tuple (match_length, suffix_node, endpos)
              
              

    o SuffixTree.SuffixNode  (I need to fix the documentation here)

        Methods of 
        num_children()
        find_child(char ch)
        children()
        next()
        parent()
        suffix_link()
        edgelen()
        edgestr()
        getch()
        labellen()
        labelstr()
        ident()
        num_leaves()
        leaf(int leafnum)



    o SuffixTree.SubstringDict -- An application of suffix trees toward
      substring matching.  An example might help:

      >>> #coding=utf-8
      >>> from SuffixTree import SubstringDict
      

      >>> sd = SubstringDict()
      >>> sd.__setitem__("我是python程序员",1)
      >>> sd.__setitem__("我是ruby程序员",2)
      >>> sd.__setitem__("我是javascript程序员",3)
      >>> sd.__setitem__("我是android程序员",4)
      >>> sd.__setitem__("我还是DBA",4)
      >>> print sd[“我是”]
      >>> print sd[“我还是”]



      >>> sd = SubstringDict()
      >>> sd["我是python程序员"] = 1
      >>> sd["我是ruby程序员"] = 2
      >>> sd["我是javascript程序员"] = 3
      >>> sd["我是android程序员"] = 4
      >>> sd["我还是DBA"] = 5
      >>> print sd[“我还是”]


      SubstringDict provides a mapping that allows for substrings of
      keys.  The keys do need to be strings though.

      支持中文的方式是使用 base64，数据量回增加30％，对性能回有些损耗，但是，损耗不大

      64 位 安装 ：
      ARCHFLAGS="-arch i386 -arch x86_64" python setup.py install

