---
title: Konfigurace počítače pro vývoj řešení pro systém Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, installing tools
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 19c7e012775ff1a761b5c267f05b8f7ff250d5c6
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672223"
---
# <a name="configure-a-computer-to-develop-office-solutions"></a>Konfigurace počítače pro vývoj řešení pro systém Office

K vytvoření doplňků VSTO a vlastní nastavení pro Microsoft Office, nainstalujte podporovanou verzi sady Visual Studio, .NET Framework a Microsoft Office.

|Software|Podporované verze|
|--------------|------------------------|
|Visual Studio 2017| Libovolná edice s **vývoj pro Office/SharePoint** pracovního vytížení.|
|.NET Framework|-Rozhraní .NET Framework 4 nebo novější.|
|Aplikace Microsoft Office|<ul><li>Jakákoli edice sady Office, včetně Office Professional Plus pro Office 365.</li><li>Některé z následujících samostatných aplikací:<br /><br /> <ul><li>Excel</li><li>InfoPath (Office 2013 a Office 2010 pouze)</li><li>Outlook</li><li>PowerPoint</li><li>Projekt</li><li>Visio</li><li>Word</li></ul></li></ul><br /> Visual Basic for Applications (VBA) musí být nainstalována jako součást sady Office. **Důležité:** klikněte na tlačítko spustit verze aplikace systému Office 2010 nejsou podporované.|

Podrobný postup instalace najdete v části [postupy: Konfigurace počítače pro vývoj řešení pro systém Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).

## <a name="if-project-templates-dont-appear-or-they-dont-work-in-visual-studio"></a>Pokud šablony projektů nejsou zobrazeny nebo nefungují v sadě Visual Studio

Je-li nainstalovat podporovanou verzi sady Visual Studio, .NET Framework a Microsoft Office, ale šablony projektů pro Office buď nejsou zobrazeny v sadě Visual Studio **nový projekt** dialogové okno, nebo k chybě při pokusu o použití, Zkontrolujte následující:

- Ujistěte se, že máte v počítači nainstalována aplikace Microsoft Office developer tools.

     Office developer tools jsou volitelnou součástí aplikace Visual Studio, ale jsou automaticky nainstalovány spolu s Visual Studio. Pokud přizpůsobíte instalaci sady Visual Studio určením funkcí, které chcete nainstalovat, ujistěte se, že zvolíte **Microsoft Office Developer Tools** během instalace k instalaci nástroje.

     Pokud chcete mít jistotu, že tyto nástroje jsou nainstalovány, spusťte instalační program sady Visual Studio a zvolte **změnit** tlačítko. Vyberte **Microsoft Office Developer Tools** zaškrtněte políčko a klikněte na tlačítko **aktualizace** tlačítko.

- Ujistěte se, že nejsou spuštěné na verzi Office, která byla odeslaná klikněte na tlačítko spustit. Zobrazit [jak: Ověřte, zda je aplikace Outlook aplikace klikněte na tlačítko spustit na počítači](/previous-versions/office/developer/office-2010/ff864733(v=office.14)).

- Ujistěte se, že používáte pouze jednu verzi Microsoft Office.

Pokud budete nadále docházet k potížím, přečtěte si téma [další podporu pro chyby v řešeních pro systém Office](../vsto/additional-support-for-errors-in-office-solutions.md).

## <a name="see-also"></a>Viz také:

[Začínáme &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)  
[Postupy: Konfigurace počítače pro vývoj řešení pro systém Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)  
[Postupy: instalace aplikace Visual Studio Tools for Office runtime redistributable](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)  
[Postupy: instalace Office primárních sestavení vzájemné spolupráce](../vsto/how-to-install-office-primary-interop-assemblies.md)  
[Zadejte dostupné funkce podle aplikace systému Office a projektu](../vsto/features-available-by-office-application-and-project-type.md)
