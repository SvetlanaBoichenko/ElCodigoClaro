# 12 имен констант

1. static  const   int    XML_MODE = 0x0001;  
   static  const   int    WRITER_XML_MODE = 0x0001;  
// Добавила указание - к какому объекту относится переменная  
     
2. int ErrorValue = 1;  
   const int ERROR_VALUE = 1;  
   // Перевела в верхний регистр, поставила разделители, обозначила как const  
  
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
  
5. const unsigned short P16   = 0xA001;  
   const unsigned short PIN_16   = 0xA001;  
   // Изменила имя, добавила разделитель  
     
6.static  const   TYPE_XML     =   0x0002;  
  static  const   TYPE_CSV     =   0x0004;   
  
  static  const   READER_TYPE_XML     =   0x0002;  
  static  const   READER_TYPE_CSV     =   0x0004;  
  // Добавила в имя тип объекта - Reader  

7-  static  const QString logDir  = "/diagnostic/logs";  
    static  const QString LOG_DIR = "/diagnostic/logs";  
    // Изменила имя , регистр, ввела разделитель  

8. static  const QString logDir  = "/diagnostic/logs";  
   static  const QString LOG_DIR = "/diagnostic/logs";  
    // Изменила регистр и добавила разделитель  

9. const QString muxDir = "/dev/input";  
   const QString soundCardsPath = "/dev/snd";  
  
   const QString MUX_DEVICE_DIR = "/dev/input";  
   const QString SOUND_CARD_DIR = "/dev/snd";  
// Изменила регистр и имя, внесла раделитель  

10. static  const   AString SLASH_STR        = ¨\¨;    
    static  const   AString SLASH_CHAR       = ¨\¨;  
// Изменила имя  

11. static  const   short  GCQueuePrioritiesCount  = 3;  
    static  const   short  GC_QUEUE_PRIORITY_COUNT  = 3;  
    // Измениля имя, регистр, ввела разделители  
  
12. static   const  FLAG   SYSTEM_FLAG_RUNTIME = 0x0001;  
    static   const  FLAG   SYSTEM_FLAG_ERROR   = 0x0002;  
    static   const  FLAG   SYSTEM_FLAG_WARNING = 0x0004;  
  
    static   const  FLAG   SYSTEM_STATE_RUNTIME = 0x0001;  
    static   const  FLAG   SYSTEM_STATE_ERROR   = 0x0002;  
    static   const  FLAG   SYSTEM_STATE_WARNING = 0x0004;  
  
    // Изменила имя констант на соответствующее их смыслу  

    
