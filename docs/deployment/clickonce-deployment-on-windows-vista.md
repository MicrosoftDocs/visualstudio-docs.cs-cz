---
title: Nasazení ClickOnce v systému Windows Vista | Microsoft Docs
description: Přečtěte si, jak Visual Studio generuje externí manifest řízení uživatelských účtů pro ClickOnce a Registration-Free aplikace COM, které vyžadují externí manifest.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: c2e09225339a87c55c31d27d26b129e199385e99
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383076"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Nasazení ClickOnce v systému Windows Vista

Sestavování aplikací v aplikaci Visual Studio pro řízení uživatelských účtů (UAC) v systému Windows Vista obvykle generuje vložený manifest kódovaný jako binární data XML ve spustitelném souboru aplikace.  ClickOnce a Registration-Free aplikace modelu COM vyžadují externí manifest, takže Visual Studio vygeneruje soubor pro tyto projekty obsahující data nástroje řízení uživatelských účtů namísto vloženého manifestu. Pro ClickOnce a Registration-Free nasazení modelu COM používá Visual Studio informace ze souboru s názvem *App. manifest* pro generování externích informací o manifestu nástroje řízení uživatelských účtů. Ve všech ostatních případech Visual Studio vloží data nástroje řízení uživatelských účtů do spustitelného souboru aplikace.

Visual Studio poskytuje následující možnosti pro generování manifestu:

- Použijte vložený manifest. Vloží data nástroje řízení uživatelských účtů do spustitelného souboru aplikace a spustí se jako normální uživatel.

   Toto je výchozí nastavení (Pokud nepoužíváte ClickOnce). Toto nastavení podporuje obvyklý způsob, jakým aplikace Visual Studio funguje v systému Windows Vista, a to s využitím interního i externího manifestu `AsInvoker` .

- Použijte externí manifest. Vygenerujte externí manifest pomocí *App. manifest*.

   Tím se vytvoří pouze externí manifest s použitím informací v *App. manifest*. Když publikujete aplikaci pomocí technologie ClickOnce nebo Registration-Free COM, Visual Studio přidá do projektu *aplikaci App. manifest* a pak přidá tuto možnost.

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