---
title: Funkce SccCheckout | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f23290ebfadd1b6e3d34f808d5ea0ccccbb3c319
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200150"
---
# <a name="scccheckout-function"></a>SccCheckout – funkce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Když se zobrazí seznam plně kvalifikovaných názvů souborů, tato funkce je vrátí na místní disk. Komentář se vztahuje na všechny rezervované soubory. Argument komentáře může být `null` řetězec.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
SCCRTN SccCheckout (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 pro Struktura kontextu modulu plug-in správy zdrojových kódů.  
  
 hWnd  
 pro Popisovač okna rozhraní IDE, který modul plug-in správy zdrojového kódu může použít jako nadřazený pro všechna dialogová okna, která poskytuje.  
  
 nFiles  
 pro Počet souborů vybraných k rezervaci.  
  
 lpFileNames  
 pro Pole plně kvalifikovaných názvů místních cest souborů, které mají být rezervovány.  
  
 lpComment  
 pro Komentář, který se má použít u všech vybraných souborů, které jsou rezervovány.  
  
 fOptions  
 pro Příznaky příkazu (viz [Bitflags používané konkrétními příkazy](../extensibility/bitflags-used-by-specific-commands.md)).  
  
 pvOptions  
 pro Možnosti specifické pro modul plug-in správy zdrojového kódu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|SCC_OK|Rezervace byla úspěšná.|  
|SCC_E_FILENOTCONTROLLED|Vybraný soubor není v rámci správy zdrojového kódu.|  
|SCC_E_ACCESSFAILURE|Při přístupu do systému správy zdrojů došlo k potížím, pravděpodobně kvůli problémům se sítí nebo kolize. Doporučuje se opakovat pokus.|  
|SCC_E_NOTAUTHORIZED|Uživatel nemá oprávnění k provedení této operace.|  
|SCC_E_NONSPECIFICERROR|Nespecifická chyba. Soubor nebyl zaregistrován.|  
|SCC_E_ALREADYCHECKEDOUT|Uživatel už soubor rezervoval.|  
|SCC_E_FILEISLOCKED|Soubor je uzamčen a je zakázán vytváření nových verzí.|  
|SCC_E_FILEOUTEXCLUSIVE|Jiný uživatel provedl exkluzivní rezervaci na tomto souboru.|  
|SCC_I_OPERATIONCANCELED|Operace byla zrušena před dokončením.|  
  
## <a name="see-also"></a>Viz také  
 [Funkce rozhraní API modulu plug-in správy zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)   
 [Příznaky bitflag používané konkrétními příkazy](../extensibility/bitflags-used-by-specific-commands.md)
