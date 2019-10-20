---
title: Definování a instalace rozšíření modelování | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending
- UML model, extending
ms.assetid: 82a58dc5-c7cf-4521-a6da-7ff09cd0de9d
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 66a9cdab1284d015e2ea76162d240b6a1232d90f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669919"
---
# <a name="define-and-install-a-modeling-extension"></a>Definování a instalace rozšíření modelování
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V aplikaci Visual Studio můžete definovat rozšíření pro modelování diagramů. Tímto způsobem můžete diagramy a modely přizpůsobit vašim potřebám. Můžete například definovat příkazy nabídky, profily UML, ověřovací omezení a položky panelu nástrojů. V jednom rozšíření můžete definovat několik komponent. Tato rozšíření můžete také distribuovat ostatním uživatelům aplikace Visual Studio ve formě [rozšíření integrace sady Visual Studio (VSIX)](http://go.microsoft.com/fwlink/?LinkId=160780). VSIX můžete vytvořit pomocí projektu VSIX v aplikaci Visual Studio.

## <a name="requirements"></a>Požadavky
 Viz [požadavky](../modeling/extend-uml-models-and-diagrams.md#Requirements).

 Chcete-li zjistit, které verze aplikace Visual Studio tuto funkci podporují, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="creating-a-modeling-extension-solution"></a>Vytvoření řešení rozšíření pro modelování
 Chcete-li definovat rozšíření modelování, je nutné vytvořit řešení, které obsahuje tyto projekty:

- Projekt rozšíření [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Integration Extension (VSIX). Tím se vygeneruje soubor, který funguje jako instalační program pro komponenty rozšíření.

- Projekt knihovny tříd, který je vyžadován pro součásti, které obsahují kód programu.

  Pokud chcete vytvořit rozšíření, které má několik komponent, můžete je vyvíjet v jednom řešení. Potřebujete pouze jeden projekt VSIX.

  Komponenty, které nevyžadují kód, jako jsou vlastní prvky sady nástrojů a vlastní profily UML, lze přidat přímo do projektu VSIX bez použití samostatných projektů knihovny tříd. Komponenty, které vyžadují programový kód, jsou snáze definovány v samostatném projektu knihovny tříd. Komponenty, které vyžadují kód, zahrnují obslužné rutiny gesta, příkazy nabídky a ověřovací kód.

#### <a name="to-create-a-class-library-project-for-menu-commands-gesture-handlers-or-validation"></a>Vytvoření projektu knihovny tříd pro příkazy nabídky, obslužné rutiny gest nebo ověřování

1. V nabídce **soubor** klikněte na příkaz **Nový**, **projekt**.

2. V části **Nainstalované šablony**vyberte **možnost C# Visual** nebo **Visual Basic**a pak zvolte možnost **Knihovna tříd**.

#### <a name="to-create-a-vsix-project"></a>Vytvoření projektu VSIX

1. Pokud vytváříte komponentu s kódem, je nejjednodušší vytvořit projekt knihovny tříd jako první. Do tohoto projektu přidáte svůj kód.

2. Vytvořte projekt VSIX.

    1. V **Průzkumník řešení**v místní nabídce řešení vyberte možnost **Přidat**, **Nový projekt**.

    2. V části **Nainstalované šablony**rozbalte **položku C# Visual** nebo **Visual Basic**a potom vyberte možnost **rozšiřitelnost**. V prostředním sloupci vyberte **projekt VSIX**.

3. Nastavte projekt VSIX jako projekt po spuštění řešení.

    - V Průzkumník řešení v místní nabídce projektu VSIX vyberte **nastavit jako spouštěný projekt**.

4. Otevřete **source. extension. vsixmanifest**. Soubor se otevře v editoru manifestu.

5. Na kartě **metadata** nastavte název a popisné pole VSIX.

6. Na kartě **cíle instalace** vyberte možnost **nové** a jako cíl nastavte verzi sady Visual Studio.

7. Na kartě **assets (prostředky** ) přidejte své komponenty do rozšíření sady Visual Studio.

    1. Klikněte na tlačítko **Nový**.

    2. Pro komponentu s kódem nastavte tato pole v dialogovém okně **Přidat nový prostředek** :

        |||
        |-|-|
        |**Zadejte**  =|**Microsoft. VisualStudio. MefComponent**|
        |@No__t_1 **zdroje**|**Projekt v aktuálním řešení**|
        |@No__t_1 **projektu**|*Váš projekt knihovny tříd*|
        |**Vložit do této složky**  =|*obsahovat*|

         Další typy komponent naleznete v odkazech v následující části.

## <a name="developing-the-component"></a>Vývoj součásti
 Pro každou komponentu, jako je například příkaz nabídky nebo obslužná rutina gesta, je nutné definovat samostatnou obslužnou rutinu. Můžete vložit několik obslužných rutin do stejného projektu knihovny tříd. Následující tabulka shrnuje různé druhy obslužných rutin.

|Typ rozšíření|Téma|Jak jsou obvykle deklarovány jednotlivé komponenty|
|--------------------|-----------|----------------------------------------------|
|Příkaz nabídky|[Definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md)|`[ClassDesignerExtension]`<br /><br /> `// or other diagram types`<br /><br /> `[Export(typeof(ICommandExtension))]`<br /><br /> `public class MyCommand : ICommandExtension`<br /><br /> `{...`|
|Přetahování nebo poklikání|[Definování obslužné rutiny gest v diagramu modelování](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)|`[ClassDesignerExtension]`<br /><br /> `// or other diagram types`<br /><br /> `[Export(typeof(IGestureExtension))]`<br /><br /> `public class MyGesture : IGestureExtension`<br /><br /> `{...`|
|Omezení ověření|[Definování omezení ověřování pro modely UML](../modeling/define-validation-constraints-for-uml-models.md)|`[Export(typeof(     System.Action<ValidationContext, object>))]`<br /><br /> `[ValidationMethod(ValidationCategories.Save`<br /><br /> `&#124; ValidationCategories.Menu)]`<br /><br /> `public void ValidateSomething`<br /><br /> `(ValidationContext context, IClassifier elementToValidate)`<br /><br /> `{...}`|
|Obslužná rutina události propojení pracovní položky|[Definování obslužné rutiny odkazu pracovní položky](../modeling/define-a-work-item-link-handler.md)|`[Export(typeof(ILinkedWorkItemExtension))]`<br /><br /> `public class MyWorkItemEventHandler : ILinkedWorkItemExtension`<br /><br /> `{...`|
|Profil UML|[Definování profilu pro rozšíření UML](../modeling/define-a-profile-to-extend-uml.md)|(Bude definováno)|
|Položka sady nástrojů|[Definování vlastní položky sady nástrojů pro modelování](../modeling/define-a-custom-modeling-toolbox-item.md)|(Bude definováno)|

## <a name="running-an-extension-during-its-development"></a>Spuštění rozšíření během vývoje

#### <a name="to-run-an-extension-during-its-development"></a>Spuštění rozšíření během vývoje

1. V nabídce **ladění** [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] vyberte možnost **Spustit ladění**.

     Sestavení projektu a nová instance [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] začínají v experimentálním režimu.

    - Případně můžete zvolit možnost **Spustit bez ladění**. Tím se zkracuje čas potřebný ke spuštění programu.

2. Vytvořte nebo otevřete projekt modelování v experimentální instanci aplikace Visual Studio a vytvořte nebo otevřete diagram.

     Vaše rozšíření se načte a spustí.

3. Pokud jste použili příkaz **Spustit bez ladění** , ale chcete použít ladicí program, vraťte se k hlavní instanci aplikace Visual Studio. V nabídce **ladění** klikněte na **připojit k procesu**. V dialogovém okně vyberte experimentální instanci aplikace Visual Studio, která má název programu **devenv**.

## <a name="Installing"></a>Instalace a odinstalace rozšíření
 Provedením následujících kroků spusťte rozšíření v hlavní instanci aplikace Visual Studio buď na svém vlastním počítači, nebo na jiných počítačích.

1. V počítači vyhledejte soubor **. vsix** , který byl vytvořen vaším projektem rozšíření.

    1. V **Průzkumník řešení**v místní nabídce projektu a pak zvolte možnost **Otevřít složku v Průzkumníku Windows**.

    2. Vyhledejte soubor **bin \\ \* \\** _YourProject_ **. vsix**

2. Zkopírujte soubor **. vsix** do cílového počítače, do kterého chcete nainstalovat rozšíření. Může to být váš vlastní počítač nebo jiný.

    - Cílový počítač musí mít jednu z edic sady Visual Studio, kterou jste zadali na kartě **cíle instalace** **zdrojového kódu. extension. vsixmanifest**.

3. V cílovém počítači otevřete soubor **. vsix** , například dvojitým kliknutím na něj.

     **Instalační program rozšíření sady Visual Studio** se otevře a nainstaluje rozšíření.

4. Spusťte nebo restartujte aplikaci Visual Studio.

#### <a name="to-uninstall-an-extension"></a>Odinstalace rozšíření

1. V nabídce **nástroje** klikněte na možnost **rozšíření a aktualizace**.

2. Rozbalte položku **nainstalovaná rozšíření**.

3. Vyberte rozšíření a pak klikněte na **odinstalovat**.

   Zřídka se vadné rozšíření nedokáže načíst a vytvoří sestavu v okně chyb, ale nezobrazí se ve Správci rozšíření. V takovém případě můžete odebrat rozšíření odstraněním souboru z následujícího umístění, kde *% localappdata%* je obvykle *jednotka*: \Users \\*username*\AppData\Local:

   *% Localappdata%* **\Microsoft\VisualStudio \\ [verze] \Extensions**

## <a name="see-also"></a>Viz také
 [Definování profilu pro rozšiřování UML](../modeling/define-a-profile-to-extend-uml.md) [Definování vlastní položky sady nástrojů pro modelování](../modeling/define-a-custom-modeling-toolbox-item.md) definování [omezení ověření pro modely UML](../modeling/define-validation-constraints-for-uml-models.md) [Definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md)
