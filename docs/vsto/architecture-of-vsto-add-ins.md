---
title: Architektura doplňků VSTO
description: Doplňky VSTO vytvořené v aplikaci Visual Studio mají funkce architektury, které zdůrazňují stabilitu a zabezpečení a umožňují, aby s systém Microsoft Office úzce spolupracovaly.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VSTOLoader.dll
- architecture [Office development in Visual Studio], application-level add-ins
- vstoee.dll
- application-level add-ins [Office development in Visual Studio], architecture
- add-ins [Office development in Visual Studio], architecture
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 136903bd6d844d57ef06fce5a62506e026355509
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882606"
---
# <a name="architecture-of-vsto-add-ins"></a>Architektura doplňků VSTO
  Doplňky VSTO vytvořené pomocí nástrojů Office Developer Tools v sadě Visual Studio mají funkce architektury, které zdůrazňují stabilitu a zabezpečení a umožňují, aby při systém Microsoft Office úzce spolupracovaly. Toto téma popisuje následující aspekty doplňků VSTO:

- [Principy doplňků VSTO](#UnderstandingAddIns)

- [Komponenty doplňků VSTO](#AddinComponents)

- [Jak doplňky VSTO pracují s aplikacemi systém Microsoft Office](#HowAddinsWork)

  [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

  Obecné informace o vytváření doplňků VSTO najdete v tématu [Přehled vývoje řešení pro systém Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) a [Začínáme s programováním doplňků VSTO](../vsto/getting-started-programming-vsto-add-ins.md).

## <a name="understand-vsto-add-ins"></a><a name="UnderstandingAddIns"></a> Principy doplňků VSTO
 Když použijete nástroje Office Developer Tools v sadě Visual Studio k sestavení doplňku VSTO, vytvoříte sestavení spravovaného kódu, které je načteno aplikací systém Microsoft Office. Po načtení sestavení může doplněk VSTO reagovat na události, které jsou vyvolány v aplikaci (například když uživatel klikne na položku nabídky). Doplněk VSTO také může volat do objektového modelu pro automatizaci a rozšiřování aplikace a může použít libovolnou třídu v [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] .

 Sestavení komunikuje s komponentami modelu COM aplikace prostřednictvím primárního definičního sestavení aplikace. Další informace najdete v tématu věnovaném [primárním sestavením vzájemné spolupráce pro Office](../vsto/office-primary-interop-assemblies.md) a na [webu přehled vývoje řešení pro office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 Je-li pro aplikaci nainstalováno více doplňků VSTO, je každý doplněk VSTO načten v jiné doméně aplikace. To znamená, že jeden doplněk VSTO, který se chová nesprávně, nemůže způsobit selhání jiných doplňků VSTO. Také pomáhá zajistit, že při zavření aplikace budou všechna sestavení doplňku VSTO uvolněna z paměti. Další informace o aplikačních doménách najdete v tématu [aplikační domény](/dotnet/framework/app-domains/application-domains).

> [!NOTE]
> Doplňky VSTO, které vytvoříte pomocí nástrojů Office Developer Tools v sadě Visual Studio, jsou navržené tak, aby se používaly jenom v případě, že je hostitelská systém Microsoft Office aplikace spuštěná koncovým uživatelem. Pokud je aplikace spouštěna programově (například pomocí automatizace), nemusí doplněk VSTO fungovat podle očekávání.

## <a name="components-of-vsto-add-ins"></a><a name="AddinComponents"></a> Komponenty doplňků VSTO
 I když je sestavení doplňku VSTO hlavní součástí, je k dispozici několik dalších komponent, které hrají důležitou roli v tématu Jak systém Microsoft Office aplikace zjišťují a načítají doplňky VSTO.

### <a name="registry-entries"></a>Položky registru
 Systém Microsoft Office aplikace zjišťují doplňky VSTO tím, že hledají sadu položek registru. Úplný seznam položek registru používaných doplňky VSTO najdete v tématu [položky registru pro doplňky VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

 Při sestavování řešení vytvoří Visual Studio všechny požadované položky registru ve vývojovém počítači, abyste mohli ladit a spustit doplněk VSTO. Další informace najdete v tématu [sestavování řešení pro systém Office](../vsto/building-office-solutions.md).

 Použijete-li k nasazení řešení ClickOnce, instalační program vygenerovaný procesem publikování automaticky vytvoří klíče registru v počítači koncového uživatele. Další informace najdete v tématu [nasazení řešení pro systém Office pomocí technologie ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

### <a name="deployment-manifest-and-application-manifest"></a>Manifest nasazení a manifest aplikace
 Doplňky VSTO používají manifesty nasazení a manifesty aplikací k identifikaci a načtení nejaktuálnější verze sestavení doplňku VSTO. Manifest nasazení odkazuje na aktuální manifest aplikace. Manifest aplikace odkazuje na sestavení doplňku VSTO a určuje třídu vstupního bodu, který má být spuštěn v sestavení. Další informace najdete v tématu [manifesty aplikací a nasazení v řešeních pro systém Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).

### <a name="visual-studio-tools-for-office-runtime"></a>Modul runtime Visual Studio Tools for Office
 Pokud chcete spouštět doplňky VSTO vytvořené pomocí nástrojů Office Developer Tools v sadě Visual Studio, musí mít počítače koncového uživatele [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] nainstalované. Modul runtime zahrnuje nespravované komponenty a sadu spravovaných sestavení. Nespravované součásti načtou sestavení doplňku VSTO. Spravovaná sestavení poskytují objektový model, který kód doplňku VSTO používá k automatizaci a rozšiřování hostitelské aplikace.

 Další informace najdete v tématu [Přehled modulu runtime Visual Studio Tools for Office](../vsto/visual-studio-tools-for-office-runtime-overview.md).

## <a name="how-vsto-add-ins-work-with-microsoft-office-applications"></a><a name="HowAddinsWork"></a> Jak doplňky VSTO pracují s aplikacemi systém Microsoft Office
 Když uživatel spustí aplikaci systém Microsoft Office, aplikace použije manifest nasazení a manifest aplikace k vyhledání a načtení nejaktuálnější verze sestavení doplňku VSTO. Následující ilustrace znázorňuje základní architekturu těchto doplňků VSTO.

 ![2007 architektura doplňků pro Office](../vsto/media/office07addin.png "2007 architektura doplňků pro Office")

> [!NOTE]
> V řešeních pro systém Office, která cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , volají řešení volání do objektového modelu aplikace hostitele pomocí informací o typu PIA, který je vložen do sestavení řešení namísto přímého volání do PIA. Další informace najdete v tématu [Návrh a vytváření řešení pro Office](../vsto/designing-and-creating-office-solutions.md).

### <a name="loading-process"></a>Proces načítání
 Pokud uživatel spustí aplikaci, dojde k následujícím krokům:

1. Aplikace kontroluje v registru položky, které identifikují doplňky VSTO vytvořené pomocí nástrojů Office Developer Tools v sadě Visual Studio.

2. Pokud aplikace nalezne tyto položky registru, aplikace načte VSTOEE.dll, který načte VSTOLoader.dll. Jedná se o nespravované knihovny DLL, které jsou komponentami zavaděče pro Visual Studio 2010 Tools for Office runtime. Další informace najdete v tématu [Přehled modulu runtime Visual Studio Tools for Office](../vsto/visual-studio-tools-for-office-runtime-overview.md).

3. *VSTOLoader.dll* načte [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] a spustí spravovanou část [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

4. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Kontroluje aktualizace manifestu a stahuje nejaktuálnější manifesty aplikace a nasazení.

5. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Provede řadu kontrol zabezpečení. Další informace najdete v tématu [zabezpečení řešení pro Office](../vsto/securing-office-solutions.md).

6. Pokud je doplněk VSTO důvěryhodný ke spuštění, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] používá manifest nasazení a manifest aplikace ke kontrole aktualizací sestavení. Pokud je k dispozici nová verze sestavení, modul runtime stáhne novou verzi sestavení do [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] mezipaměti v klientském počítači. Další informace najdete v tématu [nasazení řešení pro Office](../vsto/deploying-an-office-solution.md).

7. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Vytvoří novou doménu aplikace, ve které se načte sestavení doplňku VSTO.

8. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Načte sestavení doplňku VSTO do aplikační domény.

9. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Volá <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> metodu v doplňku VSTO, pokud jste ji přepsali.

     Volitelně můžete tuto metodu přepsat tak, aby se objekt v doplňku VSTO vystavoval jiným systém Microsoft Officem řešením. Další informace najdete v tématu [kód volání v doplňcích VSTO z jiných řešení pro Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).

10. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Volá <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> metodu v doplňku VSTO, pokud jste ji přepsali.

     Volitelně můžete tuto metodu přepsat pro rozšíření systém Microsoft Office funkce vrácením objektu, který implementuje rozhraní rozšiřitelnosti. Další informace najdete v tématu [Přizpůsobení funkcí uživatelského rozhraní pomocí rozhraní rozšiřitelnosti](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md).

    > [!NOTE]
    > [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Vytvoří samostatné volání <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> metody pro každé rozhraní rozšíření, které je podporováno hostitelskou aplikací. I když první volání <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> metody obvykle nastane před voláním `ThisAddIn_Startup` metody, váš doplněk VSTO by neměl dělat žádné předpoklady o tom <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> , kdy bude metoda volána, nebo kolikrát bude volána.

11. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Volá `ThisAddIn_Startup` metodu v doplňku VSTO. Tato metoda je výchozí obslužná rutina události pro <xref:Microsoft.Office.Tools.AddInBase.Startup> událost. Další informace najdete v tématu [události v projektech Office](../vsto/events-in-office-projects.md).

## <a name="see-also"></a>Viz také
- [Architektura řešení pro systém Office v sadě Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Architektura přizpůsobení na úrovni dokumentu](../vsto/architecture-of-document-level-customizations.md)
- [Přehled prostředí Visual Studio Tools for Office runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Programové doplňky VSTO](../vsto/programming-vsto-add-ins.md)
- [Vývoj řešení pro systém Office](../vsto/developing-office-solutions.md)
- [Zabezpečení řešení pro systém Office](../vsto/securing-office-solutions.md)
- [Nasazení řešení pro systém Office](../vsto/deploying-an-office-solution.md)
