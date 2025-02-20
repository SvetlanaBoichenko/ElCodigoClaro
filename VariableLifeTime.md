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
..  
extern char    FInpBuf[];  
extern char    FOutBuf[];  
..  
//-------------------
char    FInpBuf[IO_BUF_LEN+1];    
char    FOutBuf[IO_BUF_LEN+1];    
#ifndef PZU   
    void ASC_viIsrRx (void) interrupt S0RINT  
#else  
    static void ASC_viIsrRx (void) interrupt S0RINT using rx_reg  
#endif  
{  
    if (NetMode == RECEIVE)  	
    {  
        inp_byte = ASC_uwGetData();   
        if (FrameInputFlag == false)    
        {  
            switch (inp_byte)  
            {  
            case    '$':  
            case    '#':  
                FInpBufLen = 0;  
                FrameInputFlag = true;  
                break;  
            }  
        }    
        ..  
        ..  
   }  
void CodeFrom()  
{  
    NetErrorFlag = false;    
    FInpCommand = NET_COMMAND_NONE;  
    FOutCommand = NET_COMMAND_NO_ANSWER;  
    FNetPort = 0;  
    if (FInpBuf[FInpBufLen-1] != CR)  
    {
        NetErrorFlag = true;  
        return;  
    }  
    FInpBufLen--;  
..    
..    
}    
// Объединила чтение порта и обработку прочитанного в один модуль, сделала массв не глобальным  

# 6
extern uint PortParamTab[PORT_COUNT][PORT_PARAM_COUNT];
//-------------------  
uint PortParamTab[PORT_COUNT][PORT_PARAM_COUNT]  
void    SetBusPortFunction (int portno, uint basebit, uint lastbit)  
{  
    if ((IsBusSignal (basebit) == false) || (IsBusSignal (lastbit) == false))  
    {  
        SetError();  
        return;  
    }  
    InitPort (basebit, lastbit);  
    PortParamTab[portno][PORT_PARAM_basebit]    = basebit;     
    PortParamTab[portno][PORT_PARAM_lastbit]    = lastbit;      
}  
//Убрала объявление переменной как глобальной. Не было больше использования  

# 7-8
extern unsigned long   Freq;
extern unsigned long   TimeCount;
extern long            ZubCount; 
//--------------------  
extern unsigned long   Freq;  
unsigned long   TimeCount;  
long            ZubCount;  
oid GT2_viIsrCAPREL(void) interrupt 0X27  
{  
	ZubCount++;  
   TimeCount += CAPREL;   
	if(T5IR==0)  
	{  
		Freq = CAPREL;  
		os_send_signal (Turbo_Task);  
	}  	
	else  	
	{  
		T5IR = 0;   
        Freq = CAPREL;  
        Freq = 0;  
		os_send_signal (Turbo_Task);  
	}  
}  
// Из трех переменных есть смысл в глобальности только для Freq, ее оставила глобальной  

# 9
class	TPropElement  
{  
protected:
int	FID;  
bool	FIOFlag;  
bool	FIsTag;  
int	FType;  
bool	FAccess;  
int	FSecurity;  
...   
}    
//---------------
class	TPropElement  
{  
private:
int	FID;  
bool	FIOFlag;  
bool	FIsTag;  
int	FType;  
bool	FAccess;  
int	FSecurity;  
...   
}  
//Изменила уровень досnупа на более строгий  

# 10
public class DynHashArray  
{  
    public int count;  
    public int capacity;  
    public int step;  
    public DynHashArray()  
    {  
        count = 0;  
        step = 1;  
        makeArray(17);  
    } 
//----------------  
public class DynHashArray  
{  
    private int count;    
    private int capacity;    
    private int step;  
    public DynHashArray();    
    {  
        count = 0;    
        step = 1;    
        makeArray(17);    
    }  
int GetCount() {return count};  
int GetCapacity() {return Capacity};  
//Изменила уровень досnупа на более строгий , ввела get и set для переменных,которые могут быть вызваны извне  

# 11


