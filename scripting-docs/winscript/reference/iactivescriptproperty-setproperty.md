---
title: 'IActiveScriptProperty:: SetProperty | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 0f8307a82f181be20205c7bfcc47e881b0fa1e90
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571317"
---
# <a name="iactivescriptpropertysetproperty"></a>IActiveScriptProperty::SetProperty
Nastaví vlastnost, která je určena parametrem.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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
  
 Hodnoty povolené pro `dwProperty` jsou popsány v následující tabulce.  
  
|Konstanta|Hodnota|Význam|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Vynutí skriptovací stroj rozdělit v celočíselném režimu, nikoli v režimu plovoucí desetinné čárky. Výchozí hodnota je `False`.|  
|SCRIPTPROP_STRINGCOMPAREINSTANCE|0x00003001|Umožňuje nahradit funkci String Compare skriptovacího stroje.|  
|SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION|0x70000002|Informuje skriptovací stroj, že pro přispívání do globálního objektu neexistují žádné jiné skriptovací moduly.|  
|SCRIPTPROP_INVOKEVERSIONING|0x00004000|Vynutí, aby skriptovací modul [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] vybral sadu jazykových funkcí, které se mají podporovat. Výchozí sada jazykových funkcí podporovaných skriptovacím modulem [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] je ekvivalentní sadě funkcí jazyka, která se zobrazila ve verzi 5,7 skriptovacího stroje [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].|  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Nástup.|  
|`E_INVALIDARG`|Argument není platný.|  
|`E_UNEXPECTED`|Volání nebylo očekáváno (například skriptovací stroj ještě nebyl načten nebo inicializován).|  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li povolit nebo zakázat celočíselné dělení, vyvolat `SetProperty` a převést `Boolean` na `Object`. Ve výchozím nastavení je hodnota vlastnosti `False`. Pokud nastavíte `True`, operace dělení vrátí pouze celá čísla.  
  
 Chcete-li povolit nebo zakázat porovnání vlastního řetězce, vyvolejte `SetProperty` a předejte hodnotu `Object`. Objekt, který předáte, musí implementovat [rozhraní iactivescriptstringcompare –](../../winscript/reference/iactivescriptstringcompare-interface.md)rozhraní. Metoda [StrComp](../../winscript/reference/iactivescriptstringcompare-strcomp.md) rozhraní [iactivescriptstringcompare – Interface](../../winscript/reference/iactivescriptstringcompare-interface.md) je volána pokaždé, když je provedena funkce porovnání řetězce.  
  
 Chcete-li vybrat sadu jazykových funkcí, které mají být podporovány při inicializaci [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] skriptovacího modulu, volejte `SetProperty` a předejte hodnotu, která odpovídá jazykové funkci nastavené na povoleno pro SCRIPTPROP_INVOKEVERSIONING. Pokud je tato vlastnost nastavená na hodnotu 1 (SCRIPTLANGUAGEVERSION_5_7), jsou dostupné jazykové funkce stejné jako ty, které se nacházely ve verzi 5,7 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] skriptovacího stroje. Pokud je nastavená na 2 (SCRIPTLANGUAGEVERSION_5_8), jsou dostupné funkce jazyka, které se nacházely ve verzi 5,7, navíc k novým funkcím, které byly přidány ve verzi 5,8. Ve výchozím nastavení je tato vlastnost nastavena na hodnotu 0 (SCRIPTLANGUAGEVERSION_DEFAULT), která je ekvivalentní sadě funkcí jazyka, která se zobrazila ve verzi 5,7, pokud hostitel nepodporuje jiné výchozí chování. Například Internet Explorer 8 výslovný do funkcí jazyka [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], které jsou podporovány ve výchozím nastavení [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] skriptovacího stroje verze 5,8, pokud je výchozí režim dokumentu pro Internet Explorer 8 režim standardů aplikace Internet Explorer 8. Přepnutí režimu dokumentů Internet Exploreru 8 do standardů aplikace Internet Explorer 7 nebo režimu adaptivní resetuje skriptovací modul [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] tak, aby podporoval pouze sadu funkcí jazyka, která existovala v skriptovacím stroji [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] verze 5,7.  
  
> [!NOTE]
> SCRIPTPROP_INVOKEVERSIONING by se měla nastavit jenom v případě, že se inicializuje skriptovací modul [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vynutit skriptovací modul pro použití dělení na celé číslo a jak umožňuje přetížení funkce Compare.  
  
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
  
## <a name="see-also"></a>Viz také:  
 [Definování  kompatibility dokumentů](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85))  
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [Informace o verzích](../../javascript/reference/javascript-version-information.md)