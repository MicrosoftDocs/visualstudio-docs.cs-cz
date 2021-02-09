---
title: Použít nastavení napříč více připojeními projektů
description: Naučte se, jak pomocí modulu plug-in správy zdrojových kódů použít nastavení v rámci více připojení projektu ke spuštění dávkové operace.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 14b466112e3939756142a43568ddc3107e55d659
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906098"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Použití nastavení napříč více připojeními projektů
Modul plug-in správy zdrojových kódů sestavený pomocí rozhraní API modulu plug-in správy zdrojového kódu verze 1,2 může použít dávkovou operaci ke spuštění stejné operace správy zdrojových kódů ve více projektech nebo v několika kontextech připojení. Dávky lze použít k odstranění redundantních dialogových oken pro jednotlivé projekty z uživatelského prostředí.

 Pokud uživatel vybere více položek, které patří do více než jednoho připojení v modulu plug-in správy zdrojových kódů sestavené pomocí rozhraní API modulu plug-in správy zdrojového kódu verze 1,1 (například dva webové projekty v různých počítačích sdílených souborů) a zařadí je, uživatel uvidí totéž dialogové okno opakovaně. K tomuto scénáři dochází, i když uživatel klikne v dialogovém okně na zaškrtávací políčko **použít u všech** , protože rozhraní IDE obnoví stav pro každý kontext připojení.

## <a name="new-capability-flag"></a>Příznak nové schopnosti
 `SccBeginBatch`Funkce nastaví `SCC_CAP_BATCH` příznak tak, aby označoval, že probíhá operace dávky.

## <a name="new-functions"></a>Nové funkce
Dávková operace podporuje následující nové funkce:

- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)

- [SccEndBatch](../../extensibility/sccendbatch-function.md)

`SCCBeginBatch`Funkce spustí skupinu operací správy zdrojového kódu. `SccEndBatch`Funkce uzavře skupinu. Skupiny nesmí být vnořené.

## <a name="see-also"></a>Viz také
- [Co je nového v rozhraní API modulu plug-in správy zdrojového kódu verze 1,2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
