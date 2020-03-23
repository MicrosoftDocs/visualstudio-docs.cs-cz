---
title: Zlepšení výkonu doplňku VSTO
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: dccff7206aa9ef71596816d34a863695a10aff6b
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416546"
---
# <a name="improve-the-performance-of-a-vsto-add-in"></a>Zlepšení výkonu doplňku VSTO
  Uživatelům můžete poskytnout lepší možnosti optimalizací doplňků VSTO, které vytvoříte pro aplikace sady Office, aby se rychle spouštěli, vypínali, otevírali položky a prováděli další úkoly. Pokud je doplněk VSTO pro aplikaci Outlook, můžete také snížit pravděpodobnost, že doplněk VSTO bude zakázán z důvodu nízkého výkonu. Můžete zvýšit výkon doplňku VSTO implementací následujících strategií:

- [Načíst doplňky VSTO na vyžádání](#Load).

- [Publikujte řešení Office pomocí Instalační služby systému Windows](#Publish).

- [Obejít odchýlky pásu karet](#Bypass).

- [Proveďte nákladné operace v samostatném podprocesu spuštění](#Perform).

  Další informace o optimalizaci doplňku Aplikace Outlook VSTO naleznete v [tématu Kritéria výkonu, která ponechají povolené doplňky v nástroji VSTO](/previous-versions/office/jj228679(v=office.15)#performance-criteria-for-keeping-add-ins-enabled).

## <a name="load-vsto-add-ins-on-demand"></a><a name="Load"></a>Načtení doplňků VSTO na vyžádání
 Doplněk VSTO můžete nakonfigurovat tak, aby načítaný pouze za následujících okolností:

- Při prvním spuštění aplikace po instalaci doplňku VSTO.

- Při prvním interakci uživatele s doplňkem VSTO po spuštění aplikace kdykoli v pozdější mačká.

  Doplněk VSTO může například naplnit list daty, když uživatel zvolí vlastní tlačítko s názvem **Získat moje data**. Aplikace musí načíst doplněk VSTO alespoň jednou, aby se na pásu karet zobrazilo tlačítko **Získat moje data.** Doplněk VSTO se však při příštím spuštění aplikace znovu nenačte. Doplněk VSTO se načte pouze v případě, že uživatel zvolí tlačítko **Získat moje data.**

### <a name="to-configure-a-clickonce-solution-to-load-vsto-add-ins-on-demand"></a>Konfigurace řešení ClickOnce pro načtení doplňků VSTO na vyžádání

1. V **Průzkumníku řešení**zvolte uzel projektu.

2. Na řádku nabídek zvolte **Zobrazit** > **stránky vlastností**.

3. Na kartě **Publikovat** zvolte tlačítko **Možnosti.**

4. V dialogovém okně **Možnosti publikování** zvolte položku seznamu **Nastavení Office,** zvolte možnost **Načíst na vyžádání** a pak zvolte tlačítko **OK.**

### <a name="to-configure-a-windows-installer-solution-to-load-vsto-add-ins-on-demand"></a>Konfigurace řešení Instalační služby systému Windows pro načtení doplňků VSTO na vyžádání

1. V registru nastavte `LoadBehavior` položku ** _kořenového_\Software\Microsoft\Office\\_ApplicationName_\\\Addins Add-in ID** na **hodnotu 0x10**.

     Další informace naleznete v [tématu Položky registru pro doplňky VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

### <a name="to-configure-a-solution-to-load-vsto-add-ins-on-demand-while-you-debug-the-solution"></a>Konfigurace řešení pro načtení doplňků VSTO na vyžádání při ladění řešení

1. Vytvořte skript, `LoadBehavior` který nastaví položku ** _kořenového_\Software\Microsoft\Office\\_ApplicationName_\Addins\\Add-in ID** klíč **0x10**.

     Následující kód ukazuje příklad tohoto skriptu.

    ```cmd/sh
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\MyAddIn]
    "Description"="MyAddIn"
    "FriendlyName"="MyAddIn"
    "LoadBehavior"=dword:00000010
    "Manifest"="c:\\Temp\\MyAddIn\\bin\\Debug\\MyAddIn.vsto|vstolocal"

    ```

2. Vytvořte událost po sestavení, která aktualizuje registr pomocí skriptu.

     Následující kód ukazuje příklad příkazového řetězce, který můžete přidat do události po sestavení.

    ```cmd/sh
    regedit /s "$(SolutionDir)$(SolutionName).reg"

    ```

     Informace o tom, jak vytvořit událost po sestavení v projektu Jazyka C#, naleznete v tématu [How to: Specify build events &#40;C&#35;&#41;](../ide/how-to-specify-build-events-csharp.md).

     Informace o tom, jak vytvořit událost po sestavení v projektu jazyka Visual Basic, naleznete v tématu [How to: Specify build events &#40;Visual Basic&#41;](../ide/how-to-specify-build-events-visual-basic.md).

## <a name="publish-office-solutions-by-using-windows-installer"></a><a name="Publish"></a>Publikování řešení Office pomocí Instalační služby systému Windows
 Pokud publikujete řešení pomocí Instalační služby systému Windows, visual studio 2010 Tools for Office runtime obchází následující kroky při načtení doplňku VSTO.

- Ověření schématu manifestu.

- Automatická kontrola aktualizací.

- Ověření digitálních podpisů manifestů nasazení.

  > [!NOTE]
  > Tento přístup není nutné, pokud nasadíte doplněk VSTO do zabezpečeného umístění v počítačích uživatelů.

  Další informace naleznete [v tématu Deploy an Office solution using Windows Installer](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

## <a name="bypass-ribbon-reflection"></a><a name="Bypass"></a>Obejít odraz pásu karet
 Pokud vytváříte řešení [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]pomocí , ujistěte se, že uživatelé nainstalovali nejnovější verzi visual studio 2010 Tools for Office runtime při nasazení řešení. Starší verze runtime VSTO se projevily v sestaveních řešení a vyhledání vlastního nastavení pásu karet. Tento proces může způsobit, že doplněk VSTO načíst pomaleji.

 Jako alternativu můžete zabránit jakékoli verzi visual studio 2010 Tools for Office runtime používat reflexe k identifikaci vlastního nastavení pásu karet. Chcete-li sledovat tuto `CreateRibbonExtensibility` strategii, přepsat metodu a explicitně vrátit objekty pásu karet. Pokud doplněk VSTO neobsahuje žádné vlastní nastavení pásu karet, vraťte se `null` do části metody.

 Následující příklad vrátí objekt pásu karet na základě hodnoty pole.

 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs#1)]

## <a name="perform-expensive-operations-in-a-separate-execution-thread"></a><a name="Perform"></a>Provádění nákladných operací v samostatném podprocesu provádění
 Zvažte provádění časově náročných úloh (například dlouho běžících úloh, připojení k databázi nebo jiných druhů síťových volání) v samostatném vlákně. Další informace naleznete [v tématu Podpora vláken v sadě Office](../vsto/threading-support-in-office.md).

> [!NOTE]
> Veškerý kód, který volá do objektového modelu sady Office, se musí spustit v hlavním vlákně.

## <a name="see-also"></a>Viz také

- [Doplňky VSTO načítání poptávky](https://blogs.msdn.microsoft.com/andreww/2008/07/14/demand-loading-vsto-add-ins/)
- [Zpoždění načítání CLR v add-inů Office](https://blogs.msdn.microsoft.com/andreww/2008/04/19/delay-loading-the-clr-in-office-add-ins/)
- [Vytváření doplňků VSTO pro Office s použitím sady Visual Studio](create-vsto-add-ins-for-office-by-using-visual-studio.md)
