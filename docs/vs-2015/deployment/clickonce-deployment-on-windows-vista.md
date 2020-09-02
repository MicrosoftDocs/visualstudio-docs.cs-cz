---
title: Nasazení ClickOnce v systému Windows Vista | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: e25f9da960b1de8acb1950b2bdd3ab7e61409f17
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675465"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Implementace ClickOnce v systému Windows Vista
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sestavování aplikací v aplikaci Visual Studio pro řízení uživatelských účtů (UAC) v systému Windows Vista obvykle generuje vložený manifest kódovaný jako binární data XML ve spustitelném souboru aplikace. Vzhledem k tomu, že aplikace modelu COM pro ClickOnce a bez registrace vyžadují externí manifest, aplikace Visual Studio vygeneruje soubor pro tyto typy projektů obsahující data nástroje řízení uživatelských účtů namísto vloženého manifestu. Ve výchozím nastavení aplikace Visual Studio používá informace ze souboru s názvem App. manifest pro generování externích informací o manifestu nástroje řízení uživatelských účtů (pro nasazení COM a bezplatné registrace modelu COM) nebo pro vložení do spustitelného souboru aplikace (pro všechny ostatní případy). Visual Studio poskytuje následující možnosti pro generování manifestu:  
  
- Použijte vložený manifest. Vloží data nástroje řízení uživatelských účtů do spustitelného souboru aplikace a spustí se jako normální uživatel.  
  
   Toto je výchozí nastavení (Pokud nepoužíváte ClickOnce). Toto nastavení bude podporovat obvyklý způsob, jakým aplikace Visual Studio funguje v systému Windows Vista; To znamená generování interního a externího manifestu pomocí `AsInvoker` .  
  
- Použijte externí manifest. Vygenerujte externí manifest pomocí App. manifest.  
  
   Tím se vytvoří pouze externí manifest s použitím informací v App. manifest. Když publikujete aplikaci pomocí technologie ClickOnce nebo bez registrace modelu COM, Visual Studio přidá do projektu aplikaci App. manifest a přidá tuto možnost.  
  
- Nepoužívejte žádný manifest. Vytvoření aplikace bez manifestu.  
  
   Tento přístup se také označuje jako *virtualizace*. Tato možnost slouží k zajištění kompatibility se stávajícími aplikacemi z dřívějších verzí sady Visual Studio.  
  
  Nové vlastnosti jsou k dispozici na stránce **aplikace** Návrháře projektu (pouze pro projekty jazyka Visual C#) a ve formátu souboru projektu MSBuild.  
  
  Všimněte si, že metoda pro konfiguraci generování manifestu nástroje řízení uživatelských účtů v integrovaném vývojovém prostředí sady Visual Studio se liší v závislosti na typu projektu (Visual C# a Visual Basic).  
  
  Informace o konfiguraci projektů v jazyce Visual C# pro generování manifestu naleznete v tématu [Stránka aplikace, Návrhář projektu (C#)](../ide/reference/application-page-project-designer-csharp.md).  
  
  Informace o konfiguraci Visual Basic projektů pro generování manifestu naleznete v tématu [Stránka aplikace, Návrhář projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
## <a name="see-also"></a>Viz také  
 [ClickOnce – zabezpečení a nasazení](../deployment/clickonce-security-and-deployment.md)   
 [Uživatelská oprávnění a Visual Studio](https://msdn.microsoft.com/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [Stránka aplikace, Návrhář projektu (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Stránka Aplikace, návrhář projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
