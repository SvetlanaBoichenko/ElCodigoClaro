# 1
#ifdef __WIN32__  
    &ensp; &ensp;FRB_ReceiveRA (0, no, data)  
#else                         	     // Только МиниОС    
	&ensp; &ensp;*data = inpw ((no - 8)*2);   // В МиниОс по другому устроена организация адресов модулей    
#endif    
// Объясняет почему используется другая функция в случае загрузки в МиниОС   

# 2
BeClass::BeClass()  
{  
   &ensp; &ensp; if (FReestr == 0)   //Первый раз созд Sytem и в нем - реестр, второй  раз- Reestr не созд   
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

# 3
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
bool    BeClass::Init()  
{  
   &ensp; &ensp; BeClass*  curDevice;   
   &ensp; &ensp;  for (int i = 0;  i < devChildCount();  i++)  
   &ensp; &ensp; {  
    	&ensp; &ensp; &ensp; &ensp; curDevice = (BeClass*) GetChild(i);  
        &ensp; &ensp; &ensp; &ensp; if (curDevice != 0) &ensp; &ensp; &ensp; &ensp;  //Текущий устройство из списка у реестре устройств   
        &ensp; &ensp;&ensp; &ensp; &ensp; &ensp; curDevice->Init();  
    &ensp; &ensp; }  
    &ensp; &ensp; return (!FConfigError);  
}  
// Изменила имена переменных и сам комментарий, чтоб было более понятно

# 4
void BeKlapan2Slave::DefState()  
{  
    if(FLastCommand!= NO_VALUE)  
    {  
        FValue = FLastCommand;  //Состояние - Предыдущ поданная команда, тк концевого не видно       	
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

# 5 
struct  SDevice
{
    uint            devID; 		//идентиф устройства
    uint            devSignalCount;	//число сигн
    int             devState;		//Состояние
    PExecuteFunc    *ExecuteFunc;	//Указ на ф-цию  выполнения команд
    POnChange       *OnChangeFunc;	//Указ на ф-цию обработки изм сигнала
    PResetFunc      *OnResetFunc;       //Указатель на функцию сброса устройства
    uint             devTaskId;		//номер задачи обраб устр-во
    uint            *lisDevtSignals;	// массив сигналов
    void            *devParam;	//Структура с таймаутами и переменными
};
// Здесь считаю комментарии уместно для ясности в стрктуре описания свойств и функций устройства 

# 6
void ConfirmOnChange (DEVICE_DD *confirm_dd, int sid, int value, int valflag)
{
    switch (sid)
    {
    case CONFIRM_NET_SOUND_SIGNAL:
    case CONFIRM_NET_LIGHT_SIGNAL:
        if (value == ON)
            ConfirmExecuteCommand (confirm_dd, COMMAND_ALL_ON);//Включ сигн по сети
        else
            ConfirmExecuteCommand (confirm_dd, COMMAND_ALL_OFF);//Выыыыыключ сигн по сети
        break;

    case CONFIRM_BUTTON_SIGNAL://Кнопка квитирование
        if (value == ON)
            ConfirmExecuteCommand (confirm_dd, COMMAND_ALARM_CONFIRM);
        break;

    case CONFIRM_TIMEOUT_SIGNAL://пол секунды истекли
        ConfirmDD.Value = OFF;
        SetBit (ConfirmDD.Signals[CONFIRM_NET_SIGNAL], OFF);
        break;

    case CONFIRM_BLINK_TIME_SIGNAL://Мигание
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
// Изменила названия переменных и функций - уомментарии убрала
