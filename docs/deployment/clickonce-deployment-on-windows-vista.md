---
title: Nasazení ClickOnce v systému Windows Vista | Microsoft Docs
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b76804eb8c06acbcdeac017108773056ee38338
ms.sourcegitcommit: 1803a67b516f67b209d8f4cf147314e604ef1927
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2020
ms.locfileid: "89641495"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Nasazení ClickOnce v systému Windows Vista

Sestavování aplikací v aplikaci Visual Studio pro řízení uživatelských účtů (UAC) v systému Windows Vista obvykle generuje vložený manifest kódovaný jako binární data XML ve spustitelném souboru aplikace.  ClickOnce a aplikace COM bez registrace vyžadují externí manifest, takže Visual Studio vygeneruje soubor pro tyto projekty obsahující data UAC místo vloženého manifestu. Pro nasazení modelu COM pro ClickOnce a bezplatné registrace používá Visual Studio informace ze souboru s názvem *App. manifest* pro generování externích informací o manifestu nástroje řízení uživatelských účtů. Ve všech ostatních případech Visual Studio vloží data nástroje řízení uživatelských účtů do spustitelného souboru aplikace.

Visual Studio poskytuje následující možnosti pro generování manifestu:

- Použijte vložený manifest. Vloží data nástroje řízení uživatelských účtů do spustitelného souboru aplikace a spustí se jako normální uživatel.

   Toto je výchozí nastavení (Pokud nepoužíváte ClickOnce). Toto nastavení podporuje obvyklý způsob, jakým aplikace Visual Studio funguje v systému Windows Vista, a to s využitím interního i externího manifestu `AsInvoker` .

- Použijte externí manifest. Vygenerujte externí manifest pomocí *App. manifest*.

   Tím se vytvoří pouze externí manifest s použitím informací v *App. manifest*. Když publikujete aplikaci pomocí technologie ClickOnce nebo bez registrace modelu COM, Visual Studio přidá *aplikaci App. manifest* do projektu a pak přidá tuto možnost.

- Nepoužívejte žádný manifest. Vytvoření aplikace bez manifestu.

   Tento přístup se také označuje jako *virtualizace*. Tato možnost slouží k zajištění kompatibility se stávajícími aplikacemi z dřívějších verzí sady Visual Studio.

  Nové vlastnosti jsou k dispozici na stránce **aplikace** Návrháře projektu (pouze pro projekty jazyka Visual C#) a ve formátu souboru projektu MSBuild.

  Metoda Konfigurace vytváření manifestu nástroje řízení uživatelských účtů v integrovaném vývojovém prostředí sady Visual Studio se liší v závislosti na typu projektu (Visual C# nebo Visual Basic).

  * Informace o konfiguraci projektů v jazyce Visual C# pro generování manifestu naleznete v tématu [Stránka aplikace, Návrhář projektu (C#)](../ide/reference/application-page-project-designer-csharp.md).

  * Informace o konfiguraci Visual Basic projektů pro generování manifestu naleznete v tématu [Stránka aplikace, Návrhář projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).

## <a name="see-also"></a>Viz také
- [Zabezpečení a nasazení ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Uživatelská oprávnění a Visual Studio](/previous-versions/ms165100(v=vs.100))
- [Stránka Aplikace, návrhář projektu (C#)](../ide/reference/application-page-project-designer-csharp.md)
- [Stránka Aplikace, návrhář projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)