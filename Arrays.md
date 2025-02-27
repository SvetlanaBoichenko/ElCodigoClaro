# 1
#define MAX_DEVICE_COUNT    32

struct  SDevice *DDArray[MAX_DEVICE_COUNT];  
//--------------------------  
#include <list>
..
    std::list<int> listDevice;
    
int arrDevice [listDevice.size()];  
std::copy(listDevice.begin(), listDevice.end(), arrSevice);
  
// MAX_DEVICE_COUNT -число устройств зараннее неизвестно. Частых и быстрых обращений к массиву нет.
// на этапе инициализации можно сделать List а перед началом работы обратить в одномерный массив,   
// либо продолжать работать со списком и выбирать устройство перебором -число устройств в этой области не велико и скорости не большие  

# 2 
#include <list>
..
class	AList

{

protected:

    friend class    ATreeElement;  

    void	**FItems;

    int	    FCount;
    
    int	    FSlotCount;
    
    int  	FIncrement;

    void	Expand();
 
    ...

};

int	AList::Add (void *object)

{

    int pos = FCount;

    if (FCount >= FSlotCount)
 
    AList::Expand();

    FItems[pos] = object;

    return (FCount++);
    
}

//-----------------------------------
 
class	AList

{

protected:

friend class    ATreeElement;  

 std::list <void *> FItems;

  int	    FCount;
  
  int	    FSlotCount;

...

};

FItems.Add(void *object); 

...

//Здесь также изначально неизвестно число устройств, выбран динамический массив 
// Добавление и удаление устройств из массива совершается часто, и релокаций может быть достаточно
// Можно использовать список из библиотеки или создать сво1

# 3
#include AList.h// AList - из прошлого примера

class   ValueList  : public AList
{

public:

    virtual __fastcall  ~ValueList();

    void AddValue (float value) { Add (new ArrayValue (value)); };
};

//-------------------------------

class   ValueList  : public TList
{

public:

    virtual __fastcall  ~ValueList();

    void AddValue (float value) { Add (new ArrayValue (value)); };
};

//Так как программ написана в среде С++ Builder удобно использовать средства TList  
// вместо раннее используемого AList которыя является динамическим массивом. 
// Проект постобработки, данных не много, высокой скорости не требуется. Перебор списка не приведет к потерям производительности


# 4
    int mediana[21]={0};
    
    struct duomuo *stud = new struct duomuo[n];
    
    for(int i=0;i<n;i++) {
    .
    
    .  
     while (pazym != -1) {  
            stud[i].paz[p]=pazym;  
            stud[i].GP+=stud[i].paz[p];  
            mediana[p+1]= pazym;  
            p+=1;  
   .
   
   .
   }  

//--------------

   std::list<int> mediana;
   .
   
   .
   mediana.next = pazym;

   
//   int mediana[21] - лучше заменить на список, может быть выход за пределы массива mediana[p+1]= pazym;

# 5
    int a;
         
    for (int i = Len1-1; i >= 0; i--) {
    
        a = results[i];
        .
        
        .

    }
   //--------------------------------------------- 
   

   for (int res : results) {
   
        curResValue = res;
      
      .
      
      .
      
   } 
   // Избегание ошибок при переборе массива
   
