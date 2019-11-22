---
title: Sady VSPackage a Managed Package Framework | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- managed package framework
- VSPackages, managed package framework
- managed VSPackages, managed package framework
ms.assetid: e8d80e0f-6b5b-4baf-a7df-59fd808c60cd
caps.latest.revision: 16
manager: jillfra
ms.openlocfilehash: 84fb41bfc80415535ca41d6b1a8c9dcf47124c7a
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298237"
---
# <a name="vspackages-and-the-managed-package-framework"></a>Sady VSPackage a Managed Package Framework
Čas vývoje můžete zkrátit vytvořením VSPackage s třídami "MPF" (Managed Package Framework) místo pomocí tříd typu COM Interop.  
  
 Existují dva způsoby, jak vytvořit spravovaný VSPackage:  
  
- Použití šablony projektu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] balíčku  
  
     Další informace naleznete v tématu [Návod: vytvoření příkazu nabídky pomocí šablony balíčku sady Visual Studio](https://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de).  
  
- Sestavení balíčku VSPackage bez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] šablony projektu  
  
     Můžete například zkopírovat ukázkový VSPackage a změnit identifikátory GUID a názvy. 
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Spravované třídy architektury balíčku](../misc/managed-package-framework-classes.md)  
 Popisuje a vypíše obory názvů a soubory DLL třídy MPF.  
  
## <a name="related-sections"></a>Související oddíly  
 [Návod: vytvoření příkazu nabídky pomocí šablony balíčku sady Visual Studio](https://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de)  
 Vysvětluje, jak vytvořit spravovaný VSPackage.  
  
 [Spravované VSPackage](../misc/managed-vspackages.md)  
 Zavádí aspekty VSPackage, které se vztahují ke spravovanému kódu.