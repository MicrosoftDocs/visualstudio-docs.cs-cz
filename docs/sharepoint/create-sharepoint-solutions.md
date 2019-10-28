---
title: Vytváření řešení SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e1e5be38d0d44912052466162abaaa496c608d27
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2019
ms.locfileid: "72981300"
---
# <a name="create-sharepoint-solutions"></a>Vytváření řešení pro SharePoint
  Můžete vytvářet aplikace SharePoint v aplikaci Visual Studio jako alternativu k jejich vytváření v Návrháři služby SharePoint. Visual Studio podporuje rychlý vývoj pro SharePoint poskytnutím takových funkcí jako pokročilých ladicích nástrojů, IntelliSense, dokončování příkazů a šablon projektů. Visual Studio také využívá výhod rozšířených nástrojů a jazyků založených na .NET Framework. Projekty služby SharePoint můžete vyvíjet pomocí Visual Basic nebo vizuálu C#a můžete vyvíjet aplikace pro projekty služby SharePoint pomocí JavaScriptu.

 Informace o SharePoint 2013 a doplňkůch pro SharePoint najdete v tématu [sharepoint 2013](https://products.office.com/previous-versions/microsoft-sharepoint-2013) a [sestavování aplikací pro službu SharePoint](/sharepoint/dev/sp-add-ins/sharepoint-add-ins).

> [!NOTE]
> Zjistěte, jak pomocí nového [modelu doplňku pro SharePoint](/sharepoint/dev/sp-add-ins/sharepoint-add-ins) rozšíříte možnosti SharePointu pro vaše uživatele. Tyto doplňky mají velmi malé nároky ve srovnání s řešeními služby SharePoint a můžete je sestavit pomocí téměř libovolné technologie webového programování, jako je HTML5, JavaScript, CSS3 a XML.

|||
|-|-|
|![Dokumentace](../sharepoint/media/vs-icon-documentation.gif "Dokumentace")|**Dokumentace**<br /><br /> -   [Začínáme &#40;s vývojem pro SharePoint v&#41; aplikaci Visual Studio](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)<br />-   [vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)<br />-   [Lokalizace řešení služby SharePoint](../sharepoint/localizing-sharepoint-solutions.md)<br />-   [sestavování a ladění řešení služby SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)<br />[balíček -   a nasazení řešení služby SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)<br />-   [rozšiřování nástrojů služby SharePoint v aplikaci Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)|
|![Dokumentace](../sharepoint/media/vs-icon-documentation.gif "Dokumentace")|**Doporučené úlohy**<br /><br /> -   [Návod: vytvoření sloupce webu, typu obsahu a seznamu pro službu SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)<br />-   [Postupy: vytvoření přijímače událostí](../sharepoint/how-to-create-an-event-receiver.md)<br />-   [Postupy: vytvoření modelu služby BDC](../sharepoint/how-to-create-a-bdc-model.md)<br />-   [Postupy: Vytvoření webové části služby SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)<br />-   [Postupy: vytvoření uživatelského ovládacího prvku pro stránku aplikace SharePoint nebo webovou část](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|
|![Návody](../sharepoint/media/vs-icon-walkthroughs.gif "Postupy")|**Návody**<br /><br /> -   [návody pro vývoj pro SharePoint](../sharepoint/sharepoint-development-walkthroughs.md)|
|![Ukázky kódu](../sharepoint/media/vs-icon-codesamples.gif "Ukázky kódu")|**Ukázky kódu**<br /><br /> -   [ukázky vývoje pro SharePoint](../sharepoint/sharepoint-development-samples.md)<br />-   [soubory pro vývojáře pro SharePoint](/sharepoint/dev/)|
|![Absolv](../sharepoint/media/vs-icon-training.gif "Absolv")|**Absolv**<br /><br /> -   se [seznámit s vývojem pro SharePoint](/sharepoint/dev/)|
|![Fóra](../sharepoint/media/vs-icon-forums.gif "Diskuzní fóra")|**Fóra**<br /><br /> -   [vývoj pro SharePoint pomocí sady Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vssharepointdevelopment)<br />-   [SharePoint 2010](https://social.msdn.microsoft.com/Forums/sharepoint/home?category=sharepoint2010,sharepoint)|
|![Absolv](../sharepoint/media/vs-icon-training.gif "Absolv")|**Blogy**<br /><br /> -   [blog vývoje pro Visual Studio pro SharePoint](https://blogs.msdn.microsoft.com/vssharepointtoolsblog/)|
|![Jak mám? Videa](../sharepoint/media/vs-icon-howdoivideos.gif "Jak mám? Videa")|**Jak mám? Videa**<br /><br /> -   [Jak mohu: vytvořit visual webové části pro SharePoint 2010 ve Visual studiu 2010?](https://visualstudio.microsoft.com/)<br />-   [Postupy: vytváření typů obsahu pro SharePoint 2010 ve Visual studiu 2010?](/previous-versions/visualstudio/visual-studio-2010/dd831853\(v\=vs.100\))<br />-   [Jak mohu: vytvořit definice webu pro SharePoint 2010 ve Visual studiu 2010?](/previous-versions/visualstudio/visual-studio-2010/dd831853\(v\=vs.100\))<br />-   [Postupy: vytvoření modelu připojení obchodních dat pro SharePoint 2010 pomocí sady Visual Studio 2010?](/previous-versions/visualstudio/visual-studio-2010/dd831853\(v\=vs.100\))|
|![Videa na Channel 9](../sharepoint/media/vs-icon-channel9videos.gif "Videa na Channel 9")|**Videa na Channel 9**<br /><br /> -   [Přehled vývoje pro SharePoint v aplikaci Visual Studio 2010](https://channel9.msdn.com/blogs/funkyonex/overview-of-sharepoint-development-in-visual-studio-2010)<br />-   [osvědčené postupy pro sestavování sharepointu 2010 webové části se sadou Visual Studio 2010](https://channel9.msdn.com/blogs/funkyonex/best-practices-on-building-sharepoint-2010-web-parts-with-visual-studio-2010)<br />-   [funkce služby SharePoint a návrháři balíčků v aplikaci Visual Studio 2010](https://channel9.msdn.com/blogs/funkyonex/sharepoint-feature-and-package-designers-in-visual-studio-2010)|
|![Centrum pro vývojáře](../sharepoint/media/vs-icon-msdndevcenter.gif "Centrum pro vývojáře")|**Centra pro vývojáře**<br /><br /> -   [vývojové centrum sady Visual Studio](https://visualstudio.microsoft.com/)<br />[Centrum pro vývojáře pro SharePoint](/sharepoint/dev/) -   <br />[Centrum pro vývojáře serveru -   SharePoint](/previous-versions/office/fp161348\(v\=office.15\))<br />-   [Centrum pro vývojáře SharePoint designeru](/previous-versions/office/fp161348\(v\=office.15\))<br />[Centrum pro vývojáře -   ASP.NET](https://msdn.microsoft.com/aa336522.aspx)|
|![Poskytnutí zpětné vazby](../sharepoint/media/vs-icon-feedback.gif "Poskytnutí zpětné vazby")|**Poskytnutí zpětné vazby**<br /><br /> Poskytněte zpětnou vazbu o aplikaci Visual Studio:<br /><br /> -   [Microsoft Connect](/collaborate/connect-redirect)<br /><br /> Poskytněte zpětnou vazbu k dokumentaci k sadě Visual Studio:<br /><br /> -   **odlehčené zobrazení.** Pokud jste v horní části libovolného tématu, můžete vybrat odkaz **Ohodnotit toto téma** , abyste se přeskočili k dolnímu okraji tohoto tématu, kde můžete zadat **Ano** nebo **ne** v reakci na **tuto užitečnost** . Pak můžete zaškrtnout jedno nebo více políček, která se zobrazí, pokud vyberete možnost **ne**, zadat další informace do textového pole nebo obojí. Po dokončení klikněte na tlačítko **Odeslat** .<br />-   **zobrazení Scriptfree.** V horní části tématu klikněte na odkaz pro **zpětnou** vazbu a poskytněte nám zpětnou vazbu na webu TechNet a na fóru názory na knihovnu výrazů.<br />-   **klasické zobrazení** V horní části tématu klikněte na ikonu po **kliknutí na tlačítko ohodnoťte a poskytněte zpětnou** vazbu k tématu poskytnutí zpětné vazby k tématu dokumentačnímu týmu.|
