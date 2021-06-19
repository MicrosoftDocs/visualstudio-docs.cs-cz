---
title: Nasazení DSL v MSI a VSIX
description: Zjistěte, jak můžete nainstalovat jazyk specifický pro doménu (DSL) na vlastní počítač nebo na jiných počítačích.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 879028746eac10160492f03651ef8b51714e9c6a
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112391007"
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>Nasazení DSL v MSI a VSIX
Jazyk specifický pro doménu můžete nainstalovat na vlastní počítač nebo do jiných počítačů. Visual Studio na cílovém počítači už musí být nainstalovaná.

## <a name="choosing-between-vsix-and-msi-deployment"></a><a name="which"></a> Volba mezi nasazením VSIX a MSI
 Existují dvě metody nasazení jazyka specifického pro doménu:

|Metoda|Výhody|
|-|-|
|VSX (Visual Studio rozšíření)|Velmi snadné nasazení: Zkopírujte a spusťte **soubor .vsix** z projektu DslPackage.<br /><br /> Další informace najdete v [tématu Instalace a odinstalace DSL pomocí VSX.](#Installing)|
|MSI (instalační soubor)|– Umožňuje uživateli otevřít Visual Studio poklikáním na soubor DSL.<br />– Přidruží ikonu k typu souboru DSL v cílovém počítači.<br />– Přidruží XSD (schéma XML) k typu souboru DSL. Tím se zabrání upozorněním při načtení souboru do Visual Studio.<br /><br /> Pokud chcete vytvořit MSI, musíte do svého řešení přidat projekt instalace.<br /><br /> Další informace najdete v tématu [Nasazení DSL pomocí souboru MSI.](#msi)|

## <a name="install-and-uninstall-a-dsl-by-using-the-vsx"></a><a name="Installing"></a> Instalace a odinstalace DSL pomocí VSX

Pokud je váš DSL nainstalován touto metodou, uživatel může otevřít soubor DSL z Visual Studio, ale soubor nelze otevřít z Průzkumník Windows.

### <a name="to-install-a-dsl-by-using-the-vsx"></a>Instalace DSL pomocí VSX

1. Vyhledejte **soubor .vsix** sestavený projektem balíčku DSL:

   1. V Průzkumník řešení klikněte pravým tlačítkem na **projekt DslPackage** **a** potom klikněte na Otevřít složku **v Průzkumník souborů**.

   2. Vyhledejte **přihrádku souborů \\ \* \\**_YourProject_**. DslPackage.vsix**

2. Zkopírujte **soubor .vsix** do cílového počítače, na který chcete nainstalovat DSL. Může to být váš vlastní počítač nebo jiný.

   - Cílový počítač musí mít jednu z edicí systému , [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] které podporují seznamy DSL za běhu. Další informace najdete v tématu [Podporované Visual Studio edice pro sadu Visualization & Modeling SDK.](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md)

   - Cílový počítač musí mít jednu z edicí Visual Studio v **DslPackage\source.extensions.manifest**.

3. V cílovém počítači poklikejte na **soubor .vsix.**

    **Visual Studio se otevře Instalační** program rozšíření a nainstaluje ho.

4. Spusťte nebo restartujte [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] .

5. K otestování DSL použijte Visual Studio k vytvoření nového souboru s příponou, kterou jste definovali pro svůj DSL.

### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>Odinstalace DSL nainstalovaného pomocí VSX

1. V nabídce **Nástroje** zvolte Rozšíření a **aktualizace.**

2. Rozbalte **Nainstalované rozšíření.**

3. Vyberte rozšíření, ve kterém je definovaný DSL, a potom klikněte na **Odinstalovat.**

   Zřídkakdy se chybné rozšíření nepodaří načíst a v chybovém okně se vytvoří sestava, ale nezobrazí se ve Správci rozšíření. V takovém případě můžete příponu odebrat odstraněním souboru z:

   *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**

## <a name="deploying-a-dsl-in-an-msi"></a><a name="msi"></a> Nasazení DSL v MSI
 Definováním souboru MSI (Instalační služba systému Windows) pro DSL můžete uživatelům povolit otevření souborů DSL z Průzkumník Windows. K příponě názvu souboru můžete také přidružit ikonu a krátký popis. Kromě toho může MSI nainstalovat XSD, který lze použít k ověření souborů DSL. Pokud chcete, můžete do MSI přidat další komponenty, které se budou instalovat současně.

 Další informace o souborech MSI a dalších možnostech nasazení najdete v tématu [Nasazení aplikací, služeb](../deployment/deploying-applications-services-and-components.md)a komponent.

 Pokud chcete sestavit MSI, přidejte projekt instalace do vašeho Visual Studio řešení. Nejjednodušším způsobem vytvoření projektu instalace je použít šablonu CreateMsiSetupProject.tt, kterou si můžete stáhnout z lokality [VMSDK.](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)

### <a name="to-deploy-a-dsl-in-an-msi"></a>Nasazení DSL v MSI

1. Nastavte `InstalledByMsi` v manifestu rozšíření. Tím zabráníte instalaci a odinstalaci VSX s výjimkou MSI. To je důležité, pokud do MSI zahrníte další komponenty.

   1. Otevřete DslPackage\source.extension.tt

   2. Před vložte následující `<SupportedProducts>` řádek:

       ```xml
       <InstalledByMsi>true</InstalledByMsi>
       ```

2. Vytvořte nebo upravte ikonu, která bude představovat váš DSL v Průzkumník Windows. Upravte například **DslPackage\Resources\File.ico.**

3. Ujistěte se, že jsou správné následující atributy vašeho DSL:

   - V Průzkumníku DSL klikněte na kořenový uzel a v okno Vlastnosti zkontrolujte:

       - Popis

       - Verze

   - Klikněte na **uzel Editor** a v okno Vlastnosti klikněte na **Ikona**. Nastavte hodnotu tak, aby odkazovat na soubor ikony **ve složce DslPackage\Resources,** například **File.ico.**

   - V nabídce **Sestavení** **otevřete Správce konfigurace** a vyberte konfiguraci, kterou chcete sestavit, například **Vypustit** nebo **Ladit.**

4. Přejděte na [domovskou stránku sady Visualization and Modeling SDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)a na kartě **Soubory** ke stažení **si** CreateMsiSetupProject.tt .

5. Přidejte **CreateMsiSetupProject.tt** do projektu Dsl.

    Visual Studio vytvoří soubor s názvem **CreateMsiSetupProject.vdproj.**

6. V Průzkumník Windows zkopírujte Dsl \\ *.vdproj do nové složky s názvem Setup.

    (Pokud chcete, můžete teď vyloučit CreateMsiSetupProject.tt z projektu Dsl.)

7. V **Průzkumník řešení**, **přidejte \\ \* instalační soubor .vdproj** jako existující projekt.

8. V nabídce **Project (Projekt)** klikněte **na Project Dependencies (Závislosti projektu).**

    V **dialogovém okně Závislosti** projektu vyberte projekt instalace.

    Zaškrtněte políčko vedle položky **DslPackage**.

9. Znovu sestavte řešení.

10. V Průzkumník Windows projektu instalace vyhledejte sestavený soubor MSI.

     Zkopírujte soubor MSI do počítače, do kterého chcete dsl nainstalovat. Dvakrát klikněte na soubor MSI. Spustí se instalační program.

11. V cílovém počítači vytvořte nový soubor s příponou vašeho DSL. Ověřte, že:

    - V Průzkumník Windows seznamu se soubor zobrazí s ikonou a popisem, který jste definovali.

    - Po dvojitém kliknutí na soubor se Visual Studio a otevře se soubor DSL v editoru DSL.

    Pokud chcete, můžete místo textové šablony vytvořit projekt instalace ručně. Názorný postup, který zahrnuje tento postup, najdete v kapitole 5 v tématu [Visualization and Modeling SDK Lab](https://code.msdn.microsoft.com/DSLToolsLab/Release/ProjectReleases.aspx?ReleaseId=4207).

### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>Odinstalace DSL nainstalovaného z MSI

1. Ve Windows otevřete ovládací **panel Programy** a funkce.

2. Odinstalujte DSL.

3. Restartujte Visual Studio.
