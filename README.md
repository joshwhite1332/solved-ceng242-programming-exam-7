Download Link: https://assignmentchef.com/product/solved-ceng242-programming-exam-7
<br>
In this exam, you are going to construct some n-ary trees and handle some operations on them.

<ol>

 <li>The problem starts with the construction of the trees. For this, you are given some <em>&lt;</em>parent-child<em>&gt; </em>relationships in an <strong>unordered way</strong>, and you are expected to construct the corresponding tree(s) properly. For example:</li>

</ol>

<table width="573">

 <tbody>

  <tr>

   <td width="171">addRelation(18, 35)</td>

   <td colspan="4" width="402">The parent-child sequence given on the left</td>

  </tr>

  <tr>

   <td width="171">addRelation(20, 17) addRelation(10, 30)</td>

   <td colspan="3" width="295">results in 3 independent trees:</td>

   <td width="107"> </td>

  </tr>

  <tr>

   <td width="171">addRelation(10, 44)</td>

   <td width="119">tree-1:</td>

   <td width="115">20</td>

   <td width="61">tree-2:</td>

   <td width="107">65</td>

  </tr>

  <tr>

   <td width="171">addRelation(80, 100)</td>

   <td width="119">/</td>

   <td width="115">     |        </td>

   <td width="61"> </td>

   <td width="107">/              </td>

  </tr>

  <tr>

   <td width="171">addRelation(35, 43)</td>

   <td width="119">17</td>

   <td width="115">     19        18</td>

   <td width="61"> </td>

   <td width="107">26             10</td>

  </tr>

  <tr>

   <td width="171">addRelation(20, 19)</td>

   <td width="119">|</td>

   <td width="115">/ </td>

   <td width="61"> </td>

   <td width="107">/ | </td>

  </tr>

  <tr>

   <td width="171">addRelation(65, 26)</td>

   <td width="119">16</td>

   <td width="115">             35        42</td>

   <td width="61"> </td>

   <td width="107">        12            30 44</td>

  </tr>

  <tr>

   <td width="171">addRelation(48, 60)</td>

   <td width="119"> </td>

   <td width="115">|</td>

   <td width="61"> </td>

   <td width="107"> </td>

  </tr>

  <tr>

   <td width="171">addRelation(10, 12) addRelation(65, 10) addRelation(48, 70)</td>

   <td width="119"> </td>

   <td width="115">43</td>

   <td width="61"> </td>

   <td width="107"> </td>

  </tr>

  <tr>

   <td width="171">addRelation(20, 18)</td>

   <td width="119">tree-3:</td>

   <td width="115">____48____</td>

   <td width="61"> </td>

   <td width="107"> </td>

  </tr>

  <tr>

   <td width="171">addRelation(17, 16)</td>

   <td width="119"> </td>

   <td width="115">/           /              </td>

   <td width="61"> </td>

   <td width="107"> </td>

  </tr>

  <tr>

   <td width="171">addRelation(48, 80)</td>

   <td colspan="3" width="295">                                   60        70        80        90</td>

   <td width="107"> </td>

  </tr>

  <tr>

   <td width="171">addRelation(18, 42)</td>

   <td colspan="3" width="295">|</td>

   <td width="107"> </td>

  </tr>

  <tr>

   <td width="171">addRelation(48, 90)</td>

   <td colspan="3" width="295">100</td>

   <td width="107"> </td>

  </tr>

 </tbody>

</table>

As you see, child may be introduced before its parent in the input. It is ensured that any independent tree have unique nodes (i.e. distinct nodes from those of the other trees). Also, there will be no repetition in the input (like giving the same parent-child relationship). Moreover, ordering between the children of a node is not important.

<ol start="2">

 <li><strong>cpp: </strong>Node is the most fundamental class in this task. It represents a node holding a unique id and it is actually a tree at the same time whose starting node is itself and may have some children and a parent (if it is itself a child of another tree).</li>

</ol>

<table width="321">

 <tbody>

  <tr>

   <td width="53"> </td>

   <td width="137">?|</td>

   <td width="130">may have parent</td>

  </tr>

  <tr>

   <td width="53">Node:</td>

   <td width="137">[ int id ]/ / ….  </td>

   <td width="130"> </td>

  </tr>

  <tr>

   <td width="53"> </td>

   <td width="137">? ? … ? ?</td>

   <td width="130">may have children</td>

  </tr>

 </tbody>

</table>

This class has some some basic methods like constructor, destructor, copy cons., operator overload, etc. Each one is explained in the header file in a detailed way.

(a) <strong>DataNode.cpp: </strong>DataNode is a derivation of Node class. The difference from Node is that it also carries a char value other than id. Except than having a char data, it has the same properties with Node class. However, the implementation of some methods of DataNode may slightly differ from those of Node. These details are given in the header.

<ol start="3">

 <li><strong>cpp: </strong>NodeManager is the class carrying the independent tree pieces (i.e. independent Node objects). This class also has 3 important methods other than constructor/destructor:

  <ul>

   <li>First, it provides to add new <em>&lt;</em>parent-child<em>&gt; </em>relationships via addRelation(int parent.id, int child.id) An illustration of sequential calls of this method is given above, at article 1.</li>

   <li>Second, it enables to convert the type of a Node object into DataNode object via setDataToNode(char data, int node.id) method in which you need to find the related method and replace it with a new node of DataNode.</li>

   <li>Third, it has getNode(int node.id) method which simply returns the corresponding node.</li>

  </ul></li>

 <li><strong>cpp: </strong>Action is an abstract base class which inherits a single method named act(const Node&amp; node) to its derivations. How the action becomes depends on the derivated class, yet we can say that it conducts some operations on the given node and returns the output tree.

  <ul>

   <li><strong>cpp: </strong>CompleteAction is a derivation of abstract Action class. Its constructor saves a Node object as its member. It derives the act(const Node&amp; node) method as follows: The node object given in the parameter and the one kept as member are compared along their children one by one and produced a new tree (Node object). It is ensured that both input trees (namely Node object) has the same structure and nodes with corresponding ids. If there is object of Node type at the corresponding positions of trees, there is nothing special to do. The output tree will have the same Node object in that case. However, there may be DataNode objects at some places in the first tree instead of some bare Node objects whereas they are simply a Node object in the second tree, or vice versa. Then, in such a case the output tree will have the DataNode object at that position. Below, act() operation of</li>

  </ul></li>

</ol>

<table width="611">

 <tbody>

  <tr>

   <td colspan="3" width="321">CompleteAction class is illustrated:</td>

   <td colspan="3" width="290"> </td>

  </tr>

  <tr>

   <td colspan="3" width="321">100</td>

   <td colspan="3" width="290">[100,’G’]</td>

  </tr>

  <tr>

   <td colspan="3" width="321">___/ | ___</td>

   <td width="160">                            /             |</td>

   <td colspan="2" width="130"></td>

  </tr>

  <tr>

   <td colspan="3" width="321">             20             [50,’A’] 10</td>

   <td width="160">             [50,’A’]                20</td>

   <td colspan="2" width="130">[10,’H’]</td>

  </tr>

  <tr>

   <td colspan="3" width="321">             /                /                     </td>

   <td width="160">               /                        /</td>

   <td colspan="2" width="130"></td>

  </tr>

  <tr>

   <td colspan="3" width="321">        3          7        1        90             [2,’C’]</td>

   <td width="160">90 [1,’I’] 3 7</td>

   <td colspan="2" width="130">[2,’C’]</td>

  </tr>

  <tr>

   <td colspan="3" width="321">                   /                    |               / | _</td>

   <td width="160">        |                                      / </td>

   <td colspan="2" width="130">             /        |          </td>

  </tr>

  <tr>

   <td colspan="3" width="321">[5,’B’] 4                            8               30 40 [9,’F’]</td>

   <td width="160">        8                                 4</td>

   <td colspan="2" width="130">5                 9 [40,’K’] 30</td>

  </tr>

  <tr>

   <td colspan="3" width="321">/ </td>

   <td width="160">/ </td>

   <td colspan="2" width="130"> </td>

  </tr>

  <tr>

   <td colspan="3" width="321">6 [70,’D’]</td>

   <td width="160">6           70</td>

   <td colspan="2" width="130"> </td>

  </tr>

  <tr>

   <td colspan="3" width="321">/ </td>

   <td width="160">/ </td>

   <td colspan="2" width="130"> </td>

  </tr>

  <tr>

   <td width="53"> </td>

   <td width="252">[60,’E’] 80</td>

   <td colspan="3" width="183">60 [80,’J’]</td>

   <td width="122"> </td>

  </tr>

  <tr>

   <td width="53"> </td>

   <td width="252">(tree1)</td>

   <td colspan="3" width="183">(tree2)</td>

   <td width="122"> </td>

  </tr>

  <tr>

   <td width="53"></td>

   <td width="252"></td>

   <td width="15"></td>

   <td width="160"></td>

   <td width="8"></td>

   <td width="122"></td>

  </tr>

 </tbody>

</table>

Assume that a CompleteAction object was constructed previously by calling CompleteAction(tree1). After act() method of CompleteAction class is called with the tree2 as its argument, it is expected to return tree3 below:

[100,’G’]

<table width="412">

 <tbody>

  <tr>

   <td width="176">__/</td>

   <td width="237">|             __</td>

  </tr>

  <tr>

   <td width="176">[50,’A’]</td>

   <td width="237">20                     [10,’H’]</td>

  </tr>

  <tr>

   <td width="176">/ </td>

   <td width="237">/                                </td>

  </tr>

  <tr>

   <td width="176">90 [1,’I’]</td>

   <td width="237">3 7                               [2,’C’] _______</td>

  </tr>

  <tr>

   <td width="176">|</td>

   <td width="237">       /                         /                                </td>

  </tr>

  <tr>

   <td width="176">8/ 6 [70,’D’]/ [60,’E’] [80,’J’]</td>

   <td width="237">4 [5,’B’] [9,’F’] [40,’K’] 30</td>

  </tr>

 </tbody>

</table>

(tree3)

(The ordering of the siblings is not important)

<ul>

 <li><strong>cpp: </strong>CutAction is a derivation of abstract Action class. Its constructor saves a char value as its member, say data. It derives the act(const Node&amp; node) method as follows: It applies some cut operation on the nodes of the argument tree that satisfy a basic rule. If a node has at least 2 char value which is same with the data at the total of its children and grandchildren, then that node is cut such that in the output tree it is replaced with a new node of type DataNode which has data as its char value and has no child. <strong>Note that cut operation should start from the leaves and proceeded towards the root (i.e. from down to up). If you do it in the reverse manner, the result may change! </strong>Below, act() operation of CutAction class is illustrated:</li>

</ul>

100                                                                                                                   100

___/ | ___                                                                                                     __/ | _

20               50               10                                                                               20             50        10

/                /                                                               ===&gt;                         /                /            

3          7        1        90                  2                                                                  3        7        1             90 [2,’*’]

/                    |               / | __                                                                   /                  |

[5,’*’] 4                     8               30 40 [9,’*’]                                                  [5,’*’] 4 [8,’*’]

/                       

6 [70,’*’] [242,’*’]

/ 

[60,’*’] [80,’*’]

(tree1)                                                                                                               (tree2)

Assume that a CutAction object was constructed previously by calling

CutAction(’*’). After act() method of CutAction class is called with

the tree1 as its argument, it is expected to return the tree2.

(The ordering of the siblings is not important)

(c) <strong>CompositeAction.cpp: </strong>CompositeAction is a derivation of abstract Action class. This action is the composition of the other actions. It allows actions to be added using the

CompositeAction* addAction(const Action* action) method (notice that this method returns a reference to the object itself, i.e., return the ”this” pointer, for syntactic purposes). Note that CompositeAction is not responsible for deleting child actions when it is destructed. You may assume that there will be at least one child action added to a CompositeAction object.

<ol start="5">

 <li><strong>h: </strong>This is implemented by the author and directly supplied to you. There is nothing that you need to implement on it. It includes an InvalidRequest exception which you may need in your implementations when any data is queried from a Node yet not DataNode object.</li>

</ol>