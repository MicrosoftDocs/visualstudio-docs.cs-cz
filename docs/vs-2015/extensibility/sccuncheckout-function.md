---
title: Funkce SccUncheckout | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3ae5ecd7568a10936479f72f92e9914132f2dcdf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190854"
---
# <a name="sccuncheckout-function"></a>SccUncheckout – funkce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato funkce vrátí předchozí operaci rezervace a obnoví tak obsah vybraného souboru nebo souborů do stavu před rezervací. Všechny změny provedené v souboru od rezervace jsou ztraceny.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
SCCRTN SccUncheckout (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
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
 pro Počet souborů, které jsou zadány v `lpFileNames` poli.  
  
 lpFileNames  
 pro Pole plně kvalifikovaných názvů místních cest souborů, pro které se má vrátit rezervace  
  
 fOptions  
 pro Příznaky příkazu (nepoužívá se)  
  
 pvOptions  
 pro Možnosti specifické pro modul plug-in správy zdrojového kódu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|SCC_OK|Zrušení rezervace bylo úspěšné.|  
|SCC_E_FILENOTCONTROLLED|Vybraný soubor není v rámci správy zdrojového kódu.|  
|SCC_E_ACCESSFAILURE|Při přístupu do systému správy zdrojů došlo k potížím, pravděpodobně kvůli problémům se sítí nebo kolize. Doporučuje se opakovat pokus.|  
|SCC_E_NONSPECIFICERROR|Nespecifická chyba. Zrušení rezervace nebylo úspěšné.|  
|SCC_E_NOTCHECKEDOUT|Uživatel nemá soubor rezervován.|  
|SCC_E_NOTAUTHORIZED|Uživatel nemá oprávnění k provedení této operace.|  
|SCC_E_PROJNOTOPEN|Projekt nebyl otevřen ze správy zdrojového kódu.|  
|SCC_I_OPERATIONCANCELED|Operace byla zrušena před dokončením.|  
  
## <a name="remarks"></a>Poznámky  
 Po provedení této operace `SCC_STATUS_CHECKEDOUT` `SCC_STATUS_MODIFIED` budou pro soubory, na kterých bylo provedeno zrušení rezervace, vymazány příznaky a.  
  
## <a name="see-also"></a>Viz také  
 [Funkce modulu plug-in správy zdrojového kódu v rozhraní API](../extensibility/source-control-plug-in-api-functions.md)
