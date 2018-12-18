---
title: primární spolupracující sestavení sady Office
ms.custom: ''
ms.date: 09/20/2018
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies
- assemblies [Office development in Visual Studio], primary interop assemblies
- Office primary interop assemblies
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b44352996c1f6cf343f8100abb4f75814765c22a
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672987"
---
# <a name="office-primary-interop-assemblies"></a>primární spolupracující sestavení sady Office

Pokud chcete používat funkce aplikace Microsoft Office z projektu aplikace Office, je nutné použít sestavení primární spolupráce (PIA) pro aplikaci. PIA umožňuje spravovanému kódu pracovat s aplikací sady Microsoft Office založené na modelu COM. objektovém modelu.  
  
Když vytvoříte nový projekt sady Office, Visual Studio přidá odkazy na PIA, které jsou nutné pro sestavení projektu. V některých případech můžete potřebovat přidat odkazy na další sestavení PIA (například pokud chcete používat funkce aplikace Microsoft Office Word v projektu pro aplikaci Microsoft Office Excel).  
  
Toto téma popisuje následující aspekty v použití sestavení PIA sady Office Microsoft v projektech Office:  
  
- [Samostatné sestavení primární spolupráce pro sestavení a spuštění projektů](#separateassemblies)  
  
- [Použití funkce více aplikací sady Microsoft Office v jednom projektu](#usingfeatures)  
  
- [Úplný seznam sestavení primární spolupráce pro aplikace Microsoft Office](#pialist)  
  
Další informace o primárních sestavení vzájemné spolupráce naleznete v tématu [primárních sestavení vzájemné spolupráce](/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).  

<a name="separateassemblies"></a> 

## <a name="separate-primary-interop-assemblies-to-build-and-run-projects"></a>Samostatné sestavení primární spolupráce pro sestavení a spuštění projektů  

Visual Studio používá různé sady PIA na vývojovém počítači. Tyto různé sady sestavení jsou v následujících umístěních:  
  
- Složku v adresáři program files  
  
  Tyto kopie sestavení se používají při psaní kódu a sestavení projektů. Visual Studio automaticky nainstaluje tato sestavení.  
  
- Globální mezipaměti sestavení  
  
  Tyto kopie sestavení se používají při některých vývojářských úlohách, například při spuštění nebo ladění projektů. Visual Studio neobsahuje neinstalujte ani neregistruje tato sestavení; je nutné provést sami.  
  
### <a name="primary-interop-assemblies-in-the-program-files-directory"></a>Primární spolupracující sestavení v adresáři program files  

Při instalaci sady Visual Studio se PIA instalují automaticky do umístění v systému souborů, mimo globální mezipaměť sestavení. Při vytváření nového projektu sady Visual Studio automaticky přidá odkazy na tyto kopie PIA do vašeho projektu. Visual Studio používá tyto kopie PIA místo sestavení v globální mezipaměti sestavení, k vyřešení odkazů na typy při vývoji a sestavte projekt.  
  
Tyto kopie PIA pomáhají aplikaci Visual Studio zabránit několika vývojovým problémům, které může dojít, když různé verze PIA jsou registrovány v globální mezipaměti sestavení.  
  
Visual Studio nainstaluje tyto kopie PIA do následujících umístění na vývojovém počítači:  
  
- *%ProgramFiles%\Microsoft visual Studio 12. 0\visual Studio Tools for Office\PIA\Office14*  
  
  (nebo *% ProgramFiles (x86) %\Microsoft Visual Studio 12. 0\visual Studio Tools for Office\PIA\Office14* v 64bitových operačních systémech)  
  
- *%ProgramFiles%\Microsoft visual Studio 12. 0\visual Studio Tools for Office\PIA\Office15*  
  
  (nebo *% ProgramFiles (x86) %\Microsoft Visual Studio 12. 0\visual Studio Tools for Office\PIA\Office15* v 64bitových operačních systémech)  
  
### <a name="primary-interop-assemblies-in-the-global-assembly-cache"></a>Primární spolupracující sestavení v globální mezipaměti sestavení  

K provedení určitých úkolů vývoje, musí být nainstalovaný a zaregistrovaný v globální mezipaměti sestavení na vývojovém počítači PIA. Obvykle se PIA instalují automaticky při instalaci sady Office na vývojovém počítači. Další informace najdete v tématu [konfigurace počítače pro vývoj řešení pro systém Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
Sestavení PIA sady Office nejsou vyžadovány v počítačích koncových uživatelů ke spouštění řešení Office. Další informace najdete v tématu [návrhu a vytvořte řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md).  

<a name="usingfeatures"></a>

## <a name="use-features-of-multiple-microsoft-office-applications-in-a-single-project"></a>Použití funkce více aplikací sady Microsoft Office v jednom projektu  

Každá šablona projektu Office v sadě Visual Studio je navržena pro práci s jedinou aplikací Microsoft Office. Pokud chcete používat funkce ve více aplikacích Microsoft Office nebo použít funkce v aplikace nebo komponenty, který nemá projekt v sadě Visual Studio, musíte přidat odkaz na požadovaná PIA.  
  
Ve většině případů byste měli přidat odkazy na PIA, které jsou nainstalované ve Visual Studio v části `%ProgramFiles%\Microsoft Visual Studio 12.0\Visual Studio Tools for Office\PIA\` adresáře. Tyto verze sestavení jsou uvedeny na **Framework** karty **správce odkazů** dialogové okno. Další informace najdete v tématu [jak: aplikace Office cílové primárních sestaveních vzájemné spolupráce](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).  
  
Pokud máte nainstalována a registrována sestavení PIA v globální mezipaměti sestavení, tyto verze sestavení jsou uvedeny na **COM** karty **správce odkazů** dialogové okno. Můžete byste se vyhnout přidávání odkazů na tyto verze sestavení, protože existují některé problémy rozvoje, které může dojít, když je používáte. Například Pokud zaregistrujete různé verze PIA v globální mezipaměti sestavení, váš projekt bude automaticky svázán s verzí sestavení, která byla zaregistrována jako poslední – i v případě, že zadáte jinou verzi sestavení  **COM** karty **správce odkazů** dialogové okno.  
  
> [!NOTE]  
>  Některá sestavení jsou přidány do projektu automaticky při přidání sestavení, které na ně odkazuje. Například odkazy *sestavení Office.dll* a *Microsoft.Vbe.Interop.dll* sestavení jsou přidány automaticky, když přidáte odkaz na aplikaci Word, Excel, Outlook, Microsoft Forms nebo grafu sestavení.  

<a name="pialist"></a> 

## <a name="primary-interop-assemblies-for-microsoft-office-applications"></a>Primární spolupracující sestavení pro aplikace Microsoft Office  

V následující tabulce jsou uvedeny sestavení primární spolupráce, které jsou k dispozici pro [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] a [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)].  

<br/>

|Aplikace Office nebo komponenty|Název primárního spolupracujícího sestavení|  
|-------------------------------------|-----------------------------------|  
|Knihovna objektů Microsoft Access 14.0<br /><br /> Knihovna objektů Microsoft Access 15.0|Microsoft.Office.Interop.Access.dll|  
|Knihovna objektů databázového stroje v Microsoft Office 14.0 Access<br /><br /> Knihovna objektů databázového stroje v systému Microsoft Office 15.0 přístup|Microsoft.Office.Interop.Access.Dao.dll|  
|Knihovna objektů Microsoft Excel 14.0<br /><br /> Knihovna objektů Microsoft Excel 15.0|[Microsoft.Office.Interop.Excel.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.excel?view=excel-pia)|  
|Microsoft Graph 14.0 objekt knihovny (používané aplikace PowerPoint, Access a Word pro grafy)<br /><br /> Knihovna objektů Microsoft Graph 15.0|Microsoft.Office.Interop.Graph.dll|  
|Knihovna typů Microsoft InfoPath 2.0 (pouze pro InfoPath 2007)|[Microsoft.Office.Interop.InfoPath.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.infopath?view=infopath-form)|  
|Definiční sestavení Microsoft InfoPath XML (pouze pro InfoPath 2007)|Microsoft.Office.Interop.InfoPath.Xml.dll|  
|Knihovna objektů Microsoft Office 14.0 (sdílená funkce aplikace Office)<br /><br /> Knihovna objektů Microsoft Office 15.0 (sdílená funkce aplikace Office)|sestavení Office.dll|  
|Ovládací prvek zobrazení aplikace Microsoft Office Outlook (lze použít do webových stránek a aplikací pro přístup k vaší doručené pošty)|Microsoft.Office.Interop.OutlookViewCtl.dll|  
|Knihovna objektů Microsoft Outlook 14.0<br /><br /> Knihovna objektů Microsoft Outlook 15.0|[Microsoft.Office.Interop.Outlook.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.outlook?view=outlook-pia)|  
|Knihovna objektů Microsoft PowerPoint 14.0<br /><br /> Knihovna objektů Microsoft PowerPoint 15.0|Microsoft.Office.Interop.PowerPoint.dll|  
|Knihovna objektů Microsoft Project 14.0<br /><br /> Knihovna objektů Microsoft Project 15.0|[Microsoft.Office.Interop.MSProject.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.msproject?view=office-project-server)|  
|Knihovna objektů Microsoft Publisher 14.0<br /><br /> Knihovna objektů Microsoft Publisher 15.0|Microsoft.Office.Interop.Publisher.dll|  
|Referenční Knihovna webových objektů Microsoft SharePoint Designer 14.0|Microsoft.Office.Interop.SharePointDesigner.dll|  
|Referenční knihovna stránkových objektů Microsoft SharePoint Designer 14.0|Microsoft.Office.Interop.SharePointDesignerPage.dll|  
|Knihovna typů 2.0 inteligentní značky Microsoft **Poznámka:** inteligentní značky jsou zastaralé v [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] a [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].|Microsoft.Office.Interop.SmartTag.dll|  
|Knihovna typů Microsoft Visio 14.0<br /><br /> Knihovna typů Microsoft Visio 15.0|Microsoft.Office.Interop.Visio.dll|  
|Jako knihovna webových typů uložit aplikaci Microsoft Visio 14.0<br /><br /> Aplikace Microsoft Visio 15.0 uložit jako knihovna webových typů|Microsoft.Office.Interop.Visio.SaveAsWeb.dll|  
|Knihovna typu ovládacích prvků výkresu aplikace Microsoft Visio 14.0<br /><br /> Knihovně typů ovládacího prvku výkresu Microsoft Visia 15.0|Microsoft.Office.Interop.VisOcx.dll|  
|Knihovna objektů Microsoft Word 14.0<br /><br /> Knihovna objektů Microsoft Word 15.0|[Microsoft.Office.Interop.Word.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.word?view=word-pia)|  
|Microsoft Visual Basic for Applications – rozšiřitelnost 5.3|Microsoft.Vbe.Interop.dll|  
  
### <a name="binding-redirect-assemblies"></a>Sestavení přesměrování vazby  

Při instalaci a registraci sestavení PIA sady Office v globální mezipaměti sestavení (buď pomocí sady Office nebo instalací distribuovatelného balíčku pro PIA), nainstaluje se také sestavení vazby přesměrování pouze v globální mezipaměti sestavení. Tato sestavení pomáhají, ujistěte se, že je v době běhu načteny správné verze sestavení primární spolupráce. 

Například, když je řešení odkazující [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] sestavení běží na počítači, který má [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] dává pokyn verze stejného primárního spolupracujícího sestavení, sestavení pro přesměrování vazby [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] runtime k načtení [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] verze sestavení primární spolupráce. 

Další informace najdete v tématu [postupy: povolení a zákaz automatického přesměrování vazby](/dotnet/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection).  
  
## <a name="see-also"></a>Viz také:  

- [Postupy: aplikace Office cílové primárních sestaveních vzájemné spolupráce](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
- [Přehled modelu objektů aplikace Excel](../vsto/excel-object-model-overview.md)   
- [InfoPath – řešení](../vsto/infopath-solutions.md)   
- [Přehled modelu objektů aplikace Outlook](../vsto/outlook-object-model-overview.md)   
- [Řešení pro aplikaci PowerPoint](../vsto/powerpoint-solutions.md)   
- [Projektová řešení](../vsto/project-solutions.md)   
- [Přehled modelu objektů aplikace Visio](../vsto/visio-object-model-overview.md)   
- [Přehled modelu objektů aplikace Word](../vsto/word-object-model-overview.md)   
- [Obecné referenční informace &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/general-reference-office-development-in-visual-studio.md)  
  
  
