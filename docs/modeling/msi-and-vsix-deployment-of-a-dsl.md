---
title: Nasazení DSL v MSI a VSIX
description: Přečtěte si, jak můžete nainstalovat jazyk domény (DSL) na vlastní počítač nebo na jiné počítače.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bf6082ec8860f7f50e758eb65a8471ece94103aa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950408"
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>Nasazení DSL v MSI a VSIX
Jazyk specifický pro doménu můžete nainstalovat na vlastní počítač nebo na jiné počítače. V cílovém počítači již musí být nainstalována aplikace Visual Studio.

## <a name="choosing-between-vsix-and-msi-deployment"></a><a name="which"></a> Volba mezi nasazením VSIX a MSI
 Existují dvě metody nasazení jazyka specifického pro doménu:

|Metoda|Výhody|
|-|-|
|VSX (rozšíření sady Visual Studio)|Velmi snadné nasazení: Zkopírujte a spusťte soubor **. vsix** z projektu DslPackage.<br /><br /> Další informace najdete v tématu [instalace a odinstalace DSL pomocí nástroje VSX](#Installing).|
|MSI (instalační soubor)|– Umožní uživateli otevřít Visual Studio dvojitým kliknutím na soubor DSL.<br />– Přidruží ikonu k typu souboru DSL v cílovém počítači.<br />– Přidruží schéma XSD (XML Schema) k typu souboru DSL. Tím se zabrání upozornění při načtení souboru do sady Visual Studio.<br /><br /> Abyste mohli vytvořit MSI, musíte do svého řešení přidat projekt instalace.<br /><br /> Další informace najdete v tématu [Nasazení DSL pomocí souboru MSI](#msi).|

## <a name="install-and-uninstall-a-dsl-by-using-the-vsx"></a><a name="Installing"></a> Instalace a odinstalace DSL pomocí VSX

Pokud je vaše DSL nainstalovaná touto metodou, uživatel může otevřít soubor DSL z aplikace Visual Studio, ale soubor nejde otevřít z Průzkumníka Windows.

### <a name="to-install-a-dsl-by-using-the-vsx"></a>Instalace DSL pomocí VSX

1. Vyhledejte soubor **. vsix** , který byl vytvořen vaším projektem balíčku DSL:

   1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na projekt **DslPackage** a potom klikněte na možnost **Otevřít složku v Průzkumníku souborů**.

   2. Vyhledejte soubor **\\ \* \\ bin**_YourProject_**. DslPackage. vsix**

2. Zkopírujte soubor **. vsix** do cílového počítače, do kterého chcete nainstalovat DSL. Může to být váš vlastní počítač nebo jiný.

   - Cílový počítač musí mít jednu z edicí [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] , která podporuje DSL v době běhu. Další informace najdete v tématu [podporované edice sady Visual Studio pro vizualizaci & Modeling SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).

   - Cílový počítač musí mít jednu z edic sady Visual Studio specifikovanou v **DslPackage\source.Extensions.manifest**.

3. V cílovém počítači poklikejte na soubor **. vsix** .

    **Instalační program rozšíření sady Visual Studio** se otevře a nainstaluje rozšíření.

4. Spusťte nebo restartujte [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] .

5. K otestování DSL použijte Visual Studio k vytvoření nového souboru s příponou, kterou jste definovali pro DSL.

### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>Postup při odinstalaci DSL nainstalované pomocí VSX

1. V nabídce **nástroje** vyberte **rozšíření a aktualizace**.

2. Rozbalte položku **nainstalovaná rozšíření**.

3. Vyberte rozšíření, ve kterém je definována DSL, a pak klikněte na **odinstalovat**.

   Zřídka se vadné rozšíření nedokáže načíst a vytvoří sestavu v okně chyb, ale nezobrazí se ve Správci rozšíření. V takovém případě můžete odebrat rozšíření odstraněním souboru z:

   *Localappdata* **\Microsoft\VisualStudio\10.0\Extensions**

## <a name="deploying-a-dsl-in-an-msi"></a><a name="msi"></a> Nasazení DSL do MSI
 Definováním souboru MSI (Instalační služba systému Windows) pro vaši DSL můžete uživatelům dovolit otevírat soubory DSL z Průzkumníka Windows. K příponě názvu souboru můžete také přidružit ikonu a krátký popis. Kromě toho může MSI nainstalovat XSD, které lze použít k ověření souborů DSL. Pokud chcete, můžete do MSI přidat další součásti, které se nainstalují současně.

 Další informace o souborech MSI a dalších možnostech nasazení najdete v tématu [nasazení aplikací, služeb a součástí](../deployment/deploying-applications-services-and-components.md).

 Chcete-li vytvořit soubor MSI, přidejte projekt instalace do řešení sady Visual Studio. Nejjednodušší způsob, jak vytvořit projekt instalace, je použít šablonu CreateMsiSetupProject.tt, kterou si můžete stáhnout z [webu VMSDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db).

### <a name="to-deploy-a-dsl-in-an-msi"></a>Nasazení DSL do MSI

1. Nastavte `InstalledByMsi` v manifestu rozšíření. Tím se zabrání instalace a odinstalace VSX s výjimkou MSI. To je důležité, pokud budete do MSI zahrnout i další součásti.

   1. Otevřít DslPackage\source.extension.tt

   2. Vložte následující řádek před `<SupportedProducts>` :

       ```xml
       <InstalledByMsi>true</InstalledByMsi>
       ```

2. Vytvoří nebo upraví ikonu, která bude představovat vaši DSL v Průzkumníkovi Windows. Například upravte **DslPackage\Resources\File.ico**

3. Ujistěte se, že jsou správné následující atributy DSL:

   - V Průzkumníku DSL klikněte na kořenový uzel a v okno Vlastnosti zkontrolujte:

       - Popis

       - Verze

   - Klikněte na uzel **Editor** a v okno Vlastnosti klikněte na **ikonu**. Nastavte hodnotu tak, aby odkazovala na soubor ikony v **DslPackage\Resources**, jako je **File. ico.**

   - V nabídce **sestavení** otevřete **Configuration Manager** a vyberte konfiguraci, kterou chcete sestavit, například **vydaná verze** nebo **ladění**.

4. Přejít na [domovskou stránku vizualizace a modelování sady SDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)a na kartě **stažené soubory** stáhněte **CreateMsiSetupProject.TT**.

5. Přidejte **CreateMsiSetupProject.TT** do projektu DSL.

    V aplikaci Visual Studio se vytvoří soubor s názvem **CreateMsiSetupProject. vdproj**.

6. V Průzkumníku Windows zkopírujte DSL \\ *. vdproj do nové složky s názvem Setup.

    (Pokud chcete, můžete teď vyloučit CreateMsiSetupProject.tt z vašeho projektu DSL.)

7. V **Průzkumník řešení** přidejte **Setup \\ \* . vdproj** jako existující projekt.

8. V nabídce **projekt** klikněte na **závislosti projektu**.

    V dialogovém okně **závislosti projektu** vyberte projekt instalace.

    Zaškrtněte políčko vedle **DslPackage**.

9. Znovu sestavte řešení.

10. V Průzkumníku Windows vyhledejte v projektu instalace sestavený soubor MSI.

     Zkopírujte soubor MSI do počítače, na kterém chcete nainstalovat DSL. Dvakrát klikněte na soubor MSI. Spustí se instalační program.

11. V cílovém počítači vytvořte nový soubor, který má příponu souboru vaší DSL. Ověřte, že:

    - V zobrazení seznam Průzkumníka Windows se zobrazí soubor s ikonou a popisem, který jste definovali.

    - Když dvakrát kliknete na soubor, spustí se Visual Studio a otevře se soubor DSL v editoru DSL.

    Pokud dáváte přednost, můžete vytvořit projekt instalace ručně namísto použití textové šablony. Návod, který obsahuje tento postup, najdete v kapitole 5 [testovacího prostředí sady SDK pro vizualizaci a modelování](https://code.msdn.microsoft.com/DSLToolsLab/Release/ProjectReleases.aspx?ReleaseId=4207).

### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>Odinstalace DSL, která byla nainstalována z MSI

1. V systému Windows otevřete ovládací panel **programy a funkce** .

2. Odinstalujte DSL.

3. Restartujte Visual Studio.
