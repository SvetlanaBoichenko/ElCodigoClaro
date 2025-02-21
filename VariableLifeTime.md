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

# 4-5
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
      if (listHead == null && _nodeAfter == null) {  
            listHead = _nodeToInsert;  
            _nodeToInsert.next = null;  
            listTail = _nodeToInsert;  
            return true;  
        }  
        
	  if (listHead == _nodeAfter) {  
            _nodeToInsert.prev = head;  
            listHead.next = _nodeToInsert;  
            _nodeToInsert.next = null;  
            listTail = _nodeToInsert;  
            return true;  
        }  
        if (_nodeAfter == listTail) {  
            _nodeAfter.next = _nodeToInsert;  
            _nodeToInsert.prev = _nodeAfter;  
            _nodeToInsert.next = null;  
            listTail = _nodeToInsert;  
            return true;   
        }  
 
 	if (_nodeAfter == null) {  
            listHead.prev = _nodeToInsert;  
            _nodeToInsert.next = listHead;  
            listHead = _nodeToInsert;  
            listHead.prev = null;   
            return true;  
        }  
        if (listHead == _nodeAfter && listHead.next != null) {   
            _nodeToInsert.prev = this.head;  
            _nodeToInsert.next = this.head.next;  
            _nodeToInsert.next.prev = _nodeToInsert;  
            listHead.next = _nodeToInsert;   
            return true;  
        }  
      
      return false;  
   }  
   //Перенесла вставку узлов в список для пограничных случаев в отдельную функцию  
   //Перенесла использование переменной listTail ближе к ее объявлению
        
# 6
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

# 7
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

# 8-9
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

# 10
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

# 11
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
int GetCount() {return count;};  
int GetCapacity() {return Capacity;};  
//Изменила уровень досnупа на более строгий , ввела get для переменных,которые могут быть вызваны извне  

# 12
class   EAnalog  : public EParam  
{  
protected:  
public:  
    	float   FMinValue;  
    	float   FMaxValue;  
    	float   FSensorMinValue;  
    	float   FSensorMaxValue;  
	virtual	float	GetPresentation(float value);  
	virtual	float	SetPresentation (float value);  
...   
};  
//---------------------------  
class   EAnalog  : public EParam  
{  
private:  
    	float   FMinValue;  
    	float   FMaxValue;  
    	float   FSensorMinValue;  
    	float   FSensorMaxValue;  
public:   
	float GetMinValue() return (FMinValue);  
	float GetMinValue() return (FMinValue);  
	float GettSensorMinValuee() {return (FSensorMinValue);}
	float GettSensorMaxValuee() {return (FSensorMaxValue);}  
 	virtual	float	GetPresentation (float value);  
 	virtual	float	SetPresentation (float value);  
...    
};     
//Изменила уровень досnупа на более строгий, ввела get для переменных  

# 13
class  IDClass
{
protected:
public:
    AFlag   FAttributes;
    float   FValue;
    int     FObjectID;
    void    SetAttr (int flag) { FAttributes.Set (flag); };
    bool    IsAttr  (int flag) { return (FAttributes.IsTrue (flag)); };
    bool    FActiveClient;
    IDClass() { FObjectID = -1; FValue = 0; FActiveClient = true; };
    virtual ~IDClass() {FComment.~AString();};
};
//-------------  
class  IDClass  
{  
private:  
   	AFlag   FAttributes;  
    	float   FValue;  
    	int     FObjectID;  
	bool    FActiveClient;  
public:  
    void    SetAttr (int flag) { FAttributes.Set (flag); }  
    AFlag   GetAttr() {return FAttributes;}  
    float   GetMinValue() {return (FValue); }  
    bool    IsAttr  (int flag) { return (FAttributes.IsTrue (flag)); }     
    IDClass() { FObjectID = -1; FValue = 0; FActiveClient = true; }  
    virtual ~IDClass() {FComment.~AString();}  
    ...  
};  
//Изменила уровень досnупа на более строгий, ввела get и set для переменных  

# 14-15
int UDPPort::ReadData(char *pBuffer, unsigned int length, unsigned int delta)  
{  
    if (!mIsOpen) return -2;  
      
    sockaddr_in sender_address;  
    int sender_address_size;  
    int bytes_read;  
    int f = 0;  
    fd_set FInput;  
    timeval FTimeValue;  
      
    FD_ZERO(&FInput);  
    FD_SET(mSocket, &FInput);  
    FTimeValue.tv_sec     = 0;  
    FTimeValue.tv_usec    = delta * SYS_USEC_DEVIDER;  
      
#if defined (__WIN32__)  
	f = select(mSocket+1, &FInput, NULL, NULL, &FTimeValue);  
#else  
	f = select(mSocket+1, &FInput, NULL, NULL, &FTimeValue);  
#endif  
    if (f > 0)  
    {  
        sender_address_size = sizeof(sender_address);  
  
        bytes_read = recvfrom(mSocket,pBuffer,length,0,  
                              (sockaddr*)&sender_address,&sender_address_size);  
        if (bytes_read == SOCKET_ERROR)  
            f = -2;  
        else  
            f = bytes_read;  
    }  
    else  
        f = -2;  

    return f;  
}  
//-----------------
static int const errPortRead  = -2;
int UDPPort::ReadData(char *pBuffer, unsigned int length, unsigned int delta)  
{  
    if (!mIsOpen) return  errPortRead;  
    sockaddr_in sender_address;  
    int resPortSelect = 0;  
  
    fd_set FInput;  
    timeval FTimeValue;  
  
    FD_ZERO(&FInput);  
    FD_SET(mSocket, &FInput);  
  
    FTimeValue.tv_sec     = 0;  
    FTimeValue.tv_usec    = delta * SYS_USEC_DEVIDER;  
  
#if defined (__WIN32__)  
	resPortSelect = select(mSocket+1, &FInput, NULL, NULL, &FTimeValue);  
#else  
	resPortSelect = select(mSocket+1, &FInput, NULL, NULL, &FTimeValue);  
#endif  
    
    int sender_address_size = 0;  
    int bytes_read = 0;  
    if ( resPortCheckt > 0)  
    {  
        sender_address_size = sizeof(sender_address);  
  
        bytes_read = recvfrom(mSocket,pBuffer,length,0,  
                              (sockaddr*)&sender_address,&sender_address_size);  
        if (bytes_read == SOCKET_ERROR)  
             resPortCheck =  errPortRead;  
        else  
            resPortCheck = bytes_read;  
    }  
    else  
        resPortCheck =  errPortRead;  

    return  resPortCheck;  
}   
//Перенесла переменные bytes_read, sender_address_size к месту их использования, проинициализировала их,
// исправила имя переменной f
