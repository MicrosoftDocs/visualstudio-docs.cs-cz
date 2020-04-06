---
title: Porovnat složku projektu s úložištěm správy zdrojového kódu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: facb3b656e0ac50b50fdb0291307aa2fe98b1df4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706867"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Volitelné porovnání místní složky projektu a úložiště správy zdrojového kódu
V rozhraní Plug-in Api 1.2 správy zdrojového kódu se porovnání mezi místní složkou projektu a správu zdrojového kódu provádí pomocí funkcí [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) a [SccDirDiff](../../extensibility/sccdirdiff-function.md).

 V **Průzkumníku řešení**, pokud je vybrána složka namísto jednotlivého souboru, místní nabídka Porovnat verze vyvolá v modulu plug-in správy zdrojového kódu nové **položky** [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) a [SccDirDiff.](../../extensibility/sccdirdiff-function.md)

## <a name="new-capability-flags"></a>Příznaky nových schopností
 `SCC_CAP_DIRECTORYDIFF`

 `SCC_CAP_DIRECTORYCHECKOUT`

## <a name="new-functions"></a>Nové funkce
- [SccDirDiff](../../extensibility/sccdirdiff-function.md)

- [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)

 Funkce `SccDirQueryInfo` je volána před `SccDirDiff` k určení, zda je pracovní adresář řízen zdrojem. Funkce `SccDirDiff` zobrazuje rozdíly mezi aktuálním místním adresářem a odpovídající složkou správy zdrojového kódu. Tento příkaz požádá modul plug-in správy zdrojového kódu o zobrazení seznamu změn v adresáři. Modul plug-in správy zdrojového kódu poskytuje vlastní ui pro zobrazení rozdílů.

> [!NOTE]
> Tato funkce používá stejné příkazové příznaky jako [SccDiff](../../extensibility/sccdiff-function.md). Jako zprostředkovatel modulu plug-in správy zdrojového kódu se můžete rozhodnout nepodporovat operaci "rychlého rozdílu" pro adresáře.

## <a name="see-also"></a>Viz také
- [Co je nového v rozhraní API modulu plug-in správy zdrojového kódu ve verzi 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
