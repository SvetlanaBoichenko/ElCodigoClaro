# 1 
int i;
for (i = basebit;  i <= lastbit;  i++)
    BitsOldValue[i] = 0xFF;
//-------------------
static int NO_INIT   =  0xFF;
for ( int i = basebit;  i <= lastbit;  i++)
    BitsOldValue[i] = NO_INIT;    
// Внесла объявления счетчика цикла в заголовок цикла, ввела константу для определения 
// неинициализированной переменной   

# 2  
    uint ret = OFF;
    .. много кода
    if ((NetSetPorts[port_index] & bit_mask) != 0)
    {
        ret = ON;
     ..
    }
    ..  
    return ret;  
           
------------------------
    .. много кода
    ..       
    uint ret = OFF;       
    if ((NetSetPorts[port_index] & bit_mask) != 0)  {    
      ret = ON;    
     ..    

    }  
    .. 
   return ret;    
    // Перенесла переменную ближе к ее использованию
    
# 3
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

# 4
      int Tcur = 0;          	  // real cur pos  
      .. много кода
  
      Tcur += Len1 - Lenold;       // +next pos  
      Lenold = Len1;  
  
      if (Tcur < sv1) {  
        ..  
      }  
    
// ----------------------        
      .. много кода  
      ..
      int currrentPos += curLineLen - oldLineLen;       // +next pos  
      oldLineLen = curLineLen;  
  
      if (currrentPos < firstSemaforPos) {    
        ..  
      } 
// объявила переменную ближе к ее использованию, изменила все имана переменных

        
# 5
    boolean fret = false;  
    .. много кода 
    
     int i, j = 0;
     for (int i = 0; i <= tab1.length-tab2.length; i++ ) {
            for (int j = 0; j <= tab1[0].length - tab2[0].length; j++) {
                fret = ifsubarr2(tab1, tab2, i, j);
                if (fret)
                    return fret;
            }
        }
      return fret;
// ---------------------------------   
         
      for (i = 0; i <= baseTabPosition.length - subTabPosition.length; i++ ) {
            for (j = 0; j <= baseTabPosition[0].length - subTabPosition[0].length; j++) {
                if (isSubArrray(baseTabPosition, subTabPosition, i, j))
                    return true;
            }
        } 
  return false;

 // Внесла счетчики в заголовок цикла, избавилась от лишней переменной 
 // переименовала остальные переменные и функцию       
        
# 6
    class   AIOService     
    {
        protected:
        AInterface* FInterface;
        AProtocol*  FProtocol;
        ASreing name;
        AString comment;
        ..
        
   public:
	AIOService (AString name, AString comment);
	virtual	~AIOService();
};
//---------------      
AIOService::AIOService (AString namе , AString comment)       
{
    FInterface  = 0;
    FProtocol   = 0;
    FName = name;
    FComment = comment;
}  
// Добавила инициализацию указателей на объекты нулями

# 7  
public static boolean LineAnalysis(String line)
    {  
        String s1 = line;  
     .  
     .  
    }
// ---------------------------
   public static boolean LineAnalysis(String line)
    {
        String inputLine =new String(line);
     .
     .
    }
// Создала новый экземпляр типа String c теми же данными
// переименовала новую строку

# 8  
   public static String BastShoe(String command) {
        int cmd = 0;
        String sc = command.substring(0, 1);
    ..
}  
//---------------------
static ins=t firstCommandTypePos = 0;  
static ins=t lastCommandTypePos = 1;  

 public static String BastShoe(String command) {  
        int cmd = 0;  
        String inpCommand = new String(command);  
        String typeCommand = inpCommand.substring(firstCommandTypePos, lastCommandTypePos);  
    ..   
}
// Создала новый экземпляр типа String c теми же данными
// переименовала новую строку

# 9
  public static void MatrixChange (char[][] stmp, char[][] stmp2) {
        int S1 = stmp.length;
        int S2 = stmp[0].length;

        for (int x = 0; x < S1; x++) {
            for (int y = 0; y < S2; y++) {
                stmp[x][y] = stmp2[x][y];
            }
        }
    }
 // -------------------------
   public static char[][] MatrixChange (char[][] arrCopyTo, char[][] arrCopyFrom) {
        int FirstArrayLenRow  = arrCopyTo.length;
        int SecondArrayLenRow = arrCopyFrom[0].length;
        char [][] retArrayCopy = new char (arrCopyTo.lenght),arrCopyTo(0).lenght];

	for (int i = 0; i < arrCopyTo.lenght; i++)  {
		retArrayCopy[i]  = arrCopyTo[i].clone();
	}

       for (int x = 0; x < FirstArrayLenRow; x++) {
            for (int y = 0; y < SecondArrayLenRow; y++) {
                retArrayCopy[x][y] = arrCopyFrom[x][y];
            }
        }
    }
  return retArrayCopy;  
// Создала новый массив - копию входного
// Переименовала переменные

# 10 
class   AInterface  :   public  AObject
{
protected:
    HANDLE	Handl;
    long    FTimeOut;
    AFlag   FPortOptions;

public:
..
};
//--------------------
AInterface::AInterface(AString name, AString comment)
          : AObject (name, comment)
{
    Handl = INVALID_HANDLE;
    FTimeOut = DEFAULT_TIMEOUT;
    FPortOptions = 0;
}
//добавила инициализацию FTimeOut и FPortOptions в конструкторе класса

# 11   
    void ConfirmOnChange (DEVICE_DD *confirm_dd, int sid, int value, int valflag)  
    {  
    	uint    cf;  
    	switch (sid)  
    {
    case CONFIRM_NET_SOUND_SIGNAL:  
    case CONFIRM_NET_LIGHT_SIGNAL:  
    ..    
   }  
 }  
//--------------------
   
void ConfirmOnChange (DEVICE_DD *confirm_dd, int sid, int value, int valflag)
{
    switch (sid) 
    {
    	case CONFIRM_NET_SOUND_SIGNAL:
    	case CONFIRM_NET_LIGHT_SIGNAL:
	..
  	..
   }
   uint    countConfirms = 0;
   ..
}
// Переместила и проинициализировала функцию

# 12  
static int  const MOVE = 0x10 ;          
static int const DAMAGED =  0x40 ;          
static int const UNKNOWN = 0x0F ; 
//Ввела статические переменные вместо обычных

# 13  
BeSystem::BeSystem()
{
    REESTR->FSystem = this;

    TimerValue = 0;
    
    firstKTCConfirm = false;
    firstKTCErr = false;
    lamp_blink_mgp = false;
}
//------------------------
BeSystem::BeSystem()
{
    REESTR->FSystem = this; 
    
    firstKTCConfirm = false;
    firstKTCErr = false;
    lampBlinkMgp = false;
}
// Убрала TimerValue - нигде не используется, изменила имя переменной

# 14

сlass   BeSystem : public BeClass
{
 public:

    BeAlarm *AlarmStepList;
    BeAlarm *ExtraStepList;

	pthread_t	FThreadId;

	void    UserFixedConfig();
	bool    UserLoadConfig();
..
} 
-------------------
BeSystem::BeSystem()
{
    REESTR->FSystem = this;
    
    firstKTCConfirm = false;
    firstKTCErr = false;
    lampBlinkMgp = false;

    AlarmStepList = 0;
    ExtraStepList = 0;    
}
// Проинициализировала AlarmStepList, ExtraStepList


# 15

class   BeSyscontrol  : public BeDevice
{
protected:

    _timevalue      FAlarmOilTimeMs;
    _timevalue      FExtraSignalTimeMs;

    BeReadSignal*   FIO_SYSCONTR_NZ_OBOROTY_MAX;
 
    bool LampaBlink;
    bool LampOn;
 
    bool IskraOn;
    ..
} 
//------------------
BeSyscontrol::BeSyscontrol (int devid, char *strid)
            : BeDevice (devid, strid, SYSCONTROL_SIGNAL_COUNT)
{ 
     if ((strid == 0) || (*strid == 0))
        ErrorDetect();
 
    FIO_SYSCONTR_NZ_OBOROTY_MAX  = new BeReadSignal (this, SYSCONTR_NZ_OBOROTY_MAX, "NZ_OBOROTY_MAX");

    BlinkTimer = 0;
    FExtraSignalTimeMs = 1000;
    FAlarmOilTimeMs    = 3000;
     
    IskraFlag = false;           
    LampaBlink = false;
    LampOn = true;
 }
// добавила инициализацию булевых переменных в конструкторе
// изменила имена переменных




