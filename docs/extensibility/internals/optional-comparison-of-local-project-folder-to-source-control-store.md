---
title: Porovnat složku projektu s úložištěm správy zdrojového kódu | Microsoft Docs
description: V rozhraní API modulu plug-in správy zdrojového kódu je porovnání mezi místní složkou projektu a správou zdrojového kódu provedeno pomocí SccDirQueryInfo a SccDirDiff.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f7b334bb6e1b73dd31060020378e91b74e5af102
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063042"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Volitelné porovnání místní složky projektu a úložiště správy zdrojového kódu
V rozhraní API modulu plug-in správy zdrojových kódů 1,2 je možné porovnat mezi místní složkou projektu a správou zdrojového kódu pomocí funkcí [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) a [SccDirDiff](../../extensibility/sccdirdiff-function.md).

 Pokud je v rámci **Průzkumník řešení** vybrána složka namísto jednotlivého souboru, místní nabídka **Porovnat verze** vyvolá nové [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) a [SccDirDiff](../../extensibility/sccdirdiff-function.md) v modulu plug-in správy zdrojových kódů.

## <a name="new-capability-flags"></a>Nové příznaky schopností
 `SCC_CAP_DIRECTORYDIFF`

 `SCC_CAP_DIRECTORYCHECKOUT`

## <a name="new-functions"></a>Nové funkce
- [SccDirDiff](../../extensibility/sccdirdiff-function.md)

- [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)

 `SccDirQueryInfo`Funkce je volána před `SccDirDiff` určením, zda je pracovní adresář řízen správou zdrojového kódu. `SccDirDiff`Funkce zobrazuje rozdíly mezi aktuálním místním adresářem a odpovídající složkou správy zdrojového kódu. Tento příkaz požádá modul plug-in správy zdrojových kódů, aby zobrazil seznam změn v adresáři. Modul plug-in správy zdrojových kódů poskytuje vlastní uživatelské rozhraní pro zobrazení rozdílů.

> [!NOTE]
> Tato funkce používá stejný příznak příkazu jako [SccDiff](../../extensibility/sccdiff-function.md). Jako zprostředkovatel modulu plug-in správy zdrojového kódu se můžete rozhodnout, že nebudete podporovat operaci rychlá rozdíl pro adresáře.

## <a name="see-also"></a>Viz také
- [Co je nového v rozhraní API modulu plug-in správy zdrojového kódu ve verzi 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
