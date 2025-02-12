# 12 имен констант

1. static  const   int    XML_MODE = 0x0001;
   static  const   int    WRITER_XML_MODE = 0x0001;
// Добавила указание - к какому объекту относится переменная
   

2. int ErrorValue = 1;
   const int ERROR_VALUE = 1;
   // Перевела в верхний регистр и поставила разделители

3. const int ON = 1;
   const int OFF = 0;
   const int NONE = -1;

   const int STATE_ON = 1;
   const int STATE_OFF = 0;
   const int STATE_NONE = -1;
   const int COMMAND_ON = 1;
   const int COMMAND_OFF = 0;
    // Добавила уточнение - относится ОN и OFF к определению состояния или команде

4.  const unsigned short PAN_ID = 2;
   const unsigned short  CHAN_ANALOG_ID = 2;
// идентификатор аналогового канала, изменила имя на более понятное

5. const unsigned short P_16   = 0xA001;
   const unsigned short PIN_16   = 0xA001;
   
6.static  const   TYPE_XML     =   0x0002;
  static  const    TYPE_CSV     =   0x0004; 

  static  const   READER_TYPE_XML     =   0x0002;
  static  const   READER_TYPE_CSV     =   0x0004;
  // Добавила тип объекта - Reader

7- 
