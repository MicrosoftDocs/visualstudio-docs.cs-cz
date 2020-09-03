---
title: Nasazení typů projektů | Microsoft Docs
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
ms.openlocfilehash: 835e85ade4d309d0b5692aa9b857476cd6b5927a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708789"
---
# <a name="deploy-project-types"></a>Nasazení typů projektů
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] nainstaluje nový agregátor typu projektu (*ProjectAggregator2.dll*) a také instalační služba systému Windows balíček pro redistribuci (*ProjectAggregator2.msi*). Je nutné použít nový agregátor pro typy projektů spravovaného kódu. ProjectAggregator2 funguje kolem omezení [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Agregátoru projektu, který brání správnému fungování typů projektů spravovaného kódu. Následující postup popisuje, jak změnit VSPackage na použití nového Agregátoru.

1. Odeberte projekt NativeHierarchyWrapper z vašeho řešení.

2. Z instalačního programu odeberte všechny binární soubory NativeHierarchyWrapper.

3. Přidejte *ProjectAggregator2.msi* k instalaci.
