---
title: Visual Studio Tools for Unity programování | Microsoft Docs
description: Podívejte se na příklady programování pomocí rozhraní API Visual Studio Tools for Unity (VSTU). Přizpůsobení souborů projektu vytvořených pomocí VSTU. Sdílení zpětného volání protokolu Unity s VSTU
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: a5758cb0-e73b-45f5-8cae-c0eb40491026
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: c98a3cdbcece87ad5e8fbe0e91ae76f677494477
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2020
ms.locfileid: "94341664"
---
# <a name="program-visual-studio-tools-for-unity"></a>Programování Visual Studio Tools for Unity
V této části najdete příklady použití rozhraní Visual Studio Tools for Unity API.

## <a name="examples"></a>Příklady
 Tady je několik příkladů, které ukazují, jak můžete používat rozhraní Visual Studio Tools for Unity API.

### <a name="customize-project-files-created-by-vstu"></a>Přizpůsobení souborů projektu vytvořených pomocí VSTU
 Visual Studio Tools for Unity poskytuje zpětné volání ve stylu Unity během generování souboru projektu. Informace o tom, jak můžete upravit soubor projektu vždy, když je znovu vygenerován, naleznete v tématu [Příklad: generování souboru projektu](./customize-project-files-created-by-vstu.md).

### <a name="share-the-unity-log-callback-with-vstu"></a>Sdílení zpětného volání protokolu Unity s VSTU
 Visual Studio Tools for Unity zaregistruje zpětné volání protokolu s Unity, aby bylo možné streamovat svou konzolu do sady Visual Studio. Pokud vaše skripty v editoru také zaregistrují zpětné volání protokolu v Unity, může s ním narušit zpětné volání VSTU. Další informace o tom, jak můžete sdílet zpětné volání protokolu Unity pomocí VSTU, najdete v tématu [Příklad: zpětné volání protokolu](./share-the-unity-log-callback-with-vstu.md).
