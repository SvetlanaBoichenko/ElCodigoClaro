# Типы данных  

1.  
int ind = s1.indexOf ('*');  
  
static final char TEST_STR_BOUNDS_CHAR = '*';  
int boundTestStrIndex = s1.indexOf (TEST_STR_BOUNDS_CHAR);  
// ввела символьную константу и исправила имя переменной  

2.  
int end = stmp.indexOf(" ");      
  
static final char PRICE_STR_LAST_CHAR = '*';    
int LastPriceStrIndex = s1.indexOf (PRICE_STR_LAST_CHAR);   
//Аналогично 1.    
  
3.    
String sc = sc.replaceAll ("\\s+", "");  
  
static final String STR_FOR_REPLACE = "\\s+";   
static final String STR_TO_REPLACE = "";   

String strCommand = strCommand.replaceAll (STR_FOR_REPLACE, STR_TO_REPLACE);  
//  ввела строковую константу и исправила имя переменной    
  
  
4.  
  double per =  (vmax / sum ) * 100.0;  
  
  int voteSum....
  double votePercent;    
  if (voteSum != 0) {   
    votePercent =  (voteMax /(double) voteSum ) * 100.0;  
  }   
 // Ввела проверку деления на 0, изменила имена переменных, изменила тип voteSum на целый
 // сделала приведение типа  


5.  tf = ((float)tob2) / ZUBCOUNT;  
         new_tob = tf / TIME_READ;  
     
  
 if (ZUB_COUNT != 0 && TIME_READ_MS != 0) {    
     koef = ((float)turbOboroty) / ZUB_COUNT;    
      tt /= TIME_READ_MS;    
}      
// ввела проверку деления на 0, изменила имена переменных и констант    
  
6.   
  
 LOCAL_MASLO_GMK->SetSignal("SIGNAL", "I7053", 13, 5);   
  
 static const String  TYPE_DEVICE_SIGNAL = "SIGNAL";  
 static const String  TYPE_FRBIO_7053 = "I7053";  
 LOCAL_MASLO_GMK->SetSignal (TYPE_DEVICE_SIGNAL, TYPE_FRBIO_7053, 13, 5);   
// Изменила строковые переменные  

7.  
if (curnod != null && newnod.value.compareTo(curnod.value)== ascendval) {..}

boolean correctCurNode = (curNode != 0);
boolean newNodeEQcurNode = (newnod.value.compareTo(curnod.value)== ascendval);  
if ( correctCurNode && newNodeEQcurNode)  {..};  
// применила булевы переменные, изменила имена переменных
  
8. 
 if ( this.count - 1 < 0.5 * this.capacity) {..};  
   
 boolean countLTcapacity = (this.count - 1 < 0.5 * this.capacity);  
 if ( countLTcapacity) {..};  
 // применила булеву переменную  
  
 9. 
for (int i = 0; i < N ; i++) {  
    sum = sum +Votes[i];  
}  
  
 if (sum > Integer.MAX_VALUE) {  
        return 0;  
 }  
 // Ввела проверку на переполнение   
  
  
10. 
  float tf = ((float)ZubCount) / ZUB_COUNT;  
  
double freqTurbo = 0;  
if (ZUBCOUNT != 0) {  
  freqTurbo= ((double)ZubCount) / ZUB_COUNT;  
}    
// Изменила тип на тип с большей точностью    

11.  
 if ( per >= 50.000)    
   retstr = "majority winner " +  sindex;    

  BigDecimal percentVote = new BigDecimal(per);  
  BigDecimal valueZero = new BigDecimal(0.0);  
        if (percentVote.compareTo(zero) >= 0) { retMessage = "majority winner " +  kandidatIndex;}  
    }  
// Для сравнения вещественных чисел ввела два объекта работающих с вещ числами  
// изменила имена переменных  
  
12.  
static final int ROUND_CEILING = 1;  
static final int ROUND_FLOOR = 3;  
percentVote.setScale(4,ROUND_CEILING);  
// ОВвела точность и округлила резкльтат предыдущего сравнения

 
