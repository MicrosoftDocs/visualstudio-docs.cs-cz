---
title: Vývoj pro Office a SharePoint v sadě Visual Studio
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], about developing applications
- Office development in Visual Studio
- Office projects
- Visual Studio Tools for Office, see Office development in Visual Studio
- Office applications [Office development in Visual Studio]
- Office Business Applications
- applications [Office development in Visual Studio]
- programming [Office development in Visual Studio]
- VSTO, see Office development in Visual Studio
- Office, development with Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 38291b46f2f9fee83ba9af0ae553cecca5ee35f6
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671700"
---
# <a name="office-and-sharepoint-development-in-visual-studio"></a>Vývoj pro Office a SharePoint v sadě Visual Studio
  Můžete rozšířit vytvořením jednoduché aplikace Microsoft Office a SharePoint nebo doplněk, že uživatelé stahovat z [Office Store](https://store.office.com/) nebo organizace katalogu nebo vytvořením řešení založené na rozhraní .NET Framework, které uživatelé nainstalovat počítač.  
  
 V tomto tématu:  
  
-   [Vytváření doplňků pro Office a SharePoint](#Apps)  
  
-   [Vytvoření doplňku VSTO](#Add-ins)  
  
-   [Vytvoření řešení služby SharePoint](#Solutions)  
  
##  <a name="Apps"></a> Vytváření doplňků pro Office a SharePoint  
 Office 2013 a SharePoint 2013 zavést nový doplněk model, který pomáhá vytvářet, distribuovat a finančně zhodnotit doplňky, které rozšiřují Office a SharePoint.  Tyto doplňky můžete spustit v Office nebo SharePoint Online a mohou uživatelé komunikovat s nimi z mnoha zařízení.  
  
 Zjistěte, jak používat nové [modelu doplňku Office](/office/dev/add-ins/overview/office-add-ins) rozšířit možnosti Office pro uživatele.  
  
 Tyto doplňky mají malé pracovníkům v porovnání s doplňky VSTO a řešení a je můžete vytvořit s využitím téměř jakékoli webové programování technologie, jako je například HTML5, JavaScript, CSS3 a XML.  Abyste mohli začít, použijte nástroje Office Developer Tools v sadě Visual Studio nebo jednoduchý webový nástroj s dřívějším kódovým Napa Office 365 vývojářské nástroje, které vám umožní vytvářet projekty, psát kód a spusťte doplňky v prohlížeči.  
  
 ![Aplikace pro Office a SharePoint koncepčního modelu](../vsto/media/officeandsharepointapps2015.png "aplikace pro Office a SharePoint konceptuální model")  
  
### <a name="build-an-office-add-in"></a>Sestavení doplňku Office  
 K rozšíření funkčnosti sady Office, sestavení doplňku v Office. Je v podstatě webová stránka, která je hostována v aplikaci Office, jako je Excel, Word, Outlook a PowerPoint. Aplikace můžete přidat funkce na dokumenty, sešity, e-mailové zprávy, události, prezentace a projekty.  
  
 Můžete prodávat vaše aplikace v Office Store.  [Office Store](https://store.office.com/) usnadňuje finančně zhodnotit doplňky, spravovat aktualizace a sledování telemetrická data. Můžete také publikovat aplikace uživatelům prostřednictvím katalogu aplikací ve službě SharePoint, nebo na serveru Exchange.  
  
 Následující aplikace pro Office se zobrazí data v listu v objektu map Bing.  
  
 ![Obsahové aplikace pro Office](../vsto/media/appforoffice.png "obsahové aplikace pro Office")  
  
 **Víc se uč**  
  
|Chcete-li|Další informace naleznete v tématu|  
|--------|---------|  
|Další informace o doplňků Office a následně vytvořit jeden.|[Doplňky pro Office](/office/dev/add-ins/publish/publish)|  
|Porovnejte různé způsoby, ve kterém můžete rozšířit Office a rozhodnout, zda by měl používat aplikaci nebo doplněk aplikace Office.|[Plán pro doplňky Office, VSTO a VBA](https://blogs.msdn.microsoft.com/officeapps/2013/06/18/roadmap-for-apps-for-office-vsto-and-vba/)|  
  
### <a name="build-a-sharepoint-add-in"></a>Vytvoření doplňku Sharepointu  
 K rozšíření Sharepointu pro vaše uživatele, sestavení doplňku Sharepointu. Je v podstatě malé, snadné použití, samostatné aplikace, která řeší uživatele nebo obchodní potřebu.  
  
 Můžete svoje aplikace prodávat pro SharePoint v [Office Store](https://store.office.com/). Můžete také publikovat svůj doplněk uživatelům prostřednictvím katalogu služby SharePoint.  Mohou vlastníci webu můžete nainstalovat, upgrade a Odinstalace doplňku na stránkách SharePoint bez pomoci server farmy nebo správcem kolekce webů.  
  
 Tady je příklad aplikace pro SharePoint, která pomáhá uživatelům spravovat obchodní kontakty požádali.  
  
 ![Podnikové aplikace a požádejte správce pro službu SharePoint](../vsto/media/appforsharepoint.png "podnikové aplikace a požádejte správce pro službu SharePoint")  
  
 **Víc se uč**  
  
|Chcete-li|Další informace naleznete v tématu|  
|--------|---------|  
|Další informace o doplňcích služby SharePoint a následně vytvořit jeden.|[Doplňky pro SharePoint](/sharepoint/dev/sp-add-ins/sharepoint-add-ins)|  
|Porovnejte doplňků pro SharePoint s tradiční řešení služby SharePoint.|[SharePoint Add-ins ve srovnání s řešeními služby SharePoint](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|  
|Zvolte, jestli se má sestavení doplňku Sharepointu nebo řešení služby SharePoint.|[Rozhodování, zda doplňky Sharepointu a řešení služby SharePoint](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|
  
##  <a name="Add-ins"></a> Vytvoření doplňku VSTO  
 Vytvoření VSTO doplňku sady Office 2007 nebo Office 2010 nebo Office 2013 a Office 2016 rozšířit nad rámec, jaké jsou možnosti s doplňky sady Office. Doplňky VSTO spustit pouze na ploše. Uživatelé mají k instalaci doplňků VSTO, budete obvykle obtížnější na nasazení a podporu.  Ale doplňku VSTO je možné integrovat lépe se sadou Office. Například jej přidat karty a ovládací prvky na pásu karet Office a provádět Pokročilá automatizace úlohy, například slučování dokumentů nebo úpravy grafů. Můžete využít rozhraní .NET Framework a pracovat s objekty Office pomocí jazyka C# a Visual Basic.  
  
 Tady je příklad můžete dělat co doplňku VSTO. Tento doplněk VSTO přidá ovládací prvky pásu karet, vlastního podokna úloh a dialogového okna do PowerPointu.  
  
 ![Řešení doplňku PowerPoint](../vsto/media/powerpointaddin.png "řešení doplňku PowerPoint")  
  
 **Víc se uč**  
  
|Chcete-li|Číst|  
|--------|----------|  
|Porovnejte různé způsoby, ve kterém můžete rozšířit Office a rozhodnout, zda by měl používat doplňku VSTO nebo doplněk aplikace Office.|[Plán pro doplňky Office, VSTO a VBA](https://blogs.msdn.microsoft.com/officeapps/2013/06/18/roadmap-for-apps-for-office-vsto-and-vba/)|  
|Vytvoření doplňku VSTO.|[Vytváření doplňků VSTO pomocí sady Visual Studio](create-vsto-add-ins-for-office-by-using-visual-studio.md)|  
  
##  <a name="Solutions"></a> Vytvoření řešení služby SharePoint  
 Vytvoření řešení služby SharePoint k cílení na SharePoint Foundation 2010 a SharePoint Server 2010 nebo k rozšíření SharePoint 2013 a SharePoint 2016 způsoby rámec toho, jaké jsou možnosti s doplňku Sharepointu.  
  
 Řešení pro SharePoint vyžadují místní servery ve farmě služby SharePoint. Musí být správci nainstalovat a protože řešení spustit v Sharepointu, mohou ovlivnit výkon serveru. Řešení však poskytují lepší přístup k objektům služby SharePoint. Navíc při sestavování řešení služby SharePoint, můžete využít rozhraní .NET Framework a pracovat s objekty služby SharePoint pomocí jazyka C# a Visual Basic.  
  
 **Víc se uč**  
  
|Chcete-li|Další informace naleznete v tématu|  
|--------|---------|  
|Porovnání řešení služby SharePoint pomocí Sharepointových doplňků.|[SharePoint Add-ins ve srovnání s řešeními služby SharePoint](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|  
|Vytvoření řešení služby SharePoint.|[Vytvoření řešení služby SharePoint](../sharepoint/create-sharepoint-solutions.md)|  
  
  
