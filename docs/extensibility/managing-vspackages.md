---
title: Správa rozšíření VSPackages | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 14aa17f4692857d650cb3bc9fe1a3498fc4f147a
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639556"
---
# <a name="manage-vspackages"></a>Správa rozšíření VSPackages
Ve většině případů nemusíte starat o správu rozšíření VSPackages, protože šablony projektů a položek registrovat a automaticky načíst balíček. Ale v některých případech budete muset naučit něco, aby správu balíčků.  
  
## <a name="use-the-experimental-instance"></a>Použít experimentální instance  
 Další informace o experimentální instanci najdete v tématu [experimentální instanci](../extensibility/the-experimental-instance.md).  
  
## <a name="register-and-unregister-vspackages"></a>Registrace a zrušení registrace rozšíření VSPackages  
 Jak vytvářet a rušit registraci rozšíření VSPackages a jinými typy rozšíření najdete v tématu [vytvářet a rušit registraci rozšíření VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="load-a-vspackage"></a>Načíst VSPackage  
 Rozšíření VSPackages lze nastavit na autoload Pokud konkrétní identifikátor GUID CMDUICONTEXT zapnutá. Další informace najdete v tématu [načtení rozšíření VSPackages](../extensibility/loading-vspackages.md).  
  
## <a name="use-asyncpackage-to-load-vspackages-in-the-background"></a>Použití AsyncPackage k načtení rozšíření VSPackages na pozadí  
 `AsyncPackage` Třída umožňuje načítání balíčku na vlákně na pozadí pro lepší odezvy uživatelského rozhraní v sadě Visual Studio. Další informace najdete v tématu [postupy: použití AsyncPackage k načtení rozšíření VSPackages na pozadí](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).  
  
## <a name="rule-based-ui-context-for-extensions"></a>Podle pravidel kontextu uživatelského rozhraní pro rozšíření  
 Kontexty uživatelského rozhraní založeného na pravidlech umožňuje autorům rozšíření určit přesné podmínky, za kterých se aktivuje kontextu uživatelského rozhraní a načíst přidružené balíčky VSPackages. Další informace najdete v tématu [postupy: použití založený na pravidlech kontextu uživatelského rozhraní pro rozšíření sady Visual Studio](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).  
  
## <a name="diagnose-extension-performance"></a>Diagnostika výkonu rozšíření  
Rozšíření může ovlivnit výkon zatížení při spuštění a řešení. Zjistěte, jak se počítá dopadu rozšíření sady Visual Studio a jak se dají analyzovat místně Pokud chcete otestovat, jestli rozšíření se může zobrazit jako výkon vliv na rozšíření. Další informace najdete v tématu [postupy: Diagnostika výkonu rozšíření](how-to-diagnose-extension-performance.md). 
  
## <a name="troubleshoot-vspackages"></a>Řešení potíží s rozšířením VSPackages  
 Přečtěte si techniky pro řešení potíží s rozšířením VSPackages, který se nenačtou nebo dochází k chybám: [řešení potíží s rozšířením VSPackages](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>Viz také:  
 [Balíčky VSPackage](../extensibility/internals/vspackages.md)