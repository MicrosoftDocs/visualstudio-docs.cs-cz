---
title: 'Postupy: instalace redistribuovatelného prostředí Visual Studio Tools for Office runtime'
titleSuffix: ''
ms.custom: seodec18
ms.date: 08/14/2019
ms.topic: how-to
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
ms.openlocfilehash: ef71de75be5977ab80cbdd85448daa5de381c077
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547222"
---
# <a name="how-to-install-the-visual-studio-tools-for-office-runtime-redistributable"></a>Postupy: instalace redistribuovatelného prostředí Visual Studio Tools for Office runtime
  Nástroje Visual Studio 2010 Tools for Office runtime musí být nainstalované na každém počítači, na kterém běží řešení vytvořená pomocí nástrojů systém Microsoft Office Developer Tools v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Modul runtime se nainstaluje automaticky při instalaci nástroje [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] a systém Microsoft Office. Další informace najdete v tématu [scénáře instalace modulu runtime Visual Studio Tools for Office](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).

[!include[Add-ins note](includes/addinsnote.md)]

 Možná budete muset postupovat podle pokynů k ruční instalaci v následujících situacích:

- Musíte nainstalovat [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] na server. Například chcete použít <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> třídu ke správě řešení na úrovni dokumentu na serveru.

- Je potřeba nainstalovat modul runtime na počítač, který už má nainstalované všechny ostatní předpoklady pro řešení Office.

    > [!NOTE]
    > Abyste mohli nainstalovat .NET Framework a, musíte být správcem vývojového počítače [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

## <a name="to-install-the-visual-studio-tools-for-office-runtime"></a>Instalace modulu runtime Visual Studio Tools for Office

1. Nainstalujte [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější.

    - Pokud si chcete stáhnout [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , přečtěte si článek [Microsoft .NET Framework 4 (Webová instalační služba)](https://www.microsoft.com/download/details.aspx?id=17851).

    - Pokud si chcete stáhnout [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] , přečtěte si článek [Profil klienta Microsoft .NET Framework 4 (Webová instalační služba)](https://www.microsoft.com/download/details.aspx?id=17113).

    - Informace o stažení [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] najdete v tématu [Microsoft .NET Framework 4,5](https://www.microsoft.com/download/details.aspx?id=30653).

2. Spusťte *vstor_redist.exe* pro instalaci [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

     Tyto instalační soubory si můžete stáhnout z [nástroje Visual Studio 2010 Tools for Office runtime](https://www.microsoft.com/download/details.aspx?id=56961). Předpoklady pro [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] odpovídající požadavky pro .NET Framework.

     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Zahrnuje jazykové sady. Pokud je vaše instalace systému Windows nastavená na jiný jazyk než angličtinu, můžete zobrazit zprávy za běhu ve stejném jazyce, který používáte pro Windows. Podobně platí, že pokud koncoví uživatelé nainstalují [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] a pak spouštějí vaše řešení na instalacích systému Windows, které jsou nastaveny na jiný jazyk než angličtinu, budou se zprávy za běhu zobrazovat ve stejném jazyce jako Windows. V některých případech možná budete potřebovat další jazykové sady. Můžete například potřebovat další jazykové sady, pokud vaše kopie systému Windows používá více než jedno nastavení jazyka nebo pokud jste již nainstalovali sadu, jste přepnuli na jiný jazyk [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Jazykové sady můžete najít v [Microsoft Visual Studio 2010 nástrojích pro systém Microsoft Office systému (verze 4,0 Runtime) pro jazykovou sadu](https://www.microsoft.com/download/details.aspx?id=54246).

## <a name="see-also"></a>Viz také
- [Začněte &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Konfigurace počítače pro vývoj řešení pro systém Office](../vsto/configuring-a-computer-to-develop-office-solutions.md)
- [Postupy: Konfigurace počítače pro vývoj řešení pro systém Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Postupy: instalace primárních sestavení vzájemné spolupráce pro systém Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
- [Správa dokumentů na serveru pomocí třídy ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Nasazení řešení pro systém Office](../vsto/deploying-an-office-solution.md)
