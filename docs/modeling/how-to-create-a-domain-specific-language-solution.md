---
title: 'Postupy: Vytváření řešení jazyka specifického pro doménu'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: f138f1f809ae5a81aa97c571a147c679bacaa3b2
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967230"
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>Postupy: Vytváření řešení jazyka specifického pro doménu
Jazyka specifického pro doménu (DSL) se vytvoří s použitím specializovaná řešení sady Visual Studio.

## <a name="prerequisites"></a>Požadavky
 Před zahájením tohoto postupu, je třeba nejprve nainstalovat tyto komponenty:


| | |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580) |
| Visual Studio Visualization and Modeling SDK | |

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]


## <a name="creating-a-domain-specific-language-solution"></a>Vytváření řešení jazyka specifického pro doménu

#### <a name="to-create-a-domain-specific-language-solution"></a>K vytváření řešení jazyka specifického pro doménu

1. Spusťte průvodce nástroje DSL.

   1. Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.

   2. **Nový projekt** zobrazí se dialogové okno.

   3. V části **typy projektů**, rozbalte **ostatní typy projektů** uzel a klikněte na tlačítko **rozšiřitelnost**.

   4. Klikněte na tlačítko **návrháře jazyka specifického pro doménu**.

   5. V **název** zadejte název řešení. Klikněte na tlačítko **OK**.

       **Průvodce návrháře jazyka specifického pro doménu** se zobrazí.

      > [!NOTE]
      >  Název, který zadáte nejlépe, by měl být platný Visual C# identifikátor, protože může být použit pro generování kódu.

      ![Vytvoření dialogového okna DSL](../modeling/media/create_dsldialog.png)

2. Zvolte šablonu DSL.

    Na **vybrat možnosti jazyka specifického pro doménu** stránky, vyberte jednu z šablon řešení, jako **minimální jazykový**. Zvolte šablonu, která se podobá DSL, který chcete vytvořit.

    Další informace o šablonách řešení, najdete v části [výběr šablony řešení jazyka specifického pro doménu](../modeling/choosing-a-domain-specific-language-solution-template.md).

3. Zadejte příponu názvu souboru na **přípona souboru** stránky. By měl být jedinečný ve vašem počítači a ve všech počítačích, na kterém chcete nainstalovat DSL. Zobrazí se zpráva **žádné aplikace ani editory sady Visual Studio toto rozšíření využít**.

   -   Pokud přípona názvu souboru jste použili v předchozí experimentální DSL, která plně nenainstalovali, můžete vymazat jejich odhlašování pomocí **resetovat experimentální instanci** nástroj, který se nachází v nabídce sady Visual Studio SDK.

   -   Pokud jiné rozšíření sady Visual Studio, který používá tuto příponu souboru byl plně nainstalován v počítači, vezměte v úvahu odinstalujete ji. Na **nástroje** nabídky, klikněte na tlačítko **Správce rozšíření**.

4. Zkontrolujte a v případě potřeby upravit, pole na zbývajících stránkách průvodce. Pokud jste s nastavením spokojeni, klikněte na tlačítko **Dokončit**. Další informace o nastaveních, která najdete v tématu [stránky průvodce Návrhář DSL](#settings).

    Průvodce vytvoří řešení, která má dva projekty, které jsou pojmenovány **Dsl** a **DslPackage**.

   > [!NOTE]
   >  Pokud se zobrazí zpráva, která vás upozorní, není ke spuštění textové šablony z nedůvěryhodných zdrojů, klikněte na tlačítko **OK**. Můžete nastavit tato zpráva se zobrazí znovu.

## <a name="settings"></a> Na stránkách průvodce návrhářem DSL
 Můžete nechat několik polí nezmění z výchozí hodnoty. Nicméně Ujistěte se, že pole přípona souboru je nastavit.

### <a name="solution-settings-page"></a>Stránka nastavení řešení
 **Kterou šablonu chcete vaše jazyka specifického pro doménu vycházet?**
Zvolte šablonu, která se podobá DSL, který chcete vytvořit. Různé šablony poskytují pohodlný počátečních bodů. Když vyberete šablonu řešení, Průvodce zobrazí popis. Další informace o šablonách řešení, najdete v části [výběr šablony řešení jazyka specifického pro doménu](../modeling/choosing-a-domain-specific-language-solution-template.md).

 **Co chcete jazyka specifického pro doménu pojmenovat?**
Výchozí hodnota je název řešení. Kód je generován z této hodnoty. Musí být platný jako název třídy C#.

### <a name="file-extension-page"></a>Stránka přípona souboru
 **Jaká rozšíření by měly soubory modelu použití?**
Zadejte novou příponu souboru.

 Ověřte, že tato přípona souboru nebyla již byl registrován pro použití v tomto počítači následujícím způsobem:

 Podívejte se do části **další nástroje a aplikace zaregistrované ke zpracování této přípony**. Pokud se zobrazí zpráva **žádné aplikace ani editory sady Visual Studio toto rozšíření využít**, můžete použít tuto příponu souboru.

 Pokud se zobrazí seznam nástrojů nebo balíčky, proveďte jednu z následujících akcí:

-   Zadejte jinou příponu souboru.

     \- nebo –

-   Resetujte experimentální instanci sady Visual Studio. Zruší registraci všech DSL, které jste dříve vytvořili. Na **Start** nabídky, klikněte na tlačítko **všechny programy**, **Microsoft Visual Studio 2010 SDK**, **nástroje**a potom **resetovat Microsoft Visual Studio 2010 experimentální instanci**. Můžete znovu sestavit jiných DSL, který chcete znovu použít.

     \- nebo –

-   Pokud rozšíření aplikace Visual Studio, který používá tuto příponu souboru byl plně nainstalován v počítači, odinstalujte ji. Na **nástroje** nabídky, klikněte na tlačítko **Správce rozšíření**.

### <a name="product-settings-page"></a>Stránka nastavení produktu
 **Jaký je název produktu, který nový jazyk specifický pro doménu patří?**
Výchozí hodnota je název DSL.

 Tato hodnota se používá v Průzkumníku Windows (nebo Průzkumníka souborů) k popisu souborů, které mají tuto příponu souboru.

 **Jaký je název společnosti, která tento produkt patří?**
Název vaší společnosti.

 Tato hodnota je součástí souboru AssemblyInfo vlastnosti balíčku DSL.

 **Co je kořenový obor názvů pro projekty v tomto řešení?**
Výchozí hodnota pro název skládající se z vaší společnosti a názvy produktů.

### <a name="signing-page"></a>stránka Podepisování
 **Vytvořit soubor klíče se silným názvem** výchozí možností je vytvořit nový klíč k podepsání sestavení DSL.

 **Použít existující klíč se silným názvem** tuto možnost použijte, pokud chcete integrovat vašeho DSL pomocí jiného sestavení.

 Další informace o silné názvy najdete v tématu [vytvoření a použití sestavení](http://go.microsoft.com/fwlink/?LinkId=186073).

## <a name="see-also"></a>Viz také:

- [Jak se definuje jazyk specifický pro doménu](../modeling/how-to-define-a-domain-specific-language.md)
- [Glosář nástrojů jazyka specifického pro doménu](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
