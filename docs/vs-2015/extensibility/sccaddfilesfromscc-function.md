---
title: Funkce SccAddFilesFromSCC | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d5af748c9180644cae928d1b6db3a3f880b6b286
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200918"
---
# <a name="sccaddfilesfromscc-function"></a>SccAddFilesFromSCC – funkce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato funkce přidá seznam souborů ze správy zdrojového kódu do aktuálně otevřeného projektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SCCRTN SccAddFilesFromSCC(  
   LPVOID  pContext,  
   HWND    hWnd,  
   LPSTR   lpUser,  
   LPSTR   lpAuxProjPath,  
   LONG    cFiles,  
   LPCSTR* lpFilePaths,  
   LPCSTR  lpDestination,  
   LPCSTR  lpComment,  
   LPBOOL  pbResults  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pContext  
 pro Ukazatel kontextu modulu plug-in správy zdrojových kódů.  
  
 hWnd  
 pro Popisovač okna rozhraní IDE, který modul plug-in správy zdrojového kódu může použít jako nadřazený pro všechna dialogová okna, která poskytuje.  
  
 lpUser  
 [in, out] Uživatelské jméno (až do SCC_USER_SIZE, včetně ukončovacího znaku null).  
  
 lpAuxProjPath  
 [in, out] Pomocný řetězec identifikující projekt ( `SCC_PRJPATH_` velikost, včetně ukončovacího znaku null).  
  
 cFiles  
 pro Počet souborů vydaných `lpFilePaths` .  
  
 lpFilePaths  
 [in, out] Pole názvů souborů, které chcete přidat do aktuálního projektu.  
  
 lpDestination  
 pro Cílová cesta, kam se mají soubory zapisovat  
  
 lpComment  
 pro Komentář, který se má použít u každého přidávaného souboru.  
  
 pbResults  
 [in, out] Pole příznaků, které jsou nastaveny pro indikaci úspěchu (nenulového nebo TRUE) nebo chyby (nula nebo FALSE) pro každý soubor (velikost pole musí být alespoň `cFiles` dlouhá).  
  
## <a name="return-value"></a>Návratová hodnota  
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|SCC_E_PROJNOTOPEN|Projekt není otevřený.|  
|SCC_E_OPNOTPERFORMED|Připojení není ke stejnému projektu, jako je určeno `lpAuxProjPath.`|  
|SCC_E_NOTAUTHORIZED|Uživatel nemá oprávnění k aktualizaci databáze.|  
|SCC_E_NONSPECIFICERROR|Neznámou chybu.|  
|SCC_I_RELOADFILE|Soubor nebo projekt je třeba znovu načíst.|  
  
## <a name="see-also"></a>Viz také  
 [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
