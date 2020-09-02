---
title: Volitelné porovnání místní složky projektu do úložiště správy zdrojového kódu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: be26b4195e0db7b3b78fcc2223ff2a6f8bde47d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64819029"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Volitelné porovnání místní složky projektu a úložiště správy zdrojového kódu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

V rozhraní API modulu plug-in správy zdrojových kódů 1,2 je možné porovnat mezi místní složkou projektu a správou zdrojového kódu pomocí funkcí [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) a [SccDirDiff](../../extensibility/sccdirdiff-function.md).  
  
 Pokud je v rámci **Průzkumník řešení**vybrána složka namísto jednotlivého souboru, místní nabídka **Porovnat verze** vyvolá nové [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) a [SccDirDiff](../../extensibility/sccdirdiff-function.md) v modulu plug-in správy zdrojových kódů.  
  
## <a name="new-capability-flags"></a>Nové příznaky schopností  
 `SCC_CAP_DIRECTORYDIFF`  
  
 `SCC_CAP_DIRECTORYCHECKOUT`  
  
## <a name="new-functions"></a>Nové funkce  
 [SccDirDiff](../../extensibility/sccdirdiff-function.md)  
  
 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)  
  
 `SccDirQueryInfo`Funkce je volána před `SccDirDiff` určením, zda je pracovní adresář řízen správou zdrojového kódu. `SccDirDiff`Funkce zobrazuje rozdíly mezi aktuálním místním adresářem a odpovídající složkou správy zdrojového kódu. Tento příkaz požádá modul plug-in správy zdrojových kódů, aby zobrazil seznam změn v adresáři. Modul plug-in správy zdrojových kódů poskytuje vlastní uživatelské rozhraní pro zobrazení rozdílů.  
  
> [!NOTE]
> Tato funkce používá stejný příznak příkazu jako [SccDiff](../../extensibility/sccdiff-function.md). Jako zprostředkovatel modulu plug-in správy zdrojového kódu se můžete rozhodnout, že nebudete podporovat operaci rychlá rozdíl pro adresáře.  
  
## <a name="see-also"></a>Viz také  
 [Co je nového v rozhraní API modulu plug-in správy zdrojového kódu ve verzi 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
