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
ms.openlocfilehash: 79f1c4a55321a1b039cc2702b1040e2ab9d4ac9d
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255644"
---
# <a name="improve-the-performance-of-a-vsto-add-in"></a>Zlepšení výkonu doplňku VSTO
  Uživatelům můžete poskytnout lepší prostředí tím, že optimalizujete doplňky VSTO, které vytvoříte pro aplikace Office tak, aby se rychle spouštěly, vypnuly, otevíraly položky a prováděly další úkoly. Pokud je doplněk VSTO pro Outlook k dispozici, můžete také snížit pravděpodobnost, že bude váš doplněk VSTO zakázán z důvodu špatného výkonu. Výkon doplňku VSTO můžete zvýšit implementací následujících strategií:

- [Načíst doplňky VSTO na vyžádání](#Load)

- [Publikujte řešení pro Office pomocí Instalační služba systému Windows](#Publish).

- [Vynechat odraz pásu karet](#Bypass)

- [Provádějte náročné operace v samostatném vlákně pro spuštění](#Perform).

  Další informace o tom, jak optimalizovat doplněk pro Outlook VSTO, najdete v tématu [kritéria výkonu, aby doplňky VSTO byly povolené](http://go.microsoft.com/fwlink/?LinkID=266503).

## <a name="Load"></a>Načíst doplňky VSTO na vyžádání
 Doplněk VSTO můžete nakonfigurovat tak, aby se načetl jenom za následujících okolností:

- Když uživatel poprvé spustí aplikaci po instalaci doplňku VSTO.

- Když uživatel poprvé komunikuje s doplňkem VSTO po spuštění aplikace v dalším čase.

  Například doplněk VSTO může naplnit list daty, když uživatel zvolí vlastní tlačítko s popiskem **načíst moje data**. Aplikace musí načíst doplněk VSTO aspoň jednou, aby se na pásu karet mohl zobrazit tlačítko **získat data** . Doplněk VSTO se ale znovu nenačte, když uživatel aplikaci poprvé spustí. Doplněk VSTO se načte jenom v případě, že uživatel zvolí tlačítko **získat data** .

### <a name="to-configure-a-clickonce-solution-to-load-vsto-add-ins-on-demand"></a>Konfigurace řešení ClickOnce pro načtení doplňků VSTO na vyžádání

1. V **Průzkumník řešení**vyberte uzel projektu.

2. V panelu nabídky zvolte **zobrazení** > **stránky vlastností**.

3. Na kartě **publikovat** klikněte na tlačítko **Možnosti** .

4. V dialogovém okně **Možnosti publikování** zvolte položku seznam **nastavení sady Office** , zvolte možnost **načíst na vyžádání** a pak klikněte na tlačítko **OK** .

### <a name="to-configure-a-windows-installer-solution-to-load-vsto-add-ins-on-demand"></a>Konfigurace řešení Instalační služba systému Windows, aby se načetly doplňky VSTO na vyžádání

1. V registru nastavte `LoadBehavior` zadáním klíče **_root_\Software\Microsoft\Office\\_ApplicationName_\Addins\\_Add-in_** na **0x10**.

     Další informace najdete v tématu [položky registru pro doplňky VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

### <a name="to-configure-a-solution-to-load-vsto-add-ins-on-demand-while-you-debug-the-solution"></a>Konfigurace řešení, které načte doplňky VSTO na vyžádání při ladění řešení

1. Vytvořte skript, který `LoadBehavior` nastaví položku klíč **_ID doplňku_ _root_\Software\Microsoft\Office\\_ApplicationName_\Addins\\** na **0x10**.

     Následující kód ukazuje příklad tohoto skriptu.

    ```cmd/sh
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\MyAddIn]
    "Description"="MyAddIn"
    "FriendlyName"="MyAddIn"
    "LoadBehavior"=dword:00000010
    "Manifest"="c:\\Temp\\MyAddIn\\bin\\Debug\\MyAddIn.vsto|vstolocal"

    ```

2. Vytvořte událost po sestavení, která aktualizuje registr pomocí skriptu.

     Následující kód ukazuje příklad řetězce příkazu, který může být přidán do události po sestavení.

    ```cmd/sh
    regedit /s "$(SolutionDir)$(SolutionName).reg"

    ```

     Informace o tom, jak vytvořit událost po sestavení v C# projektu, naleznete v tématu [How to: Zadejte &#40;události sestavení C&#35;&#41;](../ide/how-to-specify-build-events-csharp.md).

     Informace o tom, jak vytvořit událost po sestavení v projektu Visual Basic, naleznete v tématu [How to: Zadejte &#40;&#41;VisualBasic](../ide/how-to-specify-build-events-visual-basic.md)události sestavení.

## <a name="Publish"></a>Publikování řešení pro Office pomocí Instalační služba systému Windows
 Pokud publikujete řešení pomocí Instalační služba systému Windows, sada Visual Studio 2010 Tools for Office runtime při načtení doplňku VSTO obejít následující kroky.

- Ověřuje se schéma manifestu.

- Automatické zjišťování aktualizací

- Ověřování digitálních podpisů manifestů nasazení.

  > [!NOTE]
  > Tento přístup není nutný, pokud doplněk VSTO nasazujete do zabezpečeného umístění v počítačích uživatelů.

  Další informace najdete v tématu [nasazení řešení pro Office pomocí Instalační služba systému Windows](../vsto/deploying-an-office-solution-by-using-windows-installer.md).

## <a name="Bypass"></a>Vynechat odraz pásu karet
 Pokud vytváříte řešení pomocí [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]nástroje, ujistěte se, že uživatelé nainstalovali nejnovější verzi sady Visual Studio 2010 Tools for Office runtime při nasazení řešení. Starší verze modulu VSTO runtime, které se projeví v sestaveních řešení pro vyhledání přizpůsobení pásu karet. Tento proces může způsobit pomalejší načtení doplňku VSTO.

 Alternativně můžete zabránit jakékoli verzi nástrojů sady Visual Studio 2010 pro prostředí Office runtime z použití reflexe k identifikaci přizpůsobení pásu karet. Chcete-li postupovat podle této `CreateRibbonExtensibility` strategie, přepište metodu a explicitně vraťte objekty pásu karet. Pokud doplněk VSTO neobsahuje žádné vlastní nastavení pásu karet, vraťte `null` se v rámci metody.

 Následující příklad vrátí objekt pásu karet na základě hodnoty pole.

 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs#1)]

## <a name="Perform"></a>Provádění náročných operací v samostatném vlákně pro spuštění
 V samostatném vlákně zvažte provádění časově náročných úloh (například dlouhotrvajících úloh, připojení k databázi nebo jiné řazení síťových volání). Další informace najdete v tématu [Podpora vláken v Office](../vsto/threading-support-in-office.md).

> [!NOTE]
> Veškerý kód, který volá do objektového modelu Office, musí být spuštěn v hlavním vlákně.

## <a name="see-also"></a>Viz také:

- [Doplňky VSTO na vyžádání – načítání doplňků](https://blogs.msdn.microsoft.com/andreww/2008/07/14/demand-loading-vsto-add-ins/)
- [Zpožděné načítání CLR v doplňcích pro Office](https://blogs.msdn.microsoft.com/andreww/2008/04/19/delay-loading-the-clr-in-office-add-ins/)
- [Vytváření doplňků VSTO pro Office pomocí sady Visual Studio](create-vsto-add-ins-for-office-by-using-visual-studio.md)
