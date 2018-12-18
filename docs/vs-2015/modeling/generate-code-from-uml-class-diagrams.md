---
title: Generování kódu z diagramů tříd UML | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.logicalclassdiagram.shapes.properties.Templates
- vs.teamarch.logicalclassdiagram.shapes.properties.Templates.TextTransformationDataCollectionEditor
helpviewer_keywords:
- code generation, UML class diagrams
- class diagrams - UML, generating code
- UML diagrams, generating code
ms.assetid: 2790e64d-7728-4c2e-a4dd-4131e795f730
caps.latest.revision: 53
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: a8108a552f21504714fea84bcb29194db4d947cf
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764777"
---
# <a name="generate-code-from-uml-class-diagrams"></a>Generování kódu z diagramů tříd UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chcete-li generovat Visual C# .NET kódu z diagramů tříd UML v sadě Visual Studio, použijte **generovat kód** příkazu. Ve výchozím nastavení tento příkaz vygeneruje typ jazyka C# pro každý vybraný typ modelu UML. Toto chování lze upravit a rozšířit úpravou nebo zkopírováním textových šablon, které generují kód. Lze určit různá chování pro typy, které jsou obsaženy v různých balíčcích modelu.  

 **Generovat kód** příkaz je velmi vhodné pro generování kódu z výběru uživatele prvků a pro generování jednoho souboru pro každou třídu modelu UML nebo jiný prvek. Například, tento snímek obrazovky ukazuje dva soubory jazyka C#, které byly vytvořeny ze dvou tříd modelu UML.  

 Případně, pokud chcete generovat kód, ve kterém generované soubory nemají s prvky modelu UML vztah 1:1, zvažte vytvoření textových šablon, které jsou vyvolány pomocí **Transformovat všechny šablony** příkazu. Další informace o této metodě naleznete v tématu [generování souborů z modelu UML](../modeling/generate-files-from-a-uml-model.md).  

 ![Třída UML, diagram a generovaný kód C&#35; soubory tříd. ](../modeling/media/oob-gencode1.png "oob_GenCode1")  

 Další informace o diagramech tříd UML v sadě Visual Studio naleznete v následujících tématech:  

- [Diagramy tříd UML: Referenční dokumentace](../modeling/uml-class-diagrams-reference.md)  

- [Diagramy tříd UML: Pokyny](../modeling/uml-class-diagrams-guidelines.md)  

  Pokud chcete zobrazit, které verze sady Visual Studio podporují diagramů tříd UML, naleznete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  

## <a name="using-the-generate-code-command"></a>Použití příkazu Generovat kód  
 Následující postup popisuje výchozí chování **generovat kód** příkaz:  

#### <a name="to-generate-a-separate-file-for-each-element"></a>Generování samostatného souboru pro každý prvek  

1. Vytvořte model UML, který obsahuje třídy. Pro prvky modelu lze použít stereotypy.  

    Další informace najdete v tématu [výchozí transformace generování kódu](#default).  

2. V diagramu tříd nebo v **Průzkumníku modelů UML**, vyberte prvky, ze kterých chcete generovat kód. Lze vybrat jednu z následujících možností:  

   -   Určitou sadu prvků.  

   -   Balíček nebo model, chcete-li z jeho obsahu vygenerovat kód.  

   -   Diagram, chcete-li vybrat všechny prvky diagramu.  

3. Otevřete místní nabídku pro vybraný element a pak zvolte **generovat kód**.  

    Při prvním použití **generovat kód** v konkrétním modelu, zobrazí se dialogové okno. Toto dialogové okno umožňuje upravit parametry pro generování kódu modelu.  

    Zvolte **OK** Pokud si nejste jisti, že chcete tyto parametry měnit.  

    Chcete-li tomuto dialogovému oknu vrátit později, otevřete **Průzkumníku modelů UML**. Otevřete místní nabídku projektu modelování a klikněte na tlačítko **nastavení generování kódu**. Další informace najdete v tématu [přizpůsobení příkazu generovat kód](#custom).  

   Vygenerují se soubory, které obsahují kód jazyka C#. Ve výchozím nastavení je vygenerován soubor pro každý typ a tyto soubory jsou vygenerovány v projektu knihovny tříd jazyka C#. Toto chování však lze přizpůsobit. Další informace najdete v tématu [přizpůsobení příkazu generovat kód](#custom).  

   Na model jsou použity některé ověřovací testy, aby bylo zajištěno, že jej lze přeložit do jazyka C#. Pokud se tyto testy nezdaří, zobrazí se chybová zpráva a generování kódu nebude provedeno. Pokud jste vytvořili příkaz nabídky ověření, kód nebude vygenerován pro žádný prvek, u kterého příkaz ověření selže. Další informace najdete v tématu [definovat omezení ověření pro modely UML](../modeling/define-validation-constraints-for-uml-models.md).  

##  <a name="default"></a> Výchozí transformace generování kódu  
 Tento oddíl shrnuje výsledky, které jsou vytvářeny **generovat kód** příkazu, pokud jste tento příkaz nepřizpůsobili. Další informace najdete v tématu [přizpůsobení příkazu generovat kód](#custom).  

- Pro každý typ je vytvořen jeden typ jazyka C#, který jste vybrali v modelu UML. Každý typ je umístěn v samostatném souboru kódu v rámci **GeneratedCode** složky.  

- Pokud je typ modelu UML obsažen v balíčku, vygenerovaný typ jazyka C# je umístěn do oboru názvů a soubor je vygenerován ve složce, která má stejný název jako tento obor názvů.  

- Vlastnost jazyka C# je vygenerována pro každý `Attribute` třídy modelu UML.  

- Metoda jazyka C# je vygenerována pro každý `Operation` typu modelu UML.  

- Pole jazyka C# je vygenerováno pro každé provázané přidružení, kterého se třída účastní.  

  Přidáním stereotypu každému typu modelu UML lze určit další vlastnosti generovaného typu jazyka C#.  

|**Chcete-li vytvořit tento typ jazyka C#**|**Nakreslete tento typ modelu UML**|**Použijte tento stereotyp**|  
|---------------------------------|----------------------------|-------------------------------|  
|Třída|Třída|\<žádný > nebo<br /><br /> třída jazyka C#|  
|Rozhraní|Rozhraní|\<žádný > nebo<br /><br /> rozhraní jazyka C#|  
|Výčet|Výčet|\<žádný > nebo<br /><br /> výčet jazyka C#|  
|Delegát|Třída|delegát jazyka C#|  
|Struktura|Třída|struktura jazyka C#|  

#### <a name="to-set-a-stereotype-on-a-type-or-other-element"></a>Nastavení stereotypu pro typ nebo jiný prvek  

1. Otevřete místní nabídku prvku v diagramu nebo v **Průzkumníku modelů UML**a klikněte na tlačítko **vlastnosti**.  

2. V **vlastnosti** okna, klikněte na šipku rozevíracího seznamu v **Stereotypy** vlastnost a potom zaškrtněte políčko stereotypu, který chcete použít.  

   > [!TIP]
   >  Pokud se stereotypy jazyka C# nezobrazí, povolte profil jazyka C# pro model nebo balíček obsahující prvky modelu, které vás zajímají. Vyberte balíček nebo kořen modelu v **Průzkumníku modelů UML**. Pak v **vlastnosti** okně zvolte **profilu**a poté povolte profil jazyka C#.  

3. Rozbalte **Stereotypy** vlastnosti chcete zobrazit další vlastnosti, které můžete nastavit.  

   **Popis** vlastnosti typů, atributů, operací a přidružení se zapisují do `<summary>` komentáře v generovaném kódu. Prvky komentářů, které jsou spojeny s typy se zapisují do `<remarks>` komentáře.  

## <a name="varying-the-generated-code"></a>Rozlišování generovaného kódu  
 Generovaný kód se liší v závislosti na vlastnostech každého typu, atributu nebo operace. Pokud nastavíte například **je abstraktní** vlastnost třídy na hodnotu true, pak bude `abstract` – klíčové slovo se zobrazí na tuto vygenerovanou třídu. Pokud jste nastavili **násobnost** atributu na ** 0..\\ , pak bude mít vygenerovaná vlastnost `IEnumerable<>` typu.  

 Každý stereotyp navíc obsahuje několik dalších vlastností, které lze nastavit. Tyto hodnoty jsou převedeny na příslušná klíčová slova v kódu jazyka C#. Například pokud nastavíte vlastnost `Is Static` na třídu, pak třída jazyka C# budou `static`.  

 Chcete-li nastavit tyto další vlastnosti, vyberte v diagramu třídu nebo jiný prvek. V okně Vlastnosti rozbalte **Stereotypy**a poté rozbalte stereotyp jazyka C#, jako **třída jazyka C#**.  V případě tříd tyto dodatečné vlastnosti zahrnují:  

- Atributy CLR  

- Je částečná  

- Je statická  

- Je nebezpečná  

- Viditelnost balíčku  

  Všechny atributy a operace mají také vlastnosti stereotypu, které lze nastavit. Pokud se vlastnosti na novém atributu nezobrazí, spusťte **generovat kód**.  

##  <a name="custom"></a> Přizpůsobení příkazu generovat kód  
 **Generovat kód** příkaz funguje pomocí transformace prvků modelu s použitím sady textových šablon. Další informace o textových šablonách naleznete v tématu [generování kódu a textové šablony T4](../modeling/code-generation-and-t4-text-templates.md).  

 Šablony jsou uvedeny v sadě *vazby textové šablony*. Vazba textové šablony určuje, co šablona měla být použita, kde by měl být umístěn generovaný výstup a jiné parametry **generovat kód** příkazu.  

 Při prvním spuštění **generovat kód** příkaz na konkrétním modelu připojí sada výchozích vazeb šablony k kořen modelu. Tyto vazby se vztahují na všechny prvky v modelu.  

 To však lze přepsat a přidat k těmto výchozím vazbám další, a to připojením vlastních vazeb balíčkům, třídám nebo jiným prvkům. Vazba se vztahuje na všechny prvky obsažené uvnitř prvku, k němuž je připojena. Pokud například chcete, aby všechny typy uvnitř konkrétního balíčku byly transformovány pomocí jiné sady šablon nebo má být výstup proveden do jiné složky, lze vazbu šablony připojit k balíčku.  

 Chcete-li zkontrolovat vazby šablony připojené k prvku modelu, zvolte tři tečky **[...]**  v **vazby textové šablony** vlastností v okně Vlastnosti.  

 **Generovat kód** šablony příkaz se vztahuje na každý prvek modelu, který jste vybrali. Pro každý prvek je sada použitých šablon kombinovaná sada šablon, které jsou připojeny k jejím kontejnerům až po kořen modelu.  

 Pokud mají dvě vazby šablony v této sadě stejný název, vazba v menším kontejneru přepíše vazbu ve větším kontejneru. Například kořen modelu má vazbu s názvem **šablony třídy**. Chcete-li mít vlastní šablonu na obsah konkrétního balíčku, definovat vlastní vazba šablony, který má název **šablony třídy**.  

 Na prvek modelu lze použít více než jednu šablonu. Z každého prvku modelu lze vytvořit více než jeden soubor.  

> [!NOTE]
>  Vazby připojené ke kořenu modelu jsou použity jako výchozí pro všechny prvky v modelu. Chcete-li zobrazit tyto výchozí vazby, otevřete **Průzkumníku modelů UML**. Otevřete místní nabídku projektu modelování, a pak zvolte **nastavení generování kódu**. Případně lze vybrat kořen modelu v Průzkumníku modelů UML. V okně Vlastnosti zvolte **[...]**  v **vazby textové šablony** vlastnost. Tyto vazby se nezobrazí, dokud jste použili **generovat kód** příkaz alespoň jednou. Vazby šablony nelze připojit k diagramu.  

#### <a name="to-attach-text-template-bindings-to-a-package-or-other-model-element"></a>Připojení vazby textové šablony k balíčku nebo jinému prvku modelu  

1. V **Průzkumníku modelů UML**, otevřete místní nabídku pro prvek modelu a klikněte na tlačítko **vlastnosti**. Obecně byste měli připojovat vazby textové šablony k balíčku nebo kořenu modelu.  

2. V **vlastnosti** okna, klikněte na tlačítko tří teček (**[...]** ) v **vazby textové šablony** vlastnost.  

    **Vazby textové šablony** zobrazí se dialogové okno.  

3. Zvolte **přidat** vytvořte novou vazbu textové šablony.  

    \- nebo –  

    Zvolte existující vazbu a upravte ji.  

    Každá vazba šablony definuje, jak by zadaná šablona měla být použita na vybraný prvek modelu a jiné prvky modelu, které obsahuje.  

4. V tomto dialogovém okně nastavte vlastnosti vazby textové šablony.  


   |    **Vlastnost**    |                                                                                                                                                                                                                                                                                                                    **Popis**                                                                                                                                                                                                                                                                                                                    |
   |--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |        Název        |                                                                                                                                                                                                                                                  Název této vazby. Chcete-li přepsat vazby zděděné od nadřazeného balíčku nebo modelu, použijte stejný název, jako je název vazby, kterou chcete přepsat.                                                                                                                                                                                                                                                  |
   |     Přepsat      |                                                                                                                                                                                                                                                                                                      Pokud je hodnota true, je existující kód přepsán.                                                                                                                                                                                                                                                                                                       |
   |    Cílový název     | Název souboru, který je generován.<br /><br /> Výrazy můžete vložit do tohoto řetězce, jako `{Name}` nebo `{Owner.Name}`. Můžete například napsat: `{Owner.Name}_{Name}`. Tento výraz je vyhodnocen pro prvek modelu. Mohou být použity vlastnosti prvků, ale nikoli metody. Pokud chcete zjistit, jaké vlastnosti lze použít, podívejte se na vlastnosti typů v **Microsoft.VisualStudio.Uml.\\ ***. \*\*Důležité:* \* `{Name}` nebo `{Owner.Name}` lze použít pouze ve **název cílového** vlastnost. Chcete-li změnit název vygenerované třídy, musíte změnit šablonu. Další informace najdete v tématu [Writing a Text Template](#writing). |
   |    Cesta k projektu    |                                                                      Určuje cestu k [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] výstupní soubory projektu, který bude obsahovat transformace. Zadávané hodnoty slouží k vytvoření nového projektu. Zvolte tlačítko se třemi tečkami (**[...]** ) vyberte existující projekt.<br /><br /> Pokud nový projekt neexistuje, bude vytvořen. Bude to projekt knihovny tříd jazyka C#.<br /><br /> Chcete-li to provést, je nutné projekt zadat přímo. Lze použít makra proměnných prostředí, například %ProgramFiles% nebo %LocalAppData%.                                                                       |
   |  Cílový adresář  |                                                                                          Složka, do které je cílový soubor generován. Tato cesta je relativní ke složce projektu.<br /><br /> Můžete použít `{PackageStructure}` výraz lze vložit cestu, která odpovídá názvům obsažených balíčků. Výchozí hodnota je `\GeneratedCode\{PackageStructure}`. Lze také použít proměnné prostředí, například %TEMP% nebo %HomePath%. **Důležité:** `{PackageStructure}` lze použít pouze ve **cílový adresář** vlastnost.                                                                                          |
   | Cesta k souboru šablony |                                                                                                                                                           Šablona, která bude provádět transformaci.<br /><br /> Lze použít buď dodané šablony, nebo vytvořit vlastní. Dodané šablony naleznete v následujícím umístění:<br /><br /> ...\Program Files\Microsoft Visual Studio 12.0\Common7\IDE\Extensions\Microsoft\Architecture Tools\Extensibility\Templates\Text\                                                                                                                                                           |


5. K prvku lze připojit libovolný počet vazeb.  

##  <a name="writing"></a> Vytvoření textové šablony  
 Lze vytvářet vlastní textové šablony. Textové šablony mohou generovat kód programu nebo jakýkoli jiný typ textového souboru.  

 Doporučujeme začít úpravou kopií standardních šablon. Tyto šablony lze zkopírovat z následujících umístění:  

 ...\Program Files\Microsoft Visual Studio 12.0\Common7\IDE\Extensions\Microsoft\Architecture Tools\Extensibility\Templates\Text\  

 Další informace o těchto textových šablonách naleznete v následujících tématech.  

- Textová šablona je prototyp výsledného souboru a obsahuje výsledný text a programový kód, který čte model. Další informace najdete v tématu [generování kódu a textové šablony T4](../modeling/code-generation-and-t4-text-templates.md).  

- Chcete-li navigovat model UML v kódu programu, je nutné použít rozhraní API modelu UML. Další informace najdete v tématu [procházení modelu UML](../modeling/navigate-the-uml-model.md) a [Reference k rozhraní API pro rozšíření modelování UML](../modeling/api-reference-for-uml-modeling-extensibility.md).  

  Použití šablon s **generovat kód** příkazu musíte přidat direktivu modelování. Příklad:  

  `<#@ Modeling ElementType="Microsoft.VisualStudio.Uml.Classes.IClass" Processor="ModelingProcessor" #>`  

  `ElementType` Atribut definuje typ prvku modelu UML, ke kterému se tato šablona vztahuje.  

  V šabloně `this` patří dočasné třídě, která má následující vlastnosti:  

- `Element` = UML <xref:Microsoft.VisualStudio.Uml.Classes.IElement> na které se je šablona použita.  

- `Errors`: <xref:System.CodeDom.Compiler.CompilerErrorCollection>  

- `Host`: <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>  

- `ModelBus`: <xref:Microsoft.VisualStudio.Modeling.Integration.ModelBus>. Další informace najdete v tématu [modely UML integrovat s jinými modely a nástroji](../modeling/integrate-uml-models-with-other-models-and-tools.md).  

- `ProfileName` = "#Profile jazyka C#"  

- `ServiceProvider`: <xref:System.IServiceProvider>  

- `Session`: <xref:Microsoft.VisualStudio.TextTemplating.TextTemplatingSession>.  

- `Store`: <xref:Microsoft.VisualStudio.Modeling.Store>. Toto je úložiště SDK vizualizace a modelování, pomocí kterého je implementován ModelStore modelu UML. Chcete-li získat UML <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml.IModelStore>, použijte `this.Element.GetModelStore()`.  

  Následující body mohou být užitečné při vytváření textové šablony. Tyto informace je podrobně popsány v [generování kódu a textové šablony T4](../modeling/code-generation-and-t4-text-templates.md).  

- Můžete nastavit příponu názvu souboru výsledku `Output` směrnice. Jeden `Output` – direktiva je vyžadována v každé textové šabloně.  

- Některá sestavení jsou automaticky odkazována pomocí šablony. Mezi tato sestavení patří například System.dll a Microsoft.VisualStudio.Uml.Interfaces.dll.  

   Chcete-li v generování programového kódu použít jiná sestavení, musíte použít `Assembly` směrnice. Příklad:  

   `<#@ Assembly Name="%ProgramFiles%\Microsoft Visual Studio 12.0\Common7\IDE\PublicAssemblies\Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll" #>`  

- Některé obory názvů, jako `System` automaticky importují do kódu programu. Pro ostatní obory názvů, můžete použít `Import` direktiv stejným způsobem, který můžete využít `using` příkazu. Příklad:  

   `<#@ Import Namespace="Microsoft.VisualStudio.Uml.Classes" #>`  

   `<#@ Import Namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml" #>`  

- Použití `Include` – direktiva lze odkazovat na text jiného souboru.  

- Části šablony uzavřené v závorkách `<# ... #>` jsou spouštěny **generovat kód** příkazu. Části šablony mimo tyto závorky jsou do výsledného souboru zkopírovány. Je důležité rozlišovat mezi generovacím kódem a generovaným textem. Generovaný text může být v libovolném jazyce.  

- `<#= Expressions #>` jsou vyhodnoceny a převedeny na řetězce.  

## <a name="see-also"></a>Viz také  
 [Diagramy tříd UML: referenční dokumentace](../modeling/uml-class-diagrams-reference.md)   
 [Diagramy tříd UML: pokyny](../modeling/uml-class-diagrams-guidelines.md)   
 [Generování souborů z modelu UML](../modeling/generate-files-from-a-uml-model.md)



