---
title: Architektura přizpůsobení na úrovni dokumentu
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VSTOLoader.dll
- formats [Office development in Visual Studio]
- file formats [Office development in Visual Studio]
- vstoee.dll
- managed code extensions [Office development in Visual Studio], definition
- document-level customizations [Office development in Visual Studio]
- AddInLoader.dll
- architecture [Office development in Visual Studio], document-level customizations
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4e07c8ae29c773a1f50fedd68376a062e2203570
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248267"
---
# <a name="architecture-of-document-level-customizations"></a>Architektura přizpůsobení na úrovni dokumentu
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] zahrnuje projekty pro vytvoření přizpůsobení na úrovni dokumentu pro aplikaci Microsoft Office Word a Microsoft Office Excel. Toto téma popisuje následující aspekty přizpůsobení na úrovni dokumentu:  
  
- [Vysvětlení přizpůsobení](#UnderstandingCustomizations)  
  
- [Součástí vlastní nastavení](#Components)  
  
- [Jak fungují vlastní nastavení pomocí aplikace Microsoft Office](#HowCustomizationsWork)  
  
  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
  Obecné informace o vytvoření přizpůsobení na úrovni dokumentu naleznete v tématu [přehled vývoje řešení pro Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md), [Začínáme programování přizpůsobení na úrovni dokumentu pro Word](../vsto/getting-started-programming-document-level-customizations-for-word.md), a [Začínáme programování přizpůsobení na úrovni dokumentu pro Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md).  
  
##  <a name="UnderstandingCustomizations"></a> Vysvětlení přizpůsobení  
 Při použití nástroje Office developer tools v sadě Visual Studio k vytvoření přizpůsobení na úrovni dokumentu, můžete vytvořit sestavení spravovaného kódu, který je spojen s určitým dokumentem. Dokumentu nebo sešitu s propojené sestavení se říká, že jste rozšíření se spravovaným kódem. Další informace najdete v tématu [návrhu a vytvořte řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md).  
  
 Když uživatel otevře dokument, sestavení je načteno aplikací Microsoft Office. Po sestavení je načteno, přizpůsobení můžou reagovat na události v otevřeném dokumentu. Přizpůsobení můžete také volat do objektového modelu automatizovat a rozšířit aplikaci a dokument je otevřen, můžete použít některý z třídy v [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].  
  
 Sestavení komunikuje s komponentami vaší aplikace modelu COM pomocí primární spolupracující sestavení aplikace. Další informace najdete v tématu [primární spolupracující sestavení Office](../vsto/office-primary-interop-assemblies.md) a [přehled vývoje řešení pro Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 Pokud uživatel otevře více přizpůsobení na úrovni dokumentu ve stejnou dobu, každé sestavení je načteno v jiné aplikační doméně. To znamená, že jedno řešení, který se chová nesprávně nemůže způsobit jiná řešení k selhání. Přizpůsobení na úrovni dokumentu jsou navrženy pro práci s jednotlivý dokument v jediné doméně aplikace. Nejsou určeny pro komunikaci mezi dokumenty. Další informace o aplikačních doménách najdete v tématu [aplikačních doménách](/dotnet/framework/app-domains/application-domains).  
  
> [!NOTE]  
>  Přizpůsobení na úrovni dokumentu, které vytvoříte pomocí nástroje Office developer tools v sadě Visual Studio jsou navrženy pro se dá použít jenom při spuštění aplikace koncovým uživatelem. Pokud je aplikace spuštěna prostřednictvím kódu programu, například pomocí automatizace, přizpůsobení nemusí fungovat podle očekávání.  
  
### <a name="design-time-and-run-time-experiences"></a>Možnosti návrhu a běhu  
 Informace o tom architektura přizpůsobení na úrovni dokumentu, dobré pochopit možnosti návrhu řešení a spuštění řešení.  
  
#### <a name="design-time"></a>Doby návrhu  
 Možnosti času návrhu zahrnuje následující kroky:  
  
1.  Vývojář vytvoří projektu na úrovni dokumentu v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Projekt obsahuje dokument a sestavení, které běží na pozadí tohoto dokumentu. Možná již existuje (vytvořené návrhářem) dokumentu nebo spolu s projektu lze vytvořit nový dokument.  
  
2.  Návrhář – buď vývojář, který vytvoří projekt, nebo někdo jiný – vytvoří konečné vzhled a chování dokumentu pro koncového uživatele.  
  
#### <a name="runtime"></a>Modul runtime  
 Běhové prostředí zahrnuje následující kroky:  
  
1.  Koncový uživatel otevře dokumentu nebo sešitu, který má rozšíření se spravovaným kódem.  
  
2.  Dokumentem nebo sešitem, načte zkompilovaného sestavení.  
  
3.  Sestavení, reaguje na události, uživatel pracuje v dokumentu nebo sešitu.  
  
#### <a name="developer-and-end-user-perspective-compared"></a>Pro vývojáře a koncový uživatel pohledu porovnání  
 Protože vývojář funguje především [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]a koncový uživatel pracuje v aplikaci Word nebo Excel, existují dva způsoby Principy přizpůsobení na úrovni dokumentu.  
  
|Perspektiva pro vývojáře|Koncový uživatel perspektivy|  
|-----------------------------|----------------------------|  
|Pomocí [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], vývojář píše kód, který je přístupný pro aplikace Word a Excel.<br /><br /> I když to může zdát, že vývojáři vytváří spustitelný soubor, na kterém běží aplikace Word nebo Excel, tento proces funguje ve skutečnosti naopak. Dokument je přidružený k sestavení a obsahuje ukazatel na toto sestavení. Po otevření dokumentu aplikace Word nebo Excel vyhledá sestavení a spuštění kódu v reakci na všechny zpracované události.|Uživateli, kteří používají řešení jednoduše otevřete dokumentem nebo sešitem, (nebo vytvořit nový dokument ze šablony) stejně jako každý jiný dokument aplikace Microsoft Office rozepínají.<br /><br /> Sestavení obsahuje vlastní nastavení v dokumentem nebo sešitem, jako je například automaticky vyplní s aktuálními údaji, nebo zobrazuje dialogové okno pro žádost o informace.|  
  
### <a name="supported-document-formats-for-document-level-customizations"></a>Podporované formáty dokumentu přizpůsobení na úrovni dokumentu  
 Při vytváření vlastního nastavení projektu, můžete formát dokumentu, který chcete použít v projektu. Další informace najdete v tématu [jak: Vytvářet projekty pro Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 V následující tabulce jsou uvedeny formáty dokumentu, která vám pomůže v přizpůsobeních na úrovni dokumentu pro Excel a Word.  
  
|Excel|Word|  
|-----------|----------|  
|Excelový sešit (*.xlsx*)<br /><br /> Excelový sešit s podporou maker (*.xlsm*)<br /><br /> Binární Excelový sešit (*.xlsb*)<br /><br /> Sešit Excelu 97 – 2003 (*.xls*)<br /><br /> Šablona aplikace Excel (*XLTX*)<br /><br /> Šablona aplikace Excel s podporou maker (*.xltm*)<br /><br /> Šablona Excelu 97 – 2003 (*.xlt*)|Wordový dokument (*.docx*)<br /><br /> Wordový dokument s podporou maker (*DOCM*)<br /><br /> Dokument Wordu 97 – 2003 (*doc*)<br /><br /> Šablona aplikace Word (*DOTX*)<br /><br /> Šablona aplikace Word s podporou maker (*.dotm*)<br /><br /> Šablona Wordu 97 – 2003 (*.dot*)|  
  
 Měli byste navrhnout rozšíření spravovaného kódu pouze pro dokumenty v podporovaných formátů. V opačném případě určité události nemusí vyvolána při otevření dokumentu v aplikaci. Například <xref:Microsoft.Office.Tools.Excel.Workbook.Open> událost se vyvolá, když používáte rozšíření spravovaného kódu s sešity uložené ve formátu tabulky XML aplikace Excel nebo webové stránky (*.htm*; *.html*) formát.  
  
### <a name="support-for-word-documents-that-have-xml-file-name-extensions"></a>Podpora pro Wordové dokumenty, které mají přípony názvů souborů XML  
 Šablony projektu na úrovni dokumentu není umožňují vytvářet projekty založené na následující formáty souborů:  
  
- Wordový dokument XML (*\*xml*).  
  
- XML dokument aplikace Word 2003 (*\*xml*).  
  
  Pokud chcete koncovým uživatelům použít vlastní nastavení do těchto formátů souborů, sestavovat a nasazovat vlastní nastavení, která používá jeden z podporovaných formátů uvedená v tabulce výše. Po instalaci přizpůsobení, koncovým uživatelům můžete uložit dokument v dokumentu XML (*\*xml*) formát nebo XML dokument aplikace Word 2003 (*\*xml*) formátu a přizpůsobení budou nadále fungovat podle očekávání.  
  
##  <a name="Components"></a> Součástí vlastní nastavení  
 Hlavní součásti přizpůsobení se dokument a sestavení. Kromě těchto součástí existuje několik částí, které hrají důležitou roli v tom, jak aplikace Microsoft Office zjišťovat a načíst vlastní nastavení.  
  
### <a name="deployment-manifest-and-application-manifest"></a>Manifest nasazení a manifest aplikace  
 Vlastní nastavení slouží k identifikaci a načíst nejnovější verzi sestavení přizpůsobení manifesty aplikace a manifesty nasazení. Nasazení manifestu odkazuje na aktuální manifest aplikace. Aplikace odkazuje na sestavení přizpůsobení manifestu a určuje vstupní bod třídy (nebo třídy) provádět v sestavení. Další informace najdete v tématu [aplikace a manifestů nasazení v řešeních pro systém Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).  
  
### <a name="visual-studio-tools-for-office-runtime"></a>Visual Studio Tools for Office Runtime  
 Ke spuštění přizpůsobení na úrovni dokumentu, které jsou vytvořeny pomocí nástroje Office developer tools v sadě Visual Studio, musí mít počítačích koncových uživatelů [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] nainstalované. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Zahrnuje nespravovanými komponentami, které načítají vlastního nastavení sestavení a sadu spravovaných sestavení. Tato spravovaná sestavení poskytuje objektový model, který používá váš kód přizpůsobení automatizovat a rozšířit hostitelskou aplikaci.  
  
 Další informace najdete v tématu [Visual Studio tools for Office runtime přehled](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
##  <a name="HowCustomizationsWork"></a> Jak fungují vlastní nastavení pomocí aplikace Microsoft Office  
 Když uživatel otevře dokument, který je součástí vlastní nastavení Microsoft Office, aplikace používá manifestu nasazení, který je propojený s dokumentu pro vyhledání a načtení nejaktuálnější verzi vlastního nastavení sestavení. Umístění manifestu nasazení je uloženo v vlastní vlastnost dokumentu s názvem **AssemblyLocation**. Řetězec, který určuje toto umístění je vložen do vlastnosti při sestavování řešení.  
  
 Nasazení manifestu odkazuje na manifest aplikace, která pak odkazuje na aktuální sestavení. Další informace najdete v tématu [aplikace a manifestů nasazení v řešeních pro systém Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).  
  
 Následující obrázek znázorňuje základní architektura přizpůsobení na úrovni dokumentu.  
  
 ![Architektura přizpůsobení systému office 2007](../vsto/media/office07-custom.png "architektura přizpůsobení systému Office 2007")  
  
> [!NOTE]  
>  V řešeních pro systém Office, které se zaměřují [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], řešení pro volání do objektového modelu hostitelské aplikace podle pomocí primárních sestavení vzájemné spolupráce (PIA) informace o typu, který je vložen do sestavení řešení, namísto volání do PIA přímo. Další informace najdete v tématu [návrhu a vytvořte řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md).  
  
### <a name="loading-process"></a>Proces načítání  
 Když uživatel otevře dokument, který je součástí řešení Microsoft Office, dojde k následujícím krokům.  
  
1.  Aplikace Microsoft Office zkontroluje vlastní vlastnosti dokumentu chcete zobrazit, zda jsou spojené s dokumentem. rozšíření spravovaného kódu. Další informace najdete v tématu [přehled vlastností dokumentu vlastní](../vsto/custom-document-properties-overview.md).  
  
2.  Pokud je rozšíření spravovaného kódu, načtení aplikace *VSTOEE.dll*, který načte *knihovna VSTOLoader.dll*. Toto nespravovaných knihoven DLL, které jsou součástí zaváděcího programu pro Visual Studio 2010 Tools for Office runtime. Další informace najdete v tématu [Visual Studio Tools for Office runtime přehled](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
3.  *Knihovna VSTOLoader.dll* načte [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] a spustí spravované část [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
4.  Pokud je dokument otevřít z jiného umístění než do místního počítače, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ověří, jestli je umístění dokumentu v **důvěryhodná umístění** v seznamu **nastavení Centra zabezpečení** pro tu konkrétní aplikaci Office. Pokud umístění dokumentu není v důvěryhodném umístění, přizpůsobení není důvěryhodný a proces načítání se tady zastaví.  
  
5.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Nainstaluje řešení, pokud modul dosud nebyl nainstalován, stáhne nejnovější manifesty aplikace a nasazení a provádí sérii kontrol zabezpečení. Další informace najdete v tématu [řešení pro systém Office zabezpečení](../vsto/securing-office-solutions.md).  
  
6.  Pokud je důvěryhodný pro spuštění, přizpůsobení [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] používá ke kontrole aktualizací sestavení manifestu nasazení a manifest aplikace. Pokud je dostupná nová verze sestavení, modul runtime stáhne novou verzi sestavení [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] mezipaměti na klientském počítači. Další informace najdete v tématu [nasazení řešení Office](../vsto/deploying-an-office-solution.md).  
  
7.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Vytvoří novou doménu aplikace, ve kterých se mají načíst vlastního nastavení sestavení.  
  
8.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Načte vlastního nastavení sestavení do domény aplikace.  
  
9. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Volání **spuštění** obslužnou rutinu události do vašeho vlastního nastavení sestavení. Další informace najdete v tématu [události v projektech pro systém Office](../vsto/events-in-office-projects.md)  
  
## <a name="see-also"></a>Viz také:  
 [Architektura řešení pro Office v sadě Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [Architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Visual Studio Tools for Office runtime – přehled](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Zabezpečení řešení pro systém Office](../vsto/securing-office-solutions.md)   
 [Návrh a vytvoření řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)   
 [Přehled přizpůsobených vlastností dokumentu](../vsto/custom-document-properties-overview.md)   
 [Data uložená v mezipaměti v přizpůsobeních na úrovni dokumentu](../vsto/cached-data-in-document-level-customizations.md)  
  
  