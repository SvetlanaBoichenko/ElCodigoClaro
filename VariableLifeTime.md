# 1
class BeAlarm
{
   protected:
    int         FCurrentIP;
    int         FCount;
    ..
};
class BeAlarm
{
   private:
    int         FCurrentIP;
    int         FCount;
    ..
};  
 // Изменила уровень досиупа на более строгий

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


