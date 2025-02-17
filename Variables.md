1.   
int i;
for (i = basebit;  i <= lastbit;  i++)
    BitsOldValue[i] = 0xFF;

static int NO_INIT   =  0xFF;
for ( int i = basebit;  i <= lastbit;  i++)
    BitsOldValue[i] = NO_INIT;

// Внесла объявления счетчика цикла в заголовок цикла, ввела константу для определения 
// неинициализированной переменной   

2.   
    uint ret = OFF;
    .
    .  много кода
    .
    if ((NetSetPorts[port_index] & bit_mask) != 0)
    {
        ret = ON;
     .
     .
    }
    .  
    .  
    return ret;  
         
//------------------------
    .  
    . много кода  
    .  
    
    uint ret = OFF;  
     
    if ((NetSetPorts[port_index] & bit_mask) != 0)  
    {  
      ret = ON;  
     .  
     .    
    }  
     .  
     . 
    return ret;

    // Перенесла переменную ближе к ее использованию  

    3.  

        int[] newArray;
        int k;
     
        for( k = 0;  k < resarray.length;  k++ ) {
            if (resarray[k] != 0)
                break;
        }
        newArray = new int[resarray.length-k];
    
//----------------------
 
        int subLine = 0;
        for(int  k = 0;  k < resarray.length;  k++ ) {
            if (resarray[k] != 0) {
                subLine = k;
                break;
            }
        }
        
        int[] newArray = new int[resarray.length-k];

// Внесла счетчик в заголовке цикла, объявила массив в месте его инициализации,
// ввела переменную  со смыслом 

4.
      int Tcur = 0;          // real cur pos//  
      .
      . много кода
  
      Tcur += Len1 - Lenold;       // +next pos  
      Lenold = Len1;  
  
      if (Tcur < sv1) {  
        .  
        .  
      }  
    
//----------------------        
      много кода  
      .
      .
  
      int currrentPos += curLineLen - oldLineLen;       // +next pos  
      oldLineLen = curLineLen;  
  
      if (currrentPos < firstSemaforPos) {  
        .  
        .  
      } 
// объявила переменную ближе к ее использованию, изменила все имана переменных

        
    5.  
    boolean fret = false;  
    .  
    .  
    .  
      int i,j = 0;
     for (int i = 0; i <= tab1.length-tab2.length; i++ ) {
            for (int j = 0; j <= tab1[0].length - tab2[0].length; j++) {
                fret = ifsubarr2(tab1, tab2, i, j);
                if (fret)
                    return fret;
            }
        }
      return fret;
//---------------------------------   
         
      for (i = 0; i <= baseTabPosition.length-subTabPosition.length; i++ ) {
            for (j = 0; j <= baseTabPosition[0].length - subTabPosition[0].length; j++) {
                if (isSubArrray(baseTabPosition, subTabPosition, i, j))
                    return true;
            }
        } 
  return false;

 // Внесла счетчики в заголовок цикла, избавилась от лишней переменной 
 // переименовала остальные переменные и функцию       
        
        6.
    class   AIOService     
    {
        protected:
        AInterface* FInterface;
        AProtocol*  FProtocol;
        ASreing name;
        AString comment;
        .
        .
   public:
	AIOService (AString name, AString comment);
	virtual	~AIOService();
};
    
AIOService::AIOService (AString namе , AString comment)       
{
    FInterface  = 0;
    FProtocol   = 0;
    FName = name;
    FComment = comment;
}  
// Добавила инициализацию указателей на объекты нулями

7.






