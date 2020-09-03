---
title: Konfigurace počítače pro vývoj řešení pro systém Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, installing tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7a0304c217599e790b8cfa9e738245927336470e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "88801838"
---
# <a name="configure-a-computer-to-develop-office-solutions"></a>Konfigurace počítače pro vývoj řešení pro systém Office

Pokud chcete vytvořit doplňky a přizpůsobení VSTO pro systém Microsoft Office, nainstalujte podporovanou verzi sady Visual Studio, .NET Framework a systém Microsoft Office.

|Software|Podporované verze|
|--------------|------------------------|
|Visual Studio 2017| Libovolná edice s úlohou **vývoje pro Office/SharePoint** .|
|.NET Framework|-.NET Framework 4 nebo novější.|
|Microsoft Office|<ul><li>Libovolná edice sady Office, včetně Microsoft 365ch aplikací pro podniky</li><li>Kterákoli z následujících samostatných aplikací:<br /><br /> <ul><li>Excel</li><li>InfoPath (pouze Office 2013 a Office 2010)</li><li>Outlook</li><li>PowerPoint</li><li>Project</li><li>Visio</li><li>Word</li></ul></li></ul><br /> Jazyk Visual Basic for Application (VBA) musí být nainstalovaný jako součást Office. **Důležité informace:** Verze aplikací Office 2010 typu Klikni a spusť nejsou podporovány.|

Podrobné pokyny k instalaci najdete v tématu [Postupy: Konfigurace počítače pro vývoj řešení pro systém Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).

## <a name="if-project-templates-dont-appear-or-they-dont-work-in-visual-studio"></a>Pokud se šablony projektu nezobrazí nebo nefungují v aplikaci Visual Studio

Pokud nainstalujete podporovanou verzi sady Visual Studio, .NET Framework a systém Microsoft Office, ale šablony projektů Office se nezobrazí v dialogovém okně **Nový projekt** sady Visual Studio nebo se zobrazí chyba při pokusu o její použití, ověřte následující:

- Ujistěte se, že máte v počítači nainstalované vývojové nástroje systém Microsoft Office.

     Sady Office Developer Tools jsou volitelnou součástí sady Visual Studio, ale jsou nainstalovány automaticky spolu se sadou Visual Studio. Pokud přizpůsobíte instalaci sady Visual Studio tak, že určíte, které funkce se mají nainstalovat, nezapomeňte při instalaci nástrojů zvolit **systém Microsoft Office vývojářské nástroje** .

     Chcete-li se ujistit, že jsou tyto nástroje nainstalovány, spusťte instalační program sady Visual Studio a klikněte na tlačítko **Upravit** . Zaškrtněte políčko **systém Microsoft Office vývojářské nástroje** a pak klikněte na tlačítko **aktualizovat** .

- Ujistěte se, že nepoužíváte verzi Office, která byla doručena kliknutím na spustit. Informace o [tom, jak ověřit, zda je aplikace Outlook aplikace typu Klikni a spusť v počítači](/previous-versions/office/developer/office-2010/ff864733(v=office.14)).

- Ujistěte se, že používáte jenom jednu verzi systém Microsoft Office.

Pokud budete mít i nadále problémy, přečtěte si [Další informace o podpoře pro chyby v řešeních pro systém Office](../vsto/additional-support-for-errors-in-office-solutions.md).

## <a name="see-also"></a>Viz také
- [Začněte &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Postupy: Konfigurace počítače pro vývoj řešení pro systém Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Postupy: instalace redistribuovatelného prostředí Visual Studio Tools for Office runtime](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Postupy: instalace primárních sestavení vzájemné spolupráce pro systém Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
- [Dostupné funkce podle aplikace systému Office a typu projektu](../vsto/features-available-by-office-application-and-project-type.md)