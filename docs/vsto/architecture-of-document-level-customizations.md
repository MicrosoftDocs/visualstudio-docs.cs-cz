---
title: Architektura přizpůsobení na úrovni dokumentu
description: Přečtěte si o aspektech přizpůsobení na úrovni dokumentu, včetně součástí přizpůsobení a způsobu, jakým přizpůsobení fungují s systém Microsoft Office aplikacemi.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a522446f9109d996088dff9389f267ef5ff39447
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845958"
---
# <a name="architecture-of-document-level-customizations"></a>Architektura přizpůsobení na úrovni dokumentu
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] obsahuje projekty pro vytváření přizpůsobení na úrovni dokumentu pro systém Microsoft Office Word a systém Microsoft Office Excel. Toto téma popisuje následující aspekty přizpůsobení na úrovni dokumentu:

- [Porozumění vlastním úpravám](#UnderstandingCustomizations)

- [Komponenty přizpůsobení](#Components)

- [Jak přizpůsobení fungují s systém Microsoft Office aplikacemi](#HowCustomizationsWork)

  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

  Obecné informace o vytváření úprav na úrovni dokumentu najdete v tématu [Přehled vývoje řešení pro systém Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md), [Začínáme s programováním přizpůsobení na úrovni dokumentu pro Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)a Začínáme [s programováním přizpůsobení na úrovni dokumentu pro aplikaci Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md).

## <a name="understand-customizations"></a><a name="UnderstandingCustomizations"></a> Porozumění vlastním úpravám
 Když použijete nástroje Office Developer Tools v sadě Visual Studio k sestavení přizpůsobení na úrovni dokumentu, vytvoříte sestavení spravovaného kódu, které je spojeno s určitým dokumentem. U dokumentu nebo sešitu s propojeným sestavením se říká, že mají rozšíření spravovaného kódu. Další informace najdete v tématu [Návrh a vytváření řešení pro Office](../vsto/designing-and-creating-office-solutions.md).

 Když uživatel otevře dokument, sestavení je načteno aplikací systém Microsoft Office. Po načtení sestavení může přizpůsobení reagovat na události, když je dokument otevřen. Přizpůsobení může také volat objektový model pro automatizaci a rozšiřování aplikace, když je dokument otevřen, a může použít libovolnou třídu v [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] .

 Sestavení komunikuje s komponentami modelu COM aplikace prostřednictvím primárního definičního sestavení aplikace. Další informace najdete v tématu věnovaném [primárním sestavením vzájemné spolupráce pro Office](../vsto/office-primary-interop-assemblies.md) a na [webu přehled vývoje řešení pro office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 Pokud uživatel otevře více přizpůsobení na úrovni dokumentu současně, je každé sestavení načteno v jiné doméně aplikace. To znamená, že jedno řešení, které se chová nesprávně, nemůže způsobit selhání jiných řešení. Přizpůsobení na úrovni dokumentu jsou navržena tak, aby fungovala s jediným dokumentem v jedné doméně aplikace. Nejsou navržené pro komunikaci mezi dokumenty. Další informace o aplikačních doménách najdete v tématu [aplikační domény](/dotnet/framework/app-domains/application-domains).

> [!NOTE]
> Přizpůsobení na úrovni dokumentu, která vytvoříte pomocí nástrojů Office Developer Tools v sadě Visual Studio, jsou navržena tak, aby se používala pouze v případě, že je aplikace spuštěna koncovým uživatelem. Pokud je aplikace spouštěna programově, například pomocí automatizace, nemusí přizpůsobení fungovat podle očekávání.

### <a name="design-time-and-run-time-experiences"></a>Prostředí pro dobu návrhu a dobu běhu
 Aby bylo možné pochopit architekturu přizpůsobení na úrovni dokumentu, pomůže vám pochopit prostředí návrhu řešení a spuštění řešení.

#### <a name="design-time"></a>Čas návrhu
 Prostředí pro dobu návrhu zahrnuje následující kroky:

1. Vývojář vytvoří projekt na úrovni dokumentu v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Projekt obsahuje dokument a sestavení, které se spouští za dokumentem. Dokument již možná existuje (vytvořený návrhářem), nebo můžete vytvořit nový dokument společně s projektem.

2. Návrhář – buď vývojář, který vytváří projekt, nebo jiný uživatel – vytvoří konečný vzhled a chování dokumentu pro koncového uživatele.

#### <a name="runtime"></a>Runtime (Modul runtime)
 Prostředí runtime zahrnuje následující kroky:

1. Koncový uživatel otevře dokument nebo sešit, který má rozšíření spravovaného kódu.

2. Dokument nebo sešit načte zkompilované sestavení.

3. Sestavení reaguje na události v případě, že uživatel funguje v dokumentu nebo v sešitu.

#### <a name="developer-and-end-user-perspective-compared"></a>Porovnání perspektivy vývojářů a koncových uživatelů
 Vzhledem k tomu, že vývojář funguje hlavně v nástroji [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , a koncový uživatel funguje ve Wordu nebo Excelu, existují dva způsoby, jak pochopit přizpůsobení na úrovni dokumentu.

|Perspektiva pro vývojáře|Perspektiva koncového uživatele|
|-----------------------------|----------------------------|
|Pomocí nástroje [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , vývojář zapisuje kód, který je přístupný pro Word a Excel.<br /><br /> I když se může zdát, že vývojář vytváří spustitelný soubor, na kterém běží Word nebo Excel, proces skutečně funguje druhým způsobem. Dokument je přidružen k sestavení a obsahuje ukazatel na toto sestavení. Po otevření dokumentu aplikace Word nebo Excel vyhledá sestavení a spustí kód v reakci na všechny zpracovávané události.|Uživatelé, kteří používají řešení, jednoduše otevřou dokument nebo sešit (nebo vytvoří nový dokument ze šablony) stejně, jako by otevřeli jiný soubor systém Microsoft Office.<br /><br /> Sestavení poskytuje přizpůsobení v dokumentu nebo sešitě, jako je například automatické vyplnění aktuálními daty nebo zobrazení dialogového okna pro vyžádání informací.|

### <a name="supported-document-formats-for-document-level-customizations"></a>Podporované formáty dokumentů pro přizpůsobení na úrovni dokumentu
 Při vytváření projektu přizpůsobení můžete zvolit formát dokumentu, který chcete použít v projektu. Další informace najdete v tématu [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

 V následující tabulce jsou uvedeny formáty dokumentů, které lze použít v přizpůsobení na úrovni dokumentu pro aplikace Excel a Word.

|Excel|Word|
|-----------|----------|
|Excelový sešit (*. xlsx*)<br /><br /> Excelový sešit s podporou maker (*. xlsm*)<br /><br /> Binární excelový sešit (*. xlsb*)<br /><br /> Sešit aplikace Excel 97-2003 (*. xls*)<br /><br /> Excelová šablona (*. xltx*)<br /><br /> Excelová šablona s podporou maker (*. xltm*)<br /><br /> Šablona Excelu 97-2003 (*. xlt*)|Wordový dokument (*. docx*)<br /><br /> Wordový dokument s podporou maker (*. docm*)<br /><br /> Dokument aplikace Word 97-2003 (*. doc*)<br /><br /> Wordová šablona (*. dotx*)<br /><br /> Šablona s podporou maker (*. dotm*)<br /><br /> Šablona pro Word 97-2003 (*. dot*)|

 Spravovaná rozšíření kódu byste měli navrhovat pouze pro dokumenty v podporovaných formátech. V opačném případě nemusí být při otevření dokumentu v aplikaci některé události vyvolány. Například <xref:Microsoft.Office.Tools.Excel.Workbook.Open> událost není vyvolána, pokud používáte rozšíření spravovaného kódu s sešity uloženými ve formátu tabulky XML Excelu nebo na webové stránce (*. htm*; *. html*) formátovat.

### <a name="support-for-word-documents-that-have-xml-file-name-extensions"></a>Podpora pro dokumenty aplikace Word, které mají příponu názvu souboru. XML
 Šablony projektů na úrovni dokumentu neumožňují vytvářet projekty na základě následujících formátů souborů:

- Dokument XML aplikace Word (*\* XML*).

- Dokument XML pro Word 2003 (*\* XML*).

  Pokud chcete, aby koncoví uživatelé používali vlastní nastavení v těchto formátech souborů, sestavte a nasaďte vlastní nastavení, které používá jeden z podporovaných formátů souborů uvedených v tabulce výše. Po instalaci vlastního nastavení mohou koncoví uživatelé dokument uložit ve formátu dokumentu XML aplikace Word (*\* XML**\* ) nebo* ve formátu dokumentu aplikace Word 2003 XML a přizpůsobení bude nadále fungovat podle očekávání.

## <a name="components-of-customizations"></a><a name="Components"></a> Komponenty přizpůsobení
 Hlavní součásti vlastního nastavení jsou dokument a sestavení. Kromě těchto součástí je několik dalších částí, které hrají důležitou roli v tématu Jak systém Microsoft Office aplikace zjišťovat a načítat přizpůsobení.

### <a name="deployment-manifest-and-application-manifest"></a>Manifest nasazení a manifest aplikace
 Přizpůsobení používají manifesty nasazení a manifesty aplikací k identifikaci a načtení nejaktuálnější verze sestavení přizpůsobení. Manifest nasazení odkazuje na aktuální manifest aplikace. Manifest aplikace odkazuje na sestavení vlastního nastavení a určuje třídu vstupního bodu (nebo třídy), která má být spuštěna v sestavení. Další informace najdete v tématu [manifesty aplikací a nasazení v řešeních pro systém Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).

### <a name="visual-studio-tools-for-office-runtime"></a>Modul runtime Visual Studio Tools for Office
 Chcete-li spustit přizpůsobení na úrovni dokumentu, která jsou vytvořena pomocí nástrojů pro vývojáře sady Office v sadě Visual Studio, musí mít počítače koncového uživatele [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] nainstalované. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Zahrnuje nespravované komponenty, které načítají sestavení vlastního nastavení a také sadu spravovaných sestavení. Tato spravovaná sestavení poskytují objektový model, který kód vlastního nastavení používá k automatizaci a rozšiřování hostitelské aplikace.

 Další informace najdete v tématu [Přehled nástrojů Visual Studio Tools for Office runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md).

## <a name="how-customizations-work-with-microsoft-office-applications"></a><a name="HowCustomizationsWork"></a> Jak přizpůsobení fungují s systém Microsoft Office aplikacemi
 Když uživatel otevře dokument, který je součástí systém Microsoft Office přizpůsobení, aplikace použije manifest nasazení, který je propojený s dokumentem k vyhledání a načtení nejaktuálnější verze sestavení přizpůsobení. Umístění manifestu nasazení je uloženo ve vlastnosti vlastního dokumentu s názvem **AssemblyLocation**. Řetězec, který určuje toto umístění, je vložen do vlastnosti při sestavení řešení.

 Manifest nasazení odkazuje na manifest aplikace, který odkazuje na aktuální sestavení. Další informace najdete v tématu [manifesty aplikací a nasazení v řešeních pro systém Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).

 Následující ilustrace znázorňuje základní architekturu přizpůsobení na úrovni dokumentu.

 ![Architektura vlastního nastavení pro Office 2007](../vsto/media/office07-custom.png "Architektura vlastního nastavení pro Office 2007")

> [!NOTE]
> V řešeních pro systém Office, která cílí na rozhraní [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , vyvolají řešení volání do objektového modelu aplikace hostitele pomocí informací o typu primární spolupráce sestavení (PIA), který je vložen do sestavení řešení namísto přímého volání do PIA. Další informace najdete v tématu [Návrh a vytváření řešení pro Office](../vsto/designing-and-creating-office-solutions.md).

### <a name="loading-process"></a>Proces načítání
 Pokud uživatel otevře dokument, který je součástí systém Microsoft Office řešení, dojde k následujícím krokům.

1. Aplikace systém Microsoft Office zkontroluje vlastní vlastnosti dokumentu a zjistí, zda jsou k dokumentu přidružena rozšíření spravovaného kódu. Další informace najdete v tématu [Přehled vlastností vlastního dokumentu](../vsto/custom-document-properties-overview.md).

2. Pokud existují rozšíření spravovaného kódu, aplikace načte *VSTOEE.dll*, která načte *VSTOLoader.dll*. Jedná se o nespravované knihovny DLL, které jsou komponentami zavaděče pro Visual Studio 2010 Tools for Office runtime. Další informace najdete v tématu [Přehled modulu runtime Visual Studio Tools for Office](../vsto/visual-studio-tools-for-office-runtime-overview.md).

3. *VSTOLoader.dll* načte [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] a spustí spravovanou část [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

4. Pokud je dokument otevřen z jiného umístění než z místního počítače, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ověří, že umístění dokumentu je v seznamu **důvěryhodných umístění** v **Nastavení centra zabezpečení** pro danou aplikaci Office. Pokud umístění dokumentu není v důvěryhodném umístění, přizpůsobení není důvěryhodné a proces načítání se zastaví.

5. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Nainstaluje řešení, pokud ještě není nainstalované, stáhne nejaktuálnější manifesty aplikace a nasazení a provede řadu kontrol zabezpečení. Další informace najdete v tématu [zabezpečení řešení pro Office](../vsto/securing-office-solutions.md).

6. Pokud je přizpůsobení důvěryhodné pro spuštění, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] používá manifest manifestu nasazení a aplikace ke kontrole aktualizací sestavení. Pokud je k dispozici nová verze sestavení, modul runtime stáhne novou verzi sestavení do [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] mezipaměti v klientském počítači. Další informace najdete v tématu [nasazení řešení pro Office](../vsto/deploying-an-office-solution.md).

7. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Vytvoří novou doménu aplikace, ve které se má načíst sestavení vlastního nastavení.

8. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Načte sestavení vlastního nastavení do domény aplikace.

9. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Volá obslužnou rutinu události **spuštění** v sestavení vlastního nastavení. Další informace najdete v tématu [události v projektech Office](../vsto/events-in-office-projects.md).

## <a name="see-also"></a>Viz také
- [Architektura řešení pro systém Office v sadě Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Přehled prostředí Visual Studio Tools for Office runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Zabezpečení řešení pro systém Office](../vsto/securing-office-solutions.md)
- [Návrh a tvorba řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)
- [Přehled vlastních vlastností dokumentu](../vsto/custom-document-properties-overview.md)
- [Data uložená v mezipaměti v přizpůsobeních na úrovni dokumentu](../vsto/cached-data-in-document-level-customizations.md)
