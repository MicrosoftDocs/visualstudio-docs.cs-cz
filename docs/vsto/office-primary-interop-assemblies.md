---
title: primární spolupracující sestavení sady Office
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies
- assemblies [Office development in Visual Studio], primary interop assemblies
- Office primary interop assemblies
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6a709a59e85f65cf2e0caa0551610dd496bedda5
ms.sourcegitcommit: 689ba54ea14257d13031de881f5d4fe937a36f56
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71342500"
---
# <a name="office-primary-interop-assemblies"></a>primární spolupracující sestavení sady Office

Chcete-li používat funkce aplikace systém Microsoft Office z projektu sady Office, je nutné použít primární definiční sestavení (PIA) pro aplikaci. PIA umožňuje spravovanému kódu pracovat s modelem objektů založenými na modelu COM pro systém Microsoft Office aplikace.

[!include[Add-ins note](includes/addinsnote.md)]

Při vytváření nového projektu sady Office přidá sada Visual Studio odkazy na PIA, které jsou požadovány pro sestavení projektu. V některých scénářích může být nutné přidat odkazy na další PIA (například pokud chcete použít funkci systém Microsoft Office Word v projektu pro systém Microsoft Office Excel).

Toto téma popisuje následující aspekty použití systém Microsoft Office PIA v projektech pro systém Office:

- [Samostatné sestavení primární spolupráce pro vytváření a spouštění projektů](#separateassemblies)

- [Použití funkcí více systém Microsoft Office aplikací v jednom projektu](#usingfeatures)

- [Úplný seznam primárních sestavení vzájemné spolupráce pro aplikace systém Microsoft Office](#pialist)

Další informace o primárních sestaveních spolupráce naleznete v tématu [primární spolupracující sestavení](/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).

<a name="separateassemblies"></a>

## <a name="separate-primary-interop-assemblies-to-build-and-run-projects"></a>Samostatné sestavení primární spolupráce pro vytváření a spouštění projektů

Sada Visual Studio používá různé sady Pia ve vývojovém počítači. Tyto různé sady sestavení jsou v následujících umístěních:

- Složka v adresáři Program Files

  Tyto kopie sestavení se používají při psaní kódu a sestavení projektů. Visual Studio tyto sestavení nainstaluje automaticky.

- Globální mezipaměť sestavení (GAC)

  Tyto kopie sestavení se používají při některých úkolech vývoje, například při spuštění nebo ladění projektů. Visual Studio nenainstaluje a neregistrují tato sestavení; musíte to udělat sami.

### <a name="primary-interop-assemblies-in-the-program-files-directory"></a>Primární spolupracující sestavení v adresáři Program Files

Při instalaci sady Visual Studio se PIA automaticky nainstalují do umístění v systému souborů, a to mimo globální mezipaměť sestavení (GAC). Když vytvoříte nový projekt, Visual Studio automaticky přidá odkazy na tyto kopie PIA do vašeho projektu. Visual Studio používá tyto kopie PIA namísto sestavení v globální mezipaměti sestavení (GAC) k vyřešení odkazů typu při vývoji a sestavování projektu.

Tyto kopie PIA umožňují aplikaci Visual Studio vyhnout se několika problémům vývoje, které mohou nastat, pokud jsou různé verze PIA registrovány v globální mezipaměti sestavení (GAC).

Počínaje sadou Visual Studio 2017 se tyto kopie PIA nainstalují do následujících sdílených umístění na vývojovém počítači:

- `%ProgramFiles%\Microsoft Visual Studio\Shared\Visual Studio Tools for Office\PIA\`

- (nebo `%ProgramFiles(x86)%\Microsoft Visual Studio\Shared\Visual Studio Tools for Office\PIA\` v 64 operačních systémech)

> [!NOTE]
> Pro starší verze sady Visual Studio budou tyto PIA nainstalovány do složky Visual Studio Tools pro složku Office\PIA ve složce `%ProgramFiles%` pro danou verzi sady Visual Studio.
> Například: `%ProgramFiles(x86)%\Microsoft Visual Studio 14.0\Visual Studio Tools for Office\PIA\`

### <a name="primary-interop-assemblies-in-the-global-assembly-cache"></a>Primární spolupracující sestavení v globální mezipaměti sestavení (GAC)

Chcete-li provést určité úlohy vývoje, je nutné nainstalovat a zaregistrovat PIA v globální mezipaměti sestavení (GAC) ve vývojovém počítači. PIA jsou obvykle nainstalovány automaticky při instalaci sady Office na vývojovém počítači. Další informace najdete v tématu [Konfigurace počítače pro vývoj řešení pro systém Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

Na počítačích koncových uživatelů se nevyžaduje použití PIA Office ke spouštění řešení pro Office. Další informace najdete v tématu [Návrh a vytváření řešení pro Office](../vsto/designing-and-creating-office-solutions.md).

<a name="usingfeatures"></a>

## <a name="use-features-of-multiple-microsoft-office-applications-in-a-single-project"></a>Použití funkcí více systém Microsoft Office aplikací v jednom projektu

Každá šablona projektu Office v sadě Visual Studio je navržena pro práci s jednou systém Microsoft Office aplikací. Chcete-li používat funkce ve více aplikacích systém Microsoft Office nebo chcete-li používat funkce aplikace nebo komponenty, které nemají projekt v aplikaci Visual Studio, je nutné přidat odkaz na požadované PIA.

Ve většině případů byste měli přidat odkazy na PIA, které jsou nainstalovány v aplikaci Visual Studio v `%ProgramFiles(x86)%\Microsoft Visual Studio\Shared\Visual Studio Tools for Office\PIA\` adresáři. Tyto verze sestavení se zobrazí na kartě **rozhraní** dialogového okna **Správce odkazů** . Další informace najdete v tématu [jak: Cílové aplikace Office v rámci primárních](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)sestavení spolupráce

Pokud jste nainstalovali a zaregistrovali PIA v globální mezipaměti sestavení (GAC), tyto verze sestavení se zobrazí na kartě **com** dialogového okna **Správce odkazů** . Měli byste se vyhnout přidávání odkazů na tyto verze sestavení, protože existují některé problémy s vývojem, které mohou nastat při jejich použití. Pokud jste například zaregistrovali různé verze PIA v globální mezipaměti sestavení (GAC), projekt se automaticky připojí k verzi sestavení, které bylo zaregistrováno jako poslední – i v případě, že zadáte jinou verzi sestavení v **modelu COM** . na kartě dialogového okna **Správce odkazů** .

> [!NOTE]
> Některá sestavení jsou přidána do projektu automaticky při přidání sestavení, které na ně odkazuje. Například odkazy na sestavení `Office.dll` a `Microsoft.Vbe.Interop.dll` jsou přidány automaticky při přidání odkazu do sestavení aplikace Word, Excel, Outlook, Microsoft Forms nebo Graph.

<a name="pialist"></a>

## <a name="primary-interop-assemblies-for-microsoft-office-applications"></a>Primární spolupracující sestavení pro aplikace systém Microsoft Office

Následující tabulka uvádí primární spolupracující sestavení, která jsou k dispozici [!INCLUDE[Office_16_short](../vsto/includes/office-16-short-md.md)]pro [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] , [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]a.

<br/>

|Aplikace nebo komponenta Office|Název primárního definičního sestavení|
|-------------------------------------|-----------------------------------|
|Knihovna objektů Microsoft Access 14,0<br /><br /> Knihovna objektů Microsoft Access 15,0|Microsoft.Office.Interop.Access.dll|
|Knihovna objektů databázového stroje systém Microsoft Office 14,0 Access<br /><br /> Knihovna objektů databázového stroje systém Microsoft Office 15,0 Access|Microsoft.Office.Interop.Access.Dao.dll|
|Knihovna objektů Microsoft Excel 14,0<br /><br /> Knihovna objektů Microsoft Excel 15,0|[Microsoft.Office.Interop.Excel.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.excel?view=excel-pia)|
|Knihovna objektů Microsoft Graph 14,0 (používaná v aplikacích PowerPoint, Access a Word pro grafy)<br /><br /> Knihovna objektů Microsoft Graph 15,0|Microsoft.Office.Interop.Graph.dll|
|Knihovna typů Microsoft InfoPath 2,0 (jenom pro InfoPath 2007)|[Microsoft.Office.Interop.InfoPath.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.infopath?view=infopath-form)|
|Definiční sestavení XML aplikace Microsoft InfoPath (pouze pro InfoPath 2007)|Microsoft.Office.Interop.InfoPath.Xml.dll|
|Knihovna objektů systém Microsoft Office 14,0 (sdílené funkce sady Office)<br /><br /> Knihovna objektů systém Microsoft Office 15,0 (sdílené funkce sady Office)|office.dll|
|Systém Microsoft Office ovládací prvek zobrazení Outlooku (dá se použít na webových stránkách a v aplikacích pro přístup do složky Doručená pošta)|Microsoft.Office.Interop.OutlookViewCtl.dll|
|Knihovna objektů Microsoft Outlook 14,0<br /><br /> Knihovna objektů Microsoft Outlook 15,0|[Microsoft.Office.Interop.Outlook.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.outlook?view=outlook-pia)|
|Knihovna objektů Microsoft PowerPoint 14,0<br /><br /> Knihovna objektů Microsoft PowerPoint 15,0|Microsoft.Office.Interop.PowerPoint.dll|
|Knihovna objektů Microsoft Project 14,0<br /><br /> Knihovna objektů Microsoft Project 15,0|[Microsoft.Office.Interop.MSProject.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.msproject?view=office-project-server)|
|Knihovna objektů Microsoft Publisher 14,0<br /><br /> Knihovna objektů Microsoft Publisher 15,0|Microsoft.Office.Interop.Publisher.dll|
|Knihovna referencí webového objektu aplikace Microsoft SharePoint Designer 14,0|Microsoft.Office.Interop.SharePointDesigner.dll|
|Knihovna odkazů na objekt stránky Microsoft SharePoint Designer 14,0|Microsoft.Office.Interop.SharePointDesignerPage.dll|
|Poznámka ke knihovně typů inteligentních značek Microsoft 2,0 **:**  Inteligentní značky jsou zastaralé v [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] a. [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]|Microsoft.Office.Interop.SmartTag.dll|
|Knihovna typů Microsoft Visia 14,0<br /><br /> Knihovna typů Microsoft Visia 15,0|Microsoft.Office.Interop.Visio.dll|
|Microsoft Visio 14,0 Uložit jako webovou knihovnu typů<br /><br /> Microsoft Visio 15,0 Uložit jako webovou knihovnu typů|Microsoft.Office.Interop.Visio.SaveAsWeb.dll|
|Knihovna typů ovládacích prvků výkresu aplikace Microsoft Visio 14,0<br /><br /> Knihovna typů ovládacích prvků výkresu aplikace Microsoft Visio 15,0|Microsoft.Office.Interop.VisOcx.dll|
|Knihovna objektů Microsoft Word 14,0<br /><br /> Knihovna objektů Microsoft Word 15,0|[Microsoft.Office.Interop.Word.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.word?view=word-pia)|
|Rozšíření Microsoft jazyk Visual Basic for Application 5,3|Microsoft.Vbe.Interop.dll|

### <a name="binding-redirect-assemblies"></a>Sestavení přesměrování vazeb

Když instalujete a zaregistrujete PIA pro Office v globální mezipaměti sestavení (buď pomocí sady Office, nebo instalací redistribuovatelného balíčku pro PIA), sestavení přesměrování vazby se také nainstalují pouze do globální mezipaměti sestavení (GAC). Tato sestavení vám pomůžou zajistit, aby byla v době běhu načtena správná verze primárních sestavení spolupráce.

Například pokud řešení, které odkazuje [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] na sestavení, běží na počítači, který [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] má verzi stejného primárního definičního sestavení, sestavení [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] přesměrování vazby vydá modulu runtime pokyn, aby načetl [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] verze primárního definičního sestavení

Další informace najdete v tématu [jak: Povolí nebo zakáže automatické přesměrování](/dotnet/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection)vazby.

## <a name="see-also"></a>Viz také:

- [Postupy: Cílové aplikace Office prostřednictvím primárních sestavení spolupráce](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Přehled modelu objektů aplikace Excel](../vsto/excel-object-model-overview.md)
- [Řešení InfoPath](../vsto/infopath-solutions.md)
- [Přehled modelu objektů aplikace Outlook](../vsto/outlook-object-model-overview.md)
- [Řešení aplikace PowerPoint](../vsto/powerpoint-solutions.md)
- [Řešení projektu](../vsto/project-solutions.md)
- [Přehled modelu objektů aplikace Visio](../vsto/visio-object-model-overview.md)
- [Přehled modelu objektů aplikace Word](../vsto/word-object-model-overview.md)
- [Obecný referenční &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/general-reference-office-development-in-visual-studio.md)
