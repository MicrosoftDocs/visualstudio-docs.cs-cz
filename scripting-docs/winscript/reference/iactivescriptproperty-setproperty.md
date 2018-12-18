---
title: IActiveScriptProperty::SetProperty | Dokumentace Microsoftu
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProperty.SetProperty
apilocation:
- scrobj.dll
helpviewer_keywords:
- SetProperty method, IActiveScriptProperty interface
ms.assetid: 0ba429c5-04a3-4505-bc5f-69c505dfca91
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 186608bc56cf8b3649f5beeb1e3a301580ce44bb
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279281"
---
# <a name="iactivescriptpropertysetproperty"></a>IActiveScriptProperty::SetProperty
Nastaví vlastnost, která je určená parametru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetProperty(  
// The property value:  
    uint dwProperty,    
// Not used:   
    IntPtr pvarIndex,    
// The value of the property:   
    out object pvarValue,    
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwProperty`  
 Hodnota vlastnosti, kterou chcete nastavit.  
  
 `pvarIndex`  
 Nepoužívá se.  
  
 `pvarValue`  
 Hodnota vlastnosti  
  
 Povolené hodnoty pro `dwProperty` jsou popsány v následující tabulce.  
  
|Konstanta|Hodnota|Význam|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Vynutí skriptovací stroj pro rozdělení v režimu celé číslo místo s plovoucí desetinnou čárkou režim bodu. Výchozí hodnota je `False`.|  
|SCRIPTPROP_STRINGCOMPAREINSTANCE|0x00003001|Povolí používání funkce porovnání řetězce skriptovací stroj se nahradí.|  
|SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION|0x70000002|Informuje o tom, který neexistuje žádné skriptovacích strojů přispívat na globální objekt skriptovací stroj.|  
|SCRIPTPROP_INVOKEVERSIONING|0x00004000|Vynutí [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] skriptovací stroj k výběru sady funkcí jazyka podporovaná. Výchozí sadu funkcí jazyka podporovaná modulem [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] skriptovací stroj je ekvivalentní k sadě funkcí jazyka, které se zobrazovalo ve verzi 5.7 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] skriptovací stroj.|  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Úspěch.|  
|`E_INVALIDARG`|Argument není platný.|  
|`E_UNEXPECTED`|Volání nebylo očekáváno (například skriptovací stroj má ještě nebyly načteny nebo inicializován).|  
  
## <a name="remarks"></a>Poznámky  
 K povolení nebo zakázání dělení celého čísla, vyvolat `SetProperty` a převést `Boolean` do `Object`. Výchozí hodnota vlastnosti je `False`. Pokud ji nastavíte na `True`, operace dělení vrátí pouze celá čísla.  
  
 K povolení nebo zakázání vlastní řetězec porovnání, vyvolat `SetProperty` a předejte mu `Object` hodnotu. Objekt, který můžete předat musí implementovat rozhraní [iactivescriptstringcompare – rozhraní](../../winscript/reference/iactivescriptstringcompare-interface.md). [StrComp](../../winscript/reference/iactivescriptstringcompare-strcomp.md) metodu [iactivescriptstringcompare – rozhraní](../../winscript/reference/iactivescriptstringcompare-interface.md) rozhraní je volána pokaždé, když je funkce porovnání řetězce se provede.  
  
 Chcete-li vybrat sadu jazykových funkcí na podporované, když [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] skriptovací stroj je inicializována, vyvolají `SetProperty` a předat hodnotu, která odpovídá sadě povolit u SCRIPTPROP_INVOKEVERSIONING funkcí jazyka. Pokud je tato vlastnost nastavena na hodnotu 1 (SCRIPTLANGUAGEVERSION_5_7), dostupné jazykové funkce jsou stejné jako ty, které se zobrazovaly ve verzi 5.7 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] skriptovací stroj. Pokud je nastavena na 2 (SCRIPTLANGUAGEVERSION_5_8), dostupné jazykové funkce jsou ty, které se zobrazovaly ve verzi 5.7 Kromě nových funkcí, které byly přidány ve verzi 5.8. Ve výchozím nastavení tato vlastnost nastavena na hodnotu 0 (SCRIPTLANGUAGEVERSION_DEFAULT), což je ekvivalentní k sadě funkcí jazyka, které se zobrazovalo ve verzi 5.7, pokud hostitel podporuje různé výchozí chování. Například v aplikaci Internet Explorer 8 požádá o [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] jazykové funkce, které jsou podporovány verze 5.8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] skriptovací stroj ve výchozím nastavení při "Standardy aplikace Internet Explorer 8" režim je výchozí režim dokumentu pro aplikaci Internet Explorer 8. Přepnutí režimu dokumentů Internet Explorer 8 pro Internet Explorer 7, režim standardů nebo adaptivním režimu resetuje [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] skriptovací stroj pro podporu pouze jazykové sadě funkcí, které existovalo v na verzi 5.7 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] skriptovací stroj.  
  
> [!NOTE]
>  SCRIPTPROP_INVOKEVERSIONING by měla být nastavena pouze tehdy, když [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] skriptovací stroj je inicializována.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak můžete vynutit skriptovací stroj použití dělení celého čísla a o tom, aby přetížení funkce porovnání.  
  
```c#  
BMLScriptEngine bmlScriptEngine = new BMLScriptEngine();  
IActiveScriptProperty scriptProperties = bmlScriptEngine as   
    IActiveScriptProperty;  
  
// Force the scripting engine to use integer division.  
Boolean enableIntegerDivision = true;  
Object vtIntegerDivInstance = (Object)enableIntegerDivision;  
                scriptProperties.SetProperty(SCRIPTPROP_INTEGERDIVISION,   
    System.IntPtr.Zero, ref vtIntegerDivInstance);  
  
// Allow overloading of the compare function.  
BMLScriptStringCompare bmlScriptStringCompareInstance = new   
    BMLScriptStringCompare();  
Object vtStrCmpInstance = (Object)bmlScriptStringCompareInstance;  
scriptProperties.SetProperty(SCRIPTPROP_STRCOMPINST,   
    System.IntPtr.Zero, ref vtStrCmpInstance);  
```  
  
## <a name="see-also"></a>Viz také  
 [Určení kompatibility dokumentu](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85))   
 [Iactivescriptproperty –](../../winscript/reference/iactivescriptproperty.md)   
 [Informace o verzích](../../javascript/reference/javascript-version-information.md)