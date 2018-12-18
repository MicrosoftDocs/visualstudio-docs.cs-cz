---
title: Architektura doplňků VSTO
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
- architecture [Office development in Visual Studio], application-level add-ins
- vstoee.dll
- application-level add-ins [Office development in Visual Studio], architecture
- add-ins [Office development in Visual Studio], architecture
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: dccfd3a3344ef9bde46b0b1e6bed50294d832acb
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248160"
---
# <a name="architecture-of-vsto-add-ins"></a>Architektura doplňků VSTO
  Doplňků VSTO vytvořené pomocí nástroje Office developer tools v sadě Visual Studio máte architektury funkce, které zdůrazňují stabilitu a zabezpečení a povolte je těsná spolupráce s Microsoft Office. Toto téma popisuje následující aspekty doplňků VSTO:  
  
- [Vysvětlení doplňků VSTO](#UnderstandingAddIns)  
  
- [Součástí doplňků VSTO](#AddinComponents)  
  
- [Jak fungují doplňků VSTO pomocí aplikace Microsoft Office](#HowAddinsWork)  
  
  [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
  Obecné informace o vytváření doplňků VSTO najdete v tématu [přehled vývoje řešení pro Office &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) a [Začínáme s programováním doplňků VSTO](../vsto/getting-started-programming-vsto-add-ins.md).  
  
##  <a name="UnderstandingAddIns"></a> Vysvětlení doplňků VSTO  
 Při použití nástroje Office developer tools v sadě Visual Studio k vytvoření doplňku VSTO můžete vytvořit sestavení spravovaného kódu, který je načten pomocí aplikace Microsoft Office. Po sestavení je načteno, doplňku VSTO můžou reagovat na události, které jsou vyvolány v aplikaci (například když uživatel klikne položku nabídky). Doplněk VSTO můžete také volat do objektového modelu automatizovat a rozšířit aplikace a můžou používat kterýkoli z třídy v [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].  
  
 Sestavení komunikuje s komponentami vaší aplikace modelu COM pomocí primární spolupracující sestavení aplikace. Další informace najdete v tématu [primární spolupracující sestavení Office](../vsto/office-primary-interop-assemblies.md) a [přehled vývoje řešení pro Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 Pokud je nainstalovaná více doplňků VSTO pro aplikaci, načíst je každý doplňku VSTO v různých aplikační domény. To znamená, že jeden doplňku VSTO, který se chová nesprávně nemůže způsobit jiných doplňků VSTO selhání. Pomáhá také ujistit, že při zavření aplikace všechna doplňku VSTO sestavení jsou uvolněna z paměti. Další informace o aplikačních doménách najdete v tématu [aplikačních doménách](/dotnet/framework/app-domains/application-domains).  
  
> [!NOTE]  
>  Doplňků VSTO, které vytvoříte pomocí nástroje Office developer tools v sadě Visual Studio jsou navrženy pro použití pouze v případě, že hostitel aplikace Microsoft Office je tím, že koncový uživatel. Pokud je aplikace spuštěna prostřednictvím kódu programu (například pomocí automatizace), doplňku VSTO nemusí fungovat podle očekávání.  
  
##  <a name="AddinComponents"></a> Součástí doplňků VSTO  
 I když je sestavení doplňku VSTO hlavní komponenty, existuje několik komponent, které hrají důležitou roli v tom, jak aplikace Microsoft Office zjišťovat a načíst doplňky VSTO.  
  
### <a name="registry-entries"></a>Položky registru  
 Aplikace Microsoft Office zjistit doplňků VSTO pomocí sady položek registru. Úplný seznam položky registru doplňků VSTO používá, najdete v části [položky registru pro doplňky VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
 Při sestavování řešení sady Visual Studio vytvoří všechny požadované položky registru na vývojovém počítači tak, aby je ladění a spouštění vašeho doplňku VSTO. Další informace najdete v tématu [řešení pro systém Office sestavení](../vsto/building-office-solutions.md).  
  
 Pokud používáte ClickOnce k nasazení svého řešení, vytvoří instalační program automaticky generovaných procesu publikování klíče registru v počítači koncového uživatele. Další informace najdete v tématu [nasazení řešení Office s použitím technologie ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
### <a name="deployment-manifest-and-application-manifest"></a>Manifest nasazení a manifest aplikace  
 Doplňky VSTO pomocí manifesty aplikace a manifesty nasazení identifikovat a načíst nejnovější verzi sestavení doplňku VSTO. Nasazení manifestu odkazuje na aktuální manifest aplikace. Manifest aplikace odkazuje na sestavení doplňku VSTO a určuje třídu vstupního bodu ke spuštění v sestavení. Další informace najdete v tématu [aplikace a manifestů nasazení v řešeních pro systém Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).  
  
### <a name="visual-studio-tools-for-office-runtime"></a>Visual Studio Tools for Office Runtime  
 Pro spuštění doplňků VSTO, které jsou vytvořeny pomocí nástroje Office developer tools v sadě Visual Studio, musíte mít počítačích koncových uživatelů [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] nainstalované. Modul runtime obsahuje nespravovanými komponentami a sadu spravovaných sestavení. Nespravované součásti načíst sestavení doplňku VSTO. Spravovaná sestavení poskytuje objektový model, který používá váš kód doplňku VSTO automatizovat a rozšířit hostitelskou aplikací.  
  
 Další informace najdete v tématu [Visual Studio Tools for Office runtime přehled](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
##  <a name="HowAddinsWork"></a> Jak fungují doplňků VSTO pomocí aplikace Microsoft Office  
 Když uživatel spustí aplikaci Microsoft Office, aplikace používá manifest nasazení a manifest aplikace pro vyhledání a načtení nejnovější verze sestavení doplňku VSTO. Následující obrázek znázorňuje základní architekturu doplňky VSTO.  
  
 ![Architektura doplňků office 2007](../vsto/media/office07addin.png "architektura doplněk Office 2007")  
  
> [!NOTE]  
>  V řešeních pro systém Office, které se zaměřují [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], řešení pro volání do objektového modelu hostitelské aplikace podle pomocí informací o typu PIA, který je vložen do sestavení řešení, namísto volání do PIA přímo. Další informace najdete v tématu [návrhu a vytvořte řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md).  
  
### <a name="loading-process"></a>Proces načítání  
 Když uživatel spustí aplikaci dojde k následujícím krokům:  
  
1.  Aplikace zkontroluje registru pro položky, které identifikují doplňků VSTO, které byly vytvořeny pomocí nástroje Office developer tools v sadě Visual Studio.  
  
2.  Pokud aplikace zjistí tyto položky registru, načtení aplikace VSTOEE.dll, která načte knihovna VSTOLoader.dll. Toto nespravovaných knihoven DLL, které jsou součástí zaváděcího programu pro Visual Studio 2010 Tools for Office Runtime. Další informace najdete v tématu [Visual Studio Tools for Office runtime přehled](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
3.  *Knihovna VSTOLoader.dll* načte [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] a spustí spravované část [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
4.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Zjišťuje dostupnost aktualizací manifestu a stáhne nejnovější manifesty aplikace a nasazení.  
  
5.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Provádí sérii kontrol zabezpečení. Další informace najdete v tématu [řešení pro systém Office zabezpečení](../vsto/securing-office-solutions.md).  
  
6.  Pokud doplňku VSTO je důvěryhodný pro spuštění, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] používá ke kontrole aktualizací sestavení manifestu nasazení a manifest aplikace. Pokud je dostupná nová verze sestavení, modul runtime stáhne novou verzi sestavení [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] mezipaměti na klientském počítači. Další informace najdete v tématu [nasazení řešení Office](../vsto/deploying-an-office-solution.md).  
  
7.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Vytvoří novou doménu aplikace 00Z načíst sestavení doplňku VSTO.  
  
8.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Načte sestavení doplňku VSTO do domény aplikace.  
  
9. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Volání <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> metoda ve vaší doplňku VSTO, pokud jste ji přepsat.  
  
     Volitelně mohou přepsat tuto metodu ke zveřejnění objektu v doplňku VSTO pro ostatní řešení pro Microsoft Office. Další informace najdete v tématu [volání kódu v doplňcích VSTO z jiných řešení pro Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
10. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Volání <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> metoda ve vaší doplňku VSTO, pokud jste ji přepsat.  
  
     Volitelně můžete přepsat tuto metodu za účelem rozšíření funkcí sady Microsoft Office tak, že vrací objekt, který implementuje rozhraní rozšíření. Další informace najdete v tématu [funkcí přizpůsobení uživatelského rozhraní pomocí rozšiřujících rozhraní](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md).  
  
    > [!NOTE]  
    >  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Provede samostatná volání <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> metodu pro každé rozšíření rozhraní, který podporuje hostitelskou aplikaci. I když se první volání <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> metoda obvykle dochází, před voláním `ThisAddIn_Startup` metody doplňku VSTO neměl by jakkoli o tom, kdy <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> volaná metoda nebo jak často bude zavolána.  
  
11. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Volání `ThisAddIn_Startup` metoda v doplňku VSTO. Tato metoda je obslužnou rutinu výchozí události pro <xref:Microsoft.Office.Tools.AddInBase.Startup> událostí. Další informace najdete v tématu [události v projektech pro systém Office](../vsto/events-in-office-projects.md).  
  
## <a name="see-also"></a>Viz také:  
 [Architektura řešení pro Office v sadě Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [Architektura přizpůsobení na úrovni dokumentu](../vsto/architecture-of-document-level-customizations.md)   
 [Visual Studio Tools for Office runtime – přehled](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Programování doplňků VSTO](../vsto/programming-vsto-add-ins.md)   
 [Vývoj řešení pro systém Office](../vsto/developing-office-solutions.md)   
 [Zabezpečení řešení pro systém Office](../vsto/securing-office-solutions.md)   
 [Nasazení řešení Office](../vsto/deploying-an-office-solution.md)  
  
  