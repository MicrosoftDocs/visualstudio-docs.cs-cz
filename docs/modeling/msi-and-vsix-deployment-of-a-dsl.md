---
title: Nasazení DSL v MSI a VSIX
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 2f5b8948d94c64d84b33714a4b432a46bfb73b59
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49931542"
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>Nasazení DSL v MSI a VSIX
Jazyka specifického pro doménu můžete nainstalovat na vlastním počítači nebo v jiných počítačích. Visual Studio musí být nainstalována na cílovém počítači.

## <a name="which"></a> Volba mezi nasazení MSI a VSIX
 Nasazení jazyka specifického pro doménu dvěma způsoby:

|Metoda|Výhody|
|-|-|
|VSX (rozšíření sady Visual Studio)|Velmi snadno se nasazuje: kopírování a spustit **VSIX** soubor z projektu DslPackage.<br /><br /> Další informace najdete v části [instalace a odinstalace DSL pomocí VSX](#Installing).|
|MSI (instalačního programu soubor)|– Umožňuje uživateli otevřít Visual Studio poklikáním souboru DSL.<br />-Přidruží ikony typu souboru DSL v cílovém počítači.<br />– Tento typ souboru DSL přidruží XSD (XML schema). Tím se vyhnete upozornění při načítání souboru do sady Visual Studio.<br /><br /> Nastavení projektu musíte přidat do svého řešení Chcete-li vytvořit instalační služba MSI.<br /><br /> Další informace najdete v tématu [nasazení DSL s použitím souboru MSI](#msi).|

## <a name="Installing"></a> Instalace a odinstalace DSL pomocí VSX
 Při instalaci vašeho DSL pomocí této metody může uživatel otevřít souboru DSL ze sady Visual Studio, ale soubor nelze otevřít v Průzkumníku Windows.

#### <a name="to-install-a-dsl-by-using-the-vsx"></a>Instalace DSL pomocí VSX

1. V počítači, vyhledejte **VSIX** soubor, který byl vytvořen vaším projektem DSL balíčku.

   1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **DslPackage** projektu a pak klikněte na tlačítko **otevřít složku v Průzkumníku Windows**.

   2.  Vyhledejte soubor **bin\\\*\\**_YourProject_**. DslPackage.vsix**

2. Kopírovat **VSIX** souboru k cílovému počítači, na kterém chcete nainstalovat DSL. To může být vlastní počítač nebo jiný.

   - Cílový počítač musí mít některou z edicí systému [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] DSL, která podporuje v době běhu. Další informace najdete v tématu [podporované edice sady Visual Studio pro Visualization & Modeling SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).

   - Cílový počítač musí mít některou z edicí sady Visual Studio podle **DslPackage\source.extensions.manifest**.

3. Na cílovém počítači, dvakrát klikněte **VSIX** souboru.

    **Instalační program rozšíření sady Visual Studio** otevře a nainstaluje rozšíření.

4. Spusťte nebo restartujte [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].

5. Pokud chcete otestovat DSL, vytvořte nový soubor, který má příponu, která jste definovali pro vašeho DSL pomocí sady Visual Studio.

#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>Chcete-li odinstalovat DSL, která byla nainstalována pomocí VSX

1. Na **nástroje** nabídky, klikněte na tlačítko **Správce rozšíření**.

2. Rozbalte **nainstalovaná rozšíření**.

3. Vyberte rozšíření, ve kterém je definována DSL a pak klikněte na tlačítko **odinstalovat**.

   Jen zřídka se chybné rozšíření se nepodaří načíst a vytvoří sestavu v okně chyb, ale nezobrazí ve Správci rozšíření. V takovém případě můžete odebrat rozšíření odstraněním souboru z:

   *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**

## <a name="msi"></a> Nasazení DSL v MSI
 Definováním soubor MSI (Instalační program Windows) pro vaše DSL umožňuje uživatelům otevírat soubory DSL z Průzkumníka Windows. Můžete taky přidružit ikonu a krátký popis vašeho příponu názvu souboru. Kromě toho soubor MSI můžete nainstalovat, který slouží k ověření DSL soubory XSD. Pokud chcete, můžete přidat další součásti do MSI, který se nainstaluje ve stejnou dobu.

 Další informace o souborech MSI a další možnosti nasazení najdete v tématu [nasazování aplikací, služeb a komponent](../deployment/deploying-applications-services-and-components.md).

 Pokud chcete vytvořit soubor MSI, přidat nastavení projektu do řešení sady Visual Studio. Nejjednodušší způsob vytváření projektu instalace je použití šablony CreateMsiSetupProject.tt, kterou si můžete stáhnout z [vmsdk následující položky lokality](http://go.microsoft.com/fwlink/?LinkID=186128).

#### <a name="to-deploy-a-dsl-in-an-msi"></a>Nasazení DSL v MSI

1. Nastavte `InstalledByMsi` v manifestu rozšíření. To brání VSX nainstalovat a odinstalovat s výjimkou MSI. To je důležité, pokud bude obsahovat jiné komponenty v MSI.

   1.  Open DslPackage\source.extension.tt

   2.  Vložte následující řádek před `<SupportedProducts>`:

       ```xml
       <InstalledByMsi>true</InstalledByMsi>
       ```

2. Vytvořte nebo upravte ikonu, která bude představovat vaše DSL v Průzkumníku Windows. Můžete třeba upravit **DslPackage\Resources\File.ico**

3. Ujistěte se, že správnost tohoto kódu DSL následující atributy:

   -   V Průzkumníku DSL klikněte na kořenový uzel a v okně Vlastnosti zkontrolujte:

       -   Popis

       -   Version

   -   Klikněte na tlačítko **Editor** uzlu a v okně Vlastnosti klikněte na tlačítko **ikonu**. Nastavte hodnotu na odkazovat na soubor ikony v **DslPackage\Resources**, jako například **File.ico**

   -   Na **sestavení** nabídce otevřete **nástroje Configuration Manager**a vyberte konfiguraci, kterou chcete sestavit, například **vydání** nebo **ladění** .

4. Přejděte na [Visualization and Modeling SDK domovskou stránku](http://go.microsoft.com/fwlink/?LinkID=186128)a od **stáhne** kartu, stáhněte si **CreateMsiSetupProject.tt**.

5. Přidat **CreateMsiSetupProject.tt** do projektu Dsl.

    Visual Studio vytvoří soubor s názvem **CreateMsiSetupProject.vdproj**.

6. V Průzkumníku Windows, zkopírujte Dsl\\\*.vdproj do nové složky s názvem instalační program.

    (Pokud chcete, můžete nyní vyloučit CreateMsiSetupProject.tt z projektu Dsl.)

7. V **Průzkumníka řešení**, přidejte **nastavení\\\*.vdproj** jako existující projekt.

8. Na **projektu** nabídky, klikněte na tlačítko **závislosti projektu**.

    V **závislosti projektu** dialogového okna, vyberte projekt instalace.

    Zaškrtněte políčko vedle položky **DslPackage**.

9. Znovu sestavte řešení.

10. V Průzkumníku Windows vyhledejte soubor Instalační služby MSI sestavené ve vašem projektu instalace.

     Zkopírujte soubor MSI do počítače, na kterém chcete nainstalovat vašeho DSL. Poklikejte na soubor MSI. Instalační program spustí.

11. V cílovém počítači vytvořte nový soubor, který má příponu souboru tohoto kódu DSL. Ověřte, že:

    -   Soubor se v zobrazení seznamu Windows Explorer, zobrazí ikonu a popis, který jste definovali.

    -   Když dvakrát klikněte na soubor, spustí aplikace Visual Studio a otevře soubor DSL v editoru DSL.

    Pokud dáváte přednost, můžete vytvořit projekt instalace ručně, namísto použití textové šablony. Návod, který zahrnuje tento postup najdete v kapitole 5 [Visualization and Modeling SDK Lab](http://go.microsoft.com/fwlink/?LinkId=208878).

#### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>Chcete-li odinstalovat DSL, která byla nainstalovaná z MSI

1.  Ve Windows, otevřete **programy a funkce** ovládacích panelech.

2.  Odinstalujte DSL.

3.  Restartujte sadu Visual Studio.