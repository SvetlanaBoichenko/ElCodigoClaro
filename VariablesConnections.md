bool    WriteDO (int no, WORD data)    
{   
&nbsp;&nbsp;  bool ret = false;  
#ifdef __WIN32__  
&nbsp; if (FRB_SendSA (0, no, data) == 0)  
&ensp; &ensp; &ensp; ret = true;  
#else  
&nbsp; &ensp; 	outpw (no*2, data);           
&nbsp; &ensp; 	ret = true;  
#endif  
&nbsp;   return (ret);  
}  
