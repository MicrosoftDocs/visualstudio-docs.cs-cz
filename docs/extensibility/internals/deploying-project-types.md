---
title: Nasazení typů projektů | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708789"
---
# <a name="deploy-project-types"></a>Nasazení typů projektů
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]Nainstaluje nový agregátor typu projektu (*ProjectAggregator2.dll*) a také balíček Instalační služby systému Windows pro redistribuci (*ProjectAggregator2.msi*). Je nutné použít nový agregátor pro typy projektů spravovaného kódu. ProjectAggregator2 pracuje kolem omezení [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] v agregátoru projektu, který zabraňuje správně pracovat typy projektů spravovaného kódu. Následující kroky popisují, jak změnit vspackage použít nový agregátor.

1. Odeberte projekt NativeHierarchyWrapper z vašeho řešení.

2. Odeberte všechny binární soubory Nativní hierarchieObálka z instalace.

3. Přidejte *projectaggregator2.msi* do nastavení.
