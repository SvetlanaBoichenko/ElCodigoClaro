# 1
	
 while(1)   
    &ensp; {   
   &ensp; &ensp; int resultfunc = SYSTEM->AlarmStepList->ExecuteAlarmCommand();   
   &ensp; &ensp; &ensp; if (resultfunc < 0)  
   &ensp; &ensp; &ensp; &ensp; {  
   &ensp; &ensp; &ensp; &ensp; &ensp;   SYSCONTROL->ClearAlarm();  
   &ensp; &ensp; &ensp; &ensp;  }  
&ensp; &ensp; &ensp; &ensp; &ensp; ..  
&ensp; }  
// использовала связывание при выполнении программыдлч остановки цикла выполнения команд,  
// когда команда из списка вернет -1.  
// для корректировки порядка выполнения действий и завершеия алгоритма необходимо корректировать список  
// выполняемых команд  

# 2
if (name.UpperCase() == "COMMENT") {  
  &ensp; &ensp; value_new = AString("Кран номер") + FObjectID ;  // comment contains  №<number>  
   &ensp; &ensp;
   }  
  //--------------- 
  const AString COMMENT_KRAN_NUMBER  = "Кран номер ";  
  const AString DEF_COMMENT  = "COMMENT";  
    
  if (name.UpperCase() == "DEF_COMMENT") {   
  &ensp; &ensp; value_new = AString("COMMENT_KRAN_NUMBER") + FObjectID ;  // comment contains  №<number>    
   &ensp; &ensp;...  
   }    
// Ввела константы вместо прямого сравнения и присвоения значений строк , так как это не локальное использование  

# 3 
 	REESTR->Syscontrol = new BeSyscontrol (SYS_SYGNALS, "SYSCONTROL");  
  
	SYSCONTROL->SetSignal ("BUTTON_ALARM",     "I7053",    9,      3);  
  
	SYSCONTROL->SetSignal ("ALARM_MASLO_NIZ",   "I7053",    13,      11);  
	SYSCONTROL->SetSignal ("ALARM_MASLO_VERH",  "I7053",    13,      8);  
 // ССлздается объект срузу после объявления, он всегда будет в этой системе, это жесткое условие
 //  Назначение свойств его сигналов сделно так, что их легко менять
 
