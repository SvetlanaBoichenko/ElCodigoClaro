# 1
/*
void BeKranSlaveDevice::DefLampState()  
{  
   switch(FValue)  
    {   
    	case OPEN:
         	FIO_KRANSL_OPEN_LAMP->StopBlink();
            FIO_KRANSL_CLOSE_LAMP->StopBlink();
         	FIO_KRANSL_CLOSE_LAMP->SetValue (OFF);
            FIO_KRANSL_OPEN_LAMP->SetValue (ON);

      	break;
..
..
*/  
//--- 11. закоментрованный код.   
//--- Убрала.  

# 2
    TMDIChild* CurrentChild = 0; 
    ...
    TBookmark SavePlace;
    //Закладка на текущей записи
    SavePlace = CurrentChild->ADOQueryEvent->GetBookmark();

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
    FWaitTimeOut = 0;                           //Сброс таймера
    FKranCommand = COMMAND_NONE;

    FIO_KRANSL_TIMEOUT->ClrTimer();		//Сброс таймера крана

    FIO_KRANSL_CONTROL_OPEN->SetValue (OFF);
    FIO_KRANSL_CONTROL_CLOSE->SetValue (OFF);  
} 

//--- Шум  
// И так понятно что сброс таймера - Убрала.  

# 4
void BeKranSlaveDevice::VerifyError()
{                                   //Неисправен  ERROR или DAMAGED
  
    if ((FValue & DAMAGED) != 0)    //Проверить!!!!!!!!!
    {
        FDamagedCount++;

        if (FDamagedCount < FMaxDamagedCount)
        {
                FValue = FLastGoodValue;    //Пока не меняем состояние

            if (FWaitTimeOut == 0)      //Если не запущен ни один из таймеров крана (по управл или срабатыванию концевого)
            {

                FWaitTimeOut = KRANSL_DEF_STATE_TIME;
                FIO_KRANSL_DEF_STATE_TIMER->SetTimer (KRANSL_DEF_STATE_TIME , FDamageDefineTime);
            }
        }
..  
..  
}  
//--- Шум и бормотание    
//--- Убрала комментарии    

# 5
  // Кран закрыт - Хочу открыть  
   else if ((FIO_KRANSL_SENSOR_OPEN->Value() == OFF)&& (FIO_KRANSL_SENSOR_CLOSE->Value() == ON))  
   {  
   		// if ((FIO_KRANSL_CONTROL_OPEN->Value() == ON) &&(FIO_KRANSL_CONTROL_CLOSE->Value() == OFF))  
        //   FValue = KRAN_OPENING1;  
  
         if ((FIO_KRANSL_CONTROL_OPEN->Value() == OFF) &&(FIO_KRANSL_CONTROL_CLOSE->Value() == ON))  
           FValue = KRAN_CLOSING;  
  
         else if ((FIO_KRANSL_CONTROL_OPEN->Value() == ON) &&(FIO_KRANSL_CONTROL_CLOSE->Value() == ON))  
        	FValue = KRAN_DAMAGED;  
         else  
         	FValue = KRAN_CLOSE;    //управляющих нет  
   }  
   //------------  
 // Кран закрыт  
   else if ((KRAN_SENSOR_OPEN->Value() == OFF) && (KRAN_SENSOR_CLOSE->Value() == ON))     
   {   
  // Только управляющий закрытия равен 1   
	if ((KRAN_CONTROL_OPEN->Value() == OFF) &&(KRAN_CONTROL_CLOSE->Value() == ON))   
           FValue = KRAN_CLOSING;  
 
 // Управляющие сигналы  - оба равны 1  
         else if ((KRAN_CONTROL_OPEN->Value() == ON) &&(KRAN_CONTROL_CLOSE->Value() == ON))  
        	FValue = KRAN_DAMAGED;  
  
  // В любой другой суперпозиции сигналов  
	 else  		
          FValue = KRAN_CLOSE;       
   }  
      
//---- Бормотание  
//---- Исправила комментарии и имена переменных для большей ясности  

# 6
     PEXEALARMFUNC Func;  // OnExecute
     SLine *LineStep;
     ..
     ..
if (command == CLOSE)  
    {        
        FIO_KLAPAN_CONTROL_CLOSE->SetValue(ON);  
        FIO_KLAPAN_CONTROL_OPEN->SetValue(OFF);  
                     //Фиксируектс¤ только OPEN & CLOSE  
     }  
    if (command == OPEN)  
    {
        FIO_KLAPAN_CONTROL_CLOSE->SetValue(OFF);  
        FIO_KLAPAN_CONTROL_OPEN->SetValue(ON);  
    }  
//---- Шум  
// Других команд здесь и нет. Убрала комментарий  

# 7
    int         FCount;
    ... 
     int ret = -1;
     FUNCRESULT result;
     PEXEALARMFUNC Func;  // OnExecute
     SLine *LineStep;
     ..
     ..
 
     result = Func(LineStep, timevalue);    //выполнить эту ф. OnExecute(...)
 //   Print("result = %i \r\n  \r\n", result);

     if (result == STEP_NEXT)                 //Если ф выполн полностью - переход на след строку
        {
            FCurrentIP++;

        if (FCurrentIP >= FCount)       //Больше чем строк в массиве записей-содерж ф.
            {                           //Закончить ав останов
                ret = -1;
                FCurrentIP=0;
            }
        }

     ret = result;
//-------------------
     static public int ALARM_STOP = -1;
     
     int         FAlarmLinesCount;
     ...
     
     int ret = -1;
     FUNCRESULT result;
     PEXEALARMFUNC AlarmFunc; 
     SLine *LineStep;
     ..
     ..
     
     result = AlarmFunc (LineStep, timevalue);    

     if (result == STEP_NEXT)       
        {
            FLineNumber++;

        if (FLineNumber >= FAlarmLinesCount)         	
            {                             	
                ret = ALARM_STOP;	//Закончить ав останов  
                FCurrentLine = 0;  
            }  
        }  

     ret = result;     
     ..  
     }  
    return ret;    
//---- 11 Шум  
// Изменила имена функций и переменных. Убрала лишние комментарии  
     
# 8 
int TaskBit (int bit_code, int task_no) {  
..  
..  
if (bit_code == TIMER_BIT)  
    {  
        bit_code = GetTimerBit();  
  
        if (bit_code < 0)     //Если ошибка  
            ret = bit_code;  
        else  
     		ret = TaskTimBit (bit_code, task_no);   // задание N задачи в массиве  
    }      
	else if (bit_code < MAX_BUS_BITS_COUNT)        // Они первые в списке бит  
   	    ret = TaskBusBit (bit_code | sec_flag, task_no);// Если SecondParent то получится Ошибка -код больше Мах числа сигналов Bus  
	else if ((bit_code >= NET_BIT_BASE) && (bit_code < MAX_NET_BIT_NUMBER))  
 ..  
 ..  
 }  

//---------------------
int TaskBit (int bitCode, int taskNo) {  
..  
..  
if (bitNumber == TIMER_BIT)  
    {  
       bitCode = GetTimerBit();  
  
        if (bitCode < 0)	// Если ошибка  
            ret = ERROR_BIT_CODE;  
        else  
     	    ret = GetTaskTimerNo (bitCode, taskNo);   // задание N задачи в массиве  
    }      
    else if (bitCode < MAX_BUS_BITS_COUNT)          
   	    ret = GetTaskTimerNo (bitCode | secondFlag, taskNo);  
	else if ((bitCode >= NET_BIT_BASE) && (bitCode < MAX_NET_BIT_NUMBER))  
 ..  
 ..  
 }  

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
//-----------------------------  
// USER CODE BEGIN (ASC_Init,1)

  P3    |= 0x0C00;    //  set P3.10 output latch (TXD0)
  DP3   |= 0x0400;    /// set P3.10 direction control (TXD0 output)
  DP3   &= 0xF7FF;    /// reset P3.11 direction control (RXD0 input)

  S0BG  = BaudNum;
  S0REN = 1;
  S0TIR = 0;

  // USER CODE END
}

// 11. Закомментированный код. Убрала

# 10










