---
title: Vlastnosti nástroje MSBuild | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, properties
ms.assetid: 962912ac-8931-49bf-a88c-0200b6e37362
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3c8835dab5ca866762a7d2b0e6cad1d0d80726b0
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2018
ms.locfileid: "48879187"
---
# <a name="msbuild-properties"></a>vlastnosti nástroje MSBuild
Vlastnosti jsou páry název-hodnota, které lze použít ke konfiguraci sestavení. Vlastnosti jsou užitečné pro předávání hodnot úkolům, vyhodnocování podmínek a ukládání hodnot, na které bude odkazováno v celém souboru projektu.  
  
## <a name="define-and-reference-properties-in-a-project-file"></a>Definování a odkazování na vlastnosti v souboru projektu  
 Vlastnosti jsou deklarovány vytvořením prvku, který má název vlastnosti jako podřízený objekt [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) elementu. Například následující XML kód vytvoří vlastnost s názvem `BuildDir`, která má hodnotu `Build`.  
  
```xml  
<PropertyGroup>  
    <BuildDir>Build</BuildDir>  
</PropertyGroup>  
```  
  
 V celém souboru projektu na vlastnosti odkazováno pomocí syntaxe $(\<PropertyName >). Například na vlastnost z předchozího příkladu se odkazuje pomocí syntaxe $(BuildDir).  
  
 Hodnoty vlastnosti lze změnit předefinováním vlastnosti. Vlastnost `BuildDir` může dostat novou hodnotu pomocí tohoto XML kódu:  
  
```xml  
<PropertyGroup>  
    <BuildDir>Alternate</BuildDir>  
</PropertyGroup>  
```  
  
 Vlastnosti jsou vyhodnocovány v pořadí, v jakém jsou uvedeny v souboru projektu. Novou hodnotu pro vlastnost `BuildDir` je třeba deklarovat poté, co je původní hodnota přiřazena.  
  
## <a name="reserved-properties"></a>Rezervované vlastnosti  
 Nástroj MSBuild rezervuje některé názvy vlastností k ukládání informací o souboru projektu a binární soubory nástroje MSBuild. Na tyto vlastnosti i jakékoli jiné vlastnosti je odkazováno pomocí zápisu $. Například syntaxe $(MSBuildProjectFile) vrátí celý název souboru projektu, včetně přípony názvu souboru.  
  
 Další informace najdete v tématu [postupy: odkazování na název nebo umístění souboru projektu](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md) a [MSBuild vyhrazené a dobře známé vlastnosti](../msbuild/msbuild-reserved-and-well-known-properties.md).  
  
## <a name="environment-properties"></a>Vlastnosti prostředí  
 V souborech projektu je možné odkazovat na proměnné prostředí stejným způsobem jako na rezervované vlastnosti. Například pro použití proměnné prostředí `PATH` v souboru projektu je třeba použít příkaz $(Path). Obsahuje-li projekt definici vlastnosti stejného názvu jako vlastnost prostředí, přepíše vlastnost v projektu hodnotu proměnné prostředí.  
  
 Každý projekt MSBuild má blok izolovaného prostředí, a tedy vidí, čte a zapisuje pouze do svého vlastního bloku.  Nástroj MSBuild načítá proměnné prostředí pouze při inicializaci kolekce vlastností a předtím, než je soubor projektu vyhodnocen nebo sestaven. Poté jsou vlastnosti prostředí statické, a tedy každý vytvořený nástroj je spuštěn se stejnými názvy a hodnotami.  
  
 Chcete-li získat aktuální hodnotu proměnných prostředí v rámci vytvořeného nástroje, použijte [funkce vlastností](../msbuild/property-functions.md) System.Environment.GetEnvironmentVariable. Upřednostňovanou metodou je však použití parametru úkolu <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A>. Vlastnosti prostředí nastavené v tomto poli řetězců mohou být předány vytvořenému nástroji bez ovlivnění systémových proměnných prostředí.  
  
> [!TIP]
>  Ne všechny proměnné prostředí jsou čteny pro potřeby počátečních vlastností. Proměnná prostředí, jehož název není platný MSBuild název vlastnosti, jako je například "386", je ignorován.  
  
 Další informace najdete v tématu [postupy: použití proměnných prostředí v sestavení](../msbuild/how-to-use-environment-variables-in-a-build.md).  
  
## <a name="registry-properties"></a>Vlastnosti registru  
 Je možné číst hodnoty systémového registru pomocí následující syntaxe, kde `Hive` je podregistr registru (například **HKEY_LOCAL_MACHINE**), `Key` je název klíče, `SubKey` je název podklíče a `Value`je hodnota v podklíči.  
  
```xml  
$(registry:Hive\MyKey\MySubKey@Value)  
```  
  
 Chcete-li získat výchozí hodnotu podklíče, je třeba vynechat `Value`.  
  
```xml  
$(registry:Hive\MyKey\MySubKey)  
```  
  
 Tato hodnota registru může sloužit k inicializaci vlastnosti sestavení. Například pro vytvoření vlastnosti sestavení, která představuje domovskou stránku webového prohlížeče sady Visual Studio, je třeba použít tento kód:  
  
```xml  
<PropertyGroup>  
  <VisualStudioWebBrowserHomePage>  
    $(registry:HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\WebBrowser@HomePage)  
  </VisualStudioWebBrowserHomePage>  
<PropertyGroup>  
```  
  
## <a name="global-properties"></a>Globální vlastnosti  
 Nástroj MSBuild umožňuje nastavit vlastnosti na příkazovém řádku s použitím **– vlastnost** (nebo **-p**) přepnutí. Tyto hodnoty globálních vlastností přepisují hodnoty vlastností, které jsou nastaveny v souboru projektu. To zahrnuje vlastnosti prostředí, ale nezahrnuje rezervované vlastnosti, které nelze změnit.  
  
 Následující příklad nastavuje globální vlastnost `Configuration` na `DEBUG`.  
  
```cmd  
msbuild.exe MyProj.proj -p:Configuration=DEBUG  
```  
  
 Globální vlastnosti je také možné nastavit nebo upravit pro podřízené projekty v sestaveních s více projekty pomocí atributu `Properties` úkolu MSBuild. Globální vlastnosti se také předávají do podřízené projekty, není-li `RemoveProperties` atribut úlohy nástroje MSBuild slouží k určení seznam vlastností není přeposlat. Další informace najdete v tématu [úlohy nástroje MSBuild](../msbuild/msbuild-task.md).
  
 Při určení vlastnosti pomocí atributu `TreatAsLocalProperty` ve značce projektu nepřepíše hodnota globální vlastnosti hodnotu vlastnosti, která je nastavena v souboru projektu. Další informace najdete v tématu [Project – element (MSBuild)](../msbuild/project-element-msbuild.md) a [postupy: sestavení stejných zdrojových souborů s různými možnostmi](../msbuild/how-to-build-the-same-source-files-with-different-options.md).  
  
## <a name="property-functions"></a>Funkce vlastností  
 Počínaje rozhraním .NET Framework verze 4 je možné použít funkce vlastností k vyhodnocení skriptů nástroje MSBuild. Ve skriptu sestavení je možné přečíst systémový čas, porovnat řetězce, porovnat regulární výrazy a provádět mnoho dalších akcí bez použití úkolů nástroje MSBuild.  
  
 Je možné použít metody řetězců (instance) na jakoukoli hodnotu vlastnosti a je možné volat statické metody mnoha systémových tříd. Například je takto možné nastavit vlastnost sestavení na dnešní datum.  
  
```xml  
<Today>$([System.DateTime]::Now.ToString("yyyy.MM.dd"))</Today>  
```  
  
 Další informace a seznam funkcí vlastností naleznete v tématu [funkce vlastností](../msbuild/property-functions.md).  
  
## <a name="create-properties-during-execution"></a>Vytvoření vlastností za běhu  
 Vlastnostem umístěným mimo prvky `Target` jsou přiřazeny hodnoty během fáze vyhodnocení sestavení. Během následující fáze vykonávání mohou být vlastnosti vytvořeny nebo upraveny následujícím způsobem:  
  
-   Vlastnost může být generována libovolným úkolem. K vygenerování vlastnosti [úloh](../msbuild/task-element-msbuild.md) element musí mít podřízený [výstup](../msbuild/output-element-msbuild.md) element, který má `PropertyName` atribut.  
  
-   Vlastnost může být vygenerována [CreateProperty](../msbuild/createproperty-task.md) úloh. Tento způsob využití je zastaralý.  
  
-   Počínaje rozhraním .NET Framework 3.5 mohou prvky `Target` obsahovat prvky `PropertyGroup`, které mohou obsahovat deklarace vlastností.  
  
## <a name="store-xml-in-properties"></a>Store XML ve vlastnostech  
 Vlastnosti mohou obsahovat libovolný XML kód, který může pomoci při předávání hodnot úkolům nebo zobrazení informací o protokolování. Následující příklad ukazuje vlastnost `ConfigTemplate`, která má hodnotu obsahující XML kód a další odkazy na vlastnosti. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] nahrazuje odkazy na vlastnosti odpovídajícími hodnotami vlastností. Hodnoty vlastností jsou přiřazeny v pořadí, v jakém jsou uvedeny. Proto by v tomto příkladu již měly být hodnoty `$(MySupportedVersion)`, `$(MyRequiredVersion)` a `$(MySafeMode)` definovány.  
  
```xml  
  
<PropertyGroup>  
    <ConfigTemplate>  
        <Configuration>  
            <Startup>  
                <SupportedRuntime  
                    ImageVersion="$(MySupportedVersion)"  
                    Version="$(MySupportedVersion)"/>  
                <RequiredRuntime  
                    ImageVersion="$(MyRequiredVersion)"  
                    Version="$(MyRequiredVersion)"  
                    SafeMode="$(MySafeMode)"/>  
            </Startup>  
        </Configuration>  
    </ConfigTemplate>  
</PropertyGroup>  
```  
  
## <a name="see-also"></a>Viz také:  
 [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)  
 [MSBuild](../msbuild/msbuild.md)  
 [Postupy: použití proměnných prostředí v sestavení](../msbuild/how-to-use-environment-variables-in-a-build.md)   
 [Postupy: odkazování na název nebo umístění souboru projektu](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md)   
 [Postupy: sestavení stejných zdrojových souborů s různými možnostmi](../msbuild/how-to-build-the-same-source-files-with-different-options.md)   
 [Nástroj MSBuild vyhrazené a dobře známé vlastnosti](../msbuild/msbuild-reserved-and-well-known-properties.md)   
 [Property – element (MSBuild)](../msbuild/property-element-msbuild.md)
