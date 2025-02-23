bool    WriteDO (int no, WORD data)    
{   
&nbsp;	bool ret = false;  
#ifdef __WIN32__  
	if (FRB_SendSA (0, no, data) == 0)  
&nbsp;ret = true;  
#else 
&nbsp;	outpw (no*2, data);           
&nbsp;	ret = true;  
#endif  
&nbsp;   return (ret);  
}  
