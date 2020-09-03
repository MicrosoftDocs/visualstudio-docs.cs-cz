---
title: Generování kódu z diagramů tříd UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.logicalclassdiagram.shapes.properties.Templates
- vs.teamarch.logicalclassdiagram.shapes.properties.Templates.TextTransformationDataCollectionEditor
helpviewer_keywords:
- code generation, UML class diagrams
- class diagrams - UML, generating code
- UML diagrams, generating code
ms.assetid: 2790e64d-7728-4c2e-a4dd-4131e795f730
caps.latest.revision: 53
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 75120b2f09c2eba3254a1b94e78875d8130c5225
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666135"
---
# <a name="generate-code-from-uml-class-diagrams"></a>Generování kódu z diagramů tříd UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chcete-li generovat kód jazyka Visual C# .NET z diagramů tříd UML v aplikaci Visual Studio, použijte příkaz **generovat kód** . Ve výchozím nastavení tento příkaz vygeneruje typ jazyka C# pro každý vybraný typ modelu UML. Toto chování lze upravit a rozšířit úpravou nebo zkopírováním textových šablon, které generují kód. Lze určit různá chování pro typy, které jsou obsaženy v různých balíčcích modelu.

 Příkaz **generovat kód** je vhodný zejména pro generování kódu z výběru prvků uživatele a pro generování jednoho souboru pro každou třídu UML nebo jiný prvek. Například, tento snímek obrazovky ukazuje dva soubory jazyka C#, které byly vytvořeny ze dvou tříd modelu UML.

 Alternativně, pokud chcete vygenerovat kód, ve kterém generované soubory nemají vztah 1:1 s prvky UML, můžete zvážit zápis textových šablon, které jsou vyvolány příkazem **Transform All Templates** . Další informace o této metodě najdete v tématu [generování souborů z modelu UML](../modeling/generate-files-from-a-uml-model.md).

 ![Diagram tříd UML a generované soubory třídy jazyka C&#35;.](../modeling/media/oob-gencode1.png "oob_GenCode1")

 Další informace o diagramech tříd UML v aplikaci Visual Studio naleznete v následujících tématech:

- [Diagramy tříd UML: Referenční dokumentace](../modeling/uml-class-diagrams-reference.md)

- [Diagramy tříd UML: Pokyny](../modeling/uml-class-diagrams-guidelines.md)

  Chcete-li zjistit, které verze aplikace Visual Studio podporují diagramy tříd UML, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="using-the-generate-code-command"></a>Použití příkazu Generovat kód
 Následující postup popisuje výchozí chování příkazu **generovat kód** :

#### <a name="to-generate-a-separate-file-for-each-element"></a>Generování samostatného souboru pro každý prvek

1. Vytvořte model UML, který obsahuje třídy. Pro prvky modelu lze použít stereotypy.

    Další informace naleznete v tématu [výchozí transformace generování kódu](#default).

2. V diagramu tříd nebo v **Průzkumníku modelů UML**vyberte prvky, ze kterých chcete generovat kód. Lze vybrat jednu z následujících možností:

   - Určitou sadu prvků.

   - Balíček nebo model, chcete-li z jeho obsahu vygenerovat kód.

   - Diagram, chcete-li vybrat všechny prvky diagramu.

3. Otevřete místní nabídku pro vybraný prvek a pak zvolte možnost **generovat kód**.

    Při prvním použití **generovat kód** v konkrétním modelu se zobrazí dialogové okno. Toto dialogové okno umožňuje upravit parametry pro generování kódu modelu.

    Pokud si nejste jisti, že chcete tyto parametry změnit, klikněte na **tlačítko OK** .

    Chcete-li se do tohoto dialogového okna vrátit později, otevřete **Průzkumníka modelů UML**. Otevřete místní nabídku projekt modelování a zvolte možnost **nastavit generování kódu**. Další informace naleznete v tématu [Přizpůsobení příkazu generovat kód](#custom).

   Vygenerují se soubory, které obsahují kód jazyka C#. Ve výchozím nastavení je vygenerován soubor pro každý typ a tyto soubory jsou vygenerovány v projektu knihovny tříd jazyka C#. Toto chování však lze přizpůsobit. Další informace naleznete v tématu [Přizpůsobení příkazu generovat kód](#custom).

   Na model jsou použity některé ověřovací testy, aby bylo zajištěno, že jej lze přeložit do jazyka C#. Pokud se tyto testy nezdaří, zobrazí se chybová zpráva a generování kódu nebude provedeno. Pokud jste vytvořili příkaz nabídky ověření, kód nebude vygenerován pro žádný prvek, u kterého příkaz ověření selže. Další informace najdete v tématu [Definování omezení ověření pro modely UML](../modeling/define-validation-constraints-for-uml-models.md).

## <a name="default-code-generation-transforms"></a><a name="default"></a> Výchozí transformace generování kódu
 V této části jsou shrnuty výsledky, které jsou vytvářeny příkazem **generovat kód** , pokud tento příkaz neupravíte. Další informace naleznete v tématu [Přizpůsobení příkazu generovat kód](#custom).

- Pro každý typ je vytvořen jeden typ jazyka C#, který jste vybrali v modelu UML. Každý typ je umístěn v samostatném souboru kódu ve složce **GeneratedCode** .

- Pokud je typ modelu UML obsažen v balíčku, vygenerovaný typ jazyka C# je umístěn do oboru názvů a soubor je vygenerován ve složce, která má stejný název jako tento obor názvů.

- Vlastnost jazyka C# je vygenerována pro každou `Attribute` třídu UML.

- Metoda jazyka C# je vygenerována pro každý `Operation` typ UML.

- Pole jazyka C# je vygenerováno pro každé provázané přidružení, kterého se třída účastní.

  Přidáním stereotypu každému typu modelu UML lze určit další vlastnosti generovaného typu jazyka C#.

|**Vytvoření tohoto typu jazyka C#**|**Nakreslit tento typ UML**|**Použít tento stereotyp**|
|---------------------------------|----------------------------|-------------------------------|
|Třída|Třída|\<none> nebo<br /><br /> třída jazyka C#|
|Rozhraní|Rozhraní|\<none> nebo<br /><br /> rozhraní jazyka C#|
|Výčet|Výčet|\<none> nebo<br /><br /> výčet jazyka C#|
|Delegát|Třída|delegát jazyka C#|
|Struktura|Třída|struktura jazyka C#|

#### <a name="to-set-a-stereotype-on-a-type-or-other-element"></a>Nastavení stereotypu pro typ nebo jiný prvek

1. Otevřete místní nabídku pro prvek v diagramu nebo v **Průzkumníku modelů UML**a poté zvolte možnost **vlastnosti**.

2. V okně **vlastnosti** zvolte šipku rozevíracího seznamu ve vlastnosti **Stereotypy** a potom zaškrtněte políčko stereotypu, který chcete použít.

   > [!TIP]
   > Pokud se stereotypy jazyka C# nezobrazí, povolte profil jazyka C# pro model nebo balíček obsahující prvky modelu, které vás zajímají. Vyberte balíček nebo kořen modelu v **Průzkumníku modelů UML**. Poté v okně **vlastnosti** zvolte možnost **profil**a poté povolte profil jazyka C#.

3. Rozbalením vlastnosti **Stereotypy** zobrazíte další vlastnosti, které lze nastavit.

   Vlastnosti **popisu** typů, atributů, operací a přidružení jsou zapisovány do `<summary>` komentářů ve vygenerovaném kódu. Prvky komentáře, které jsou propojeny s typy, jsou zapsány do `<remarks>` komentářů.

## <a name="varying-the-generated-code"></a>Rozlišování generovaného kódu
 Generovaný kód se liší v závislosti na vlastnostech každého typu, atributu nebo operace. Například pokud nastavíte vlastnost **is abstract** třídy na hodnotu true, `abstract` klíčové slovo se zobrazí ve vygenerované třídě. Pokud nastavíte **násobnost** atributu na **hodnotu 0. \* .**, bude mít vygenerovaná vlastnost `IEnumerable<>` typ.

 Každý stereotyp navíc obsahuje několik dalších vlastností, které lze nastavit. Tyto hodnoty jsou převedeny na příslušná klíčová slova v kódu jazyka C#. Například pokud nastavíte vlastnost `Is Static` pro třídu, bude třída jazyka C# `static` .

 Chcete-li nastavit tyto další vlastnosti, vyberte v diagramu třídu nebo jiný prvek. V okno Vlastnosti rozbalte **Stereotypy**a potom rozbalte stereotyp c#, jako je například **Třída jazyka c#**.  V případě tříd tyto dodatečné vlastnosti zahrnují:

- Atributy CLR

- Je částečná

- Je statická

- Je nebezpečná

- Viditelnost balíčku

  Všechny atributy a operace mají také vlastnosti stereotypu, které lze nastavit. Pokud nevidíte vlastnosti u nového atributu, spusťte příkaz **generovat kód**.

## <a name="customizing-the-generate-code-command"></a><a name="custom"></a> Přizpůsobení příkazu generovat kód
 Příkaz **generovat kód** funguje pomocí transformace prvků modelu pomocí sady textových šablon. Další informace o textových šablonách naleznete v tématu [Code Generation and T4 text Templates](../modeling/code-generation-and-t4-text-templates.md).

 Šablony jsou určeny v sadě *vazeb textových šablon*. Vazba textové šablony určuje, která šablona se má použít, kde by se měl umístit generovaný výstup, a další parametry příkazu pro **Vytvoření kódu** .

 Při prvním spuštění příkazu **generovat kód** na konkrétním modelu připojí výchozí sadu vazeb šablony ke kořenu modelu. Tyto vazby se vztahují na všechny prvky v modelu.

 To však lze přepsat a přidat k těmto výchozím vazbám další, a to připojením vlastních vazeb balíčkům, třídám nebo jiným prvkům. Vazba se vztahuje na všechny prvky obsažené uvnitř prvku, k němuž je připojena. Pokud například chcete, aby všechny typy uvnitř konkrétního balíčku byly transformovány pomocí jiné sady šablon nebo má být výstup proveden do jiné složky, lze vazbu šablony připojit k balíčku.

 Chcete-li zkontrolovat vazby šablony připojené k prvku modelu, klikněte na tlačítko se třemi tečkami **[...]** ve vlastnosti **vazby textové šablony** v okno Vlastnosti.

 Příkaz **generovat kód** použije šablony pro každý prvek modelu, který jste vybrali. Pro každý prvek je sada použitých šablon kombinovaná sada šablon, které jsou připojeny k jejím kontejnerům až po kořen modelu.

 Pokud mají dvě vazby šablony v této sadě stejný název, vazba v menším kontejneru přepíše vazbu ve větším kontejneru. Například kořen modelu má vazbu se **šablonou třídy**název. Chcete-li použít vlastní šablonu na obsah konkrétního balíčku, definujte vlastní vazbu šablony, která má **šablonu třídy**název.

 Na prvek modelu lze použít více než jednu šablonu. Z každého prvku modelu lze vytvořit více než jeden soubor.

> [!NOTE]
> Vazby připojené ke kořenu modelu jsou použity jako výchozí pro všechny prvky v modelu. Chcete-li zobrazit tyto výchozí vazby, otevřete **Průzkumníka modelů UML**. Otevřete místní nabídku projektu modelování a pak zvolte **nastavit generování kódu**. Alternativně můžete vybrat kořen modelu v Průzkumníku modelů UML. V okno Vlastnosti vyberte **[...]** ve vlastnosti **vazby textové šablony** . Vazby se nezobrazí, dokud nepoužijete příkaz **generovat kód** alespoň jednou. Vazby šablony nelze připojit k diagramu.

#### <a name="to-attach-text-template-bindings-to-a-package-or-other-model-element"></a>Připojení vazby textové šablony k balíčku nebo jinému prvku modelu

1. V **Průzkumníku modelů UML**otevřete místní nabídku pro prvek modelu a poté zvolte možnost **vlastnosti**. Obecně byste měli připojovat vazby textové šablony k balíčku nebo kořenu modelu.

2. V okně **vlastnosti** klikněte na tlačítko se třemi tečkami (**[...]**) ve vlastnosti **vazby textové šablony** .

    Zobrazí se dialogové okno **vazby textové šablony** .

3. Klikněte na tlačítko **Přidat** a vytvořte novou vazbu textové šablony.

    \- ani

    Zvolte existující vazbu a upravte ji.

    Každá vazba šablony definuje, jak by zadaná šablona měla být použita na vybraný prvek modelu a jiné prvky modelu, které obsahuje.

4. V tomto dialogovém okně nastavte vlastnosti vazby textové šablony.

   |    **Vlastnost**    |                                                                                                                                                                                                                                                                                                                    **Popis**                                                                                                                                                                                                                                                                                                                    |
   |--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |        Název        |                                                                                                                                                                                                                                                  Název této vazby. Chcete-li přepsat vazby zděděné od nadřazeného balíčku nebo modelu, použijte stejný název, jako je název vazby, kterou chcete přepsat.                                                                                                                                                                                                                                                  |
   |     Přepsat      |                                                                                                                                                                                                                                                                                                      Pokud je hodnota true, je existující kód přepsán.                                                                                                                                                                                                                                                                                                       |
   |    Cílový název     | Název souboru, který je generován.<br /><br /> Do tohoto řetězce lze vkládat výrazy, například `{Name}` nebo `{Owner.Name}` . Můžete například napsat: `{Owner.Name}_{Name}` . Tento výraz je vyhodnocen pro prvek modelu. Mohou být použity vlastnosti prvků, ale nikoli metody. Chcete-li zjistit, jaké vlastnosti lze použít, podívejte se na vlastnosti typů v **Microsoft. VisualStudio. UML \* .**. \*\*Důležité: \* \* `{Name}` nebo `{Owner.Name}` se dá použít jenom ve vlastnosti **název cíle** .   Chcete-li změnit název vygenerované třídy, musíte změnit šablonu. Další informace najdete v tématu [Vytvoření textové šablony](#writing). |
   |    Cesta k projektu    |                                                                      Určuje cestu k [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu, který bude obsahovat výstupní soubory transformace. Zadávané hodnoty slouží k vytvoření nového projektu. Kliknutím na tlačítko se třemi tečkami (**[...]**) vyberte existující projekt.<br /><br /> Pokud nový projekt neexistuje, bude vytvořen. Bude to projekt knihovny tříd jazyka C#.<br /><br /> Chcete-li to provést, je nutné projekt zadat přímo. Lze použít makra proměnných prostředí, například %ProgramFiles% nebo %LocalAppData%.                                                                       |
   |  Cílový adresář  |                                                                                          Složka, do které je cílový soubor generován. Tato cesta je relativní ke složce projektu.<br /><br /> Pomocí `{PackageStructure}` výrazu můžete vložit cestu, která odpovídá názvům obsahujícího balíčky. Výchozí hodnota je `\GeneratedCode\{PackageStructure}`. Lze také použít proměnné prostředí, například %TEMP% nebo %HomePath%. **Důležité informace:** `{PackageStructure}` dá se použít jenom ve vlastnosti **cílového adresáře** .                                                                                            |
   | Cesta k souboru šablony |                                                                                                                                                           Šablona, která bude provádět transformaci.<br /><br /> Lze použít buď dodané šablony, nebo vytvořit vlastní. Dodané šablony naleznete v následujícím umístění:<br /><br /> ...\Program Files\Microsoft Visual Studio 12.0\Common7\IDE\Extensions\Microsoft\Architecture Tools\Extensibility\Templates\Text\                                                                                                                                                           |

5. K prvku lze připojit libovolný počet vazeb.

## <a name="writing-a-text-template"></a><a name="writing"></a> Zápis textové šablony
 Lze vytvářet vlastní textové šablony. Textové šablony mohou generovat kód programu nebo jakýkoli jiný typ textového souboru.

 Doporučujeme začít úpravou kopií standardních šablon. Tyto šablony lze zkopírovat z následujících umístění:

 ...\Program Files\Microsoft Visual Studio 12.0\Common7\IDE\Extensions\Microsoft\Architecture Tools\Extensibility\Templates\Text\

 Další informace o těchto textových šablonách naleznete v následujících tématech.

- Textová šablona je prototyp výsledného souboru a obsahuje výsledný text a programový kód, který čte model. Další informace najdete v tématu [generování kódu a textové šablony T4](../modeling/code-generation-and-t4-text-templates.md).

- Chcete-li navigovat model UML v kódu programu, je nutné použít rozhraní API modelu UML. Další informace najdete v tématu [navigace modelu UML](../modeling/navigate-the-uml-model.md) a [referenční informace k rozhraní API pro rozšíření modelování UML](../modeling/api-reference-for-uml-modeling-extensibility.md).

  Chcete-li použít šablony s příkazem **generovat kód** , je nutné zahrnout direktivu Modeling. Příklad:

  `<#@ Modeling ElementType="Microsoft.VisualStudio.Uml.Classes.IClass" Processor="ModelingProcessor" #>`

  `ElementType`Atribut definuje typ prvku UML, na který se tato šablona vztahuje.

  V šabloně `this` patří do dočasné třídy, která má následující vlastnosti:

- `Element` = [IELEMENT](/previous-versions/dd516035(v=vs.140)) UML, na který je šablona použita.

- `Errors`: <xref:System.CodeDom.Compiler.CompilerErrorCollection>

- `Host`: [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))

- `ModelBus`: [ModelBus](/previous-versions/ee904639(v=vs.140)). Další informace najdete v tématu [Integrace modelů UML s jinými modely a nástroji](../modeling/integrate-uml-models-with-other-models-and-tools.md).

- `ProfileName` = "Profil C #"

- `ServiceProvider`: <xref:System.IServiceProvider>

- `Session`: <xref:Microsoft.VisualStudio.TextTemplating.TextTemplatingSession>.

- `Store`: <xref:Microsoft.VisualStudio.Modeling.Store>. Toto je úložiště SDK vizualizace a modelování, pomocí kterého je implementován ModelStore modelu UML. Chcete-li získat [IMODELSTORE](/previous-versions/ee789385(v=vs.140))UML, použijte `this.Element.GetModelStore()` .

  Následující body mohou být užitečné při vytváření textové šablony. Tyto informace jsou podrobně popsané v článku [generování kódu a textové šablony T4](../modeling/code-generation-and-t4-text-templates.md).

- V direktivě můžete nastavit příponu názvu souboru výsledku `Output` . `Output`Každá textová šablona vyžaduje jednu direktivu.

- Některá sestavení jsou automaticky odkazována pomocí šablony. Mezi tato sestavení patří například System.dll a Microsoft.VisualStudio.Uml.Interfaces.dll.

   Chcete-li použít jiná sestavení v kódu vygenerování programu, je nutné použít `Assembly` direktivu. Příklad:

   `<#@ Assembly Name="%ProgramFiles%\Microsoft Visual Studio 12.0\Common7\IDE\PublicAssemblies\Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll" #>`

- Některé obory názvů, jako je například, `System` jsou automaticky importovány do kódu programu. Pro jiné obory názvů můžete použít `Import` direktivu stejným způsobem, jako byste použili `using` příkaz. Příklad:

   `<#@ Import Namespace="Microsoft.VisualStudio.Uml.Classes" #>`

   `<#@ Import Namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml" #>`

- Pomocí `Include` direktivy můžete odkazovat na text jiného souboru.

- Části šablony uzavřené v závorkách `<# ... #>` jsou spouštěny příkazem **generovat kód** . Části šablony mimo tyto závorky jsou do výsledného souboru zkopírovány. Je důležité rozlišovat mezi generovacím kódem a generovaným textem. Generovaný text může být v libovolném jazyce.

- `<#= Expressions #>` jsou vyhodnocovány a převedeny na řetězce.

## <a name="see-also"></a>Viz také
 [Diagramy tříd UML: referenční](../modeling/uml-class-diagrams-reference.md) dokumentace [diagramů tříd UML: pokyny](../modeling/uml-class-diagrams-guidelines.md) [generují soubory z modelu UML](../modeling/generate-files-from-a-uml-model.md)
