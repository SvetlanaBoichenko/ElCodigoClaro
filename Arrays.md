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
class	AList
{
protected:
friend class    ATreeElement;  

	void	**FItems;

  int	    FCount;
  int	    FSlotCount;

  int  	FIncrement;

	void	Expand();



 
