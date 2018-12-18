---
title: 'Postupy: vytváření řešení jazyka specifického pro doménu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
ms.assetid: e585b63b-34d2-405a-8d81-39ea22317975
caps.latest.revision: 43
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 2650afc2172cdcceca892d4ad19a05becac3e472
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49908915"
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>Postupy: Vytváření řešení jazyka specifického pro doménu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vytvoření jazyka specifického pro doménu (DSL) pomocí specializovaný [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] řešení.  
  
## <a name="prerequisites"></a>Požadavky  
 Před zahájením tohoto postupu, je třeba nejprve nainstalovat tyto komponenty:  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|  
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|  
|Visual Studio Visualization and Modeling SDK|[http://go.microsoft.com/fwlink/?LinkID=185581](http://go.microsoft.com/fwlink/?LinkID=185581)|  
  
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
  
      ![Vytvoření dialogového okna DSL](../modeling/media/create-dsldialog.png "Create_DSLDialog")  
  
2. Zvolte šablonu DSL.  
  
    Na **vybrat možnosti jazyka specifického pro doménu** stránky, vyberte jednu z šablon řešení, jako **minimální jazykový**. Zvolte šablonu, která se podobá DSL, který chcete vytvořit.  
  
    Další informace o šablonách řešení, najdete v části [výběr šablony řešení jazyka specifického pro doménu](../modeling/choosing-a-domain-specific-language-solution-template.md).  
  
3. Zadejte příponu názvu souboru na **přípona souboru** stránky. By měl být jedinečný ve vašem počítači a ve všech počítačích, na kterém chcete nainstalovat DSL. Zobrazí se zpráva **žádné aplikace ani editory sady Visual Studio toto rozšíření využít**.  
  
   -   Pokud přípona názvu souboru jste použili v předchozí experimentální DSL, která plně nenainstalovali, můžete vymazat jejich odhlašování pomocí **resetovat experimentální instanci** nástroj, který se nachází v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nabídky sady SDK.  
  
   -   Pokud jiný [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozšíření, která používá tuto příponu souboru plně nainstalovaný v počítači, zvažte jeho odinstalaci. Na **nástroje** nabídky, klikněte na tlačítko **Správce rozšíření**.  
  
4. Zkontrolujte a v případě potřeby upravit, pole na zbývajících stránkách průvodce. Pokud jste s nastavením spokojeni, klikněte na tlačítko **Dokončit**. Další informace o nastaveních, která najdete v tématu [stránky průvodce Návrhář DSL](#settings).  
  
    Průvodce vytvoří řešení, která má dva projekty, které jsou pojmenovány **Dsl** a **DslPackage**.  
  
   > [!NOTE]
   >  Pokud se zobrazí zpráva, která vás upozorní, není ke spuštění textové šablony z nedůvěryhodných zdrojů, klikněte na tlačítko **OK**. Můžete nastavit tato zpráva se zobrazí znovu.  
  
##  <a name="settings"></a> Na stránkách průvodce návrhářem DSL  
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
  
-   Obnovit [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] experimentální instanci aplikace. Zruší registraci všech DSL, které jste dříve vytvořili. Na **Start** nabídky, klikněte na tlačítko **všechny programy**, **Microsoft Visual Studio 2010 SDK**, **nástroje**a potom **resetovat Microsoft Visual Studio 2010 experimentální instanci**. Můžete znovu sestavit jiných DSL, který chcete znovu použít.  
  
     \- nebo –  
  
-   Pokud [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozšíření, která používá tuto příponu souboru plně nainstalovaný v počítači, odinstalujte ho. Na **nástroje** nabídky, klikněte na tlačítko **Správce rozšíření**.  
  
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
 **Vytvořit soubor klíče se silným názvem**  
 Výchozí možností je vytvořit nový klíč k podepsání sestavení DSL.  
  
 **Použít existující klíč se silným názvem**  
 Tuto možnost použijte, pokud chcete integrovat vašeho DSL pomocí jiného sestavení.  
  
 Další informace o silné názvy najdete v tématu [vytvoření a použití sestavení](http://go.microsoft.com/fwlink/?LinkId=186073).  
  
## <a name="see-also"></a>Viz také  
 [Jak se definuje jazyk specifický pro doménu](../modeling/how-to-define-a-domain-specific-language.md)   
 [Glosář nástrojů jazyka specifického pro doménu](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



