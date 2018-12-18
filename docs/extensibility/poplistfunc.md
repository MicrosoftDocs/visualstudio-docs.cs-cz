---
title: POPLISTFUNC | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 061f7b4d1c1fb9ddeb76444f058a95fe30abe47c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49920869"
---
# <a name="poplistfunc"></a>POPLISTFUNC
Toto zpětné volání je zadán do [sccpopulatelist –](../extensibility/sccpopulatelist-function.md) integrovaným vývojovým prostředím a modulu plug-in správy zdrojového kódu slouží k aktualizaci seznamu souborů nebo adresářů (také zadaný pro `SccPopulateList` funkce).  
  
 Když uživatel klikne **získat** příkazu v prostředí IDE, rozhraní IDE zobrazí seznam všech souborů, které můžete získat uživatele. Bohužel rozhraní IDE nezná přesný seznam všech souborů, které může uživatel získat; pouze modul plug-in je tento seznam. Pokud ostatním uživatelům přidali soubory do projektu ve správě zdrojového kódu, tyto soubory by se zobrazit v seznamu, ale rozhraní IDE neví o nich. Rozhraní IDE vytvoří seznam souborů, které se domnívá, že uživatel může dostat. Předtím, než se uživateli zobrazí tento seznam, zavolá [sccpopulatelist –](../extensibility/sccpopulatelist-function.md) `,` poskytuje modul plug-in správy zdrojového kódu příležitost pro přidávání a odstraňování souborů ze seznamu.  
  
## <a name="signature"></a>podpis  
 Modul plug-in správy zdrojového kódu změní seznamu pomocí volání funkce implementované integrované vývojové prostředí s následující prototyp:  
  
```cpp  
typedef BOOL (*POPLISTFUNC) (  
   LPVOID pvCallerData,  
   BOOL fAddRemove,  
   LONG nStatus,  
   LPSTR lpFileName  
);  
```  
  
## <a name="parameters"></a>Parametry  
 pvCallerData  
 `pvCallerData` Byl předán parametr volající (IDE) [sccpopulatelist –](../extensibility/sccpopulatelist-function.md). Modul plug-in správy zdrojového kódu by měl předpokládat nic neříká o obsah tohoto parametru.  
  
 fAddRemove  
 Pokud `TRUE`, `lpFileName` je soubor přidaný do seznamu. Pokud `FALSE`, `lpFileName` je soubor, který by měl být odstraněn ze seznamu souborů.  
  
 nStatus  
 Stav `lpFileName` (kombinace `SCC_STATUS` bits; viz [souboru stavový kód](../extensibility/file-status-code-enumerator.md) podrobnosti).  
  
 lpFileName  
 Úplná cesta k adresáři názvu souboru přidat nebo odstranit ze seznamu.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`TRUE`|Modul plug-in můžete dál volání této funkce.|  
|`FALSE`|Na straně integrovaného vývojového prostředí (například z důvodu nedostatku paměti situace) došlo k potížím. Modul plug-in by se měla zastavit operaci.|  
  
## <a name="remarks"></a>Poznámky  
 Pro každý soubor, který chce, aby se modul plug-in správy zdrojového kódu pro přidání nebo odebrání ze seznamu souborů, které volá tuto funkci a předává jí `lpFileName`. `fAddRemove` Příznak označuje nového souboru do seznamu přidat nebo odstranit původní soubor. `nStatus` Parametr poskytuje stav souboru. Po dokončení přidávání a odstraňování souborů modulu plug-in SCC vrátí z [sccpopulatelist –](../extensibility/sccpopulatelist-function.md) volání.  
  
> [!NOTE]
>  `SCC_CAP_POPULATELIST` Bit funkce se vyžaduje pro Visual Studio.  
  
## <a name="see-also"></a>Viz také:  
 [Funkce zpětného volání implementované integrovaným vývojovým prostředím](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Ovládací prvek moduly plug-in zdrojového kódu](../extensibility/source-control-plug-ins.md)   
 [Sccpopulatelist –](../extensibility/sccpopulatelist-function.md)   
 [Kód stavu souboru](../extensibility/file-status-code-enumerator.md)