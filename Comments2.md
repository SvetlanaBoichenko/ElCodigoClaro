# 1
/*
void BeKranSlaveDevice::DefLampState()  
{  
   switch(FValue)  
    {   
    	&ensp; case OPEN:  
         &ensp;&ensp;    FIO_KRANSL_OPEN_LAMP->StopBlink();  
         &ensp;&ensp;    FIO_KRANSL_CLOSE_LAMP->StopBlink();  
         &ensp;&ensp;    FIO_KRANSL_CLOSE_LAMP->SetValue (OFF);  
         &ensp;&ensp;    FIO_KRANSL_OPEN_LAMP->SetValue (ON);  
      	&ensp;break;  
..  
..  
*/  
//--- 11. закоментрованный код.   
//--- Убрала.  

# 2
TMDIChild* CurrentChild = 0;  
...  
Bookmark SavePlace;  
SavePlace = CurrentChild->ADOQueryEvent->GetBookmark();  //Закладка на текущей записи   
//-------------------      
TMDIChild* currentWindow = 0;    
...   
TBookmark saveRecordPlace;   
saveRecordPlace = currentWindow->ADOQueryEvent->GetBookmark(); 
  
//--- 12. Не используйте комментарии там, где можно использовать функцию или переменную      
//--- Изменила имя функции и переменной на более понятные  

# 3
  void BeKranSlaveDevice::OnReset()   
{   
   &ensp; FWaitTimeOut = 0;                           //Сброс таймера  
    &ensp; FKranCommand = COMMAND_NONE;  
    &ensp; FIO_KRANSL_TIMEOUT->ClrTimer();		//Сброс таймера крана   
    &ensp; FIO_KRANSL_CONTROL_OPEN->SetValue (OFF);
    &ensp;  FIO_KRANSL_CONTROL_CLOSE->SetValue (OFF);  
}   
  
//--- 4. Шум   
// И так понятно что сброс таймера - Убрала.  

# 4
void BeKranSlaveDevice::VerifyError() // Неисправен  ERROR или DAMAGED    
{                                      
    if ((FValue & DAMAGED) != 0)    // Проверить!!!!!!!!!    
    {   
         &ensp; FDamagedCount++;    
        &ensp; if (FDamagedCount < FMaxDamagedCount)    
         &ensp;{    
             &ensp; FValue = FLastGoodValue;    //Пока не меняем состояние  
             &ensp; if (FWaitTimeOut == 0)      //Если не запущен ни один из таймеров крана (по управл или срабатыванию концевого)  
..      
}    
  
//---4. Шум и бормотание      
//--- Убрала комментариивообще      

# 5
  // Кран закрыт - Хочу открыть    
   else if ((FIO_KRANSL_SENSOR_OPEN->Value() == OFF)&& (FIO_KRANSL_SENSOR_CLOSE->Value() == ON)) {     
   	// if ((FIO_KRANSL_CONTROL_OPEN->Value() == ON) &&(FIO_KRANSL_CONTROL_CLOSE->Value() == OFF))    
        //   FValue = KRAN_OPENING1;   
	//Только управляющий закрытия   
           &ensp; &ensp;if ((FIO_KRANSL_CONTROL_OPEN->Value() == OFF) &&(FIO_KRANSL_CONTROL_CLOSE->Value() == ON))   
             &ensp; &ensp; &ensp;FValue = KRAN_CLOSING;   
	   //  Два управляющих взведены  
          &ensp; &ensp; else if ((FIO_KRANSL_CONTROL_OPEN->Value() == ON) &&(FIO_KRANSL_CONTROL_CLOSE->Value() == ON))     
        	  &ensp; &ensp; &ensp; FValue = KRAN_DAMAGED;   
           &ensp; &ensp; else    
         	 &ensp; &ensp; &ensp; FValue = KRAN_CLOSE;    //управляющих нет    
   }    
   //------------  
 // Кран закрыт  
   else if ((KRAN_SENSOR_OPEN->Value() == OFF) && (KRAN_SENSOR_CLOSE->Value() == ON))  {     
	&ensp;if ((KRAN_CONTROL_CLOSE->Value() == ON) &&(KRAN_CONTROL_OPEN->Value() == ON))    
       &ensp;&ensp;    FValue = KRAN_CLOSING;   
      &ensp;   else if ((KRAN_CONTROL_OPEN->Value() == ON) &&(KRAN_CONTROL_CLOSE->Value() == ON))   
        &ensp;&ensp;	FValue = KRAN_DAMAGED;    
	&ensp; else   		 
       &ensp;&ensp;   FValue = KRAN_CLOSE;         
   }   
      
//----7. Излишние комментарии   
//---- Исправила комментарии и имена переменных для большей ясности    

# 6
if (command == CLOSE)    
     &ensp;{        
      &ensp; &ensp;   FIO_KLAPAN_CONTROL_CLOSE->SetValue(ON);  
      &ensp; &ensp;   FIO_KLAPAN_CONTROL_OPEN->SetValue(OFF);  
                     //Фиксируектс¤ только OPEN & CLOSE  
      &ensp;}  
     &ensp;if (command == OPEN)  
    &ensp; {
       &ensp; &ensp;  FIO_KLAPAN_CONTROL_CLOSE->SetValue(OFF);  
       &ensp; &ensp;  FIO_KLAPAN_CONTROL_OPEN->SetValue(ON);  
     &ensp;}    
       
//----4. Шум   
// Других команд здесь и нет. Убрала комментарий    

# 7
result = Func(LineStep, timevalue);    // выполнить эту ф. OnExecute(...)     
 //   Print("result = %i \r\n  \r\n", result);     
     if (result == STEP_NEXT)  //Если ф выполн полностью - переход на след строку   
        {   
         &ensp;   FCurrentIP++;   
         &ensp; if (FCurrentIP >= FCount)       //Больше чем строк в массиве записей-содерж ф.  
           &ensp; {                           //Закончить ав останов  
           &ensp;&ensp;     ret = -1;  
            &ensp;&ensp;    FCurrentIP=0;   
           &ensp; }   
        }  
	  
//-------------------       
     result = AlarmFunc (LineStep, timevalue);       
     if (result == STEP_NEXT)           
        {   
          &ensp;  FLineNumber++;    
         &ensp;   if (FLineNumber >= FAlarmLinesCount)             	
         &ensp;   {                                 	
            &ensp;&ensp;    ret = ALARM_STOP;	//Закончить аварийный останов      
            &ensp;&ensp;    FCurrentLine = 0;      
            }     
        }     
	   
//---- 4. Шум    
// Изменила имена функций и переменных. Убрала лишние комментарии    
     
# 8 
..
if (bit_code < 0)     //Если ошибка     
&ensp;    ret = bit_code;  
else    
&ensp;    ret = TaskTimBit (bit_code, task_no);      // Задание N задачи в массиве         
else if (bit_code < MAX_BUS_BITS_COUNT)        // Они первые в списке бит  
   &ensp;	ret = TaskBusBit (bit_code | sec_flag, task_no); // Если SecondParent то получится Ошибка -код больше Мах числа сигналов Bus    
 ..     
   
//---------------------    
if (bitCode < 0)  	   
  &ensp;  ret = ERROR_BIT_CODE;    
else  
 &ensp;    ret = GetTaskTimerNo (bitCode, taskNo);   // номер задачи в массиве задач       
  
// 7. Избыточные комментарии      
// убрала неочевидные коммантарии, измениля имена функции и переменных      

# 9

// USER CODE BEGIN (ASC_Init,1)  
  //   ASC baudrate reload register  
  ///  baudrate =  9600 Baud  

  P3    |= 0x0C00;    //  set P3.10 output latch (TXD0)  
  DP3   |= 0x0400;    /// set P3.10 direction control (TXD0 output)  
  DP3   &= 0xF7FF;    /// reset P3.11 direction control (RXD0 input)  
//  P1H  = 0x0000;????????      // set port data register?  
//  _nop_();???????  
//  DP1H = 0x07; ?????       // set port direction register  
//  _nop_();?????????  
  S0BG  = BaudNum;  
  S0REN = 1;  
  S0TIR = 0;  
// USER CODE END  
}    
  
// 11. Закомментированный код. Убрала

# 10
DP8  = 0x009F;  // Бойченко для резервов 8_5 и 8_6 на вход //0x00FF;// set port direction register  
//---------------------------  
DP8  = 0x009F;  // настройка порта 8 для пинов 5 и 6 на вход для сигнализации   
  
// Убрала лишенее, изменила комментарий    

# 11
   FOutCommand = NET_COMMAND_ERROR_ANSWER; //Выставляем ответ с ошибкой, пока...    
   FOutCommand = NET_COMMAND_ERROR_ANSWER; //По умолчанию - команда с ошибкой.    
    
// 2. Бормотание. Изменила  комментарий  

# 12
bool BeReestr::SetIOPin (char *devtype, BeSignal* sig, int iodevid, int pinid) {    
    bool    ret = false;    
    if (sig != 0)  {    
        // Вернуть флаг    
        FLAG        sigtype   = sig->GetFlags (SIG_MAYBECONFIG);    
        FLAG        sigrw     = sig->GetFlags (SIG_RW);    
..    
..   
}     
// 3. Недостоверные комментарии. Флаг здесь не возвращается. Убрала комментарий  

# 13
   if(T5IR==0)				//Если переполнения не было то посылаем сигнал о тике  
   {  
	Freq = CAPREL;			//Chislo Tikov  
	os_send_signal (Turbo_Task);  
   }	.  

//-------------------------------  
  
 if(T5IR == 0)				// Переполнения нет  
   {  
	Freq = CAPREL;			// Берем частоту из содержимого спец регистра  CAPREL  
	os_send_signal (Turbo_Task);      
   }	

// 9. Нелокальная информация.   

# 14
ClearCom (DEF_COM_PORT);  	//Помогает убрать накапливающуюся(???) ошибку обмена      
// 3. Недостоверный комментарий. Убрала    

 # 15 
 
sig = (BeSignal*)GetByStringID (sigid); //СОздать сиг с именем, из списка имен если его пор номер не > FCount    
                                                //FCount - при созд объ - кран    
// 3. Недостоверный комментарий. Убрала  

