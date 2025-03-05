# 1
// Необходимо проверять полноту заполнения свойств - а вдруг забыли что то 
bool    ALimit::OnAfterLoad()      
{  
    AObject  *par = (AObject*)GetParam();  
    if (par != 0)  
        return = true;  
    return (false);  
}   
//1. Информативное сообщение Пояснение к функции  

# 2
    ..
    if (state.IsHave (PARAM_EVENT_MESSAGE | PARAM_EVENT_ERROR))
    {
        eventvalue = AString (ev->FEventValue).FloatFormat() +  " - ";
        eventvalue = ev->FValue;            //todo Надо заменить на текст из списка в следующей версии
        out.AddStringAtPos (eventvalue, 55);
    }
//6. Заметка на будущее

# 3
AClass::AClass (AString name, AString comment)
      : ANode (name, comment),
        AList (1)
{
    ClrStructOptions (COMPONENT_NO_OWNER);    //На этом много завязано - не менять! может все слететь
}
// 4. Предупреждение о последствиях

# 4
// ToDo   Нужно будет сделать доп. проверку по connect.  
ADescriptor*    GetClassDescriptor (AString class_name, FLAG connect_type)  
{  
    ADescriptor *ret = (ADescriptor*)LPClassDescriptorList->GetChildByName (class_name);  
    if (ret != 0)  
    {  
        FLAG    id = ret->GetID();  
        AFlag   key = connect_type;  
        if (!key.IsTrue (id))  
            ret = 0;  
    }  
    return (ret);  
} 
//6. Заметка на будущее

# 5
#if !defined (__WIN32__) // This function defined only in Windows!!!    
unsigned char* _mbsspnp (unsigned char *s1, unsigned char *s2)   
{   
	bool	f;   
	unsigned char *pout = 0;   
..   
..   
 return (pout);   
}   
#endif     
// 3. Прояснение при использовнии системной функции для разных ОС  

# 6  
#if !defined (__WIN32__)  
static const ATIME   BASE_INTERVAL_VALUE = 10;  //Больше нельзя - линукс дурит, обрезает MAXLONG  
// 3. Прояснение при использовнии системной функции для разных ОС 

# 7
AComponent*	AComponent::GetChildByName (AString name)   //ToDo нужна проверка на пустое имя   
{   
    AComponent* node = 0;  
    int         child_count = ChildCount();   
    name = name.UpperCase();   
    ..   
    ..   
}   
//6. Заметка на будущее ToDo

# 8
ACoProcess::~ACoProcess()
{
    FProcess = 0;    //Удалять не надо - сам удалится в списке процессов
}

// 1. Информативный комментарий, предупреждение

# 9
class   AObject : public AClass, public APropertyClass, public AStateClass, public ACommandClass  
{  
protected:  
    static  long    FTimerIndex;  
    AClass*     FListRegistrator;   //Для хранения списков команд и пр.  
    long        FAddressIndex;  
..  
..  
    virtual void        RegistrateInternalList (AClass *list);   //Для регистрации спискрв типа состояний и команд  
// 1. Информативные комментарии

# 10
ATimerManager::ATimerManager()  
             : AProcess ("SysTimer", "Системный таймер", PROCESS_READ)  
{  
    SetStructOptions (COMPONENT_NO_OWNER | COMPONENT_FOREIGN_CHILD);  
    FProcessOptions.Set(PROCESS_IS_KERNEL);  
    FTimerIndex = FAddressIndex;      //Заполняем статическое поле для адресации к таймеру  
}  

# 11





