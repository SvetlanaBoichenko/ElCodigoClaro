bool    WriteDO (int no, WORD data)  
{  
	bool ret = false;  

#ifdef __WIN32__

	if (FRB_SendSA (0, no, data) == 0)  
		ret = true;
#else
  
	outpw (no*2, data);         
	ret = true;
  
#endif

    return (ret);
}
