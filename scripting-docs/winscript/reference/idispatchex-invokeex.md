---
title: IDispatchEx::InvokeEx | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 6302228b110e2b0a6296190079bf60b3d92980bd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24795177"
---
# <a name="idispatchexinvokeex"></a>IDispatchEx::InvokeEx
Poskytuje přístup k vlastnosti a metody, které jsou vystavené `IDispatchEx` objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 Identifikuje člena. Používá `GetDispID` nebo `GetNextDispID` získat identifikátor odesílání.  
  
 `lcid`  
 Kontext národního prostředí pro interpretaci argumentů. `lcid` Předaný `InvokeEx` umožňující objekt interpretovat její argumenty, které jsou specifické pro národní prostředí.  
  
 `wFlags`  
 Právní hodnoty pro `wFlags` jsou:  
  
 DISPATCH_PROPERTYGET &#124; DISPATCH_METHOD &#124; DISPATCH_PROPERTYPUT &#124; DISPATCH_PROPERTYPUTREF &#124; DISPATCH_CONSTRUCT  
  
 Příznaky popisující kontextu `InvokeEx` volání:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|DISPATCH_METHOD|Člen je vyvolána jako metodu. Pokud vlastnost má stejný název, může být nastaven to a příznak DISPATCH_PROPERTYGET (definované `IDispatch`).|  
|DISPATCH_PROPERTYGET|Člen je načíst jako člena vlastnost nebo data (definované `IDispatch`).|  
|DISPATCH_PROPERTYPUT|Člen mění jako člena vlastnost nebo data (definované `IDispatch`).|  
|DISPATCH_PROPERTYPUTREF|Člen je změnit přiřazení odkaz spíše než přiřazení hodnoty. Tento příznak je platná pouze v případě, že tato vlastnost přijímá parametry odkazem na objekt (definované `IDispatch`).|  
|DISPATCH_CONSTRUCT|Člen je používán jako konstruktor. (Toto je nová hodnota definované `IDispatchEx`). Právní hodnoty pro `wFlags` jsou:<br /><br /> DISPATCH_PROPERTYGET DISPATCH_METHOD DISPATCH_PROPERTYPUT DISPATCH_PROPERTYPUTREF DISPATCH_CONSTRUCT|  
  
 `pdp`  
 Ukazatel na strukturu obsahující matici argumentů, pole DISPID pro pojmenované argumenty a počty prvků v polích. Najdete v článku `IDispatch` dokumentace úplný popis DISPPARAMS struktury.  
  
 `pVarRes`  
 Ukazatel na umístění, kde je výsledek uložené, nebo hodnotu Null, pokud má volající očekává žádný výsledek. Tento argument se ignoruje, pokud je zadána DISPATCH_PROPERTYPUT nebo DISPATCH_PROPERTYPUTREF.  
  
 `pei`  
 Ukazatel na strukturu, která obsahuje informace o výjimce. Tato struktura je nutné zadat Pokud `DISP_E_EXCEPTION` je vrácen. Může mít hodnotu Null. Najdete v článku `IDispatch` dokumentaci úplný popis `EXCEPINFO` struktura.  
  
 `pspCaller`  
 Ukazatel na objekt zprostředkovatele služby poskytl volajícího, který umožňuje získat services volající objekt. Může mít hodnotu Null.  
  
 `IDispatchEx::InvokeEx`poskytuje všechny stejné funkce jako `IDispatch::Invoke` a přidá několik rozšíření:  
  
|||  
|-|-|  
|DISPATCH_CONSTRUCT|Určuje, že položka je používán jako konstruktor.|  
|`pspCaller`|`pspCaller` Umožňuje přístup k objektům na služeb poskytovaných volající. Konkrétní služby může zpracovávat volající sám sebe nebo delegovaný pro volající další řetězem volání. Například pokud se modul skriptu v prohlížeči provede `InvokeEx` volání externí objekt objektu, můžete postupovat podle `pspCaller` řetězu získat services z skriptovací stroj nebo prohlížeče. (Všimněte si, že řetězu volání není stejný jako řetězu vytvoření – taky známé jako kontejner řetězec nebo řetězec lokality. Vytváření řetězu může být k dispozici prostřednictvím jinému kontrolnímu mechanismu, jako `IObjectWithSite`.)|  
|`this`ukazatele|Pokud je DISPATCH_METHOD nastavená `wFlags`, může být "s názvem parametr" pro "Tato" hodnota. DISPID bude DISPID_THIS a musí být první parametr s názvem.|  
  
 Nepoužívané `riid` parametr v `IDispatch::Invoke` byla odebrána.  
  
 `puArgArr` Parametr v `IDispatch::Invoke` byla odebrána.  
  
 Najdete v článku `IDispatch::Invoke` dokumentace pro následující příklady:  
  
 "Voláním metody bez argumentů."  
  
 "Načtení a nastavení vlastnosti"  
  
 "Předávání parametrů"  
  
 "Indexované vlastnosti"  
  
 "Vyvolání výjimky během Invoke"  
  
 "Vrací chyby"  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|||  
|-|-|  
|`S_OK`|Úspěch.|  
|DISP_E_BADPARAMCOUNT|Počet elementů poskytované DISPPARAMS se liší od počet argumentů akceptovat metody nebo vlastnosti.|  
|DISP_E_BADVARTYPE|Jeden z argumentů v `rgvarg` není platný typ varianty.|  
|DISP_E_EXCEPTION|Aplikace musí vyvolat výjimku. V takovém případě strukturu předaná `pei` by měly být vyplněny.|  
|DISP_E_MEMBERNOTFOUND|Požadovaný člen neexistuje, nebo volání `InvokeEx` se pokusila nastavit hodnotu vlastnosti jen pro čtení.|  
|DISP_E_NONAMEDARGS|Tato implementace `IDispatch` nepodporuje pojmenované argumenty.|  
|DISP_E_OVERFLOW|Jeden z argumentů v `rgvarg` se neshoduje se zadaným typem.|  
|DISP_E_PARAMNOTFOUND|Jeden z parametrů hodnoty dispID neodpovídá parametru na metodu.|  
|DISP_E_TYPEMISMATCH|Jeden nebo více parametrů se neshoduje.|  
|DISP_E_UNKNOWNLCID|Člen interpretuje řetězcové argumenty podle LCID, a identifikátor LCID nebyl rozpoznán. Pokud LCID není nutné interpretovat argumenty, by neměl být bude vrácena tato chyba.|  
|DISP_E_PARAMNOTOPTIONAL|Požadovaný parametr byl vynechán.|  
  
## <a name="example"></a>Příklad  
  
```  
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
 [IDispatchEx – rozhraní](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)