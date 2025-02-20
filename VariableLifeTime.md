# 1
class BeAlarm  
{  
   protected:  
    int         FCurrentIP;  
    int         FCount;  
    ..  
};  
//----------------  
class BeAlarm  
{
   private:  
    int         FCurrentIP;  
    int         FCount;  
    ..  
};    
 // Изменила уровень досnупа на более строгий

 # 2
 ..  
  Node cur_node = this.head;  
  while (cur_node != null) {  
            if (cur_node.value == _value){  
                return cur_node;  
            cur_node = cur_node.next;//.next;  
        }  
 ..  
}  
//-----------------   
  Node FindValue (Node listHead) {  
    Node cur_node = listHead;  
    while (cur_node != null) {  
      if (cur_node.value == _value){  
          return cur_node;  
          cur_node = cur_node.next;  
       }  
  }  
return null;  
}   
// Перенесла поиск узла у отдельную функцию  

# 3
ArrayList<Node> nodes = new ArrayList<Node>();  
if (this.head == null)  
      return nodes;  
if (this.head.next == null && this.head.value == _value) {   
      nodes.add(this.head);  
      return (nodes);  
}  
if (this.head.next == null) {  
            return nodes;  
}  
//--------------------------  
Node LookBorderCase (Node listHead) {   
   ArrayList<Node> nodes = new ArrayList<Node>();   
   if (listHead == null)  
      return nodes;  
   if (listHead.next == null && listHead.value == _value) {     
      nodes.add(this.head);   
      return (nodes);  
   }   
   if (listHead.next == null) {   
         return nodes;  
   }   
}  
//Перенесла поиск пограничных случаев для узлов в отдельную функцию

# 4
 if (this.head == null && _nodeAfter == null) {  
            this.head = _nodeToInsert;  
            _nodeToInsert.next = null;  
            tail = _nodeToInsert;  
            this.nodecount++;  
            return;  
        }  
        if (_nodeAfter == null) {  
            this.head.prev = _nodeToInsert;  
            _nodeToInsert.next = this.head;  
            this.head = _nodeToInsert;  
            this.head.prev = null;  
            this.nodecount ++;  
            return;  
        }  
        if (this.head == _nodeAfter && this.head.next != null) {   
            _nodeToInsert.prev = this.head;  
            _nodeToInsert.next = this.head.next;  
            _nodeToInsert.next.prev = _nodeToInsert;  
            this.head.next = _nodeToInsert;  
            this.nodecount++;  
            return;  
        }  
        if (this.head == _nodeAfter) {  
            _nodeToInsert.prev = head;  
            this.head.next = _nodeToInsert;  
            _nodeToInsert.next = null;  
            tail = _nodeToInsert;  
            this.nodecount++;  
            return;  
        }  
        if (_nodeAfter == tail) {  
            _nodeAfter.next = _nodeToInsert;  
            _nodeToInsert.prev = _nodeAfter;  
            _nodeToInsert.next = null;  
            tail = _nodeToInsert;  
            this.nodecount++;  
            return;  
        }  
        ..
   }   
   //-----------------  
   bool InsertForBorderCase (LinkedList2 list, Node _nodeAfter, Node _nodeToInsert) {  
      Node listHead = list.head;
      Node listTail = list.tail;
      
      if (this.head == null && _nodeAfter == null) {  
            listHead = _nodeToInsert;  
            _nodeToInsert.next = null;  
            listTail = _nodeToInsert;  
            return true;  
        }  
        if (_nodeAfter == null) {  
            listHead.prev = _nodeToInsert;  
            _nodeToInsert.next = this.head;  
            listHead = _nodeToInsert;  
            listHead.prev = null;   
            return true;  
        }  
        if (this.head == _nodeAfter && this.head.next != null) {   
            _nodeToInsert.prev = this.head;  
            _nodeToInsert.next = this.head.next;  
            _nodeToInsert.next.prev = _nodeToInsert;  
            listHead.next = _nodeToInsert;   
            return true;  
        }  
        if (this.head == _nodeAfter) {  
            _nodeToInsert.prev = head;  
            listHead.next = _nodeToInsert;  
            _nodeToInsert.next = null;  
            listTail = _nodeToInsert;  
            return true;  
        }  
        if (_nodeAfter == tail) {  
            _nodeAfter.next = _nodeToInsert;  
            _nodeToInsert.prev = _nodeAfter;  
            _nodeToInsert.next = null;  
            listTail = _nodeToInsert;  
            return true;   
        }  
      return false;  
   }  
   //Перенесла вставку узлов в список для пограничных случаев в отдельную функцию
        
# 5





