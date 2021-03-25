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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 121dda58b8e01c5b0029d8b3c93ef66d2657446e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090990"
---
# <a name="deploy-project-types"></a>Nasazení typů projektů
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] nainstaluje nový agregátor typu projektu (*ProjectAggregator2.dll*) a také instalační služba systému Windows balíček pro redistribuci (*ProjectAggregator2.msi*). Je nutné použít nový agregátor pro typy projektů spravovaného kódu. ProjectAggregator2 funguje kolem omezení [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Agregátoru projektu, který brání správnému fungování typů projektů spravovaného kódu. Následující postup popisuje, jak změnit VSPackage na použití nového Agregátoru.

1. Odeberte projekt NativeHierarchyWrapper z vašeho řešení.

2. Z instalačního programu odeberte všechny binární soubory NativeHierarchyWrapper.

3. Přidejte *ProjectAggregator2.msi* k instalaci.
