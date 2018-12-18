---
title: 'Postupy: použití kontextu uživatelského rozhraní založeného na pravidlo pro rozšíření sady Visual Studio | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
author: gregvanl
ms.author: gregvanl
ms.workload:
- vssdk
ms.openlocfilehash: 75b181be5665d6416aee4f3f011d0d5d2a1d4237
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49866347"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>Postupy: použití založený na pravidlech kontextu uživatelského rozhraní pro rozšíření sady Visual Studio
Visual Studio umožňuje načítání rozšíření VSPackages při některých dobře známé <xref:Microsoft.VisualStudio.Shell.UIContext>s aktivují. Kontexty uživatelského rozhraní nejsou jemné grained, což ponechá autoři rozšíření žádná volba ale vybrat k dispozici kontextu uživatelského rozhraní, který se aktivuje před bodem VSPackage načíst opravdu chtěli. Seznam dobře známé uživatelské rozhraní kontextech najdete v tématu <xref:Microsoft.VisualStudio.Shell.KnownUIContexts>.  
  
 Načítají se balíčky může mít dopad na výkon a jejich načtení dřív, než je potřeba není nejlepším postupem. Visual Studio 2015 představil nový koncept kontexty uživatelského rozhraní založeného na pravidlech, mechanismus, který umožňuje autorům rozšíření určit přesné podmínky, za kterých se aktivuje kontextu uživatelského rozhraní a jsou načteny přidružené balíčky VSPackages.  
  
## <a name="rule-based-ui-context"></a>Kontext založený na pravidlech uživatelského rozhraní  
 "Pravidlo" se skládá z nového kontextu uživatelského rozhraní (GUID) a logický výraz, který odkazuje na jeden nebo více "Terms" kombinovat pomocí logické "a", "nebo", "not" operace. "Terms" jsou vyhodnoceny dynamicky za běhu a výraz je již znovu pokaždé, když některý z jeho podmínek změny. Pokud je výraz vyhodnocen jako true, je aktivováno souvisejícího kontextu uživatelského rozhraní. V opačném případě je deaktivován kontextu uživatelského rozhraní.  
  
 Podle pravidel kontextu uživatelského rozhraní lze použít různými způsoby:  
  
1. Zadejte omezení viditelnost příkazů a oken nástrojů. Příkazy a nástroje pro windows můžete skrýt, až do splnění pravidla kontextu uživatelského rozhraní.  
  
2. Jako automatické omezení zatížení: automatické načtení balíčků jenom v případě splnění pravidla.  
  
3. Jako úlohu zpožděné: zpoždění načítání až do uplynutí zadaného intervalu a pravidlo je stále splněny.  
  
   Mechanismu, který mohou využívat všechny rozšíření sady Visual Studio.  
  
## <a name="create-a-rule-based-ui-context"></a>Vytvoření uživatelského rozhraní kontextu založený na pravidlech  
 Předpokládejme, že máte volá TestPackage rozšíření, která nabízí příkaz nabídky, které platí pouze pro soubory s *.config* rozšíření. Před VS2015, nejlepší možností je načíst TestPackage při <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> kontextu uživatelského rozhraní se aktivovala. Načítání TestPackage tímto způsobem není efektivní, protože ještě nesmí obsahovat načtené řešení *.config* souboru. Tyto kroky ukazují, jak na základě pravidel kontextu uživatelského rozhraní lze použít k aktivaci kontextu uživatelského rozhraní, pouze v případě, že soubor s *.config* rozšíření je vybraná a načíst TestPackage při aktivaci tohoto kontextu uživatelského rozhraní.  
  
1. Definovat nový identifikátor GUID UIContext a přidejte do třídy balíčku VSPackage <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> a <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>.  
  
    Například předpokládejme, že nové UIContext "UIContextGuid" se má přidat. Vytvoří identifikátor GUID (identifikátor GUID můžete vytvořit kliknutím na **nástroje** > **Create GUID**) je "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B". Pak přidejte následující deklarace uvnitř třídy balíčku:  
  
   ```csharp  
   public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";  
   ```  
  
    Atributy, přidejte následující hodnoty: (podrobnosti o těchto atributů budou vysvětlena dále)  
  
   ```csharp  
   [ProvideAutoLoad(TestPackage.UIContextGuid)]      
   [ProvideUIContextRule(TestPackage.UIContextGuid,  
       name: "Test auto load",   
       expression: "DotConfig",  
       termNames: new[] { "DotConfig" },  
       termValues: new[] { "HierSingleSelectionName:.config$" })]  
   ```  
  
    Tato metadata definovat nový identifikátor GUID UIContext (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) a výraz odkazuje na jeden termín "DotConfig". Termín "DotConfig" vyhodnotí jako true, vždy, když aktuální výběr v aktivní hierarchii má název, který odpovídá vzoru regulárního výrazu "\\.config$" (končí *.config*). (Výchozí) Určuje volitelný název pravidla, které jsou užitečné pro ladění.  
  
    Hodnoty atributu jsou přidány do pkgdef generovány během doby sestavení později.  
  
2. V souboru VSCT pro příkazy TestPackage přidejte příznak "DynamicVisibility" příslušnými příkazy:  
  
   ```xml  
   <CommandFlag>DynamicVisibility</CommandFlag>  
   ```  
  
3. V části viditelnosti VSCT tie příslušné příkazy, které nový UIContext GUID definované v #1:  
  
   ```xml  
   <VisibilityConstraints>   
       <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="guidTestUIContext"/>   
   </VisibilityConstraints>  
   ```  
  
4. V části symboly přidáte definici UIContext:  
  
   ```xml  
   <GuidSymbol name="guidTestUIContext" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />  
   ```  
  
    Nyní, v místní nabídce příkazů pro  *\*.config* soubory budou viditelné pouze, pokud je na vybranou položku v Průzkumníku řešení *.config* souboru a balíček nebude načtena do jednoho z těchto příkazy se vybere.  
  
   Pak potvrďte, že načte balíček pouze když je pravděpodobné, že ho pomocí ladicího programu. Chcete-li ladit TestPackage:  
  
5. Nastavit zarážku <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody.  
  
6. Sestavení TestPackage a spusťte ladění.  
  
7. Vytvoření projektu nebo některou aplikaci otevřete.  
  
8. Vybrat libovolný soubor s příponou jiné než *.config*. By neměl být zarážka dosažena.  
  
9. Vyberte *App.Config* souboru.  
  
   TestPackage načte a zastaví na zarážce.  
  
## <a name="add-more-rules-for-ui-context"></a>Přidat další pravidla pro kontext uživatelského rozhraní  
 Vzhledem k tomu, že pravidla kontextu uživatelského rozhraní jsou logické výrazy, můžete přidat více omezený pravidla pro kontext uživatelského rozhraní. Například v rámci výše uvedené uživatelské rozhraní, můžete určit, že pravidlo platí, pouze když je načtené řešení s projektem. Tímto způsobem příkazy nezobrazí případě otevíráte *.config* soubor jako samostatný soubor, nikoli jako součást projektu.  
  
```csharp  
[ProvideAutoLoad(TestPackage.UIContextGuid)]      
[ProvideUIContextRule(TestPackage.UIContextGuid,    
    name: "Test auto load",  
    expression: "(SingleProject | MultipleProjects) & DotConfig",    
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },     
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]  
```  
  
 Nyní odkazuje na výraz tří podmínek. První dvě podmínky, "SingleProject" a "MultipleProjects", najdete v jiných kontextech dobře známé uživatelské rozhraní (pomocí jejich identifikátorů GUID). Třetí výraz "DotConfig" je založený na pravidlech kontextu uživatelského rozhraní definované výše v tomto článku.  
  
## <a name="delayed-activation"></a>Odloženou aktivací  
 Pravidla můžou mít volitelné "zpoždění". Zpoždění se zadává v milisekundách. Pokud jsou k dispozici, způsobí zpoždění aktivace nebo deaktivace kontextu uživatelského rozhraní pravidla k změnit podle tohoto časového intervalu. Pokud pravidlo zpět před interval prodlevy, pak nic se nestane. Tento mechanismus je možné "rozložte" kroků inicializace – zejména jednorázová inicializace bez spoléhání se na časovače nebo registrace k oznámením nečinnosti.  
  
 Můžete například zadat pravidla zkušební zatížení mít ke zpoždění 100 milisekund:  
  
```csharp  
[ProvideAutoLoad(TestPackage.UIContextGuid)]  
[ProvideUIContextRule(TestPackage.UIContextGuid,   
    name: "Test auto load",  
    expression: "DotConfig",   
    termNames: new[] { "DotConfig" },  
    termValues: new[] { "HierSingleSelectionName:.config$" },   
    delay: 100)]  
```  
  
## <a name="term-types"></a>Typy termín  
 Tady jsou různé typy podmínek, které jsou podporovány:  
  
|Termín|Popis|  
|-|-|  
|{nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn}|Identifikátor GUID odkazuje na kontextu uživatelského rozhraní. Výraz bude mít hodnotu true, pokaždé, když se kontextu uživatelského rozhraní v opačném případě je aktivní a false.|  
|HierSingleSelectionName:\<vzor >|Výraz bude mít hodnotu true, pokaždé, když se výběr v aktivní hierarchii je jednu položku a název vybrané položky odpovídající regulární výraz platformy .net Dal "vzor".|  
|UserSettingsStoreQuery:\<dotaz >|"dotaz" představuje úplnou cestu do úložiště uživatelských nastavení, která se musí vyhodnotit na nenulovou hodnotu. Dotaz je rozdělit na "kolekce" a "propertyName" za poslední lomítko.|  
|ConfigSettingsStoreQuery:\<dotaz >|"dotaz" představuje úplnou cestu do úložiště nastavení konfigurace, který musí být vyhodnocen na nenulovou hodnotu. Dotaz je rozdělit na "kolekce" a "propertyName" za poslední lomítko.|  
|ActiveProjectFlavor:\<projectTypeGuid >|Výraz bude mít hodnotu true, pokaždé, když je aktuálně vybraného projektu flavored (souhrn) a má flavor odpovídající danému projektu typu GUID.|  
|ActiveEditorContentType:\<contentType >|Termín se být pravdivá, když je vybraný dokument s daným typem obsahu textového editoru.|  
|ActiveProjectCapability:\<výrazu >|Termín má hodnotu true, když aktivní projekt možnosti odpovídají zadaného výrazu. Výraz může být třeba VB &#124; CSharp.|  
|SolutionHasProjectCapability:\<výrazu >|Podobně jako výše, ale termín je true, pokud řešení obsahuje načtený projekt, který odpovídá výrazu.|  
|SolutionHasProjectFlavor:\<projectTypeGuid >|Výraz bude mít hodnotu true, vždy, když řešení obsahuje projekt, který je flavored (souhrn) a má flavor odpovídající danému projektu typu GUID.|


  
## <a name="compatibility-with-cross-version-extension"></a>Kompatibilita s verzí rozšíření  
 Podle pravidel kontexty uživatelského rozhraní je nová funkce v sadě Visual Studio 2015 a nebude přenést do starší verze. Portování není na starší verze vytvoří problém s rozšíření/balíčky, které cílí více verzí sady Visual Studio. Tyto verze by mohl být automaticky načíst v sadě Visual Studio 2013 a starší, ale může přinést založený na pravidlech uživatelského rozhraní kontexty zabránit automatické načítání v aplikaci Visual Studio 2015.  
  
 Za účelem podpory těchto balíčků teď AutoLoadPackages položky v registru můžete zadat příznak v poli hodnota označující, že má být položka vynecháno v sadě Visual Studio 2015 a vyšší. To můžete udělat tak, že přidáte příznaky možnost <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>. Teď můžete přidávat rozšíření VSPackages **SkipWhenUIContextRulesActive** umožňuje jejich <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> atribut označuje položku v sadě Visual Studio 2015 a novější ignorovat.  
  
## <a name="extensible-ui-context-rules"></a>Rozšiřitelné pravidla kontextu uživatelského rozhraní  
 V některých případech balíčky nelze použít statická pravidla kontextu uživatelského rozhraní. Například předpokládejme, že máte balíček podporuje rozšiřitelnost tak, aby stav příkaz je založen na editoru typy podporovaných poskytovateli importované MEF. Pokud je rozšíření podporuje aktuální typ upravit, je příkaz povolen. V takových případech samotném balíčku nelze statické kontextu uživatelského rozhraní pravidlo použít, protože podmínky změní v závislosti na tom, jaké MEF rozšíření jsou k dispozici.  
  
 Za účelem podpory těchto balíčků, založený na pravidlech kontexty uživatelského rozhraní podporují výraz pevně zakódované "*", který označuje všechny níže uvedené podmínky se jde připojit k nebo. To umožňuje hlavní balíček a definovat známé uživatelské rozhraní kontext založený na pravidlech a provázat postupy stavu příkazu k tomuto kontextu. Později můžete přidat jakékoli MEF rozšíření určená pro hlavní balíček její podmínky pro editorů, které podporuje bez dopadu na ostatní podmínky nebo hlavní výraz.  
  
 Konstruktor <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> dokumentaci ukazuje syntaxi pro extensible pravidla kontextu uživatelského rozhraní.