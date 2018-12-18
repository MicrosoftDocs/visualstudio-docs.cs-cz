---
title: Správa rozšíření VSPackages | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
caps.latest.revision: 36
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8cb96dfbdecd5182d328d425a209f52833ede23c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781592"
---
# <a name="managing-vspackages"></a>Správa rozšíření VSPackages
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ve většině případů nemusíte starat o správu rozšíření VSPackages, protože šablony projektů a položek registrovat a automaticky načíst balíček. Ale v některých případech budete muset naučit něco, aby správu balíčků.  
  
## <a name="using-the-experimental-instance"></a>Používáte-li experimentální instanci  
 Další informace o experimentální instanci najdete v tématu [experimentální instanci](../extensibility/the-experimental-instance.md).  
  
## <a name="registering-and-unregistering-vspackages"></a>Registrace a zrušení registrace rozšíření VSPackages  
 Jak vytvářet a rušit registraci rozšíření VSPackages a jinými typy rozšíření najdete v tématu [registrace a zrušení registrace rozšíření VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="loading-a-vspackage"></a>Načítání VSPackage  
 Rozšíření VSPackages lze nastavit na autoload Pokud konkrétní identifikátor GUID CMDUICONTEXT zapnutá. Další informace najdete v tématu [načítání rozšíření VSPackages](../extensibility/loading-vspackages.md).  
  
## <a name="using-asyncpackage-to-load-vspackages-in-the-background"></a>Použití AsyncPackage k načtení rozšíření VSPackages na pozadí  
 Třída AsyncPackage umožňuje balíček načítání ve vlákně na pozadí pro lepší odezvy uživatelského rozhraní v sadě Visual Studio. Další informace najdete v tématu [postupy: použití AsyncPackage k načtení rozšíření VSPackages na pozadí](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).  
  
## <a name="rule-based-ui-context-for-extensions"></a>Kontext založený na pravidlech uživatelského rozhraní pro rozšíření  
 Kontexty uživatelského rozhraní založeného na pravidlech umožňuje autorům rozšíření určit přesné podmínky, za kterých se aktivuje kontextu uživatelského rozhraní a načíst přidružené balíčky VSPackages. Další informace najdete v tématu [postupy: použití pravidla na základě kontextu uživatelského rozhraní pro rozšíření sady Visual Studio](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).  
  
## <a name="troubleshooting-vspackages"></a>Řešení potíží s rozšířením VSPackages  
 Přečtěte si techniky pro řešení potíží s rozšířením VSPackages, který se nenačtou nebo dochází k chybám: [řešení potíží s rozšířením VSPackages](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>Viz také  
 [Balíčky VSPackage](../extensibility/internals/vspackages.md)

