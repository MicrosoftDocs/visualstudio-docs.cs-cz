---
title: Správa vspackages | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60745d07679ae53b85d169473ed37ab314b67624
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702656"
---
# <a name="manage-vspackages"></a>Správa balíčků VSPackage
Ve většině případů se nemusíte starat o správu VSPackages, protože šablony projektu a položky zaregistrovat a načíst balíček automaticky. Nicméně, v některých případech budete muset naučit trochu více, aby se spravovat balíček.

## <a name="use-the-experimental-instance"></a>Použití experimentální instance
 Další informace o experimentální instanci naleznete v [tématu Experimentální instance](../extensibility/the-experimental-instance.md).

## <a name="register-and-unregister-vspackages"></a>Registrace a zrušení registrace vspackages
 Chcete-li zjistit, jak zaregistrovat a zrušit registraci VSPackages a další typy rozšíření, naleznete [v tématu Register and unregister VSPackages](../extensibility/registering-and-unregistering-vspackages.md).

## <a name="load-a-vspackage"></a>Načtení balíčku VSPackage
 VSPackages lze nastavit automatické načtení při určitém IDENTIFIKÁTORU GUID CMDUICONTEXT. Další informace naleznete v [tématu Load VSPackages](../extensibility/loading-vspackages.md).

## <a name="use-asyncpackage-to-load-vspackages-in-the-background"></a>Použití balíčku AsyncPackage k načtení balíčků VSPackages na pozadí
 Třída `AsyncPackage` umožňuje načítání balíčku ve vlákně na pozadí pro lepší odezvu uživatelského rozhraní v sadě Visual Studio. Další informace naleznete v [tématu How to: Use AsyncPackage to load VSPackages in the background](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).

## <a name="rule-based-ui-context-for-extensions"></a>Kontext ui založené na pravidlech pro rozšíření
 Kontexty ui založené na pravidlech umožňuje autorům rozšíření definovat přesné podmínky, za kterých je aktivován kontext ui a přidružené VSPackages načteny. Další informace naleznete v [tématu How to: Use rule-based UI Context for Visual Studio extensions](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).

## <a name="diagnose-extension-performance"></a>Diagnostika výkonu rozšíření
Rozšíření může mít vliv na spuštění a výkon načítání řešení. Zjistěte, jak se počítá dopad rozšíření sady Visual Studio a jak jej lze analyzovat místně a otestovat, zda rozšíření může být zobrazeno jako rozšíření ovlivňující výkon. Další informace naleznete v [tématu How to: Diagnose extension performance](how-to-diagnose-extension-performance.md).

## <a name="troubleshoot-vspackages"></a>Poradce při potížích s balíčky VSPackages
 Zjistěte techniky pro řešení potíží s balíčky VSPackages, které se nenačítají nebo dochází k chybám: [Poradce při potížích s balíčky VSPackages](../extensibility/troubleshooting-vspackages.md)

## <a name="see-also"></a>Viz také
- [Balíčky VSPackage](../extensibility/internals/vspackages.md)
