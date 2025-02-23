# 1
	
 while(1)   
    &ensp; {   
   &ensp; &ensp; int resultfunc = Sys->AlarmStepList->ExecuteAlarmCommand();   
   &ensp; &ensp; &ensp; if(resultfunc < 0)  
   &ensp; &ensp; &ensp; &ensp; {  
   &ensp; &ensp; &ensp; &ensp; &ensp;   SYSCONTROL->ClearAlarm();  
   &ensp; &ensp; &ensp; &ensp;  }  
&ensp; &ensp; &ensp; &ensp; &ensp; ..  
&ensp; }
// использовала связывание при выполнении программыдлч остановки цикла выполнения команд,  
//когда команда из списка вернет -1.  
// для корректировки порядка выполнения действий и завершеия алгоритма необходимо корректировать список  
// выполняемых команд  

# 2

