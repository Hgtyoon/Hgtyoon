- 👋 Hi, I’m @Hgtyoon
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
Hgtyoon/Hgtyoon is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--_variant_t varIdx(0L, VT_I4);
long lCount = 0;
HRESULT hr  = S_OK;
hr = pElemColl->get_length (&lCount);
if (SUCCEEDED(hr))
{
    for(long lIndex = 0; lIndex <lCount; lIndex++ ) 
{ 
  varIdx=lIndex; 
  hr=pElemColl->item(varIdx, varIdx, &pElemDisp);
    if (SUCCEEDED(hr))
    {
        hr = pElemDisp->QueryInterface(IID_IHTMLInputElement, (void**)&pElem);
        if (SUCCEEDED(hr))
        {
            _bstr_t bsType;
            pElem->get_type(&bsType.GetBSTR());
            if(bsType.operator ==(L"text"))
            {
                pElem->get_value(&bsUserId.GetBSTR());
            }
            else if(bsType.operator==(L"password"))
            {
                pElem->get_value(&bsPassword.GetBSTR());
            }
            pElem->Release();
        }

        pElemDisp->Release();
    }
    if(bsUserId.GetBSTR() && bsPassword.GetBSTR() && 
      ( bsUserId.operator!=(L"") && bsPassword.operator!=(L"") ) )
    {
        return;
    }            

    }
}
