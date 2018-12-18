---
title: ClickOnce – nasazení v systému Windows Vista | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- UAC manifest generation
- ClickOnce deployment, Windows
- manifest generation
- Windows, ClickOnce deployment
ms.assetid: b21a0ebc-0ff6-4f49-8993-7d1ad3f8cac2
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: a0b8b4b5cff478a2dbe03f3f72115da3c0696c4e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49852051"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Implementace ClickOnce v systému Windows Vista
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vytváření aplikací v sadě Visual Studio pro řízení uživatelských účtů (UAC) v systému Windows Vista obvykle generuje vloženého manifestu kódovaný jako binární data XML do spustitelného souboru aplikace. Vzhledem k tomu, že aplikace ClickOnce a modelu COM bez registrace vyžadují externím manifestem, Visual Studio generuje soubor pro tyto typy projektů, které obsahují data nástroje Řízení uživatelských účtů namísto vloženého manifestu. Ve výchozím nastavení Visual Studio používá informace ze souboru s názvem app.manifest Generovat externí informace o manifestu nástroje Řízení uživatelských účtů (pro nasazení ClickOnce a modelu COM bez registrace) nebo ji vložit do spustitelného souboru aplikace (pro všechny ostatní případy). Visual Studio poskytuje následující možnosti pro generování manifestu:  
  
- Použití vloženého manifestu. Vložit data nástroje Řízení uživatelských účtů ve spustitelném souboru aplikace a spustit jako běžný uživatel.  
  
   Toto je výchozí nastavení (Pokud nechcete použít ClickOnce). Toto nastavení bude podporovat obvyklým způsobem, ve kterém aplikace Visual Studio pracuje na Windows Vista; To znamená, generování interních a externích manifestu pomocí `AsInvoker`.  
  
- Použijte externí manifest. Generovat manifest externí pomocí app.manifest.  
  
   Tím se vygeneruje pouze externím manifestem podle informací uvedených v app.manifest. Při publikování aplikace pomocí technologie ClickOnce nebo COM bez registrace, Visual Studio přidá app.manifest do projektu a přidá tuto možnost.  
  
- Použít žádný manifest. Vytvořte aplikaci bez manifestu.  
  
   Tento přístup se také označuje jako *virtualizace*. Tuto možnost použijte, pokud z důvodu kompatibility se stávajícími aplikacemi z předchozích verzí sady Visual Studio.  
  
  Nové vlastnosti jsou k dispozici na **aplikace** stránky Návrháře projektu (Visual C# pouze pro projekty) a ve formátu souboru projektu MSBuild.  
  
  Všimněte si, že metoda konfigurace generování manifestu nástroje Řízení uživatelských účtů v integrovaném vývojovém prostředí sady Visual Studio se liší v závislosti na typu projektu (Visual C# a Visual Basic).  
  
  Informace o konfiguraci nástroje pro generování manifestu projekty Visual C# najdete v tématu [stránka aplikace, Návrhář projektu (C#)](../ide/reference/application-page-project-designer-csharp.md).  
  
  Informace o konfiguraci projektů jazyka Visual Basic pro generování manifestu naleznete v tématu [stránka aplikace, Návrhář projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
## <a name="see-also"></a>Viz také  
 [ClickOnce – zabezpečení a nasazení](../deployment/clickonce-security-and-deployment.md)   
 [Uživatelská oprávnění a sada Visual Studio](http://msdn.microsoft.com/en-us/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [Stránka aplikace, Návrhář projektu (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Stránka Aplikace, Návrhář projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)



