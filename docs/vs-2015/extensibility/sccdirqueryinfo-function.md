---
title: Funkce SccDirQueryInfo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7334ddd1ce6c7f9feac63253246e55b65121e18b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64780278"
---
# <a name="sccdirqueryinfo-function"></a>SccDirQueryInfo – funkce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato funkce prověřuje seznam plně kvalifikovaných adresářů pro jejich aktuální stav.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
SCCRTN SccDirQueryInfo(  
LPVOID  pContext,  
LONG    nDirs,  
LPCSTR* lpDirNames,  
LPLONG  lpStatus  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pContext  
 pro Struktura kontextu modulu plug-in správy zdrojových kódů.  
  
 nDirs  
 pro Počet adresářů vybraných k dotazování.  
  
 lpDirNames  
 pro Pole plně kvalifikovaných cest k adresářům, které mají být dotazovány.  
  
 lpStatus  
 [in, out] Struktura pole pro modul plug-in správy zdrojových kódů, která vrátí stavové příznaky (podrobnosti viz [kód stavu adresáře](../extensibility/directory-status-code-enumerator.md) ).  
  
## <a name="return-value"></a>Návratová hodnota  
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|SCC_OK|Dotaz byl úspěšný.|  
|SCC_E_OPNOTSUPPORTED|Systém správy zdrojového kódu tuto operaci nepodporuje.|  
|SCC_E_ACCESSFAILURE|Při přístupu do systému správy zdrojů došlo k potížím, pravděpodobně kvůli problémům se sítí nebo kolize. Doporučuje se opakovat pokus.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nespecifická chyba.|  
  
## <a name="remarks"></a>Poznámky  
 Funkce vyplní vrácené pole maskou bitů z `SCC_DIRSTATUS` rodiny (viz [stavový kód adresáře](../extensibility/directory-status-code-enumerator.md)), jednu položku pro každý zadaný adresář. Pole stav je přiděleno volajícím.  
  
 Rozhraní IDE používá tuto funkci před přejmenováním adresáře, aby zkontrolovala, zda je adresář pod správou zdrojových kódů pomocí dotazu, zda má odpovídající projekt. Pokud adresář není pod správou zdrojových kódů, rozhraní IDE může poskytnout správné upozornění uživateli.  
  
> [!NOTE]
> Pokud se modul plug-in správy zdrojových kódů rozhodne neimplementovat jednu nebo více hodnot stavu, musí být neimplementovaná bity nastavena na hodnotu nula.  
  
## <a name="see-also"></a>Viz také  
 [Funkce rozhraní API modulu plug-in správy zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)   
 [Kód stavu adresáře](../extensibility/directory-status-code-enumerator.md)
