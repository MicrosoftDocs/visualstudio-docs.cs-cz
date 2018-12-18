---
title: 'Postupy: instalace sady Visual Studio Tools for Office runtime redistributable'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio]
- installing Office development tools in Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 15e3c1b25d4834808fb17e596fcc7babe7dd969f
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255847"
---
# <a name="how-to-install-the-visual-studio-tools-for-office-runtime-redistributable"></a>Postupy: instalace sady Visual Studio Tools for Office runtime redistributable
  Visual Studio 2010 Tools for Office runtime musí být nainstalován na každém počítači, který spouští řešení, které jsou vytvořené pomocí nástroje Microsoft Office developer tools v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Modul runtime se nainstaluje automaticky při instalaci [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]a Microsoft Office. Další informace najdete v tématu [Visual Studio Tools for Office runtime instalace scénáře](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).  
  
 Je třeba postupovat podle pokynů ruční instalace níže v následujících situacích:  
  
-   Je potřeba nainstalovat [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] na serveru. Například chcete použít <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> třídy ke správě řešení na úrovni dokumentu na serveru.  
  
-   Potřebujete nainstalovat modul runtime na počítači, který již má všechny další požadavky pro řešení pro systém Office nainstalován.  
  
    > [!NOTE]  
    >  Musíte být správce na vývojovém počítači, aby instalaci rozhraní .NET Framework a [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
## <a name="to-install-the-visual-studio-tools-for-office-runtime"></a>K instalaci sady Visual Studio Tools for Office runtime  
  
1.  Nainstalujte [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější.  
  
    -   Ke stažení [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], najdete v části [rozhraní Microsoft .NET Framework 4 (Webová instalační služba)](http://go.microsoft.com/fwlink/?LinkId=178957).  
  
    -   Ke stažení [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)], najdete v části [rozhraní Microsoft .NET Framework 4 Client Profile (Webová instalační služba)](http://go.microsoft.com/fwlink/?LinkId=178958).  
  
    -   Ke stažení [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], najdete v části [rozhraní Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653).  
  
2.  Spustit *vstor_redist.exe* k instalaci [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
     Můžete stáhnout tyto soubory instalaci ze [Visual Studio 2010 Tools for Office runtime](http://go.microsoft.com/fwlink/?LinkId=140384). Požadavky na [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] shodovat s požadavky na rozhraní .NET Framework.  
  
     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Obsahuje jazykové sady. Pokud vaše instalace systému Windows je nastavena na jiný jazyk než anglický, můžete zobrazit zprávy runtime ve stejném jazyce, který používáte pro Windows. Podobně pokud koncoví uživatelé instalovat [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] a poté spusťte řešení v instalaci systému Windows, které jsou nastaveny na jiný jazyk než anglický, runtime zprávy se zobrazí ve stejném jazyce jako Windows. V některých případech může být nutné další jazykové sady. Například může být nutné další jazykové sady, pokud vaše kopie systému Windows používá více než jedna jazyková nastavení nebo přepnutí na jiný jazyk po jste již nainstalovali [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Můžete najít jazykové sady v [Microsoft Visual Studio 2010 Tools pro sadu Microsoft Office system (verze 4.0 runtime) language pack](http://go.microsoft.com/fwlink/?LinkId=140386).  
  
## <a name="see-also"></a>Viz také:  
 [Začínáme &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Konfigurace počítače pro vývoj řešení pro systém Office](../vsto/configuring-a-computer-to-develop-office-solutions.md)   
 [Postupy: Konfigurace počítače pro vývoj řešení pro systém Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)   
 [Postupy: Primární spolupracující sestavení Office instalace](../vsto/how-to-install-office-primary-interop-assemblies.md)   
 [Správa dokumentů na serveru s použitím třídy ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Nasazení řešení Office](../vsto/deploying-an-office-solution.md)  
  
  