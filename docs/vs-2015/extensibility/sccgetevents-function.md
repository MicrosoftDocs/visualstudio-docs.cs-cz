---
title: Funkce SccGetEvents | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccGetEvents
helpviewer_keywords:
- SccGetEvents function
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d975570334aeab7c6709db92f3240a8e8d06b131
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200121"
---
# <a name="sccgetevents-function"></a>SccGetEvents – funkce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato funkce načte událost stavu ve frontě.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
SCCRTN SccGetEvents (  
   LPVOID pvContext,  
   LPSTR  lpFileName,  
   LPLONG lpStatus,  
   LPLONG pnEventsRemaining  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pvContext  
 pro Struktura kontextu modulu plug-in správy zdrojových kódů.  
  
 lpFileName  
 [in, out] Vyrovnávací paměť, kde modul plug-in správy zdrojových kódů vloží vrácený název souboru (až _MAX_PATH znaků).  
  
 lpStatus  
 [in, out] Vrátí stavový kód (možné hodnoty naleznete v části [kód stavu souboru](../extensibility/file-status-code-enumerator.md) ).  
  
 pnEventsRemaining  
 [in, out] Vrátí počet položek zbývajících ve frontě po tomto volání. Pokud je toto číslo velké, volající se může rozhodnout volat [SccQueryInfo](../extensibility/sccqueryinfo-function.md) a získat všechny informace najednou.  
  
## <a name="return-value"></a>Návratová hodnota  
 Při implementaci modulu plug-in správy zdrojových kódů této funkce se očekává, že se vrátí jedna z následujících hodnot:  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|SCC_OK|Získání událostí bylo úspěšné.|  
|SCC_E_OPNOTSUPPORTED|Tato funkce není podporována.|  
|SCC_E_NONSPECIFICERROR|Nespecifická chyba.|  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce se volá během nečinného zpracování, aby se zjistilo, jestli v rámci správy zdrojového kódu nebyly nějaké aktualizace stavu souborů. Modul plug-in správy zdrojových kódů udržuje stav všech souborů, o kterých ví, a pokaždé, když modul plug-in zaznamená změnu stavu, je stav a přidružený soubor uložen ve frontě. Při `SccGetEvents` volání metody se načte a vrátí nejvyšší prvek fronty. Tato funkce je omezená, aby vracela pouze dříve uložené informace v mezipaměti a musí mít velmi rychlý vyřízení (to znamená, že žádné čtení disku nepožaduje stav systému správy zdrojového kódu); v opačném případě může výkon prostředí IDE začínat na zhoršení.  
  
 Pokud není k dispozici žádná aktualizace stavu sestav, modul plug-in správy zdrojových kódů ukládá prázdný řetězec ve vyrovnávací paměti, na kterou ukazuje `lpFileName` . V opačném případě modul plug-in uloží úplný název cesty k souboru, pro který se změnily informace o stavu, a vrátí příslušný stavový kód (jednu z hodnot popsaných ve [stavovém kódu souboru](../extensibility/file-status-code-enumerator.md)).  
  
## <a name="see-also"></a>Viz také  
 [Funkce rozhraní API modulu plug-in správy zdrojového kódu](../extensibility/source-control-plug-in-api-functions.md)   
 [Kód stavu souboru](../extensibility/file-status-code-enumerator.md)
