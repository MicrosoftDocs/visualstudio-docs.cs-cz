---
title: Vývoj pro Office a SharePoint v sadě Visual Studio
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bc1241a39707eedc4b34e0ef3531ab65e49b8238
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90811029"
---
# <a name="office-and-sharepoint-development-in-visual-studio"></a>Vývoj pro Office a SharePoint v sadě Visual Studio
  Systém Microsoft Office a SharePoint můžete roztáhnout vytvořením zjednodušené aplikace nebo doplňku, kterou uživatelé stahují z [Office Storu](https://store.office.com/) nebo z katalogu organizací, nebo vytvořením řešení založeného na .NET Framework, které uživatelé nainstalují do počítače.

 V tomto tématu:

- [Vytváření doplňků pro Office a SharePoint](#Apps)

- [Vytvoření doplňku VSTO](#Add-ins)

- [Vytvoření řešení služby SharePoint](#Solutions)

## <a name="create-add-ins-for-office-and-sharepoint"></a><a name="Apps"></a> Vytváření doplňků pro Office a SharePoint
 Sady Office 2013 a SharePoint 2013 zavádí nový model doplňku, který vám pomůže sestavovat, distribuovat a monetizovat doplňky, které rozšiřují Office a SharePoint.  Tyto doplňky můžou běžet v Office nebo SharePointu Online a uživatelé je můžou s nimi pracovat z mnoha zařízení.

 Zjistěte, jak pomocí nového [modelu doplňku Office](/office/dev/add-ins/overview/office-add-ins) rozšíříte možnosti Office pro vaše uživatele.

 Tyto doplňky mají malé nároky v porovnání s doplňky a řešeními VSTO a můžete je sestavit pomocí prakticky libovolné technologie webového programování, jako je HTML5, JavaScript, CSS3 a XML.  Chcete-li začít, použijte Office Developer Tools v aplikaci Visual Studio, který umožňuje vytvářet projekty, psát kód a spouštět doplňky v prohlížeči.

 ![Konceptuální model aplikací pro Office a SharePoint](../vsto/media/officeandsharepointapps2015.png "Konceptuální model aplikací pro Office a SharePoint")

### <a name="build-an-office-add-in"></a>Sestavení doplňku pro Office
 Pro rozšiřování funkcí Office si vytvořte doplněk pro Office. Je v podstatě webová stránka, která je hostovaná v aplikaci Office, jako je Excel, Word, Outlook a PowerPoint. Vaše aplikace může přidat funkce k dokumentům, listům, e-mailovým zprávám, událostem, prezentacím a projektům.

 Svou aplikaci můžete prodávat v Office Storu.  [Office Store](https://store.office.com/) umožňuje snadno monetizovat doplňky, spravovat aktualizace a sledovat telemetrii. Aplikaci můžete také publikovat uživatelům prostřednictvím katalogu aplikací v SharePointu nebo na serveru Exchange.

 Následující aplikace pro Office zobrazuje data listu v mapě Bingu.

 ![Aplikace obsahu pro Office](../vsto/media/appforoffice.png "Aplikace obsahu pro Office")

 **Další informace**

|Záměr|Seznamte se s |
|--------|---------|
|Přečtěte si další informace o doplňcích Office a potom si ji sestavte.|[Doplňky pro Office](/office/dev/add-ins/publish/publish)|
|Porovnejte různé způsoby, jak můžete sadu Office rozhodovat, a rozhodněte se, jestli byste měli použít aplikaci nebo doplněk Office.|[Plán pro Doplňky Office, VSTO a VBA](/archive/blogs/officeapps/roadmap-for-apps-for-office-vsto-and-vba)|

### <a name="build-a-sharepoint-add-in"></a>Sestavení doplňku pro SharePoint
 Pokud chcete SharePoint pro uživatele zvětšit, vytvořte doplněk pro SharePoint. Je to v podstatě malá, snadno použitelná samostatná aplikace, která řeší potřebu vašich uživatelů nebo podnikových aplikací.

 Aplikaci pro SharePoint můžete prodávat v [Office Storu](https://store.office.com/). Doplněk můžete také publikovat uživatelům prostřednictvím katalogu doplňků v SharePointu.  Vlastníci webů můžou nainstalovat, upgradovat a odinstalovat doplněk na svých webech SharePointu bez nutnosti pomáhat se serverem farmy nebo správcem kolekce webů.

 Tady je příklad aplikace pro SharePoint, která uživatelům pomáhá spravovat obchodní kontakty.

 ![Aplikace Business Contact Manager pro SharePoint](../vsto/media/appforsharepoint.png "Aplikace Business Contact Manager pro SharePoint")

 **Další informace**

|Záměr|Seznamte se s |
|--------|---------|
|Přečtěte si další informace o SharePointových doplňcích a pak je sestavte.|[Doplňky SharePointu](/sharepoint/dev/sp-add-ins/sharepoint-add-ins)|
|Porovnejte doplňky pro SharePoint s tradičními řešeními služby SharePoint.|[Doplňky SharePointu v porovnání s řešeními služby SharePoint](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|
|Vyberte, zda chcete vytvořit doplněk pro SharePoint nebo řešení služby SharePoint.|[Rozhodování mezi doplňky SharePointu a řešeními služby SharePoint](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|

## <a name="create-a-vsto-add-in"></a><a name="Add-ins"></a> Vytvoření doplňku VSTO
 Vytvoření doplňku VSTO pro cílení na Office 2007 nebo Office 2010 nebo pro rozšiřování sady Office 2013 a Office 2016 nad rámec toho, co je možné u doplňků Office. Doplňky VSTO se spouštějí jenom na ploše. Uživatelé musí nainstalovat doplňky VSTO, aby byly obvykle obtížnější nasazovat a podporovat.  Doplněk VSTO se ale dá s Office integrovat podrobněji. Například může přidat karty a ovládací prvky na pás karet Office a provádět pokročilé úlohy automatizace, jako je například sloučení dokumentů nebo úprava grafů. Můžete využít .NET Framework a používat C# a Visual Basic k interakci s objekty Office.

 Tady je příklad toho, co může doplněk VSTO dělat. Tento doplněk VSTO přidá ovládací prvky pásu karet, vlastní podokno úloh a dialogové okno do PowerPointu.

 ![Řešení doplňku PowerPointu](../vsto/media/powerpointaddin.png "Řešení doplňku PowerPointu")

 **Další informace**

|Záměr|Číst|
|--------|----------|
|Porovnejte různé způsoby, kterými můžete sadu Office rozhodovat, a rozhodněte se, jestli byste měli použít doplněk VSTO nebo doplněk pro Office.|[Plán pro Doplňky Office, VSTO a VBA](/archive/blogs/officeapps/roadmap-for-apps-for-office-vsto-and-vba)|
|Vytvořte doplněk VSTO.|[Doplňky VSTO – sestavení pomocí sady Visual Studio](create-vsto-add-ins-for-office-by-using-visual-studio.md)|

## <a name="create-a-sharepoint-solution"></a><a name="Solutions"></a> Vytvoření řešení služby SharePoint
 Vytvořte řešení služby SharePoint pro cílení na SharePoint Foundation 2010 a SharePoint Server 2010 nebo rozšiřujete službu SharePoint 2013 a SharePoint 2016, a to nad rámec toho, co je možné u doplňku pro SharePoint.

 Řešení služby SharePoint vyžadují místní servery SharePoint farmy. Správci je musí nainstalovat a protože řešení se spouštějí v SharePointu, můžou ovlivnit výkon serveru. Řešení však poskytují hlubší přístup k objektům služby SharePoint. Při sestavování řešení služby SharePoint můžete také využít .NET Framework a použít jazyk C# a Visual Basic k interakci s objekty služby SharePoint.

 **Další informace**

|Záměr|Seznamte se s |
|--------|---------|
|Porovnání řešení služby SharePoint s doplňky služby SharePoint.|[Doplňky SharePointu v porovnání s řešeními služby SharePoint](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|
|Vytvořte řešení služby SharePoint.|[Vytváření řešení pro SharePoint](../sharepoint/create-sharepoint-solutions.md)|