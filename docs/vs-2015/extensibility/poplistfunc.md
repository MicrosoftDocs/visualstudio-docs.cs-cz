---
title: POPLISTFUNC | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8c3ae2ce451f076c33ea5613b71c6d262c1d7a0e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64811734"
---
# <a name="poplistfunc"></a>POPLISTFUNC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto zpětné volání je dodáno rozhraním IDE do [SccPopulateList](../extensibility/sccpopulatelist-function.md) a používá ho modul plug-in správy zdrojových kódů k aktualizaci seznamu souborů nebo adresářů (také dodaných do `SccPopulateList` funkce).  
  
 Když uživatel zvolí příkaz **Get** v integrovaném vývojovém prostředí (IDE), rozhraní IDE zobrazí seznam všech souborů, které uživatel může získat. Rozhraní IDE bohužel neví přesný seznam všech souborů, které uživatel může získat. Tento seznam obsahuje jenom modul plug-in. Pokud jiní uživatelé přidali soubory do projektu správy zdrojového kódu, tyto soubory by se měly zobrazit v seznamu, ale rozhraní IDE je neví. Rozhraní IDE vytvoří seznam souborů, které může uživatel získat. Před zobrazením tohoto seznamu uživateli volá SccPopulateList, který dává modulu [SccPopulateList](../extensibility/sccpopulatelist-function.md) `,` Plug-in správy zdrojového kódu možnost Přidat a odstranit soubory ze seznamu.  
  
## <a name="signature"></a>Podpis  
 Modul plug-in správy zdrojových kódů upraví seznam voláním funkce implementované rozhraním IDE s následujícím prototypem:  
  
```cpp#  
typedef BOOL (*POPLISTFUNC) (  
   LPVOID pvCallerData,  
   BOOL fAddRemove,  
   LONG nStatus,  
   LPSTR lpFileName  
);  
```  
  
## <a name="parameters"></a>Parametry  
 pvCallerData  
 `pvCallerData`Parametr předaný volajícím (IDE) do [SccPopulateList](../extensibility/sccpopulatelist-function.md). Modul plug-in správy zdrojových kódů by neměl předpokládat žádné informace o obsahu tohoto parametru.  
  
 fAddRemove  
 Pokud `TRUE` `lpFileName` je, je soubor, který by měl být přidán do seznamu souborů. Pokud `FALSE` `lpFileName` je soubor, který by se měl odstranit ze seznamu souborů.  
  
 nStatus  
 Stav `lpFileName` (kombinace `SCC_STATUS` bitů; podrobnosti naleznete v [souboru stavového kódu](../extensibility/file-status-code-enumerator.md) ).  
  
 lpFileName  
 Úplná cesta k adresáři pro název souboru, který se má přidat nebo odstranit ze seznamu.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`TRUE`|Modul plug-in může pokračovat v volání této funkce.|  
|`FALSE`|Došlo k potížím na straně integrovaného vývojového prostředí (například situace typu nedostatek paměti). Modul plug-in by měl zastavit operaci.|  
  
## <a name="remarks"></a>Poznámky  
 Pro každý soubor, který modul plug-in správy zdrojových kódů chce přidat nebo odstranit ze seznamu souborů, volá tuto funkci, která předává do `lpFileName` . `fAddRemove`Příznak označuje nový soubor, který se má přidat do seznamu, nebo starý soubor, který se má odstranit. `nStatus`Parametr poskytuje stav souboru. Když modul plug-in SCC dokončí přidávání a odstraňování souborů, vrátí se z volání [SccPopulateList](../extensibility/sccpopulatelist-function.md) .  
  
> [!NOTE]
> V `SCC_CAP_POPULATELIST` aplikaci Visual Studio je vyžadován bit schopností.  
  
## <a name="see-also"></a>Viz také  
 [Funkce zpětného volání implementované rozhraním IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)   
 [Kód stavu souboru](../extensibility/file-status-code-enumerator.md)
