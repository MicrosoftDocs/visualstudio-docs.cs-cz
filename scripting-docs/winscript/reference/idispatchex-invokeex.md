---
title: 'IDispatchEx –:: InvokeEx | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.InvokeEx
apilocation:
- scrobj.dll
helpviewer_keywords:
- InvokeEx method
ms.assetid: d90783e6-4b89-4423-8a56-a9c8b4b2c813
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 673b3f1e64caa79dc2b21641209423d93fe0f834
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144412"
---
# <a name="idispatchexinvokeex"></a>IDispatchEx::InvokeEx
Poskytuje přístup k vlastnostem a metodám vystaveným `IDispatchEx` objektem.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT InvokeEx(  
   DISPID id,  
   LCID lcid,  
   WORD wFlags,  
   DISPARAMS *pdp,  
   VARIANT *pVarRes,   
   EXCEPINFO *pei,   
   IServiceProvider *pspCaller   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `id`  
 Identifikuje člena. Pomocí `GetDispID` nebo `GetNextDispID` Získá identifikátor odeslání.  
  
 `lcid`  
 Kontext národního prostředí pro interpretaci argumentů. `lcid`Je předán do, `InvokeEx` aby mohl objekt interpretovat své argumenty specifické pro národní prostředí.  
  
 `wFlags`  
 Platné hodnoty pro `wFlags` jsou:  
  
 DISPATCH_PROPERTYGET &#124; DISPATCH_METHOD &#124; DISPATCH_PROPERTYPUT &#124; DISPATCH_PROPERTYPUTREF &#124; DISPATCH_CONSTRUCT  
  
 Příznaky popisující kontext `InvokeEx` volání:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|DISPATCH_METHOD|Člen je vyvolán jako metoda. Pokud má vlastnost stejný název, může být tento i příznak DISPATCH_PROPERTYGET nastaven (definováno pomocí `IDispatch` ).|  
|DISPATCH_PROPERTYGET|Člen je načten jako vlastnost nebo datový člen (definován pomocí `IDispatch` ).|  
|DISPATCH_PROPERTYPUT|Člen se změní jako vlastnost nebo datový člen (definován pomocí `IDispatch` ).|  
|DISPATCH_PROPERTYPUTREF|Člen je změněn pomocí přiřazení odkazu namísto přiřazení hodnoty. Tento příznak je platný pouze v případě, že vlastnost přijímá odkaz na objekt (definovaný pomocí `IDispatch` ).|  
|DISPATCH_CONSTRUCT|Člen se používá jako konstruktor. (Jedná se o novou hodnotu definovanou v rámci `IDispatchEx` ). Platné hodnoty pro `wFlags` jsou:<br /><br /> DISPATCH_PROPERTYGET DISPATCH_METHOD DISPATCH_PROPERTYPUT DISPATCH_PROPERTYPUTREF DISPATCH_CONSTRUCT|  
  
 `pdp`  
 Ukazatel na strukturu obsahující matici argumentů, pole DISPID pro pojmenované argumenty a počty prvků v polích. `IDispatch`Úplný popis struktury DISPPARAMS najdete v dokumentaci.  
  
 `pVarRes`  
 Ukazatel na umístění, kde má být výsledek uložen, nebo hodnotu null, pokud volající neočekává žádný výsledek. Tento argument je ignorován, pokud je zadána DISPATCH_PROPERTYPUT nebo DISPATCH_PROPERTYPUTREF.  
  
 `pei`  
 Ukazatel na strukturu, která obsahuje informace o výjimce. Tato struktura by měla být vyplněna, pokud `DISP_E_EXCEPTION` je vrácena. Může mít hodnotu null. `IDispatch`Úplný popis struktury najdete v dokumentaci `EXCEPINFO` .  
  
 `pspCaller`  
 Ukazatel na objekt poskytovatele služeb dodaný volajícím, který umožňuje objektu získat služby od volajícího. Může mít hodnotu null.  
  
 `IDispatchEx::InvokeEx`poskytuje všechny stejné funkce jako `IDispatch::Invoke` a přidává několik rozšíření:  
  
|Hodnota|Význam|
|-|-|  
|DISPATCH_CONSTRUCT|Označuje, že položka se používá jako konstruktor.|  
|`pspCaller`|`pspCaller`Umožňuje objektu přístup ke službám poskytovaným volajícím. Konkrétní služby mohou být zpracovávány samotným volajícím nebo delegovany volajícímu v průběhu řetězce volání. Například pokud skriptovací stroj v prohlížeči provede `InvokeEx` volání na externí objekt, může objekt podstoupit `pspCaller` řetězec a získat tak služby ze skriptovacího stroje nebo prohlížeče. (Všimněte si, že řetěz volání není stejný jako řetěz pro vytváření, označovaný také jako řetěz kontejneru nebo řetězec webu. Řetěz vytvoření může být k dispozici prostřednictvím některého jiného mechanismu, jako je například `IObjectWithSite` .)|  
|`this`ukazatele|Pokud je DISPATCH_METHOD nastaveno v `wFlags` , může existovat "pojmenovaný parametr" pro hodnotu "This". Identifikátor DISPID bude DISPID_THIS a musí se jednat o první pojmenovaný parametr.|  
  
 Nepoužitý `riid` parametr v `IDispatch::Invoke` byl odebrán.  
  
 `puArgArr`Parametr v `IDispatch::Invoke` byl odebrán.  
  
 `IDispatch::Invoke`Následující příklady najdete v dokumentaci:  
  
 "Volání metody bez argumentů"  
  
 "Získávání a nastavování vlastností"  
  
 "Předávání parametrů"  
  
 "Indexované vlastnosti"  
  
 "Vyvolávání výjimek během vyvolání"  
  
 "Vracení chyb"  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|Hodnota|Význam|  
|-|-|  
|`S_OK`|Úspěch.|  
|DISP_E_BADPARAMCOUNT|Počet elementů poskytnutých pro DISPPARAMS se liší od počtu argumentů akceptovaných metodou nebo vlastností.|  
|DISP_E_BADVARTYPE|Jeden z argumentů v `rgvarg` není platný typ variant.|  
|DISP_E_EXCEPTION|Aplikace musí vyvolat výjimku. V tomto případě `pei` by měla být naplněná struktura předaná.|  
|DISP_E_MEMBERNOTFOUND|Požadovaný člen neexistuje nebo volání se `InvokeEx` pokusilo nastavit hodnotu vlastnosti jen pro čtení.|  
|DISP_E_NONAMEDARGS|Tato implementace nepodporuje `IDispatch` pojmenované argumenty.|  
|DISP_E_OVERFLOW|Jeden z argumentů v `rgvarg` nemohlo být převedeno na zadaný typ.|  
|DISP_E_PARAMNOTFOUND|Jeden z parametrů identifikátorů DISPID neodpovídá parametru metody.|  
|DISP_E_TYPEMISMATCH|Jeden nebo více argumentů nelze přiřadit.|  
|DISP_E_UNKNOWNLCID|Vyvolaný člen interpretuje řetězcové argumenty podle identifikátoru LCID a Identifikátor LCID není rozpoznán. Pokud LCID není nutné k interpretaci argumentů, tato chyba by neměla být vrácena.|  
|DISP_E_PARAMNOTOPTIONAL|Byl vynechán požadovaný parametr.|  
  
## <a name="example"></a>Příklad  
  
```cpp
VARIANT var;  
   BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;  
   DISPPARAMS dispparamsNoArgs = {NULL, NULL, 0, 0};  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
   {  
      pdex->InvokeEx(dispid, LOCALE_USER_DEFAULT,  
         DISPATCH_PROPERTYGET, &dispparamsNoArgs,   
         &var, NULL, NULL);  
   }  
```  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní IDispatchEx –](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx –:: GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)