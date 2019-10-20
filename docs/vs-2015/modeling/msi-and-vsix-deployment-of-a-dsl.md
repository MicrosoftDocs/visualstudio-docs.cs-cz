---
title: Nasazení MSI a VSIX pro DSL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6ce16f06-1978-4e19-8cdc-441ee65a3fb2
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 749763a9a2bb742bb3670050010f497c5c15fba4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668600"
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>Nasazení DSL v MSI a VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jazyk specifický pro doménu můžete nainstalovat na vlastní počítač nebo na jiné počítače. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] již musí být v cílovém počítači nainstalovány.

## <a name="which"></a>Volba mezi nasazením VSIX a MSI
 Existují dvě metody nasazení jazyka specifického pro doménu:

|Metoda|Výhody|
|------------|--------------|
|VSX (rozšíření [!INCLUDE[vsprvs](../includes/vsprvs-md.md)])|Velmi snadné nasazení: Zkopírujte a spusťte soubor **. vsix** z projektu DslPackage.<br /><br /> Další informace najdete v tématu [instalace a odinstalace DSL pomocí nástroje VSX](#Installing).|
|MSI (instalační soubor)|– Umožní uživateli otevřít [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dvojitým kliknutím na soubor DSL.<br />– Přidruží ikonu k typu souboru DSL v cílovém počítači.<br />– Přidruží schéma XSD (XML Schema) k typu souboru DSL. Tím se zabrání upozornění při načtení souboru do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].<br /><br /> Abyste mohli vytvořit MSI, musíte do svého řešení přidat projekt instalace.<br /><br /> Další informace najdete v tématu [Nasazení DSL pomocí souboru MSI](#msi).|

## <a name="Installing"></a>Instalace a odinstalace DSL pomocí VSX
 Pokud je vaše DSL nainstalovaná touto metodou, může uživatel otevřít soubor DSL v rámci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ale soubor nejde otevřít z Průzkumníka Windows.

#### <a name="to-install-a-dsl-by-using-the-vsx"></a>Instalace DSL pomocí VSX

1. V počítači vyhledejte soubor **. vsix** , který byl vytvořen projektem balíčku DSL.

    1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt **DslPackage** a potom klikněte na možnost **Otevřít složku v Průzkumníku Windows**.

    2. Vyhledejte soubor **bin \\ \* \\** _YourProject_ **. DslPackage. vsix**

2. Zkopírujte soubor **. vsix** do cílového počítače, do kterého chcete nainstalovat DSL. Může to být váš vlastní počítač nebo jiný.

    - Cílový počítač musí mít jednu z edic [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], která podporuje DSL v době běhu. Další informace najdete v tématu [podporované edice sady Visual Studio pro vizualizaci & Modeling SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).

    - Cílový počítač musí mít jednu z edic [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] specifikovanou v **DslPackage\source.Extensions.manifest**.

3. V cílovém počítači poklikejte na soubor **. vsix** .

     **Instalační program rozšíření sady Visual Studio** se otevře a nainstaluje rozšíření.

4. Spusťte nebo restartujte [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

5. K otestování DSL použijte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] k vytvoření nového souboru s příponou, kterou jste definovali pro DSL.

#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>Postup při odinstalaci DSL nainstalované pomocí VSX

1. V nabídce **nástroje** klikněte na **Správce rozšíření**.

2. Rozbalte položku **nainstalovaná rozšíření**.

3. Vyberte rozšíření, ve kterém je definována DSL, a pak klikněte na **odinstalovat**.

   Zřídka se vadné rozšíření nedokáže načíst a vytvoří sestavu v okně chyb, ale nezobrazí se ve Správci rozšíření. V takovém případě můžete odebrat rozšíření odstraněním souboru z:

   *Localappdata* **\Microsoft\VisualStudio\10.0\Extensions**

## <a name="msi"></a>Nasazení DSL do MSI
 Definováním souboru MSI (Instalační služba systému Windows) pro vaši DSL můžete uživatelům dovolit otevírat soubory DSL z Průzkumníka Windows. K příponě názvu souboru můžete také přidružit ikonu a krátký popis. Kromě toho může MSI nainstalovat XSD, které lze použít k ověření souborů DSL. Pokud chcete, můžete do MSI přidat další součásti, které se nainstalují současně.

 Další informace o souborech MSI a dalších možnostech nasazení najdete v tématu [nasazení aplikací, služeb a součástí](../deployment/deploying-applications-services-and-components.md).

 Chcete-li vytvořit soubor MSI, přidejte projekt instalace do řešení [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Nejjednodušší způsob, jak vytvořit projekt instalace, je použít šablonu CreateMsiSetupProject.tt, kterou si můžete stáhnout z [webu VMSDK](http://go.microsoft.com/fwlink/?LinkID=186128).

#### <a name="to-deploy-a-dsl-in-an-msi"></a>Nasazení DSL do MSI

1. Nastavte `InstalledByMsi` v manifestu rozšíření. Tím se zabrání instalace a odinstalace VSX s výjimkou MSI. To je důležité, pokud budete do MSI zahrnout i další součásti.

   1. Otevřít DslPackage\source.extension.tt

   2. Před `<SupportedProducts>` vložte následující řádek:

       ```
       <InstalledByMsi>true</InstalledByMsi>
       ```

2. Vytvoří nebo upraví ikonu, která bude představovat vaši DSL v Průzkumníkovi Windows. Například upravte **DslPackage\Resources\File.ico**

3. Ujistěte se, že jsou správné následující atributy DSL:

   - V Průzkumníku DSL klikněte na kořenový uzel a v okno Vlastnosti zkontrolujte:

       - Popis

       - Version

   - Klikněte na uzel **Editor** a v okno Vlastnosti klikněte na **ikonu**. Nastavte hodnotu tak, aby odkazovala na soubor ikony v **DslPackage\Resources**, jako je **File. ico.**

   - V nabídce **sestavení** otevřete **Configuration Manager**a vyberte konfiguraci, kterou chcete sestavit, například **vydaná verze** nebo **ladění**.

4. Přejít na [domovskou stránku vizualizace a modelování sady SDK](http://go.microsoft.com/fwlink/?LinkID=186128)a na kartě **stažené soubory** stáhněte **CreateMsiSetupProject.TT**.

5. Přidejte **CreateMsiSetupProject.TT** do projektu DSL.

    [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vytvoří soubor s názvem **CreateMsiSetupProject. vdproj**.

6. V Průzkumníku Windows zkopírujte DSL \\ *. vdproj do nové složky s názvem Setup.

    (Pokud chcete, můžete teď vyloučit CreateMsiSetupProject.tt z vašeho projektu DSL.)

7. V **Průzkumník řešení**přidejte **instalační \\ \*. vdproj** jako existující projekt.

8. V nabídce **projekt** klikněte na **závislosti projektu**.

    V dialogovém okně **závislosti projektu** vyberte projekt instalace.

    Zaškrtněte políčko vedle **DslPackage**.

9. Znovu sestavte řešení.

10. V Průzkumníku Windows vyhledejte v projektu instalace sestavený soubor MSI.

     Zkopírujte soubor MSI do počítače, na kterém chcete nainstalovat DSL. Dvakrát klikněte na soubor MSI. Spustí se instalační program.

11. V cílovém počítači vytvořte nový soubor, který má příponu souboru vaší DSL. Ověřte, že:

    - V zobrazení seznam Průzkumníka Windows se zobrazí soubor s ikonou a popisem, který jste definovali.

    - Když dvakrát kliknete na soubor, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] spustí a otevře se soubor DSL v editoru DSL.

    Pokud dáváte přednost, můžete vytvořit projekt instalace ručně namísto použití textové šablony. Návod, který obsahuje tento postup, najdete v kapitole 5 [testovacího prostředí sady SDK pro vizualizaci a modelování](http://go.microsoft.com/fwlink/?LinkId=208878).

#### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>Odinstalace DSL, která byla nainstalována z MSI

1. V systému Windows otevřete ovládací panel **programy a funkce** .

2. Odinstalujte DSL.

3. Restartujte sadu Visual Studio.
