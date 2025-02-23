bool    WriteDO (int no, WORD data)    
{   
&nbsp;&nbsp;  bool ret = false;  
#ifdef __WIN32__  
&nbsp;&nbsp;&nbsp;   if (FRB_SendSA (0, no, data) == 0)  
&ensp; &ensp; &ensp;     ret = true;  
#else 
&nbsp;	outpw (no*2, data);           
&nbsp;	ret = true;  
#endif  
&nbsp;   return (ret);  
}  
