---
title: Ladění projektů Office
ms.date: 08/14/2019
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 92cc0922a36d8c57b54b69ad984d18cf4742b823
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "73189696"
---
# <a name="debug-office-projects"></a>Ladění projektů Office
  Projekty systému Office můžete ladit pomocí stejných nástrojů společnosti Microsoft [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , které používáte pro jiné [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projekty. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] funkce ladicího programu, jako je možnost vložení zarážek a zobrazení proměnných v okně **místní** hodnoty, jsou také k dispozici při ladění projektů Office. Další informace o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nástrojích pro ladění naleznete [v tématu ladění v aplikaci Visual Studio](../debugger/debugger-feature-tour.md).

> [!TIP]
> Chcete-li zjednodušit ladění, před sestavením a laděním zavřete všechny otevřené instance aplikace Office.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="start-and-stop-the-debugger"></a>Spuštění a zastavení ladicího programu
 Můžete spustit ladění projektu Office stejným způsobem jako při spuštění ladění jiných [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektů, například stisknutím klávesy **F5** . Po zahájení ladění projektu doplňku VSTO se spustí nový proces pro cílovou aplikaci Office a načte se doplněk VSTO.

 Když začnete ladit projekt na úrovni dokumentu, dokument nebo sešit se otevře v novém procesu Wordu nebo Excelu.

 Při zastavení ladicího programu ukončí proces aplikace náhle nebo se odpojí, pokud máte ladicí program nastavený na odpojení. Všechny ostatní dokumenty, které jsou otevřeny v ukončeném procesu aplikace sady Office, jsou také uzavřeny bez upozornění a veškeré neuložené změny budou ztraceny. To může zahrnovat všechny dokumenty nebo sešity, které jsou otevřeny v době, kdy je spuštěn ladicí program.

 Obvykle je lepší se před zastavením ladicího programu od tohoto procesu odpojit, takže můžete aplikaci Office ukončit běžným způsobem. Můžete se také odpojit od procesu, pokud stále chcete pracovat s otevřeným dokumentem nebo listem po zastavení ladicího programu.

 Pokud ladíte přizpůsobení na úrovni dokumentu pro aplikaci Word, opakované zastavení ladicího programu a způsob, jakým má dojít k náhlému ukončení aplikace Word, může vést k nepoškození šablony Normal. Pokud k tomu dojde, můžete odstranit poškozenou normální šablonu a při příštím otevření aplikace Word se automaticky znovu vytvoří. Žádná makra, která byla uložena v šabloně Normal, však nebudou znovu vytvořena.

### <a name="debug-office-2013-vsto-add-ins-by-using-either-office-2013-or-office-2016"></a>Ladění doplňků pro Office 2013 VSTO pomocí sady Office 2013 nebo Office 2016
 Pokud používáte sadu Visual Studio 2015 a máte nainstalovanou obě verze sady Office vedle sebe, Visual Studio spustí sadu Office 2016. Pokud používáte Visual Studio 2013, Visual Studio spustí sadu Office 2013.

 Pokud chcete ladit doplněk VSTO pomocí jiné verze sady Office (2013 nebo 2016), otevřete **Návrháře projektu**a na kartě **ladění** klikněte na tlačítko **spustit externí program** . Pak přejděte do umístění příslušného spustitelného souboru aplikace Office.

## <a name="f10-and-f11-behavior"></a>F10 a F11 – chování
 Když spustíte ladění projektu Office, **F10** a **F11** nemají stejné chování jako při zahájení ladění jiných projektů Visual Basic nebo C#. V projektech Visual Basic nebo C# se ladicí program zastaví na hlavní funkci; v projektech pro systém Office nemá sada Visual Studio kontrolu nad hlavní funkcí aplikace Office. Během ladění mají však aplikace **F10** a **F11** stejné funkce jako v projektech Visual Basic a C#.

## <a name="display-exceptions"></a>Zobrazit výjimky
 Kvůli způsobu, jakým spravovaný kód komunikuje s nespravovaným kódem, Visual Studio nezobrazuje chyby, které jsou vyvolány systém Microsoft Office aplikacemi. Pokud například doplněk VSTO vytvořený pomocí vývojářských nástrojů pro Office v sadě Visual Studio vyvolá výjimku, aplikace systém Microsoft Office bude pokračovat bez zobrazení chyby. Chcete-li zobrazit tyto chyby, nastavte ladicí program pro přerušení při výjimkách modulu CLR (Common Language Runtime). Další informace naleznete v tématu [Správa výjimek pomocí ladicího programu](../debugger/managing-exceptions-with-the-debugger.md).

 Pokud nastavíte ladicí program na výjimky modulu CLR (Common Language Runtime), všechny výjimky budou nyní přerozděleny do ladicího programu, včetně těch, které jste provedli, a některých výjimek z samotného modulu runtime, které nemusí být relevantní pro váš projekt. V každém projektu se zobrazí chyby odkazující na msosec, které se nevyskytují, ale je bezpečné je ignorovat. Tyto výjimky msosec nebudou mít vliv na vaše řešení.

 Můžete také použít **Try... Zachytit** příkazy kolem vašich metod pro zachycení výjimek.

 Ve výchozím nastavení sada Visual Studio také nezobrazuje chyby ladění za běhu pro projekty Office; tuto funkci však můžete povolit, abyste viděli chyby, které jsou vyvolány. Další informace naleznete v tématu [ladění za běhu v aplikaci Visual Studio](../debugger/just-in-time-debugging-in-visual-studio.md).

## <a name="command-line-arguments"></a>Argumenty příkazového řádku
 Pokud je **akce spustit** na stránce vlastností **ladění** nastavena na **spustit projekt**, sada Visual Studio při ladění projektu nepoužívá argumenty příkazového řádku, a to ani v případě, že jste zadali argumenty příkazového řádku jako možnosti spuštění. Pokud chcete použít argumenty příkazového řádku při spuštění ladění, je nutné vybrat jinou **akci spuštění** než **projekt spustit**.

## <a name="source-control"></a>Správa zdrojového kódu
 Vlastnosti ladění nejsou sdíleny mezi více uživateli v rámci správy zdrojového kódu. Projekty Visual Basic a C# ukládají vlastnosti ladění do souboru specifického pro uživatele (*ProjectName*. vbproj. User nebo *ProjectName*. csproj. User) a tento soubor není pod správou zdrojových kódů. Pokud je ladění více než jedna osoba, musí každá osoba zadat vlastnosti ladění ručně.

## <a name="debug-cached-datasets-in-a-document-level-project"></a>Ladění datových sad uložených v mezipaměti v projektu na úrovni dokumentu
 Pokaždé, když sestavíte projekt, datová sada se vyprázdní a znovu vytvoří. Chcete-li ladit datovou sadu uloženou v mezipaměti, je nutné otevřít dokument mimo aplikaci Visual Studio a následně připojit ladicí program.

## <a name="debug-word-document-projects-based-on-the-word-97-2003-document-doc-format"></a>Ladit projekty dokumentů aplikace Word na základě formátu dokumentu aplikace Word 97-2003 (*. doc)
 Chcete-li ladit projekt dokumentu aplikace Word na základě formátu dokumentu aplikace Word 97-2003 ( */* . doc *), je nutné přidat složku projektu do seznamu důvěryhodných složek. Další informace o tom, jak to provést, najdete v tématu [udělení důvěryhodnosti k dokumentům](../vsto/granting-trust-to-documents.md).

## <a name="debug-disabled-add-ins"></a>Ladit zakázané Doplňky
 Aplikace systém Microsoft Office mohou zakázat doplňky VSTO, které se chovají neočekávaně. Systém Microsoft Office aplikace zakáže doplňky VSTO, aby se zabránilo nasazování problematického kódu při každém spuštění aplikace. Nicméně je také snadné způsobit neočekávané chování během typického ladění. Informace o tom, jak znovu povolit doplňky VSTO, najdete v tématu [Postup: opětovné povolení doplňku VSTO, který je zakázaný](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md).

 Existují dva typy zakázání, které systém Microsoft Office aplikace používají pro doplňky VSTO: tvrdý zákaz a slabé vypnutí.

### <a name="hard-disabling"></a>Pevné vypnutí
 Pokud doplněk VSTO způsobuje neočekávané ukončení aplikace, může dojít k zablokování pevného vypnutí. Může k tomu také dojít ve vývojovém počítači, pokud ukončíte ladicí program, zatímco <xref:Microsoft.Office.Tools.AddIn.Startup> je spuštěná obslužná rutina události v doplňku VSTO. Pokud je doplněk VSTO špatně zakázaný, zobrazí se v seznamu **zakázaných položek** v aplikaci.

 Pokud aplikace Office zablokuje doplněk VSTO vytvořený pomocí vývojářských nástrojů pro Office v sadě Visual Studio, aplikace zakáže jenom doplněk VSTO, který tuto chybu způsobil. Další doplňky VSTO vytvořené pomocí vývojářských nástrojů Office v sadě Visual Studio pro tuto aplikaci Office se budou i nadále načítat.

### <a name="soft-disabling"></a>Slabé vypnutí
 Pokud doplněk VSTO vytváří chybu, která nezpůsobí neočekávané ukončení aplikace, může dojít k tichému vypnutí. Aplikace může například softwarově zakázat doplněk VSTO, pokud vyvolá neošetřenou výjimku při <xref:Microsoft.Office.Tools.AddIn.Startup> provádění obslužné rutiny události. Když je doplněk VSTO v tichém stavu zakázaný, zobrazí se v seznamu **neaktivních doplňků aplikace** v aplikaci a aplikace změní hodnotu položky registru **LOADBEHAVIOR** pro doplněk VSTO tak, aby označovala, že je uvolněný. Další informace o položce registru **LoadBehavior** najdete v tématu [položky registru pro doplňky VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

## <a name="troubleshoot-installation-errors-by-using-the-event-viewer"></a>Řešení chyb při instalaci pomocí Prohlížeč událostí
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Zapisuje zprávy do Prohlížeč událostí ve Windows pro všechny výjimky, které jsou vyvolány při instalaci nebo odinstalaci řešení Office. Tyto zprávy můžete použít k řešení problémů s instalací a nasazením.

## <a name="troubleshoot-startup-errors-by-using-a-log-file-and-error-messages"></a>Řešení chyb při spuštění pomocí souboru protokolu a chybových zpráv
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Může zapisovat všechny chyby, ke kterým došlo během spuštění do souboru protokolu, nebo zobrazit každou chybu v okně se zprávou. Ve výchozím nastavení jsou tyto možnosti vypnuté. Možnosti můžete zapnout vytvořením proměnných prostředí.

 Chcete-li zobrazit každou chybu v okně se zprávou, vytvořte proměnnou prostředí s názvem `VSTO_SUPPRESSDISPLAYALERTS` a nastavte ji na hodnotu 0 (nula). Zprávy můžete potlačit odstraněním proměnné prostředí nebo její nastavením na hodnotu 1 (jedna).

 Chcete-li zapsat chyby do souboru protokolu, vytvořte proměnnou prostředí s názvem `VSTO_LOGALERTS` a nastavte ji na hodnotu 1 (jedna). [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Vytvoří soubor protokolu ve složce, která obsahuje manifest nasazení pro doplněk VSTO, nebo ve složce obsahující dokument nebo sešit, který je spojen s přizpůsobením. Pokud se to nepovede, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] vytvoří soubor protokolu v místní složce *% TEMP%* . Pro doplňky VSTO na úrovni aplikace je výchozím názvem *doplněk název*. VSTO. log. U projektů na úrovni dokumentu je názvem souboru protokolu *název dokumentu*. *přípona*. log, například ExcelWorkbook1.xlsx. log. Chcete-li zastavit protokolování chyb, odstraňte proměnnou prostředí nebo ji nastavte na hodnotu 0 (nula).

## <a name="see-also"></a>Viz také

- [Sestavování řešení pro systém Office](../vsto/building-office-solutions.md)
- [Postupy: opětovné povolení zakázaného doplňku VSTO](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)
- [Programové doplňky VSTO](../vsto/programming-vsto-add-ins.md)