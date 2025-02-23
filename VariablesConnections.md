
	while(1)   
    &ensp; {   
   &ensp; &ensp; int resultfunc = Sys->AlarmStepList->ExecuteAlarmCommand();   
   &ensp; &ensp; &ensp; if(resultfunc < 0)  
   &ensp; &ensp; &ensp; &ensp; {  
   &ensp; &ensp; &ensp; &ensp; &ensp;   //Print("Terminate Thread \r\n");  
   &ensp; &ensp; &ensp; &ensp; &ensp;   SYSCONTROL->ClearAlarm();  
   &ensp; &ensp; &ensp; &ensp;  }  
&ensp; &ensp; &ensp; &ensp; &ensp; ..  
&ensp; }
