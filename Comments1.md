# 1
// Необходимо проверять полноту заполнения свойств - а вдруг забыли что то   
bool    ALimit::OnAfterLoad()      
{  
   &ensp; &ensp;  AObject  *par = (AObject*)GetParam();  
    &ensp; &ensp; if (par != 0)  
     &ensp; &ensp; &ensp; &ensp;    return = true;  
    &ensp; &ensp; return (false);  
}   
//----- 1. Информативное сообщение Пояснение к функции  

# 2
..   
    if (state.IsHave (PARAM_EVENT_MESSAGE | PARAM_EVENT_ERROR))  
    {  
      &ensp; &ensp; eventvalue = AString (ev->FEventValue).FloatFormat() +  " - ";  
      &ensp; &ensp;   eventvalue = ev->FValue;	&ensp; &ensp; &ensp; &ensp; // ToDo Надо заменить на текст из списка в следующей версии  
       &ensp; &ensp;  out.AddStringAtPos (eventvalue, 55);   
    }   
//----- 6. Заметка на будущее  

# 3
AClass::AClass (AString name, AString comment)  
     &ensp; &ensp;  : ANode (name, comment),  
     &ensp; &ensp;    AList (1)  
{  
    &ensp; &ensp; ClrStructOptions (COMPONENT_NO_OWNER); &ensp; &ensp;  // На этом много завязано - не менять! может все слететь   
}   
//----- 4. Предупреждение о последствиях 

# 4
// ToDo   Нужно будет сделать доп. проверку по connect.  
ADescriptor*    GetClassDescriptor (AString class_name, FLAG connect_type)  
{  
    &ensp; &ensp; ADescriptor *ret = (ADescriptor*) LPClassDescriptorList->GetChildByName (class_name);  
    &ensp; &ensp; if (ret != 0)  
    &ensp; &ensp; {  
     &ensp; &ensp; &ensp; &ensp;    FLAG    id = ret->GetID();  
     &ensp; &ensp; &ensp; &ensp;    AFlag   key = connect_type;  
      &ensp; &ensp; &ensp; &ensp;   if (!key.IsTrue (id))  
      &ensp; &ensp; &ensp; &ensp; &ensp; &ensp;       ret = 0;  
    &ensp; &ensp; }  
    return (ret);  
}    
//----- 6. Заметка на будущее

# 5
#if !defined (__WIN32__)  &ensp;  //  This function defined only in Windows!!!    
unsigned char* _mbsspnp (unsigned char *s1, unsigned char *s2)   
{   
 &ensp; &ensp;	bool	f;   
 &ensp; &ensp;	unsigned char *pout = 0;   
 &ensp; &ensp;..   
 &ensp; &ensp;..   
 &ensp; &ensp; return (pout);   
}   
#endif     
//------ 3. Прояснение при использовнии системной функции для разных ОС  

# 6  
#if !defined (__WIN32__)  
static const ATIME   BASE_INTERVAL_VALUE = 10;   &ensp; &ensp;// Больше нельзя - линукс дурит, обрезает MAXLONG   
//------ 3. Прояснение при использовнии системной функции для разных ОС  

# 7
AComponent*	AComponent::GetChildByName (AString name)   // ToDo нужна проверка на пустое имя   
{   
  &ensp; &ensp;   AComponent* node = 0;  
  &ensp; &ensp;   int         child_count = ChildCount();   
  &ensp; &ensp;   name = name.UpperCase();   
  &ensp; &ensp;   ..   
  &ensp; &ensp;   ..   
}   
//------ 6. Заметка на будущее ToDo

# 8
ACoProcess::~ACoProcess()  
{  
  &ensp; &ensp;   FProcess = 0;  &ensp; &ensp; //Удалять не надо - сам удалится в списке процессов  
}  
//------ 1. Информативный комментарий, предупреждение

# 9
class   AObject : public AClass, public APropertyClass, public AStateClass, public ACommandClass  
{  
protected:  
  &ensp; &ensp;   static  long    FTimerIndex;  
  &ensp; &ensp;   AClass*     FListRegistrator;  &ensp;  // Для хранения списков команд и пр.  
  &ensp; &ensp;   long        FAddressIndex;  
..  
..  
  &ensp; &ensp;   virtual void        RegistrateInternalList (AClass *list);   // Для регистрации спискрв типа состояний и команд  
//------ 1. Информативные комментарии

# 10
ATimerManager::ATimerManager()  
       &ensp; &ensp;       : AProcess ("SysTimer", "Системный таймер", PROCESS_READ)  
{  
  &ensp; &ensp;   SetStructOptions (COMPONENT_NO_OWNER | COMPONENT_FOREIGN_CHILD);  
  &ensp; &ensp;   FProcessOptions.Set(PROCESS_IS_KERNEL);  
  &ensp; &ensp;   FTimerIndex = FAddressIndex;     &ensp;  //Заполняем статическое поле для адресации к таймеру  
}  
//------ 1. Информативные комментарии


# 11
uword ASC_uwGetData (void)  
{  
  &ensp; &ensp;   S0RIR = 0;             // reset receive interrupt request flag  
  &ensp; &ensp;   return(S0RBUF);        // return receive buffer register  
}   
//------ 3. Прояснение при использовнии системной функции микроконтроллера

# 12
void Kran2OnSignal (DEVICE_DD *kran2_dd, int sid, int value, int valflag)   
{   
 &ensp; &ensp;   struct SKran2Param  *kran2_Param;    
 &ensp; &ensp;   kran2_Param = kran2_dd->DevParam;     
 &ensp; &ensp;   switch (sid)		//  Здесь только концевые-остальные обрабатываем в Kran.c   
 &ensp; &ensp;   {   
 &ensp; &ensp;    case KRAN_OPEN_SENSOR_SIGNAL:   
 &ensp; &ensp;    if (value == ON) 
 {     
 &ensp; &ensp;&ensp;&ensp; SetBit (kran2_dd->Signals[KRAN_NET_OPEN_SENSOR_SIGNAL], ON);  &ensp;  // Прямая установка ON в МГП-кажд кран отдельно      
 &ensp; &ensp;&ensp;&ensp; if (ValueOfBit (kran2_dd->Signals[KRAN_OPEN_SENSOR_SIGNAL_2] )== ON)  
 &ensp; &ensp; &ensp; &ensp;&ensp; &ensp; {  
 
&ensp; &ensp; &ensp; &ensp;&ensp; &ensp;&ensp; if (kran2_Param->FOpenOverTime != 0)   
&ensp; &ensp; &ensp; &ensp;&ensp; &ensp;&ensp; {   

&ensp; &ensp; &ensp; &ensp; &ensp; &ensp; &ensp; &ensp;  kran2_Param->FWaitTimeOut = KRAN_OPEN_OVER_TIME;  &ensp; // Заряжаем таймаут на дожим крана       
 &ensp; &ensp; &ensp; &ensp; &ensp; &ensp;  SetBit (kran2_dd->Signals[KRAN_TIMEOUT_SIGNAL], kran2_Param-> FOpenOverTime);     
       &ensp; &ensp;      }   
       &ensp; &ensp;     else  
         &ensp; &ensp;&ensp; &ensp;   KranOnReset(kran2_dd);  	        
 	 &ensp; &ensp;   }   
          &ensp; &ensp; }   
	 &ensp; &ensp;  else  	 	  
	  &ensp; &ensp; &ensp; &ensp;SetBit (kran2_dd->Signals[KRAN_NET_OPEN_SENSOR_SIGNAL],  OFF);  &ensp; 
  // Прямая установка значения OFF как и ON      		
	 &ensp; &ensp; break;   
..  
..  
}  
//------ 1. Пояснения к алгоритму обработки сигналов крана  





