---
title: Nasazování požadavků pro 64 – bitové aplikace | Microsoft Docs
description: Přečtěte si o prodaných distribuovatelných, které můžete použít jako předpoklady pro nasazení aplikace ClickOnce na 64 bitů platformy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [Visual Studio], 64-bit
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- 64-bit applications [Visual Studio]
ms.assetid: 87399e20-5510-41e4-b5b7-4a87c5773f21
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: abc44c679e65cc49f6a491e9435fdaeffed5e9c8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893942"
---
# <a name="deploy-prerequisites-for-64-bit-applications"></a>Nasazení nezbytných součástí pro 64bitové aplikace
Nasazení ClickOnce podporuje instalaci aplikací na 64 platforem. Cílové platformy jsou **x86** pro 32 platforem, **x64** pro počítače, které podporují INSTRUKČNÍ sady AMD64 a EM64T a **Itanium** pro procesor s procesorem Itanium pro 64.

## <a name="prerequisites"></a>Požadavky
 V následující tabulce jsou uvedeny distribuovatelné součásti, které můžete použít jako předpoklady pro instalaci vaší 64 bitové aplikace.

 Pokud vyberete požadovanou součást, která nemá 64 bitové součásti, může se zobrazit upozornění, že vybrané balíčky nejsou k dispozici pro 64 platformu.

| Distribuovatelné součásti | Podpora x64 | Podpora IA64 |
| - |-------------|--------------|
| [!INCLUDE[vsto_runtime](../deployment/includes/vsto_runtime_md.md)] | Ano | Ne |
| Knihovny runtime Visual C++ 2010 (IA64) | Ne | Ano |
| Běhové knihovny Visual C++ 2010 (x64) | Ano | Ne |
| Microsoft .NET Framework 4 (x86 a x64) | Ano | |
| Profil klienta Microsoft .NET Framework 4 (x86 a x64) | Ano | |

## <a name="see-also"></a>Viz také
- [Nasazení aplikací, služeb a komponent](../deployment/deploying-applications-services-and-components.md)
- [Postupy: Instalace předpokladů s aplikací ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [64 – bitové aplikace](/dotnet/framework/64-bit-apps)