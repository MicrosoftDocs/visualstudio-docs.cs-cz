---
title: Vlastnosti nástroje MSBuild | Microsoft Docs
description: Přečtěte si, jak páry vlastností název-hodnota MSBuild můžou předat hodnoty úkolům, vyhodnotit podmínky a uložit hodnoty.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, properties
ms.assetid: 962912ac-8931-49bf-a88c-0200b6e37362
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a8f53613c71a51ab2e5bd8441cb4605da795e8a7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897760"
---
# <a name="msbuild-properties"></a>vlastnosti nástroje MSBuild

Vlastnosti jsou páry název-hodnota, které lze použít ke konfiguraci sestavení. Vlastnosti jsou užitečné pro předávání hodnot úkolům, vyhodnocování podmínek a ukládání hodnot, na které bude odkazováno v celém souboru projektu.

## <a name="define-and-reference-properties-in-a-project-file"></a>Definování a reference vlastností v souboru projektu

 Vlastnosti jsou deklarovány vytvořením prvku, který má název vlastnosti jako podřízený prvek elementu [Property](../msbuild/propertygroup-element-msbuild.md) . Například následující XML kód vytvoří vlastnost s názvem `BuildDir`, která má hodnotu `Build`.

```xml
<PropertyGroup>
    <BuildDir>Build</BuildDir>
</PropertyGroup>
```

 V celém souboru projektu je na vlastnosti odkazováno pomocí syntaxe $(\<PropertyName>). Například na vlastnost z předchozího příkladu se odkazuje pomocí syntaxe $(BuildDir).

 Hodnoty vlastnosti lze změnit předefinováním vlastnosti. Vlastnost `BuildDir` může dostat novou hodnotu pomocí tohoto XML kódu:

```xml
<PropertyGroup>
    <BuildDir>Alternate</BuildDir>
</PropertyGroup>
```

 Vlastnosti jsou vyhodnocovány v pořadí, v jakém jsou uvedeny v souboru projektu. Novou hodnotu pro vlastnost `BuildDir` je třeba deklarovat poté, co je původní hodnota přiřazena.

## <a name="reserved-properties"></a>Rezervované vlastnosti

 Nástroj MSBuild si vyhrazuje některé názvy vlastností pro ukládání informací o souboru projektu a binárních souborech nástroje MSBuild. Na tyto vlastnosti i jakékoli jiné vlastnosti je odkazováno pomocí zápisu $. Například syntaxe $(MSBuildProjectFile) vrátí celý název souboru projektu, včetně přípony názvu souboru.

 Další informace najdete v tématu [Postup: odkazování na název nebo umístění souboru projektu](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md) a [rezervované a dobře známé vlastnosti nástroje MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md).

## <a name="environment-properties"></a>Vlastnosti prostředí

 V souborech projektu je možné odkazovat na proměnné prostředí stejným způsobem jako na rezervované vlastnosti. Například pro použití proměnné prostředí `PATH` v souboru projektu je třeba použít příkaz $(Path). Obsahuje-li projekt definici vlastnosti stejného názvu jako vlastnost prostředí, přepíše vlastnost v projektu hodnotu proměnné prostředí.

 Každý projekt MSBuild má blok izolovaného prostředí, a tedy vidí, čte a zapisuje pouze do svého vlastního bloku.  Nástroj MSBuild načítá proměnné prostředí pouze při inicializaci kolekce vlastností a předtím, než je soubor projektu vyhodnocen nebo sestaven. Poté jsou vlastnosti prostředí statické, a tedy každý vytvořený nástroj je spuštěn se stejnými názvy a hodnotami.

 Chcete-li získat aktuální hodnotu proměnných prostředí v rámci vytvořeného nástroje, použijte [funkci Property](../msbuild/property-functions.md) System. Environment. GetEnvironmentVariable. Upřednostňovanou metodou je však použití parametru úkolu <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A>. Vlastnosti prostředí nastavené v tomto poli řetězců mohou být předány vytvořenému nástroji bez ovlivnění systémových proměnných prostředí.

> [!TIP]
> Ne všechny proměnné prostředí jsou čteny pro potřeby počátečních vlastností. Jakákoli proměnná prostředí, jejíž název není platným názvem vlastnosti MSBuild, například "386", je ignorována.

 Další informace najdete v tématu [Postupy: použití proměnných prostředí v sestavení](../msbuild/how-to-use-environment-variables-in-a-build.md).

## <a name="registry-properties"></a>Vlastnosti registru

 Hodnoty systémového registru můžete číst pomocí následující syntaxe, kde `Hive` je podregistr registru (například **HKEY_LOCAL_MACHINE**), `MyKey` je název klíče, `MySubKey` je název podklíče a `Value` je hodnota podklíče.

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

 Nástroj MSBuild umožňuje nastavit vlastnosti v příkazovém řádku pomocí přepínače **-Property** (nebo **-p**). Tyto hodnoty globálních vlastností přepisují hodnoty vlastností, které jsou nastaveny v souboru projektu. To zahrnuje vlastnosti prostředí, ale nezahrnuje rezervované vlastnosti, které nelze změnit.

 Následující příklad nastavuje globální vlastnost `Configuration` na `DEBUG`.

```cmd
msbuild.exe MyProj.proj -p:Configuration=DEBUG
```

 Globální vlastnosti je také možné nastavit nebo upravit pro podřízené projekty v sestaveních s více projekty pomocí atributu `Properties` úkolu MSBuild. Globální vlastnosti jsou také předávány podřízeným projektům, pokud `RemoveProperties` atribut úlohy MSBuild není použit k určení seznamu vlastností, které nemají být předány. Další informace najdete v tématu [Úloha MSBuild](../msbuild/msbuild-task.md).

 Při určení vlastnosti pomocí atributu `TreatAsLocalProperty` ve značce projektu nepřepíše hodnota globální vlastnosti hodnotu vlastnosti, která je nastavena v souboru projektu. Další informace naleznete v tématu [Project element (MSBuild)](../msbuild/project-element-msbuild.md) a [Postupy: sestavení stejných zdrojových souborů s různými možnostmi](../msbuild/how-to-build-the-same-source-files-with-different-options.md).

## <a name="property-functions"></a>Funkce vlastností

 Počínaje rozhraním .NET Framework verze 4 je možné použít funkce vlastností k vyhodnocení skriptů nástroje MSBuild. Ve skriptu sestavení je možné přečíst systémový čas, porovnat řetězce, porovnat regulární výrazy a provádět mnoho dalších akcí bez použití úkolů nástroje MSBuild.

 Je možné použít metody řetězců (instance) na jakoukoli hodnotu vlastnosti a je možné volat statické metody mnoha systémových tříd. Například je takto možné nastavit vlastnost sestavení na dnešní datum.

```xml
<Today>$([System.DateTime]::Now.ToString("yyyy.MM.dd"))</Today>
```

 Další informace a seznam funkcí vlastností naleznete v tématu [funkce vlastností](../msbuild/property-functions.md).

## <a name="create-properties-during-execution"></a>Během provádění vytvořit vlastnosti

 Vlastnostem umístěným mimo prvky `Target` jsou přiřazeny hodnoty během fáze vyhodnocení sestavení. Během následující fáze vykonávání mohou být vlastnosti vytvořeny nebo upraveny následujícím způsobem:

- Vlastnost může být generována libovolným úkolem. Chcete-li vygenerovat vlastnost, musí mít element [Task](../msbuild/task-element-msbuild.md) podřízený element [Output](../msbuild/output-element-msbuild.md) , který má `PropertyName` atribut.

- Vlastnost může být vygenerována úlohou [CreateProperty –](../msbuild/createproperty-task.md) . Tento způsob využití je zastaralý.

- Počínaje rozhraním .NET Framework 3.5 mohou prvky `Target` obsahovat prvky `PropertyGroup`, které mohou obsahovat deklarace vlastností.

## <a name="store-xml-in-properties"></a>Uložit XML ve vlastnostech

 Vlastnosti mohou obsahovat libovolný XML kód, který může pomoci při předávání hodnot úkolům nebo zobrazení informací o protokolování. Následující příklad ukazuje vlastnost `ConfigTemplate`, která má hodnotu obsahující XML kód a další odkazy na vlastnosti. MSBuild nahrazuje odkazy na vlastnosti pomocí jejich příslušných hodnot vlastností. Hodnoty vlastností jsou přiřazeny v pořadí, v jakém jsou uvedeny. Proto by v tomto příkladu již měly být hodnoty `$(MySupportedVersion)`, `$(MyRequiredVersion)` a `$(MySafeMode)` definovány.

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

## <a name="see-also"></a>Viz také

- [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [Postupy: použití proměnných prostředí v sestavení](../msbuild/how-to-use-environment-variables-in-a-build.md)
- [Postupy: odkazování na název nebo umístění souboru projektu](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md)
- [Postupy: sestavení stejných zdrojových souborů s různými možnostmi](../msbuild/how-to-build-the-same-source-files-with-different-options.md)
- [Vyhrazené a známé vlastnosti nástroje MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
- [Property – element (MSBuild)](../msbuild/property-element-msbuild.md)
