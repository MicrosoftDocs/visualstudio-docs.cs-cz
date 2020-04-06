---
title: Aplikace nastavení napříč více připojeními k projektu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bcaed0f7f2380dd36bcbffd776839025fe9efa16
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710065"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Použití nastavení napříč více připojeními projektu
Modul plug-in správy zdrojového kódu vytvořený pomocí rozhraní API plug-in správy zdrojového kódu verze 1.2 může pomocí dávkové operace provést stejnou operaci správy zdrojového kódu ve více projektech nebo v kontextu připojení. Listy lze použít k odstranění redundantních dialogových oken pro jednotlivé projekty z uživatelského prostředí.

 Pokud uživatel vybere více položek, které patří k více než jednomu připojení v modulu plug-in správy zdrojového kódu vytvořenépomocí modulu plug-in modulu zdrojového kódu rozhraní API verze 1.1 (například dva webové projekty na různých počítačích pro sdílení souborů) a rezervuje je, uživatel se opakovaně zobrazí stejné dialogové okno. K tomuto scénáři dochází i v případě, že uživatel klepne na **zaškrtávací políčko Použít na vše** v dialogovém okně, protože rozhraní IDE obnoví svůj stav pro každý kontext připojení.

## <a name="new-capability-flag"></a>Příznak nové schopnosti
 Funkce `SccBeginBatch` nastaví `SCC_CAP_BATCH` příznak označující, že probíhá dávková operace.

## <a name="new-functions"></a>Nové funkce
Následující nové funkce podporují dávkovou operaci:

- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)

- [SccEndBatch](../../extensibility/sccendbatch-function.md)

Funkce `SCCBeginBatch` spustí skupinu operací správy zdrojového kódu. Funkce `SccEndBatch` zavře skupinu. Skupiny nemusí být vnořené.

## <a name="see-also"></a>Viz také
- [Co je nového v rozhraní Plug-in Plug-in API správy zdrojového kódu verze 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
