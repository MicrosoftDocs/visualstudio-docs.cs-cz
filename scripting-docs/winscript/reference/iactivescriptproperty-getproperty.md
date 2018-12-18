---
title: IActiveScriptProperty::GetProperty | Dokumentace Microsoftu
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 7cd5c7ac948a9001688de69f9db9ee31624ca33d
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44284140"
---
# <a name="iactivescriptpropertygetproperty"></a>IActiveScriptProperty::GetProperty
Získá vlastnost, která je určená parametru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 Hodnota vlastnosti zobrazíte.  
  
 `pvarIndex`  
 Nepoužívá se.  
  
 `pvarValue`  
 Hodnota vlastnosti  
  
 Povolené hodnoty pro `dwProperty` jsou popsány v následující tabulce.  
  
|Konstanta|Hodnota|Význam|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Vynutí skriptovací stroj pro rozdělení v režimu celé číslo místo s plovoucí desetinnou čárkou režim bodu.|  
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
 Vlastnost SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION hostitele slouží k informování skriptovací stroj, který neexistuje žádné skriptovacích strojů přispívat na globální objekt. Například může informovat aplikaci Internet Explorer [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] modul, který obsahuje pouze vykreslované stránky [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] skripty. Proto pouze [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] modul můžete přidat nové vlastnosti do okna globálních objektů a neexistuje žádný modul Visual Basic Scripting Edition (VBScript) škol. Modul může ignorují tento příznak nebo můžete použít k optimalizaci správy nových členů, které jsou přidány do globálního objektu.  
  
 Hostitele můžete použít vlastnost SCRIPTPROP_INVOKEVERSIONING vybrat sadu jazykových funkcí na podporovaná, až [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] skriptovací stroj spustil. Pokud je tato vlastnost nastavena na hodnotu 1 (SCRIPTLANGUAGEVERSION_5_7), dostupné jazykové funkce jsou stejné jako ty, které se zobrazovaly ve verzi 5.7 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] skriptovací stroj. Pokud je nastavena na 2 (SCRIPTLANGUAGEVERSION_5_8), dostupné jazykové funkce jsou ty, které se zobrazovaly ve verzi 5.7 Kromě funkcí, které byly přidány ve verzi 5.8. Ve výchozím nastavení tato vlastnost nastavena na hodnotu 0 (SCRIPTLANGUAGEVERSION_DEFAULT), což je ekvivalentní k sadě funkcí jazyka, které se zobrazovalo ve verzi 5.7, pokud hostitel podporuje různé výchozí chování. Pro instanci aplikace Internet Explorer 8 požádá o do [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] funkcí jazyka podporovaná modulem verze 5.8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] skriptovací stroj ve výchozím nastavení při "Standardy aplikace Internet Explorer 8" režimu je režim dokumentu pro aplikaci Internet Explorer 8.  
  
## <a name="see-also"></a>Viz také  
 [Určení kompatibility dokumentu](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85))   
 [Iactivescriptproperty –](../../winscript/reference/iactivescriptproperty.md)   
 [Informace o verzích](../../javascript/reference/javascript-version-information.md)