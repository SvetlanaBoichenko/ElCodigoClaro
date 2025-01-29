# 6.1

 RegList - internListRegistrator  
 // список внутренних списков объектов

 Name - portName  
 // имя порта 
 
 Mode - portWorkMode   
// режим работы порта чтение или запись

MsCounter - msAnswerCount  
// счетчик времени ожидания ответа 

 AddressIndex - fullDeviceAddress     
// переменная получаемая после добавления доп. подстроки к основному адресу устройства

WErr - writeErrorCode  
RErr - readErrorCode  
//Коды ошибок записи и чтения получаемые при обмене данными

# 6.2. 

Type - eventType   
// Тип события
 
 IsForMe - isMyEvent  
 // Адресовано ли событие этому объекту

queueRecord  
// получаемая запись из очереди

threadParam   
// указатель на переменную передаваемую в функции потока

# 6.3. 

devid - deviceID  
// идентификатор устройства в функции создания обьекта класса Device

sid  - signalID   
// идентификатор сигнала в функции его обработки

KlapanSlave1  - slaveKlapan  
// указатель на объект класса Klapan 


# 6.4. 
FPtr - prtFunction  
ret  -  returnValue  
Device_ESZ_Zapazdivanie - devEszZapazdivanie  
inp  - inputValue    
pos  - curLenPos  


