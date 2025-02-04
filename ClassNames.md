# имена классов

BeKran2ManDevice  - BeKranMaster   
BeKran2ServDevice - BeKranSlave   
BeReestr          - BeObjRegistrator     
BeIODevice        - BeIOEquipment     
ABaseSystem       - AMainSystem     
AArchManager      - ArchiveDirector     
BeSyscontrol      - BeSysOperator   
BeDevice          - BeModule
   
# имена методов и объектов 
//Объекты  
  VSAS -   masterVsas,    KLAPAN_TK - masterKlapanTk      
  VSAS1 -  slaveVsas1,    VSAS2 - slaveVsas2, KLAPAN_TK2 - slaveKlapanTK      
  SYSCONTROl -  SysOperator      
    
  // Методы  
  SYSCONTROL::SetLampaNZStop  - SysOperator::SetNZIndicator(..)    
  SYSCONTROL::StartAlarmFunction  -  SysOperator::SetSysAlarm(..),  SysOperator::SetExtraAlarm(..)    
  BeDevice:: UpdateData()  -  BeModule::UpdateSignals()  
  BeDevice::IsAlarm()      -  BeModule::IsAlarmState()  
  
 
