---
title: Nasazení typů projektů | Microsoft Docs
description: Naučte se, jak nasadit typy projektů spravovaného kódu pomocí nového Agregátoru typu projektu a balíčku Instalační služba systému Windows pro redistribuci v sadě Visual Studio SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1b015f29b6521482013a77bbcf7c44d8a79afa6
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329871"
---
# <a name="deploy-project-types"></a>Nasazení typů projektů
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] nainstaluje nový agregátor typu projektu (*ProjectAggregator2.dll*) a také instalační služba systému Windows balíček pro redistribuci (*ProjectAggregator2.msi*). Je nutné použít nový agregátor pro typy projektů spravovaného kódu. ProjectAggregator2 funguje kolem omezení [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Agregátoru projektu, který brání správnému fungování typů projektů spravovaného kódu. Následující postup popisuje, jak změnit VSPackage na použití nového Agregátoru.

1. Odeberte projekt NativeHierarchyWrapper z vašeho řešení.

2. Z instalačního programu odeberte všechny binární soubory NativeHierarchyWrapper.

3. Přidejte *ProjectAggregator2.msi* k instalaci.
