---
title: Ladění projektů Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel projects [Office development in Visual Studio], debugging
- Word projects [Office development in Visual Studio], debugging
- Outlook [Office development in Visual Studio], debugging
- debugging [Office development in Visual Studio], Outlook projects
- Office projects [Office development in Visual Studio], debugging
- Outlook [Office development in Visual Studio], projects
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cc1774e57fafadafc7087bb498e0b77a90e96d85
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35675865"
---
# <a name="debug-office-projects"></a>Ladění projektů Office
  Můžete ladit projekty Office s použitím stejného Microsoft [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nástrojů, které používáte pro jiné [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projekty. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Funkce, jako je možnost Vložit zarážky a proměnné v zobrazení ladicího programu **lokální** okna, jsou také k dispozici při ladění projektů Office. Další informace o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nástroje pro ladění, naleznete v tématu [ladit v sadě Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).  
  
> [!TIP]  
>  Pro zjednodušení, ladění, zavřete všechny otevřené instance aplikace Office, než sestavení a ladění.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
> [!NOTE]  
>  Zajímá vás vývoj řešení, které rozšiřují Office prostředí napříč [více platforem](https://dev.office.com/add-in-availability)? Podívejte se na nové [Office Add-ins modelu](https://dev.office.com/docs/add-ins/overview/office-add-ins). Doplňky sady Office mají malé náklady v porovnání s doplňky VSTO a řešení a je můžete vytvořit s využitím téměř jakékoli webové programování technologie, jako je například HTML5, JavaScript, CSS3 a XML.  
  
## <a name="start-and-stop-the-debugger"></a>Spuštění a zastavení ladicího programu  
 Můžete spustit ladění projektu pro Office, stejně jako spuštění ladění jiných [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projekty; třeba, stisknutí klávesy **F5** klíč. Při spuštění ladění projektu doplňku VSTO spuštěn nový proces pro cílové aplikace Office a načtení doplňku VSTO.  
  
 Při spuštění ladění projektu úrovni dokumentu, dokumentu nebo sešitu se otevře v nový proces aplikace Word nebo Excel.  
  
 Při zastavení ladicího programu, ladicí program bezodkladně ukončuje proces aplikace, nebo pokud máte nastavení odpojit ladicí program se odpojí. Všechny dokumenty, které jsou otevřeny v procesu ukončen aplikace Office jsou také uzavřeny bez upozornění a všechny neuložené změny budou ztraceny. To může zahrnovat všechny dokumenty a sešity, které jsou otevřeny, když ladicí program běží.  
  
 Obvykle je lepší odpojit od procesu před při zastavení ladicího programu, aby aplikace sady Office můžete ukončit běžným způsobem. Můžete také odpojit od procesu nejprve Pokud nadále chcete pracovat s otevřeného dokumentu nebo listu po zastavení ladicího programu.  
  
 Pokud ladíte přizpůsobení úrovni dokumentu pro Word, opakovaně při zastavení ladicího programu a způsobit tak Wordu zavřete náhle může vést k poškození normální šablony. Pokud k tomu dojde, můžete odstranit poškozený normální šablony a to se automaticky znovu vytvoří při příštím otevření aplikace Word. Makra, které byly uloženy v normální šablony se však nejsou znovu vytvořit.  
  
### <a name="debug-office-2013-vsto-add-ins-by-using-either-office-2013-or-office-2016"></a>Office 2013 VSTO doplňků ladit pomocí Office 2013 nebo Office 2016  
 Pokud používáte Visual Studio 2015, a budete mít obě verze nainstalovaná sada Office vedle sebe, spustí aplikace Visual Studio Office 2016. Pokud používáte Visual Studio 2013, Visual Studio spustí Office 2013.  
  
 Pokud chcete ladit doplňku VSTO pomocí jiná verze systému Office (2013 nebo 2016), otevřete **Návrháře projektu**a **ladění** , vyberte **Start externí program**přepínač. Přejděte do umístění spustitelného souboru příslušné aplikace Office.  
  
## <a name="f10-and-f11-behavior"></a>Chování F10 a F11  
 Při spuštění ladění projektu Office, **F10** a **F11** nemají stejné chování jako při spuštění ladění jiných projektů jazyka Visual Basic nebo C#. V projektech Visual Basic nebo C# ladicí program se zastaví na hlavní funkci. Visual Studio v projektech pro systém Office nemá kontrolu nad hlavní funkce aplikace Office. Nicméně během ladění, **F10** a **F11** nemají stejné funkce jako v projektech Visual Basic a C#.  
  
## <a name="display-exceptions"></a>Zobrazit výjimky  
 Kvůli způsobu, jakým spravovaný kód pracuje s nespravovaným kódem, Visual Studio nezobrazuje chyby, které jsou vyvolány pomocí aplikace Microsoft Office. Například pokud doplňku VSTO vytvořené pomocí nástroje pro vývoj pro Office v sadě Visual Studio vyvolá výjimku, aplikace Microsoft Office bude pokračovat bez zobrazení chybu. Pokud chcete zobrazit tyto chyby, nastavte ladicí program na přerušení na výjimky modulu common language runtime. Další informace najdete v tématu [Správa výjimek pomocí ladicího programu](/visualstudio/debugger/managing-exceptions-with-the-debugger).  
  
 Pokud nastavíte ladicí program na přerušení na výjimky modulu common language runtime, všechny výjimky se nyní přerušení ladicího programu, včetně těch, které mají zpracovat a některých výjimkách first-chance z modulu runtime, která nemusí být relevantní pro váš projekt. Chyby odkazující na msosec není jsou zjištěny zobrazují v každém projektu, ale jsou bezpečně ignorovat. Tyto výjimky msosec nebude mít vliv na vaše řešení.  
  
 Můžete také použít **zkuste... Zachytit** příkazy kolem svoje metody pro zachycení výjimky.  
  
 Ve výchozím nastavení Visual Studio také nemá zobrazení Just-In-Time chyby ladění projektů Office; Můžete ale povolit tuto funkci tak, aby se zobrazí chyby, které jsou vyvolány. Další informace najdete v tématu [Just-In-Time ladění v sadě Visual Studio](/visualstudio/debugger/just-in-time-debugging-in-visual-studio).  
  
## <a name="command-line-arguments"></a>Argumenty příkazového řádku  
 Pokud **spustit akci** na **ladění** vlastností stránky je nastavené na **spustit projekt**, Visual Studio nebude používat argumenty příkazového řádku při ladění projektu, i když máte zadat argumenty příkazového řádku jako možnosti spuštění. Pokud chcete používat argumenty příkazového řádku při spuštění ladění, je nutné vybrat **spustit akci** jiné než **spustit projekt**.  
  
## <a name="source-control"></a>Správy zdrojového kódu  
 Ladit vlastnosti nejsou sdílí několik uživatelů pod správou zdrojových kódů. Projekty Visual Basic a C# uložit vlastnosti ladění do souboru konkrétního uživatele (*ProjectName*. vbproj.user nebo *ProjectName*. csproj.user), a tento soubor není pod správou zdrojových kódů. Pokud je ladění více než jednou osobou, každý uživatel, který musíte zadat vlastnosti ladění ručně.  
  
## <a name="debug-cached-datasets-in-a-document-level-project"></a>Ladit datové sady v mezipaměti v projektu úrovni dokumentu  
 Pokaždé, když vytvoříte projekt, datová sada vyprázdnění a znovu vytvořit. Pokud chcete ladit datové sady v mezipaměti, musíte otevřít dokument mimo sadu Visual Studio a potom připojit ladicí program.  
  
## <a name="debug-word-document-projects-based-on-the-word-97-2003-document-doc-format"></a>Ladění aplikace Word dokumentu projekty založené na dokument Wordu 97 – 2003 (* .doc) formát  
 Chcete-li ladit Wordový dokument projektu založeného na dokument Wordu 97 – 2003 (*/* doc *) formát, složky projektu musíte přidat do seznamu důvěryhodných složek. Další informace o tom, jak to provést, najdete v části [udělit důvěryhodnost dokumenty](../vsto/granting-trust-to-documents.md).  
  
## <a name="debug-disabled-add-ins"></a>Ladění zakázané doplňky  
 Aplikace Microsoft Office můžete zakázat doplňků VSTO, které neočekávané chování. Aplikace Microsoft Office zakáže doplňků VSTO zabránit problematického kódu načítání při každém spuštění aplikace. Je však také snadno způsobit neočekávané chování během ladění typické. Informace o tom, jak znovu povolit doplňků VSTO najdete v tématu [postupy: opětovné povolení VSTO doplňku, který byl zakázán](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md).  
  
 Existují dva typy zakazuje, aby aplikace Microsoft Office použijte pro doplňky VSTO: pevné zakázání a obnovitelně zakázání.  
  
### <a name="hard-disabling"></a>Intenzivně zakázání  
 Intenzivně zakázání může dojít, když doplňku VSTO způsobí, že aplikace nečekaně zavře. To může vzniknout také ve svém vývojovém počítači zastavení ladicího programu při <xref:Microsoft.Office.Tools.AddIn.Startup> provádění obslužné rutiny události v doplňku VSTO. Doplněk VSTO je obtížné zakázáno, zobrazí se v **zakázané položky** seznamu v aplikaci.  
  
 Pokud zakáže pevné aplikace Office doplňku VSTO vytvořené pomocí nástroje pro vývoj pro Office v sadě Visual Studio, aplikace se zakáže pouze doplňku VSTO, která způsobila selhání. Načíst bude pokračovat další doplňků VSTO vytvořené pomocí nástroje pro vývoj pro Office v sadě Visual Studio pro příslušnou aplikaci Office.  
  
### <a name="soft-disabling"></a>Obnovitelně zakázání  
 Zakázání obnovitelně může dojít, když doplňku VSTO dojde k chybě, který nevyvolá aplikace neočekávaně zavřít. Například aplikace může být obnovitelné zakázat doplňku VSTO Pokud vyvolá neošetřenou výjimku při <xref:Microsoft.Office.Tools.AddIn.Startup> provádění obslužné rutiny události. Pokud doplňku VSTO se obnovitelného zakázaná, zobrazí se v **neaktivní aplikace Add-ins** seznamu v aplikaci a aplikace změní hodnotu **LoadBehavior** položky registru doplňku VSTO k označení, že je uvolněna. Další informace o **LoadBehavior** položky registru, najdete v článku [položky registru pro doplňky VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
## <a name="troubleshoot-installation-errors-by-using-the-event-viewer"></a>Řešení potíží s chybami instalace s použitím prohlížeče události  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Zapisuje zprávy do prohlížeče událostí ve Windows pro všechny výjimky, které jsou vyvolány při instalaci nebo odinstalaci řešení Office. Tyto zprávy můžete vyřešit instalací a problémů s nasazením.  
  
## <a name="troubleshoot-startup-errors-by-using-a-log-file-and-error-messages"></a>Řešení chyb při spuštění pomocí protokolu souborů a chybové zprávy  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Lze zapsat všechny chyby, ke kterým došlo během spouštění protokolového souboru nebo zobrazení jednotlivých chyb v okně se zprávou. Tyto možnosti jsou ve výchozím nastavení vypnuté. Možnosti můžete zapnout tak, že vytvoříte proměnné prostředí.  
  
 Chcete-li zobrazit všechny chyby v okně se zprávou, vytvořte proměnnou prostředí s názvem `VSTO_SUPPRESSDISPLAYALERTS` a nastavte ho na hodnotu 0 (nula). Odstraňuje se proměnná prostředí nebo nastavení na hodnotu 1 (jeden) můžete potlačit zprávy.  
  
 Zapsat chyby do souboru protokolu, vytvořte proměnnou prostředí s názvem `VSTO_LOGALERTS` a nastavte ho na hodnotu 1 (jedna). [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Vytváří protokolový soubor ve složce, která obsahuje manifest nasazení pro doplňku VSTO nebo ve složce, která obsahuje dokumentem nebo sešitem, který je přidružený k přizpůsobení. Pokud se to nepodaří, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] vytváří protokolový soubor v místním *% TEMP %* složky. Pro aplikace úrovně doplňků VSTO, výchozí název je *název doplňku*. vsto.log. Pro projekty na úrovni dokumentu, je název souboru protokolu *název dokumentu*. *rozšíření*.log, jako je například ExcelWorkbook1.xlsx.log. Zastavit protokolování chyb, odstranění proměnné prostředí nebo ji nastavte na hodnotu 0 (nula).  
  
## <a name="see-also"></a>Viz také:  
 [Vytváření řešení pro systém Office](../vsto/building-office-solutions.md)   
 [Postupy: opětovné povolení VSTO doplňku, který byl zakázán](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)   
 [Programování doplňků VSTO](../vsto/programming-vsto-add-ins.md)  
  
  