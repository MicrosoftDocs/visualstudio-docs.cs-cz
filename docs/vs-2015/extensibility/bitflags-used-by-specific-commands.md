---
title: Příznaky Bitflag používané konkrétními příkazy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, bitflags used by specific commands
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e8ea658e62ca2bcd3ca4d423f00a94f83f2a2086
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51798180"
---
# <a name="bitflags-used-by-specific-commands"></a>Příznaky bitflag používané konkrétními příkazy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chování počet funkcí v rozhraní API modulu Plug-in zdroje ovládacího prvku, které lze upravit tak, že nastavíte jeden nebo více bits jedinou hodnotu. Tyto hodnoty jsou označovány jako bitové příznaky. Různé příznaky bitflag používané rozhraní API modulu Plug-in zdroje ovládacího prvku je podrobně popsaný tady, seskupené podle funkce, která je používá.  
  
## <a name="checked-out-flag"></a>Rezervovat příznak  
 Tento příznak může nastavit buď [sccadd –](../extensibility/sccadd-function.md) nebo [scccheckin –](../extensibility/scccheckin-function.md).  
  
|Příznak|Hodnota|Popis|  
|----------|-----------|-----------------|  
|`SCC_KEEP_CHECKEDOUT`|0x1000|Ponechte soubor rezervován.|  
  
## <a name="add-flags"></a>Přidání příznaků  
 Tyto příznaky jsou používány [sccadd –](../extensibility/sccadd-function.md).  
  
|Příznak|Hodnota|Popis|  
|----------|-----------|-----------------|  
|`SCC_FILETYPE_AUTO`|0x00|Modul plug-in správy zdrojového kódu by měl automaticky zjišťovat, zda je text nebo binární soubor.|  
|`SCC_FILETYPE_TEXT`|0x01|Typ souboru je text.|  
|`SCC_FILETYPE_BINARY`|0x04|Typ souboru není binární. **Poznámka:** `SCC_FILETYPE_TEXT` a `SCC_FILETYPE_BINARY` příznaky se vzájemně vylučují. Nastavte právě jeden, nebo ani jeden.|  
|`SCC_ADD_STORELATEST`|0x02|Store pouze nejnovější verze (žádné rozdíly).|  
  
## <a name="diff-flags"></a>Příznaky diff  
 [Sccdiff –](../extensibility/sccdiff-function.md) používá tyto příznaky pro určení oboru rozdílové operaci. `SCC_DIFF_QD_xxx` Příznaky se vzájemně vylučují. Pokud některý z nich není zadána, žádný vizuální zpětnou vazbu je má být poskytnut. V "rychlé diff" (hloubka fronty), modul plug-in neurčuje, čím se liší, pouze pokud je jiný soubor. Pokud žádná z těchto příznaků není zadán, že se provádí "visual diff"; podrobný soubor rozdíly jsou vypočítané a zobrazí. Pokud hf požadovaný není podporován, modul plug-in přesune dalšímu nejlepší. Například pokud rozhraní IDE požaduje kontrolní součet a modulu plug-in ji nepodporuje, modul plug-in nepodporuje full obsah zkontrolujte (stále mnohem rychleji než zobrazení vizuálu).  
  
|Příznak|Hodnota|Popis|  
|----------|-----------|-----------------|  
|`SCC_DIFF_IGNORECASE`|0x0002|Ignorujte velká rozdíly.|  
|`SCC_DIFF_IGNORESPACE`|0x0004|Ignorujte prázdné znaky rozdíly. **Poznámka:** `SCC_DIFF_IGNORECASE` a `SCC_DIFF_IGNORESPACE` příznaky jsou volitelné příznaky bitflag.|  
|`SCC_DIFF_QD_CONTENTS`|0x0010|Hloubka fronty porovnáním obsah celý soubor.|  
|`SCC_DIFF_QD_CHECKSUM`|0x0020|HF podle kontrolního součtu.|  
|`SCC_DIFF_QD_TIME`|0x0040|HF podle razítko data a času souboru.|  
|`SCC_DIFF_QUICK_DIFF`|0x0070|Toto je maska sloužící ke kontrole všechny příznaky bitflag hloubka fronty. By neměl být předán do funkce; tři příznaky bitflag hloubka fronty se vzájemně vylučují. Hloubka fronty vždy znamená bez zobrazení uživatelského rozhraní.|  
  
## <a name="populatelist-flag"></a>Příznak PopulateList  
 Tento příznak se používá [sccpopulatelist –](../extensibility/sccpopulatelist-function.md) v `fOptions` parametru.  
  
|Příznak|Hodnota|Popis|  
|----------|-----------|-----------------|  
|`SCC_PL_DIR`|0x00000001L|Rozhraní IDE dojde k předání adresáře, nikoli soubory.|  
  
## <a name="populatedirlist-flags"></a>Příznaky PopulateDirList  
 Tyto příznaky jsou používány [sccpopulatedirlist –](../extensibility/sccpopulatedirlist-function.md) v `fOptions` parametru.  
  
|Hodnota možnosti|Hodnota|Popis|  
|------------------|-----------|-----------------|  
|SCC_PDL_ONELEVEL|0x0000|Prozkoumejte pouze jednu úroveň adresářů pro adresáře (to je výchozí hodnota).|  
|SCC_PDL_RECURSIVE|0x0001|Rekurzivně zkontrolujte všechny adresáře v rámci každého daného adresáře.|  
|SCC_PDL_INCLUDEFILES|0x0002|Názvy vložených souborů v procesu šetření.|  
  
## <a name="openproject-flags"></a>Příznaky OpenProject  
 Tyto příznaky jsou používány [sccopenproject –](../extensibility/sccopenproject-function.md) v `dwFlags` parametru.  
  
|Hodnota možnosti|Hodnota|Popis|  
|------------------|-----------|-----------------|  
|SCC_OP_CREATEIFNEW|0x00000001L|Pokud projekt neexistuje ve správě zdrojového kódu, vytvořte ho. Pokud není tento příznak nastaven, zobrazit výzvu uživateli pro projekt pro vytvoření (není-li `SCC_OP_SILENTOPEN` zadán příznak).|  
|SCC_OP_SILENTOPEN|0x00000002L|Nezobrazovat výzvu k vytvoření projektu. jenom vrátit `SCC_E_UNKNOWNPROJECT`.|  
  
## <a name="get-flags"></a>Získat příznaky  
 Tyto příznaky jsou používány [sccget –](../extensibility/sccget-function.md) a [scccheckout –](../extensibility/scccheckout-function.md).  
  
|Příznak|Hodnota|Popis|  
|----------|-----------|-----------------|  
|`SCC_GET_ALL`|0x00000001L|Rozhraní IDE prochází adresáře, nikoli soubory: získání všech souborů v těchto adresářích.|  
|`SCC_GET_RECURSIVE`|0x00000002L|Rozhraní IDE je předání adresáře: Získejte tyto adresáře a jejich podsložky.|  
  
## <a name="noption-values"></a>nOption hodnoty  
 Tyto příznaky jsou používány [sccsetoption –](../extensibility/sccsetoption-function.md) v `nOption` parametru.  
  
|Příznak|Hodnota|Popis|  
|----------|-----------|-----------------|  
|`SCC_OPT_EVENTQUEUE`|0x00000001L|Nastavit stav fronty událostí.|  
|`SCC_OPT_USERDATA`|0x00000002L|Určení uživatelských dat pro `SCC_OPT_NAMECHANGEPFN`.|  
|`SCC_OPT_HASCANCELMODE`|0x00000003L|Rozhraní IDE může zpracovávat Storno|  
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|Nastaví zpětné volání pro změny názvu.|  
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|Zakázat Kontrola uživatelského rozhraní modulu plug-in správy zdrojového a nenastavujte pracovní adresář.|  
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|Přidáte ze systému správy zdrojového kódu k určení do pracovního adresáře. Zkuste sdílet do přidružený projekt, pokud je potomkem s přímým přístupem.|  
  
## <a name="dwval-bitflags"></a>dwVal bitové příznaky  
 Tyto příznaky jsou používány [sccsetoption –](../extensibility/sccsetoption-function.md) v `dwVal` parametru.  
  
|Příznak|Hodnota|Popis|Používá `nOption` hodnota|  
|----------|-----------|-----------------|-----------------------------|  
|`SCC_OPT_EQ_DISABLE`|0x00L|Pozastaví činnost fronty událostí.|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_EQ_ENABLE`|0x01L|Povolí protokolování fronty událostí.|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_HCM_NO`|0L|(Výchozí) Nemá žádný režim Storno; modul plug-in musí zadat v případě potřeby.|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_HCM_YES`|1L|Integrované vývojové prostředí zpracovává zrušení.|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_SCO_NO`|0L|(Výchozí) Podívejte se na uživatelské rozhraní modulu plug-in; OK pracovní adresář není nastaven.|`SCC_OPT_SCCCHECKOUTONLY`|  
|`SCC_OPT_SCO_YES`|1L|Žádný modul plug-in checkout uživatelského rozhraní, pracovní adresář.|`SCC_OPT_SCCCHECKOUTONLY`|  
  
## <a name="see-also"></a>Viz také  
 [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md)

