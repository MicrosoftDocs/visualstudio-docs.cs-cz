---
title: IDispatchEx – rozhraní | Dokumentace Microsoftu
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDispatchEx interface, about IDispatchEx
- IDispatchEx interface
ms.assetid: 37a3303f-f78e-4b5b-aac8-b836c92819de
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 22ccc54dee335fd8c81343557d2f32c48eb30560
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49837916"
---
# <a name="idispatchex-interface"></a>IDispatchEx – rozhraní
`IDispatchEx`, rozšíření `IDispatch` rozhraní, podporuje funkce vhodné pro dynamické jazyky, jako je například skriptovací jazyky. Tato část popisuje `IDispatchEx` rozhraní, rozdíly mezi `IDispatch` a `IDispatchEx`a důvody tohoto rozšíření. Očekává se, že čtečky obeznámeni s `IDispatch` a mají přístup k `IDispatch` dokumentaci.  
  
## <a name="remarks"></a>Poznámky  
 `IDispatch` byl vyvinut v podstatě pro Microsoft Visual Basicu. Primární omezení `IDispatch` se předpokládá, že objekty jsou statické. Jinými slovy protože objekty nejsou změnit za běhu, informace o typu můžete plně popisují je v době kompilace. Dynamické modely za běhu, které se nacházejí v skriptovacích jazyků, jako je například Visual Basic Scripting Edition (VBScript) a [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] a objekt modely, jako je Dynamic HTML vyžadují flexibilnější rozhraní.  
  
 `IDispatchEx` byla vyvinuta poskytují všechny služby `IDispatch` a také některá rozšíření, které jsou vhodné pro dynamičtějších s pozdní vazbou jazyků, jako je skriptovací jazyky. Další funkce `IDispatchEx` nad rámec těch, které poskytuje podle `IDispatch` jsou:  
  
- Přidat nové členy do objektu ("expando" "") – použijte `GetDispID` s `fdexNameEnsure` příznak.  
  
- Odstranit členy objektu – použijte `DeleteMemberByName` nebo `DeleteMemberByDispID`.  
  
- Operace odeslání velká a malá písmena, použijte `fdexNameCaseSensitive` nebo `fdexNameCaseInsensitive`.  
  
- Hledání pro člena s názvem implicitní – použijte `fdexNameImplicit`.  
  
- Vytvořit výčet hodnoty dispID objektu – použijte `GetNextDispID`.  
  
- Mapování z DISPID pro název elementu – použijte `GetMemberName`.  
  
- Získání vlastností členů objektu – použijte `GetMemberProperties`.  
  
- Volání metody s `this` ukazatel – použijte `InvokeEx` s DISPATCH_METHOD.  
  
- Povolit prohlížeče, které podporují koncept obory názvů získat nadřazené místo názvu objektu – použijte `GetNameSpaceParent`.  
  
  Objekty, které podporují `IDispatchEx` může také podporovat `IDispatch` z důvodu zpětné kompatibility. Dynamické povaze objekty, které podporují `IDispatchEx` má několik vliv `IDispatch` rozhraní těchto objektů. Například `IDispatch` díky následujících předpokladů:  
  
- Člen a parametr hodnoty dispID musí zůstat konstantní dobu života objektu. To umožňuje klientům získat hodnoty dispID jednou a mezipaměti pro pozdější použití.  
  
  Protože `IDispatchEx` umožňuje přidávání a odstraňování členů sady platné hodnoty dispID zůstat není konstantní. Ale `IDispatchEx` vyžaduje, aby zůstal neměnný mapování mezi DISPID a názvu člena. To znamená, že pokud je člen odstraněn:  
  
- Hodnota DISPID nesmí znovu použít, dokud se nevytvoří člena se stejným názvem.  
  
- Hodnota DISPID musí zůstat platný pro `GetNextDispID`.  
  
- Hodnota DISPID musí být přijata řádně podle těchto sloupců `IDispatch` nebo `IDispatchEx` metody – musí rozpoznat člena jako odstraněný a vrátí příslušnou chybovou kód (obvykle DISP_E_MEMBERNOTFOUND nebo S_FALSE).  
  
## <a name="examples"></a>Příklady  
 To [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] kódu ve funkci test() provede následující akce:  
  
- Vytvoří nový objekt voláním `Object` konstruktor a přiřadí ukazatel na objekt, nové proměnné knihovna  
  
- Vytvoří nový prvek v objektu s názvem Elem a přiřadí ukazatel na funkci cat tohoto elementu.  
  
- Volá tuto funkci. Protože je volána jako metody, `this` ukazatel odkazuje na objekt knihovna Funkce přidá nový prvek panel na objekt.  
  
  Úplný kód HTML je:  
  
```  
<html>  
<body>  
<script type="text/javascript">  
function cat()  
{  
   // Create new element and assign the value 10  
   this.Bar = 10;  
}  
  
function test()  
{  
   // Construct new object  
   Obj = new Object();  
  
   // Create new element and assign function pointer  
   Obj.Elem = cat;  
  
   // Call Elem method ("this" == Obj)  
   Obj.Elem();  
  
   // Obj.Bar now exists  
}  
test();  
</script>  
</body>  
</html>  
```  
  
 Prvek řízení umístěný na tomto stejné webové stránce může získat odeslání ukazatele na skriptovacích strojů ukládaných z prohlížeče. Ovládací prvek pak může implementovat test() funkce:  
  
```  
<html>  
<body>  
<script type="text/javascript">  
function cat()  
{  
   // Create new element and assign the value 10  
   this.Bar = 10;  
}  
</script>  
<object id="test" <CLASSID="CLSID:9417DB5D-FA2A-11D0-8CB3-00C04FC2B085">>  
</object>  
</body>  
</html>  
```  
  
 Kódu z ovládacího prvku, testování, provede totéž, jako [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] funkce `test()`. Všimněte si, že tyto odeslání volání do běhu [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] motoru a ke změně stavu modul:  
  
- Získá ukazatel odeslání ke cat pomocí funkce `GetDispID()`.  
  
- Získá odeslání ukazatel na objekt pomocí funkce `GetDispID()`.  
  
- Vytvoří objekt voláním funkce objektu s `InvokeEx()` a získá odeslání ukazatel na nově vytvořený objekt.  
  
- Vytvoří nový prvek Elem, v objektu pomocí `GetDispID()` s `fdexNameEnsure` příznak.  
  
- Umístí ukazatel odeslání cat v prvku pomocí `InvokeEx()`.  
  
- Volá metodu odeslání ukazatel ke cat voláním `InvokeEx()` a předání v odesílání ukazateli na konstruovaný objekt jako `this` ukazatele.  
  
- Metoda cat vytvoří nový prvek panel na aktuální `this` objektu.  
  
- Ověřuje, že nový prvek panelu byl vytvořen ve vytvořeném objektu vytyčením přes prvky pomocí `GetNextDispID()`.  
  
  Kód pro ovládací prvek testu:  
  
```  
   BOOL test(IDispatchEx *pdexScript)  
   {  
      HRESULT hr;  
      VARIANT var;  
      DISPID dispid, putid;  
      BOOL retval = FALSE;  
      BSTR bstrName = NULL;  
      IDispatch   *pdispObj = NULL, *pdispCat = NULL;  
      IDispatchEx *pdexObj = NULL;  
      DISPPARAMS dispparams, dispparamsNoArgs = {NULL, NULL, 0, 0};  
  
      // Get dispatch pointer for "cat"  
      bstrName = SysAllocString(OLESTR("cat"));  
         if (bstrName == NULL) goto LDone;  
      hr = pdexScript->GetDispID(bstrName, 0, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
      hr = pdexScript->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_PROPERTYGET, &dispparamsNoArgs,   
         &var, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
      pdispCat = var.pdispVal;  
  
      // Create object by calling "Object" constructor  
      bstrName = SysAllocString(OLESTR("Object"));  
         if (NULL == bstrName) goto LDone;  
      hr = pdexScript->GetDispID(bstrName, 0, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
      hr = pdexScript->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_CONSTRUCT, &dispparamsNoArgs,   
         &var, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
      pdispObj = var.pdispVal;  
      hr = pdispObj->QueryInterface(IID_IDispatchEx, (void **)&pdexObj);  
         if (FAILED(hr)) goto LDone;  
  
      // Create new element in object  
      bstrName = SysAllocString(OLESTR("Elem"));  
         if (NULL == bstrName) goto LDone;  
      hr = pdexObj->GetDispID(bstrName, fdexNameEnsure, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
  
      // Assign "cat" dispatch pointer to element  
      putid = DISPID_PROPERTYPUT;  
      var.vt = VT_DISPATCH;  
      var.pdispVal = pdispCat;  
      dispparams.rgvarg = &var;  
      dispparams.rgdispidNamedArgs = &putid;  
      dispparams.cArgs = 1;  
      dispparams.cNamedArgs = 1;  
      hr = pdexObj->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_PROPERTYPUTREF, &dispparams,  
         NULL, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
  
      // Invoke method with "this" pointer  
      putid = DISPID_THIS;  
      var.vt = VT_DISPATCH;  
      var.pdispVal = pdispObj;  
      dispparams.rgvarg = &var;  
      dispparams.rgdispidNamedArgs = &putid;  
      dispparams.cArgs = 1;  
      dispparams.cNamedArgs = 1;  
      hr = pdexObj->InvokeEx(dispid, LOCALE_USER_DEFAULT,  
         DISPATCH_METHOD, &dispparams,  
            NULL, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
  
      // Confirm that new element "Bar" is in object  
      hr = pdexObj->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);  
      while (hr == NOERROR)  
      {  
            hr = pdexObj->GetMemberName(dispid, &bstrName);  
            if (FAILED(hr)) goto LDone;  
            retval = !wcscmp(bstrName, OLESTR("Bar"));  
            SysFreeString(bstrName);  
            bstrName = NULL;  
            if (retval) goto LDone;  
         hr = pdexObj->GetNextDispID(fdexEnumAll, dispid, &dispid);  
      }  
LDone:  
   SysFreeString(bstrName);  
   if (pdispCat != NULL)  
      pdispCat->Release();  
   if (pdispObj != NULL)  
      pdispObj->Release();  
   if (pdexObj != NULL)  
      pdexObj->Release();  
  
   return retval;  
   }  
```  
  
## <a name="methods"></a>Metody  
 [IDispatchEx – metody](../../winscript/reference/idispatchex-methods.md)