# 1
#ifdef __WIN32__
    FRB_ReceiveRA (0, no, data)  
#else                         	     // Только МиниОС    
	*data = inpw ((no - 8)*2);   // В МиниОс по другому устроена организация адресов модулей    
#endif    
// Объясняет почему используется другая функция в случае загрузки в МиниОС   

# 2
BeClass::BeClass()  
{  
    if (FReestr == 0)   //Первый раз созд Sytem и в нем - реестр, второй  раз- Reestr не созд   
    {  
        FReestr = this;      
        FReestr = new BeReestr();  
    }    
    FID = NO_VALUE;  
}  
//--------------------    
bool REESRT_NO_EXIST = {return (FReestr == 0)};  
  
if (REESTR_NO_EXIST)      
    {   
        FReestr = this;       
        FReestr = new BeReestr();  
    }  
    FID = NO_VALUE;  
}  
// Заменить 0 на крнстанту - станет более понятно   
