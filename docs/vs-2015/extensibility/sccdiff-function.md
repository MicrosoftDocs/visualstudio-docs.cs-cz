---
title: Sccdiff – funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccDiff
helpviewer_keywords:
- SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ed4ca5cefa45f041e4285b00d7a2d9682e6565a0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51795749"
---
# <a name="sccdiff-function"></a>SccDiff – funkce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato funkce zobrazí (nebo volitelně právě vyhledává) systém správy rozdíly mezi aktuálního souboru (na místním disku) a její verzi poslední vrácené se změnami ve zdroji.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
SCCRTN SccDiff(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LPCSTR    lpFileName,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 [in] Struktura kontext modulu plug-in zdroje ovládacího prvku.  
  
 hWnd  
 [in] Popisovač okna integrovaného vývojového prostředí, které modul plug-in správy zdrojového kódu můžete použít jako nadřazený pro všechna dialogová okna, které poskytuje.  
  
 lpFileName  
 [in] Název souboru, pro kterou je požadována rozdíl.  
  
 fOptions  
 [in] Příkaz příznaky. Podrobnosti najdete v části poznámky.  
  
 pvOptions  
 [in] Možností správy zdrojového kódu plug-konkrétní.  
  
## <a name="return-value"></a>Návratová hodnota  
 Modul plug-in implementaci ovládacího prvku zdroje této funkce má vracet instanci jednoho z následujících hodnot:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|SCC_OK|Verze v pracovní kopie a serveru jsou stejné.|  
|SCC_I_FILESDIFFERS|Pracovní kopie se liší od verze pod správou zdrojových kódů.|  
|SCC_I_RELOADFILE|Soubor nebo projekt je potřeba znovu načíst.|  
|SCC_E_FILENOTCONTROLLED|Soubor není pod správou zdrojových kódů.|  
|SCC_E_NOTAUTHORIZED|Uživatel nemůže k provedení této operace.|  
|SCC_E_ACCESSFAILURE|Došlo k problému, přístup k systému správy zdrojového kódu, pravděpodobně kvůli problémům se síti nebo kolize. Doporučuje se zkuste to znovu.|  
|SCC_E_NONSPECIFICERROR|Obecná chyba; rozdíl souboru nebyl získán.|  
|SCC_E_FILENOTEXIST|Místní soubor se nenašel.|  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce slouží dva různé účely. Ve výchozím nastavení zobrazí seznam změny do souboru. Modul plug-in správy zdrojového kódu se otevře vlastního okna, v libovolné formátu zvolí, chcete-li zobrazit rozdíly mezi uživatele souboru na disku a nejnovější verzi souboru pod správou zdrojových kódů.  
  
 Můžete také integrovaného vývojového prostředí může jednoduše je potřeba určit, zda má soubor změněn. Rozhraní IDE může například potřebovat k určení, jestli je bezpečný pro rezervovat soubor bez informující uživatele. V takovém případě předá integrovaného vývojového prostředí `SCC_DIFF_CONTENTS` příznak. Modul plug-in správy zdrojového kódu musí najdete v souboru na disku, bajt po bajtu pro tento soubor se spravovanými zdroji a vrátí hodnotu určující, zda jsou dva soubory bez zobrazení nic uživateli jiný.  
  
 Optimalizace výkonu, modul plug-in správy zdrojového kódu použít alternativu založené na součtu nebo časové razítko namísto porovnání bajt po bajtu volané pro `SCC_DIFF_CONTENTS`: porovnání jsou samozřejmě rychlejší, ale méně spolehlivé. Ne všechny systémy správy zdrojového kódu může podporovat tyto alternativní porovnávací metody a modulu plug-in může být nutné vrátit zpět k porovnání obsahu. Minimálně musí všechny zdroje moduly plug-in správy podporují porovnání obsahu.  
  
> [!NOTE]
>  Rychlé rozdíl příznaky se vzájemně vylučují. Je možné předat žádné příznaky, ale není platné. současně předat více než jeden. `SCC_DIFF_QUICK_DIFF`, což je masku, která kombinuje všechny příznaky, lze použít k testování, ale je nikdy byste je předat jako parametr.  
  
|`fOption`|Význam|  
|---------------|-------------|  
|SCC_DIFF_IGNORECASE|Porovnávání (lze použít pro rychlé nebo vizuální rozdíl).|  
|SCC_DIFF_IGNORESPACE|Ignoruje prázdné znaky (lze použít pro rychlé nebo vizuální rozdíl).|  
|SCC_DIFF_QD_CONTENTS|Bezobslužná porovná soubor bajt po bajtu.|  
|SCC_DIFF_QD_CHECKSUM|Bezobslužná porovná soubor prostřednictvím kontrolního součtu, pokud je podporovaná. Pokud není podporován, přejde k porovnání obsahu.|  
|SCC_DIFF_QD_TIME|Bezobslužná porovná soubor prostřednictvím její časové razítko, pokud je podporovaná. Pokud není podporován, přejde k porovnání obsahu.|  
  
## <a name="see-also"></a>Viz také  
 [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)

