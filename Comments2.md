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

