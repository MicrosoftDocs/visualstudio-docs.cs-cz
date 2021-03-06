---
title: 'Postupy: instalace primárních sestavení vzájemné spolupráce pro systém Office'
description: Naučte se, jak při instalaci Office nainstalovat primární spolupracující sestavení (PIA) systém Microsoft Office.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies [Office development in Visual Studio], installing
- Office primary interop assemblies, installing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 432b2a74eb7ea4753cd110956c9dc9313e1a5d6e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934816"
---
# <a name="how-to-install-office-primary-interop-assemblies"></a>Postupy: instalace primárních sestavení vzájemné spolupráce pro systém Office
  Při instalaci Office nainstalujte systém Microsoft Office primární spolupracující sestavení (PIA).

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-install-the-pias-when-you-install-office"></a>Instalace PIA při instalaci Office

1. Ujistěte se, že máte verzi .NET Framework, která není starší než 2,0.

2. Nainstalujte systém Microsoft Office a ujistěte se, že je pro aplikace, které chcete zvětšit, vybraná funkce **Podpora programovatelnosti rozhraní .NET** (Tato funkce je součástí výchozí instalace).

    > [!WARNING]
    > Ve výchozím nastavení jsou ve vašem řešení při sestavování služby PIA vloženy do vašeho řešení, takže nemusíte distribuovat PIA uživatelům jako předpoklady pro používání doplňku VSTO nebo přizpůsobení.

## <a name="see-also"></a>Viz také
- [Sestavení primární spolupráce pro Office](../vsto/office-primary-interop-assemblies.md)
- [Postupy: cílení aplikací Office prostřednictvím primárních sestavení spolupráce](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Postupy: Konfigurace počítače pro vývoj řešení pro systém Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Postupy: instalace redistribuovatelného prostředí Visual Studio Tools for Office runtime](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Přehled vývoje řešení pro systém Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Začněte &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
