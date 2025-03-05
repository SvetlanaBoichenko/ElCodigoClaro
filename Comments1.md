# 1
bool    ALimit::OnAfterLoad()      //Необходимо проверить полноту заполнения свойств - а вдруг забыли...
{
    AObject  *par = (AObject*)GetParam();
  
    if (par != 0)
        return = true;

    return (false);
}

