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
