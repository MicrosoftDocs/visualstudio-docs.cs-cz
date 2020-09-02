---
title: Správa VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0b56ab490342cfbda9c16408aa0937abd80728c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194375"
---
# <a name="managing-vspackages"></a>Správa rozšíření VSPackages
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ve většině případů se nemusíte starat o správu VSPackage, protože šablony projektů a položek registrují a automaticky načítají balíček. V některých případech se ale může vyžadovat, abyste se o správě balíčku dozvěděli trochu víc.  
  
## <a name="using-the-experimental-instance"></a>Použití experimentální instance  
 Další informace o experimentální instanci naleznete v [experimentální instanci](../extensibility/the-experimental-instance.md).  
  
## <a name="registering-and-unregistering-vspackages"></a>Registrace a zrušení registrace rozšíření VSPackages  
 Chcete-li zjistit, jak registrovat a odregistrovat sady VSPackage a jiné typy rozšíření, přečtěte si téma [registrace a zrušení registrace VSPackage](../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="loading-a-vspackage"></a>Načítání VSPackage  
 Sady VSPackage lze nastavit na automatické načtení, pokud je zapnut konkrétní CMDUICONTEXT identifikátor GUID. Další informace najdete v tématu [načítání VSPackage](../extensibility/loading-vspackages.md).  
  
## <a name="using-asyncpackage-to-load-vspackages-in-the-background"></a>Načtení VSPackage na pozadí pomocí AsyncPackage  
 Třída AsyncPackage umožňuje načtení balíčku ve vlákně na pozadí pro lepší rychlost odezvy uživatelského rozhraní v aplikaci Visual Studio. Další informace naleznete v tématu [How to: use AsyncPackage (načíst sady VSPackage](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md)) na pozadí.  
  
## <a name="rule-based-ui-context-for-extensions"></a>Kontext uživatelského rozhraní založeného na pravidlech pro rozšíření  
 Kontexty uživatelského rozhraní založeného na pravidlech umožňují autorům rozšíření definovat přesné podmínky, za kterých je kontext uživatelského rozhraní aktivovaný a které přidružené sady VSPackage jsou načtené. Další informace najdete v tématu [Postupy: použití kontextu uživatelského rozhraní založeného na pravidlech pro rozšíření sady Visual Studio](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).  
  
## <a name="troubleshooting-vspackages"></a>Řešení potíží s rozšířením VSPackages  
 Přečtěte si postupy pro řešení potíží s VSPackage, které se nečtou nebo dochází k chybám: [řešení problémů VSPackage](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>Viz také  
 [Balíčky VSPackage](../extensibility/internals/vspackages.md)
