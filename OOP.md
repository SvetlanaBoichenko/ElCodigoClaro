# Три примера методов-фабрик  
      
    public class Devices {  
    private int type;  
    private String name;  
    private int timeToMove;  
  
    public String GetName() { return name;}   
    public int GetMoveTime() {return timeToMove;}  
    public int GetDeviceType() {return type; }   
  
    public Devices (int type, String name, int timeToMove)  {  
        this.type = type;  
        this.name = name;  
        this.timeToMove = timeToMove;  
    }  

    static class BitDevice { 
        private boolean isInput; 
        private String name; 
        
    } 

   ##   1 
    public static BitDevice  MakeBitDevice () {   
        BitDevice SignalNZ = new BitDevice();   
        SignalNZ.name ="Неоткл защита";   
        SignalNZ.isInput = false;  
        return SignalNZ;  
    }  
  
  ##   2
    public static Kran MakeNewKran (int type, String name, int timeToMove) {    
        return new Kran (1, "Vsas", 40);    
    }    
  
   ##  3  
    public static Klapan MakeNewKlapan (int type, String name) {    
        return new Klapan(1, "TK", 0);    
    }    
  
  ### Вызов методов
    public static void main(String[] args)  
    {
        Kran kranVsas = Devices.MakeNewKran (2, "Vsas", 15);
        Klapan klapanTK = Devices.MakeNewKlapan (2, "TK");
        BitDevice NZ  = Devices.MakeBitDevice();
    }  
}  
  
 // классы   
 class Klapan extends Devices {  
     public Klapan(int type, String name, int timeToMove) {  
         super(type, name,0);  
       }  
  }  

class Kran extends Devices {  
    public Kran(int type, String name, int timeToMove) {  
        super(type, name, timeToMove);  
      }  
  }  


# Абстрактные классы
// Класс для записи в файл  

class   AWriter  : public  AFile    
{   
private:   
protected:  
    
    virtual void    OnOpenTag (AString str) = 0;    
    virtual void    OnCloseTag (AString str) = 0;       
.  
.  
}  

 // Базовый класс для создания интерфейсов обмена данными  
 
class   AInterface  :   public  AObject  
{  
protected:  
  
    HANDLE	Handl;  
    long    FTimeOut;  
    AFlag   FPortOptions;  
  
public:  
	virtual	int		WriteData (void *buf, unsigned int len) = 0;  
	virtual	int		ReadData  (void *buf, unsigned int len) = 0;  
.  
.  
}  
