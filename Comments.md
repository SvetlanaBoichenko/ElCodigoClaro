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




