---------комментарии оставила -------------------------  

# 1
#ifdef __WIN32__  
    &ensp; &ensp;FRB_ReceiveRA (0, no, data)  
#else                         	     // Только МиниОС    
	&ensp; &ensp;*data = inpw ((no - 8)*2);   // В МиниОс по другому устроена организация адресов модулей    
#endif    
// Объясняет почему используется другая функция в случае загрузки в МиниОС   

# 2
bool    BeClass::Init()  
{  
     &ensp; &ensp; BeClass* tmp_obj;  
    &ensp; &ensp;  for (int i = 0;  i < ChildCount();  i++)  
    &ensp; &ensp;  {  
     &ensp; &ensp; &ensp; &ensp;	tmp_obj = (BeClass*)GetChild(i);  
         &ensp; &ensp; &ensp; if (tmp_obj != 0)                
	 &ensp; &ensp; &ensp; &ensp;  tmp_obj->Init();  //Иниц портов Net TimeIO
     &ensp; &ensp; &ensp; &ensp;}  
     &ensp; &ensp;return (!FConfigError);    
}  
//-----------------------------    
bool    BeBaseClass::Init()  
{  
   &ensp; &ensp; BeBaseClass*  curDevice;   
   &ensp; &ensp;  for (int i = 0;  i < devChildCount();  i++)  
   &ensp; &ensp; {  
    	&ensp; &ensp; &ensp; &ensp; curChildDevice = (BeBaseClass*) GetChildDevice(i);  
        &ensp; &ensp; &ensp; &ensp; if (cuChildrDevice != 0) &ensp; &ensp; &ensp; &ensp;//Текущий устройство из списка у реестре устройств   
        &ensp; &ensp;&ensp; &ensp; &ensp; &ensp; curChildDevice->Init();  
    &ensp; &ensp; }  
    &ensp; &ensp; return (!FConfigError);  
}  
// Изменила имена переменных и сам комментарий, чтоб было более понятно  

# 3 
struct  SDevice  
{  
    uint            devID; 		&ensp; &ensp; &ensp; &ensp; //идентиф устройства  
    uint            devSignalCount;	&ensp; &ensp; &ensp; &ensp; //число сигн  
    int             devState;		&ensp; &ensp; &ensp; &ensp; //Состояние  
    PExecuteFunc    *ExecuteFunc;	&ensp; &ensp; &ensp; &ensp; //Указ на ф-цию  выполнения команд  
    POnChange       *OnChangeFunc;	&ensp; &ensp; &ensp; &ensp; //Указ на ф-цию обработки изм сигнала  
    PResetFunc      *OnResetFunc;       &ensp; &ensp; &ensp; &ensp; //Указатель на функцию сброса устройства  
    uint             devTaskId;		&ensp; &ensp; &ensp; &ensp; //номер задачи обраб устр-во  
    uint            *lisDevtSignals;	&ensp; &ensp; &ensp; &ensp; // массив сигналов  
    void            *devParam;	//Структура с таймаутами и переменными  
};  
// Здесь считаю комментарии уместно для ясности в стрктуре описания свойств и функций устройства   

# 4
int    GetTimerBit()  
{  
    for (int i = 0;  i <= MAX_TIM_BITS_COUNT;  i++)  
    {  
        if (TimBitToTask[i] == 0)	 	
            return (i + TIM_BIT_BASE);	//IM_BIT_BASE - сдвиг для вычисления сигнала таймера в списке сигналов  
    }  
    SetError();		//Это если сигнал больше чем MAX_TIM_BITS_COUNT  
    return (-1);  
}   
// Здесь комментарии поясняют принцип поиска сигнала в списке   

# 5
#define	ZUBCOUNT   	6	 &ensp; &ensp; // число зубов вала турбокомпрессора   
#define TICK_PER_SECOND          (39062.5) &ensp; &ensp;//расчет 20000000/512!! время тика = OneTick = 1./39062.5 Sec  
#define TICK_PER_SECOND_INT      (39063)  &ensp; &ensp; // округление для целого  
#define TIME_CONVERTER          (TICK_PER_SECOND*60) &ensp; &ensp; //  число тиков в минуту  
#define PART_OF_SEC             (10)    &ensp; &ensp;   // т.е. секунду делим на ...  = ~100 мСек  
#define TICKS_PER_PERIOD        (TICK_PER_SECOND_INT/PART_OF_SEC) &ensp; &ensp; // число тиков в сек  
#define ERROR_FOR_OTKAZ_COUNT   (5) &ensp; &ensp; // число отказов до выставление ошибки   
#define IZM_TIME                10  &ensp; &ensp ;//Время замера оборотов = ~100 мСек  
// Здесь комментарии - пояснения физических констант  

# 6
struct SThreadEvent  
{  
    &ensp; &ensp; unsigned long FEventParam;    //ВНИМАНИЕ!!!  Важно и для Линукс и для Винды
   &ensp; &ensp;  union  
    &ensp; &ensp; {  
     &ensp; &ensp;&ensp; &ensp;  void*           FPointer;  
     &ensp; &ensp;&ensp; &ensp;  unsigned int    FEventField;  
    &ensp; &ensp; };  
};  
// Замечание по типу переменной считаю уместной

# 7
TCursor Save_Cursor = Screen->Cursor;   
Screen->Cursor = crHourGlass; // изменяем вид курсора  

SavePlace = MainForm->FCurrentGrid->Row;  //Закладка на текущей записи      
// Здесь бы также оставила комментарий, он поясняет функции С++ Builder        
-----------------Комментарии убираю-------------------------------

# 8
void BeKlapan2Slave::DefState()  
{  
    if(FLastCommand!= NO_VALUE)  
    {  
        FValue = FLastCommand;  //Состояние - Предыдущ поданная команда,тк концевого не видно       	
     }  
    else  
       BeKlapanSlvDevice::DefState();  
       Master->DefState();  
}  
//--------------------------  
void BeKlapan2Slave::DefState()
{
    if(FLastCommand!= NO_VALUE) {
        FKlapanState = FLastCommand;      	
     } 
   else
       BeKlapanSlvDevice::DefState();
       BeKlapanMaster->DefState()
} 
// Изменила имена переменной-состояния и имя функции, для большей ясности. Комментарий не нужен уже  


# 9
void ConfirmOnChange (DEVICE_DD *confirm_dd, int sid, int value, int valflag)  
{  
    switch (sid)  
    {  
    case CONFIRM_NET_SOUND_SIGNAL:  
    case CONFIRM_NET_LIGHT_SIGNAL:  
        if (value == ON)  
            ConfirmExecuteCommand (confirm_dd, COMMAND_ALL_ON);  //Включ сигн по сети  
        else
            ConfirmExecuteCommand (confirm_dd, COMMAND_ALL_OFF); //Выыключ сигн по сети  
        break;  
    case CONFIRM_BUTTON_SIGNAL: //Кнопка квитирование  
        if (value == ON)  
            ConfirmExecuteCommand (confirm_dd, COMMAND_ALARM_CONFIRM);  
        break;  
    case CONFIRM_TIMEOUT_SIGNAL: //пол секунды истекли  
        ConfirmDD.Value = OFF;  
        SetBit (ConfirmDD.Signals[CONFIRM_NET_SIGNAL], OFF);  
        break;  
    case CONFIRM_BLINK_TIME_SIGNAL: //Мигание  
        if (ConfirmParam.FBlinkFlag == false)  
            break;  
..  
}  
//------------------------------  
void ConfirmOnChange (DEVICE_DD *confirm_dd, int typeSignal, int value, int valflag)  
{  
    switch (typeSignal)  
    {  
    case CONFIRM_NET_SOUND_SIGNAL:  
    case CONFIRM_NET_LIGHT_SIGNAL:  

        if (value == ON)  
            ConfirmExecuteCommand (deviceConfirm, COMMAND_ON_ALL);  
        else  
            ConfirmExecuteCommand (deviceConfirm, COMMAND_OFF_ALL);  
        break;  
    case CONFIRM_BUTTON_SIGNAL:	  
        if (value == ON)  
            ConfirmExecuteCommand (deviceConfirm, COMMAND_ALARM_CONFIRM);  
        break;  
    case CONFIRM_TIMEOUT_TERMINATE:  
        ConfirmDD.Value = OFF;  
        SetBit (ConfirmDD.Signals[CONFIRM_NET_SIGNAL], OFF);  
        break;  
    case CONFIRM_BLINK_ON:  
        if (ConfirmParam.FBlinkFlag == false)  
            break;  
     ..  
}  
// Изменила названия переменных и функций - комментарии убрала  

# 10  
BeClass::BeClass()  
{  
   &ensp; &ensp; if (FReestr == 0)   //Первый раз созд Sytem и в нем -реестр, второй раз- Reestr не созд   
    &ensp; &ensp;{  
        &ensp; &ensp;&ensp; &ensp;FReestr = this;      
        &ensp; &ensp;&ensp; &ensp;FReestr = new BeReestr();  
    &ensp; &ensp;}    
    &ensp; &ensp;FID = NO_VALUE;  
}  
//--------------------    
bool REESRT_NO_EXIST = {return (FReestr == 0)};  
  
if (REESTR_NO_EXIST)      
    &ensp; &ensp;{   
        &ensp; &ensp;&ensp; &ensp;FReestr = this;       
       &ensp; &ensp;&ensp; &ensp; FReestr = new BeReestr();  
   &ensp; &ensp; }  
    &ensp; &ensp;FID = NO_VALUE;  
}  
// Заменить 0 на переменную - станет более понятно    


# 11
//Вернуть объект типа BeClass с заданным именем - строкой     
BeClass* BeObjList::GetByStringID  (char* strid){    

    BeClass *node_ptr = 0;    
    if ((strid == 0) || (*strid == 0))    
        return (0);  
    for (int i = 0;  i < FCount;  i++)  
    {  
    	node_ptr = (BeClass*)GetItem(i); // Вытащить сигнал, если его номер не больше общего числа сигналов  
        if (node_ptr != 0)  
        {  
            if (node_ptr->FStrID != 0)  
                if (strcmp (node_ptr->FStrID, strid) == 0) //Если  совпад назв сигнала в конфиге и внутри объекта  
            		break;     // вернуть адрес объ если совпад названия иначе  вернуть 0  
            node_ptr = 0;  
        }  
    }  
    return (node_ptr);  
}   
//------------------------    
BeClass*	BeObjList::GetObjectByName  (char* curObjectName)    
{  
    BeClass	*curObject = 0;  
    if ((curObjectName == NO_NAME) || (*curObjectName == 0))  
    
        return (0);  
    for (int i = 0;  i < FChildCount;  FChildCount ++)  
    {  
    	curObject = (BeObjList*)GetItem (i);   
        if (curObject != 0)  
        {  
            if (curObject->FName != 0 && (strcmp (curObject->FName, objectName)) == 0)  
            	return (curObject);  
        }  
    }  
    return (0);  
}  
// Изменила код и необходимость в коментариях отпала  

# 12
SetBit (SysControlDD.Signals[SYSCONTROL_NET_EXTRASTOP_SIGNAL], ON);    	
SetBit (SysControlDD.Signals[SYSCONTROL_NET_STATUSSTOP_SIGNAL], ON);   
ExtraStopFunction();  
Delay(2000); //Чтоб успеть поймать по сети аварию-если она быстро прошла  
//-----------------------------------------------  
static int TimeToCatchAlarmMs = 2000;  
SetBit (SysControlDD.Signals[SYSCONTROL_NET_EXTRASTOP_SIGNAL], ON);    	
SetBit (SysControlDD.Signals[SYSCONTROL_NET_STATUSSTOP_SIGNAL], ON);   
ExtraStopFunction();  
Delay(TimeToCatchAlarmMs);   
//Можно убрать комментарий или перенести его в месть объявления переменной TimeToCatchAlarmMs




