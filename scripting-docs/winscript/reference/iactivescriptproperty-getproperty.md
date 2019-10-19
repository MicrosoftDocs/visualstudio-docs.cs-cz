---
title: 'IActiveScriptProperty:: GetProperty | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProperty.GetProperty
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetProperty method, IActiveScriptProperty interface
ms.assetid: a43383db-b148-4d76-83bd-4f0e899b7cb1
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1eeec6472a067d18a8b8962cfac70c25c0ff971
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571411"
---
# <a name="iactivescriptpropertygetproperty"></a>IActiveScriptProperty::GetProperty
Získá vlastnost, která je určena parametrem.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetProperty(  
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
 Hodnota vlastnosti, která má být získána.  
  
 `pvarIndex`  
 Nepoužívá se.  
  
 `pvarValue`  
 Hodnota vlastnosti  
  
 Hodnoty povolené pro `dwProperty` jsou popsány v následující tabulce.  
  
|Konstanta|Hodnota|Význam|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Vynutí skriptovací stroj rozdělit v celočíselném režimu, nikoli v režimu plovoucí desetinné čárky.|  
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
 Hostitel může použít vlastnost SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION k informování skriptovacího stroje, že pro přispívání do globálního objektu neexistují žádné jiné skriptovací moduly. Aplikace Internet Explorer může například informovat modul [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], který vykreslená stránka obsahuje pouze [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] skriptů. Proto pouze modul [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] může přidat nové vlastnosti do okna globálního objektu a není k dispozici žádný modul Visual Basic Scripting Edition (VBScript). Modul může tento příznak ignorovat nebo ho může použít k optimalizaci správy nových členů přidaných do globálního objektu.  
  
 Hostitel může pomocí vlastnosti SCRIPTPROP_INVOKEVERSIONING vybrat sadu jazykových funkcí, které budou podporovány při spuštění skriptovacího modulu [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Pokud je tato vlastnost nastavená na hodnotu 1 (SCRIPTLANGUAGEVERSION_5_7), jsou dostupné jazykové funkce stejné jako ty, které se nacházely ve verzi 5,7 skriptovacího modulu [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Pokud je nastavená na hodnotu 2 (SCRIPTLANGUAGEVERSION_5_8), jsou dostupné funkce jazyka, které se nacházely ve verzi 5,7, kromě funkcí přidaných ve verzi 5,8. Ve výchozím nastavení je tato vlastnost nastavena na hodnotu 0 (SCRIPTLANGUAGEVERSION_DEFAULT), která je ekvivalentní sadě funkcí jazyka, která se zobrazila ve verzi 5,7, pokud hostitel nepodporuje jiné výchozí chování. Například Internet Explorer 8 výslovný do funkcí jazyka [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], které podporuje skriptovací stroj [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] verze 5,8 ve výchozím nastavení, pokud je režim dokumentu pro Internet Explorer 8 režim standardů aplikace Internet Explorer 8.  
  
## <a name="see-also"></a>Viz také:  
 [Definování   kompatibility dokumentů](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85))  
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)    
 [Informace o verzích](../../javascript/reference/javascript-version-information.md)