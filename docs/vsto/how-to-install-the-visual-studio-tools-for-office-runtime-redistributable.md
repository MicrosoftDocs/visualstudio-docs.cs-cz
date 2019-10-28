---
title: 'Postupy: instalace redistribuovatelného prostředí Visual Studio Tools for Office runtime'
titleSuffix: ''
ms.custom: seodec18
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio]
- installing Office development tools in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 801486e7c0abfa2cb91f7fb7237cf3a48e8bc916
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985909"
---
# <a name="how-to-install-the-visual-studio-tools-for-office-runtime-redistributable"></a>Postupy: instalace redistribuovatelného prostředí Visual Studio Tools for Office runtime
  Nástroje Visual Studio 2010 Tools for Office runtime musí být nainstalované na každém počítači, na kterém běží řešení vytvořená pomocí nástrojů systém Microsoft Office Developer Tools v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Modul runtime se nainstaluje automaticky při instalaci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]a systém Microsoft Office. Další informace najdete v tématu [scénáře instalace modulu runtime Visual Studio Tools for Office](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).

[!include[Add-ins note](includes/addinsnote.md)]

 Možná budete muset postupovat podle pokynů k ruční instalaci v následujících situacích:

- [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] musíte nainstalovat na server. Například chcete použít třídu <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> ke správě řešení na úrovni dokumentu na serveru.

- Je potřeba nainstalovat modul runtime na počítač, který už má nainstalované všechny ostatní předpoklady pro řešení Office.

    > [!NOTE]
    > Chcete-li nainstalovat .NET Framework a [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], musíte být správcem vývojového počítače.

## <a name="to-install-the-visual-studio-tools-for-office-runtime"></a>Instalace modulu runtime Visual Studio Tools for Office

1. Nainstalujte [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější.

    - Pokud chcete stáhnout [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], přečtěte si článek [Microsoft .NET Framework 4 (Webová instalační služba)](https://www.microsoft.com/download/details.aspx?id=17851).

    - Pokud si chcete stáhnout [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)], přečtěte si článek [Profil klienta Microsoft .NET Framework 4 (Webová instalační služba)](https://www.microsoft.com/download/details.aspx?id=17113).

    - Pokud si chcete stáhnout [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], přečtěte si článek [Microsoft .NET Framework 4,5](https://www.microsoft.com/download/details.aspx?id=30653).

2. Spusťte *vstor_redist. exe* a nainstalujte [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].

     Tyto instalační soubory si můžete stáhnout z [nástroje Visual Studio 2010 Tools for Office runtime](https://www.microsoft.com/download/details.aspx?id=56961). Požadavky na [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] odpovídají požadavkům pro .NET Framework.

     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] zahrnuje jazykové sady. Pokud je vaše instalace systému Windows nastavená na jiný jazyk než angličtinu, můžete zobrazit zprávy za běhu ve stejném jazyce, který používáte pro Windows. Podobně platí, že pokud koncoví uživatelé nainstalují [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] a pak svá řešení spouští na instalacích systému Windows, které jsou nastavené na jiný jazyk než angličtinu, budou se zprávy za běhu zobrazovat ve stejném jazyce jako Windows. V některých případech možná budete potřebovat další jazykové sady. Můžete například potřebovat další jazykové sady, pokud vaše kopie systému Windows používá více než jedno nastavení jazyka nebo po instalaci [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]přepnete na jiný jazyk. Jazykové sady můžete najít v [Microsoft Visual Studio 2010 nástrojích pro systém Microsoft Office systému (verze 4,0 Runtime) pro jazykovou sadu](https://www.microsoft.com/download/details.aspx?id=54246).

## <a name="see-also"></a>Viz také:
- [Začínáme &#40;s vývojem pro Office v sadě Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Konfigurace počítače pro vývoj řešení pro systém Office](../vsto/configuring-a-computer-to-develop-office-solutions.md)
- [Postupy: Konfigurace počítače pro vývoj řešení pro systém Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Postupy: instalace primárních sestavení vzájemné spolupráce pro systém Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
- [Správa dokumentů na serveru pomocí třídy ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Nasazení řešení pro systém Office](../vsto/deploying-an-office-solution.md)
