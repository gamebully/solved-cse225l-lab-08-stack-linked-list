Download Link: https://assignmentchef.com/product/solved-cse225l-lab-08-stack-linked-list
<br>
In today’s lab we will design and implement the Stack ADT using linked list.

<table width="0">

 <tbody>

  <tr>

   <td width="319"><strong><u>stacktype.h</u></strong> #ifndef STACKTYPE_H_INCLUDED #define STACKTYPE_H_INCLUDED class FullStack{};class EmptyStack{};template &lt;class ItemType&gt; class StackType{struct NodeType{ItemType info;NodeType* next;};     public:StackType();         ~StackType();         void Push(ItemType);         void Pop();         ItemType Top();         bool IsEmpty();         bool IsFull();     private:NodeType* topPtr;};#endif // STACKTYPE_H_INCLUDED<strong><u>stacktype.cpp</u> </strong> #include &lt;iostream&gt; #include “stacktype.h” using namespace std; template &lt;class ItemType&gt;StackType&lt;ItemType&gt;::StackType(){topPtr = NULL;}template &lt;class ItemType&gt;bool StackType&lt;ItemType&gt;::IsEmpty(){     return (topPtr == NULL);}template &lt;class ItemType&gt;ItemType StackType&lt;ItemType&gt;::Top(){if (IsEmpty())         throw EmptyStack();     elsereturn topPtr-&gt;info; }</td>

   <td width="393">template &lt;class ItemType&gt;bool StackType&lt;ItemType&gt;::IsFull(){NodeType* location;     try     {location = new NodeType;         delete location;         return false;}catch(bad_alloc&amp; exception){return true;} }template &lt;class ItemType&gt;void StackType&lt;ItemType&gt;::Push(ItemType newItem){if (IsFull())         throw FullStack();     else{NodeType* location;         location = new NodeType;         location-&gt;info = newItem;         location-&gt;next = topPtr;         topPtr = location;} } template &lt;class ItemType&gt; void StackType&lt;ItemType&gt;::Pop(){if (IsEmpty())         throw EmptyStack();     else{NodeType* tempPtr;         tempPtr = topPtr;         topPtr = topPtr-&gt;next;         delete tempPtr;} }template &lt;class ItemType&gt;StackType&lt;ItemType&gt;::~StackType(){NodeType* tempPtr;     while (topPtr != NULL){tempPtr = topPtr;         topPtr = topPtr-&gt;next;         delete tempPtr;}}</td>

  </tr>

 </tbody>

</table>







Generate the <strong>driver file (main.cpp) </strong>where you perform the following tasks. Note that you cannot make any change to the header file or the source file.

<table width="0">

 <tbody>

  <tr>

   <td width="345"><strong>Operation to Be Tested and Description of Action </strong></td>

   <td width="191"><strong>Input Values </strong></td>

   <td width="167"><strong>Expected Output </strong></td>

  </tr>

  <tr>

   <td width="345">•     Take infix expressions from the user as input, determine the outcome of the expression and gives that back to user as output, or the text “Invalid expression” if the expression is not a valid one. You will have to solve this problem in two steps. First, you have to convert the expression from infix notation to postfix notation. You are going to need a stack in order to do so. In the next step, you will have to evaluate the postfix expression and determine the final result. Again, you will need a stack in order to do this. All the operands in the infix expressions are single digit non-negative operands and the operators include addition (+), subtraction (-), multiplication (*) and division (/).</td>

   <td width="191">10 + 3 * 5 / (16 – 4) (5 + 3) * 12 / 33 + 4 / (2 – 3) * / 57 / 5 + (4 – (2) * 3</td>

   <td width="167"> 11.2532Invalid expressionInvalid expression</td>

  </tr>

 </tbody>

</table>

<strong> </strong>