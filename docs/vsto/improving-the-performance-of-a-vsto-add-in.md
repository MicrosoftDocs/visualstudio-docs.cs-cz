---
title: Zvýšení výkonu doplňku VSTO
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 918ff0ac0a0b7f4e16c779516c015d7b74cec415
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672649"
---
# <a name="improve-the-performance-of-a-vsto-add-in"></a>Zvýšení výkonu doplňku VSTO
  Může dát uživatelům lepší prostředí pomocí optimalizace doplňků VSTO, které vytvoříte pro Office, aplikace tak, aby jejich rychlé spuštění, vypnutí, otevřete položky a provádět další úlohy. Pokud váš doplněk VSTO pro Outlook, může snížit pravděpodobnost, že váš doplněk VSTO bude zakázána z důvodu nízký výkon. Můžete zvýšit výkon vašeho doplňku VSTO pomocí implementace následujících strategií:  
  
- [Načtení doplňků VSTO na vyžádání](#Load).  
  
- [Publikování řešení pro systém Office pomocí Instalační služby systému Windows](#Publish).  
  
- [Obejít pásu karet reflexe](#Bypass).  
  
- [Provádět nákladné operace v samostatných prováděcího vlákna](#Perform).  
  
  Další informace o tom, jak optimalizovat doplňku VSTO pro Outlook, naleznete v tématu [kritéria výkonu zachovat doplňků VSTO povolené](http://go.microsoft.com/fwlink/?LinkID=266503).  
  
##  <a name="Load"></a> Načtení doplňků VSTO na vyžádání  
 Můžete nakonfigurovat doplňku VSTO pro načtení pouze za následujících okolností:  
  
- Když se poprvé uživatel spustí aplikaci, která po instalaci doplňku VSTO.  
  
- Když se poprvé interakci uživatele po spuštění aplikace kdykoli následné s doplňku VSTO.  
  
  Například doplňku VSTO může vyplnit tabulku s daty když se uživatel rozhodne, která má popisek tlačítka s vlastní **získat Moje Data**. Aplikace musí načíst doplňku VSTO aspoň jednou tak, aby **získat Moje Data** tlačítko můžete zobrazit na pásu karet. Ale doplňku VSTO nenačte znovu když uživatel spustí aplikaci, která příště. Doplněk VSTO načte, pouze když uživatel vybere možnost **získat Moje Data** tlačítko.  
  
### <a name="to-configure-a-clickonce-solution-to-load-vsto-add-ins-on-demand"></a>Konfigurace řešení ClickOnce k načtení doplňků VSTO na vyžádání  
  
1.  V **Průzkumníka řešení**, zvolte uzel projektu.  
  
2.  V panelu nabídky zvolte **zobrazení** > **stránky vlastností**.  
  
3.  Na **publikovat** , vyberte **možnosti** tlačítko.  
  
4.  V **možnosti publikování** dialogového okna zvolte **nastavení Office** položky seznamu, zvolte **načíst na požádání** možnost a klikněte na tlačítko **OK**tlačítko.  
  
### <a name="to-configure-a-windows-installer-solution-to-load-vsto-add-ins-on-demand"></a>Konfigurace řešení Instalační služby systému Windows pro načtení doplňků VSTO na vyžádání  
  
1.  V registru, nastavte `LoadBehavior` vstupu **_kořenové_\Software\Microsoft\Office\\_ApplicationName_\Addins\\  _ID doplňku_** klíč **0x10**.  
  
     Další informace najdete v tématu [položky registru pro doplňky VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
### <a name="to-configure-a-solution-to-load-vsto-add-ins-on-demand-while-you-debug-the-solution"></a>Konfigurace řešení načítá doplňků VSTO na vyžádání při ladění řešení  
  
1.  Vytvořit skript, který nastaví `LoadBehavior` vstupu **_kořenové_\Software\Microsoft\Office\\_ApplicationName_\Addins\\  _ID doplňku_** klíč **0x10**.  
  
     Následující kód ukazuje příklad tohoto skriptu.  
  
    ```cmd/sh
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\MyAddIn]  
    "Description"="MyAddIn"  
    "FriendlyName"="MyAddIn"  
    "LoadBehavior"=dword:00000010  
    "Manifest"="c:\\Temp\\MyAddIn\\bin\\Debug\\MyAddIn.vsto|vstolocal"  
  
    ```  
  
2.  Vytvořte událost po sestavení, která aktualizuje registr pomocí skriptu.  
  
     Následující kód ukazuje příklad příkazu řetězec, který můžete přidat událost po sestavení.  
  
    ```cmd/sh
    regedit /s "$(SolutionDir)$(SolutionName).reg"  
  
    ```  
  
     Informace o tom, jak vytvořit událost po sestavení v C# projektu naleznete v tématu [postupy: určení události sestavení &#40;C&#35;&#41;](/visualstudio/ide/how-to-specify-build-events-csharp).  
  
     Informace o tom, jak vytvořit událost po sestavení v projektu jazyka Visual Basic najdete v tématu [postupy: určení událostí sestavení &#40;jazyka Visual Basic&#41;](/visualstudio/ide/how-to-specify-build-events-visual-basic).  
  
##  <a name="Publish"></a> Publikování řešení pro systém Office pomocí Instalační služby systému Windows  
 Pokud publikujete vašeho řešení pomocí Instalační služby systému Windows, Visual Studio 2010 Tools for Office runtime obchází následující kroky při načtení doplňku VSTO.  
  
- Ověření schématu manifestu.  
  
- Automatické zjišťování aktualizací.  
  
- Ověření digitálních podpisů manifesty nasazení.  
  
  > [!NOTE]  
  >  Tento přístup není nutné v případě nasazení doplňku VSTO do zabezpečeného umístění v počítačích uživatelů.  
  
  Další informace najdete v tématu [nasazení řešení Office s použitím Instalační služby systému Windows](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
##  <a name="Bypass"></a> Obejít reflexe pásu karet  
 Při sestavování řešení s použitím [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)], ujistěte se, že vaši uživatelé nainstalovali nejnovější verzi aplikace Visual Studio 2010 Tools for Office runtime při nasazení řešení. Starší verze tohoto modulu runtime projeví do řešení sestavení k vyhledání vlastních nastavení pásu karet. Tento proces může způsobit doplňku VSTO pro načítají se pomaleji.  
  
 Jako alternativu můžete zabránit všechny verze sady Visual Studio 2010 Tools for Office runtime k identifikaci vlastních nastavení pásu karet pomocí operace reflection. Pokud chcete postupovat podle této strategie, přepsat `CreateRibbonExtensibility` metoda a explicitně návratových objektů pásu karet. Pokud váš doplněk VSTO neobsahuje všechna vlastní nastavení pásu karet, vrátí `null` uvnitř metody.  
  
 Následující příklad vrátí objekt pásu karet na základě hodnoty pole.  
  
 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs#1)]  
  
##  <a name="Perform"></a> Provádět nákladné operace v samostatných prováděcího vlákna  
 Vezměte v úvahu provádění časově náročných úloh (jako je například dlouhotrvající úlohy, připojení k databázi nebo jiné druhy volání sítě) v samostatném vlákně. Další informace najdete v tématu [podpora v systému Office práce s vlákny](../vsto/threading-support-in-office.md).  
  
> [!NOTE]  
>  Veškerý kód, který volá do objektového modelu Office musí být spuštěn v hlavním vlákně.  
  
## <a name="see-also"></a>Viz také:  
 [Doplňky VSTO vyžádání načítání](https://blogs.msdn.microsoft.com/andreww/2008/07/14/demand-loading-vsto-add-ins/)   
 [Zpoždění načtení modulu CLR v doplňky sady Office](https://blogs.msdn.microsoft.com/andreww/2008/04/19/delay-loading-the-clr-in-office-add-ins/)   
 [Vytváření doplňků VSTO pro Office s použitím sady Visual Studio](create-vsto-add-ins-for-office-by-using-visual-studio.md)   
