---
title: Definování a instalace rozšíření modelování | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML - extending
- UML model, extending
ms.assetid: 82a58dc5-c7cf-4521-a6da-7ff09cd0de9d
caps.latest.revision: 39
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 6f7895916cc4ee877c53b056f703d8e46b64b409
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51805564"
---
# <a name="define-and-install-a-modeling-extension"></a>Definování a instalace rozšíření modelování
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V sadě Visual Studio můžete definovat rozšíření pro modelování diagramů. Tímto způsobem můžete přizpůsobit diagramy a modely pro vaše konkrétní potřeby. Například můžete definovat příkazy nabídek, profilů UML, omezení ověření a položky panelu nástrojů. Můžete definovat několik komponent v jedné rozšíření. Můžete také distribuovat ostatním uživatelům aplikace Visual Studio ve formě tato rozšíření [rozšíření integrace Visual Studio (VSIX)](http://go.microsoft.com/fwlink/?LinkId=160780). Můžete vytvořit rozšíření VSIX použití projektu VSIX v sadě Visual Studio.  
  
## <a name="requirements"></a>Požadavky  
 Zobrazit [požadavky](../modeling/extend-uml-models-and-diagrams.md#Requirements).  
  
 Tuto funkci podporovat kterou verzí sady Visual Studio najdete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="creating-a-modeling-extension-solution"></a>Vytvoření řešení rozšíření modelování  
 Chcete-li definovat rozšíření modelování, musíte vytvořit řešení obsahující projekty:  
  
- A [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projekt integrace Extension (VSIX). Tím se vytvoří soubor, který funguje jako instalační program pro součásti tohoto rozšíření.  
  
- Projekt knihovny tříd, vyžaduje se pro součásti, které obsahují kód programu.  
  
  Pokud chcete, aby rozšíření, které má několik součástí, je možné vyvinout v jediném řešení. Budete potřebovat pouze jeden projekt VSIX.  
  
  Součásti, které nevyžadují kód, jako je například vlastní sady nástrojů položky a vlastních profilů UML lze přidat přímo do projektu VSIX bez použití samostatné třídy knihovny projektů. Komponenty, které vyžadují programového kódu jsou snadněji definované v projektu knihovny samostatné třídy. Komponenty, které vyžadují kód zahrnují obslužnými rutinami gest, příkazy nabídky a kód pro ověření.  
  
#### <a name="to-create-a-class-library-project-for-menu-commands-gesture-handlers-or-validation"></a>Chcete-li vytvořit projekt knihovny tříd pro ověření, obslužné rutiny gesta nebo příkazů nabídky  
  
1.  Na **souboru** nabídce zvolte **nový**, **projektu**.  
  
2.  V části **nainstalované šablony**vyberte **Visual C#** nebo **jazyka Visual Basic**, klikněte na tlačítko **knihovny tříd**.  
  
#### <a name="to-create-a-vsix-project"></a>Vytvoření projektu VSIX  
  
1.  Pokud vytváříte komponentu s kódem, je nejjednodušší nejprve vytvořte projekt knihovny tříd. Váš kód přidá do projektu.  
  
2.  Vytvořte projekt VSIX.  
  
    1.  V **Průzkumníka řešení**, v místní nabídce řešení zvolte **přidat**, **nový projekt**.  
  
    2.  V části **nainstalované šablony**, rozbalte **Visual C#** nebo **jazyka Visual Basic**a pak vyberte **rozšiřitelnost**. V prostředním sloupci zvolte **projekt VSIX**.  
  
3.  Nastavte projekt VSIX jako projekt po spuštění řešení.  
  
    -   V Průzkumníku řešení v místní nabídce projektu VSIX zvolte **nastavit jako spouštěný projekt**.  
  
4.  Otevřít **source.extension.vsixmanifest**. Soubor se otevře v editoru manifestu.  
  
5.  Na **metadat** kartu, nastavte název a popisné pole rozšíření VSIX.  
  
6.  Na **cíle instalace** kartě **nový** a nastavte verze sady Visual Studio jako cíle.  
  
7.  Na **prostředky** kartu, přidání komponenty do rozšíření aplikace Visual Studio.  
  
    1.  Zvolte **nové**.  
  
    2.  Pro součást s kódem, nastavte těchto polí **přidat nové aktivum** dialogové okno:  
  
        |||  
        |-|-|  
        |**Typ** =|**Microsoft.VisualStudio.MefComponent**|  
        |**Zdroj** =|**Projekt v aktuálním řešení**|  
        |**Projekt** =|*Váš projekt knihovny tříd*|  
        |**Vložit do této složky** =|*(prázdné)*|  
  
         Jiné typy komponenty najdete na odkazech v další části.  
  
## <a name="developing-the-component"></a>Vývoj komponenty  
 Pro každou komponentu, jako je například obslužnou rutinu příkazu nebo gesta nabídky je nutné definovat zvláštní obslužné rutiny. Několik obslužných rutin můžete umístit do stejného projektu knihovny tříd. Následující tabulka shrnuje různé druhy obslužné rutiny.  
  
|Typ rozšíření|Téma|Jak je obvykle deklarované jednotlivé komponenty|  
|--------------------|-----------|----------------------------------------------|  
|Příkaz nabídky|[Definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md)|`[ClassDesignerExtension]`<br /><br /> `// or other diagram types`<br /><br /> `[Export(typeof(ICommandExtension))]`<br /><br /> `public class MyCommand : ICommandExtension`<br /><br /> `{...`|  
|Přetáhněte myší nebo dvakrát klikněte na|[Definování obslužné rutiny gest v diagramu modelování](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)|`[ClassDesignerExtension]`<br /><br /> `// or other diagram types`<br /><br /> `[Export(typeof(IGestureExtension))]`<br /><br /> `public class MyGesture : IGestureExtension`<br /><br /> `{...`|  
|Omezení ověření|[Definování omezení ověřování pro modely UML](../modeling/define-validation-constraints-for-uml-models.md)|`[Export(typeof(     System.Action<ValidationContext, object>))]`<br /><br /> `[ValidationMethod(ValidationCategories.Save`<br /><br /> `&#124; ValidationCategories.Menu)]`<br /><br /> `public void ValidateSomething`<br /><br /> `(ValidationContext context, IClassifier elementToValidate)`<br /><br /> `{...}`|  
|Obslužné rutiny propojení položky práce|[Definování obslužné rutiny odkazu pracovní položky](../modeling/define-a-work-item-link-handler.md)|`[Export(typeof(ILinkedWorkItemExtension))]`<br /><br /> `public class MyWorkItemEventHandler : ILinkedWorkItemExtension`<br /><br /> `{...`|  
|Profilu UML|[Definování profilu pro rozšíření UML](../modeling/define-a-profile-to-extend-uml.md)|(Chcete-li definován)|  
|Položku sady nástrojů|[Definování vlastní položky sady nástrojů pro modelování](../modeling/define-a-custom-modeling-toolbox-item.md)|(Chcete-li definován)|  
  
## <a name="running-an-extension-during-its-development"></a>Spuštění rozšíření během vývoje  
  
#### <a name="to-run-an-extension-during-its-development"></a>Ke spuštění rozšíření při jeho vývoji  
  
1.  V [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] **ladění** nabídce zvolte **spustit ladění**.  
  
     Sestavování projektu a novou instanci třídy [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] začne v experimentálním režimu.  
  
    -   Případně můžete použít **spustit bez ladění**. To snižuje čas potřebný ke spuštění programu.  
  
2.  Vytvořte nebo otevřete projekt modelování v experimentální instanci sady Visual Studio a vytvořte nebo otevřete diagram.  
  
     Rozšíření načte a spustí.  
  
3.  Pokud jste použili **spustit bez ladění** ale budete chtít použít ladicí program, přejděte zpět na hlavní instanci aplikace Visual Studio. Na **ladění** nabídky, klikněte na tlačítko **připojit k procesu**. V dialogovém okně vyberte experimentální instanci sady Visual Studio, který má název programu **devenv**.  
  
##  <a name="Installing"></a> Instalace a odinstalace rozšíření  
 Proveďte tyto kroky a spusťte rozšíření v instanci hlavní aplikace Visual Studio na vlastním počítači nebo na jiném počítači.  
  
1.  V počítači, vyhledejte **VSIX** soubor, který byl vytvořen vaším projektem rozšíření.  
  
    1.  V **Průzkumníka řešení**, v místní nabídce vašeho projektu a klikněte na tlačítko **otevřít složku v Průzkumníku Windows**.  
  
    2.  Vyhledejte soubor **bin\\\*\\**_YourProject_**VSIX.**  
  
2.  Kopírovat **VSIX** souboru k cílovému počítači, na kterém chcete nainstalovat rozšíření. To může být vlastní počítač nebo jiný.  
  
    -   Cílový počítač musí mít některou z edicí sady Visual Studio, který jste zadali na **cíle instalace** kartě **source.extension.vsixmanifest**.  
  
3.  V cílovém počítači, otevřete **VSIX** souboru, například poklepáním.  
  
     **Instalační program rozšíření sady Visual Studio** otevře a nainstaluje rozšíření.  
  
4.  Spusťte nebo restartujte sadu Visual Studio.  
  
#### <a name="to-uninstall-an-extension"></a>Odinstalace rozšíření  
  
1. Na **nástroje** nabídky, klikněte na tlačítko **rozšíření a aktualizace**.  
  
2. Rozbalte **nainstalovaná rozšíření**.  
  
3. Vyberte požadované rozšíření a pak klikněte na tlačítko **odinstalovat**.  
  
   Jen zřídka se chybné rozšíření se nepodaří načíst a vytvoří sestavu v okně chyb, ale nezobrazí ve Správci rozšíření. V takovém případě můžete odebrat rozšíření odstraněním souboru z následujícího umístění kde *% LocalAppData %* je obvykle *DriveName*: \Users\\*uživatelskéjméno*\AppData\Local:  
  
   *% LocalAppData %* **\Microsoft\VisualStudio\\\Extensions [verze]**  
  
## <a name="see-also"></a>Viz také  
 [Definování profilu pro rozšíření UML](../modeling/define-a-profile-to-extend-uml.md)   
 [Definování vlastní položky sady nástrojů pro modelování](../modeling/define-a-custom-modeling-toolbox-item.md)   
 [Definování omezení ověření pro modely UML](../modeling/define-validation-constraints-for-uml-models.md)   
 [Definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md)



