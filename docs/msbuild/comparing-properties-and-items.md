---
title: Porovnávání vlastností a položek | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, msbuild properties
ms.assetid: b9da45ae-d6a6-4399-8628-397deed31486
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 96166caefa749138371dd8a5ab2ea9d496553557
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2018
ms.locfileid: "39177111"
---
# <a name="compare-properties-and-items"></a>Porovnávání vlastností a položek
Vlastnosti nástroje MSBuild a položek se používají k předávání informací do úlohy, vyhodnocení podmínky a ukládat hodnoty, které může být odkazováno v celém souboru projektu.  
  
-   Vlastnosti jsou páry název hodnota. Další informace najdete v tématu [vlastnosti nástroje MSBuild](../msbuild/msbuild-properties.md).  
  
-   Položky jsou objekty, které obvykle představují soubory. Položka objekty mohou být přidruženy kolekce metadat. Metadata jsou páry název hodnota. Další informace najdete v tématu [položky](../msbuild/msbuild-items.md).  
  
## <a name="scalars-and-vectors"></a>Skaláry a vektorů  
 Protože vlastnosti nástroje MSBuild jsou páry název hodnota, které mají pouze jednu řetězcovou hodnotu, jsou často popisuje jako *skalární*. Protože MSBuild typů položek jsou seznamy položek, jsou často popisuje jako *vektoru*. V praxi však vlastnosti mohou představovat několik hodnot a typů položek může mít nejvýše jedno položky.  
  
### <a name="target-dependency-injection"></a>Injektáž závislostí cíl  
 Pokud chcete zobrazit, jak vlastnosti může představovat více hodnot, vezměte v úvahu běžným vzorem využití pro přidání cíle do seznamu cílů, které má být sestaven. Tento seznam je obvykle reprezentována hodnotu vlastnosti s cílové názvy oddělené středníky.  
  
```xml  
<PropertyGroup>  
    <BuildDependsOn>  
        BeforeBuild;  
        CoreBuild;  
        AfterBuild  
    </BuildDependsOn>  
</PropertyGroup>  
```  
  
 `BuildDependsOn` Vlastnost se obvykle používá jako argument cíl `DependsOnTargets` atribut efektivně jeho převodu do seznamu položek. Tuto vlastnost lze přepsat, chcete-li přidat cíl nebo chcete-li změnit pořadí provádění cílů. Například  
  
```xml  
<PropertyGroup>  
    <BuildDependsOn>  
        $(BuildDependsOn);  
        CustomBuild;  
    </BuildDependsOn>  
</PropertyGroup>  
```  
  
 Přidá cílový CustomBuild do cílového seznamu poskytuje `BuildDependsOn` hodnota `BeforeBuild;CoreBuild;AfterBuild;CustomBuild`.  
  
 Od verze MSBuild 4.0, vkládání závislostí cíl je zastaralý. Použití `AfterTargets` a `BeforeTargets` místo toho atributy. Další informace najdete v tématu [pořadí sestavení cílové](../msbuild/target-build-order.md).  
  
### <a name="conversions-between-strings-and-item-lists"></a>Převody mezi řetězci a položek seznamů  
 Nástroj MSBuild provádí převody do a z typů položek a řetězcové hodnoty podle potřeby. Pokud chcete zobrazit, jak seznam položek se může stát řetězcovou hodnotu, zvažte, co se stane, když typ položky, který se používá jako hodnotu vlastnosti nástroje MSBuild:  
  
```xml  
<ItemGroup>  
    <OutputDir Include="KeyFiles\;Certificates\" />  
  </ItemGroup>  
<PropertyGroup>  
    <OutputDirList>@(OutputDir)</OutputDirList>  
</PropertyGroup>  
```  
  
 Typ položky OutputDir má `Include` atributu s hodnotou "klíčového souboru\\; Certifikáty\\". Nástroj MSBuild analyzuje tento řetězec na dvě položky: KeyFiles\ a certifikáty\\. Pokud typ položky OutputDir slouží jako hodnota vlastnosti OutputDirList, MSBuild převede nebo "sloučí" typu položky do oddělených středníkem řetězec "klíčového souboru\\; Certifikáty\\".  
  
## <a name="properties-and-items-in-tasks"></a>Vlastnosti a položky v úlohách  
 Vlastností a položek se používají jako vstupy a výstupy pro úlohy nástroje MSBuild. Další informace najdete v tématu [úlohy](../msbuild/msbuild-tasks.md).  
  
 Vlastnosti jsou předány na úkoly jako atributy. V úloze vlastnost MSBuild představuje typ vlastnosti, jehož hodnota je možné převést do a z řetězce. Typy podporovaných vlastností zahrnují `bool`, `char`, `DateTime`, `Decimal`, `Double`, `int`, `string`, a jakýkoli typ, který <xref:System.Convert.ChangeType%2A> dokáže zpracovat.  
  
 Položky jsou předány na úkoly jako <xref:Microsoft.Build.Framework.ITaskItem> objekty. V úloze <xref:Microsoft.Build.Framework.ITaskItem.ItemSpec%2A> představuje hodnotu položky a <xref:Microsoft.Build.Framework.ITaskItem.GetMetadata%2A> načte jeho metadata.  
  
 Seznam položek typu položky mohou být předány jako pole `ITaskItem` objekty. Od verze rozhraní .NET Framework 3.5, položky můžete odebrat ze seznamu položek v cíli s použitím `Remove` atribut. Protože položky je odebrat ze seznamu položek, je možné pro typ položky, který chcete obsahují nulové položky. Pokud seznam položek je předán úkolu, by měla tato možnost vyhledávat kód v úloze.  
  
## <a name="property-and-item-evaluation-order"></a>Pořadí vyhodnocování vlastností a položek  
 Během fáze vyhodnocení sestavení importované soubory jsou součástí sestavení v pořadí, v jakém jsou uvedeny. Vlastnosti a položky jsou definovány v tři průchody v následujícím pořadí:  
  
-   Vlastnosti jsou definovány a upravovat v pořadí, ve kterém jsou uvedeny.  
  
-   Definice položek jsou definovány a upravovat v pořadí, ve kterém jsou uvedeny.  
  
-   Položky jsou definovány a upravovat v pořadí, ve kterém jsou uvedeny.  
 
 
 Během fáze spuštění sestavení vlastností a položek, které jsou definovány v rámci cíle jsou vyhodnocovány společně v jedné fáze v pořadí, v jakém jsou uvedeny.  
 
 Ale to není celý příběh. Když je definována vlastnost, definice položky nebo položky, jeho hodnota se vyhodnocuje. Chyba při vyhodnocování výrazu rozšíří řetězec, který určuje hodnotu parametru. Řetězec rozbalení je závislé na fázi sestavení. Tady je podrobnější pořadí vyhodnocování vlastností a položek:  
  
-   Během fáze vyhodnocení sestavení:  
  
    -   Vlastnosti jsou definovány a upravovat v pořadí, ve kterém jsou uvedeny. Funkce vlastností jsou spuštěny. Hodnoty vlastností ve formě $(PropertyName) rozbaleny v rámci výrazů. Hodnota vlastnosti je nastavena na rozbalené výraz.  
  
    -   Definice položek jsou definovány a upravovat v pořadí, ve kterém jsou uvedeny. Funkce vlastností byl rozbalen ve výrazech. Metadata hodnoty jsou nastaveny na rozbalené výrazy.  
  
    -   Typy položek jsou definovány a upravovat v pořadí, ve kterém jsou uvedeny. Hodnoty položek ve formuláři @(ItemType) rozbaleny. Transformace položky jsou také rozšířit. Funkce vlastností a hodnot už rozšířily ve výrazech. Hodnoty položky seznamu a metadata jsou nastaveny na rozbalené výrazy.  
  
-   Během fáze spuštění sestavení:  
  
    -   Vlastnosti a položky, které jsou definovány v rámci cíle jsou vyhodnocovány společně v pořadí, v jakém jsou uvedeny. Vlastnosti funkcí se spustí a hodnoty vlastností jsou rozbaleny v rámci výrazů. Hodnoty položek a transformace položky jsou také rozšířit. Hodnoty vlastností, hodnoty položek typu a hodnoty metadat jsou nastaveny na rozbalené výrazy.  
  
### <a name="subtle-effects-of-the-evaluation-order"></a>Malý vliv pořadí vyhodnocování  
 Vyhodnocení vlastnosti v fáze vyhodnocení sestavení předchází vyhodnocení položky. Vlastnosti však může mít hodnoty, které se zobrazují závisí na hodnoty položek. Vezměte v úvahu následující skript.  
  
```xml  
<ItemGroup>  
    <KeyFile Include="KeyFile.cs">  
        <Version>1.0.0.3</Version>  
    </KeyFile>  
</ItemGroup>  
<PropertyGroup>  
    <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>  
</PropertyGroup>  
<Target Name="AfterBuild">  
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />  
</Target>  
```  
  
 Provádění úlohy zpráva se zobrazí tato zpráva:  
  
```  
KeyFileVersion: 1.0.0.3  
```  
  
 Důvodem je, že hodnota `KeyFileVersion` je ve skutečnosti řetězec "\@(KeyFile -> % (verze))". Položka a transformace položky nebyly rozšířeny při prvním byla definována vlastnost, proto `KeyFileVersion` vlastnost byla přiřazena hodnota nerozbalený řetězce.  
  
 Během fáze spuštění sestavení po zpracování zprávy úloh, nástroj MSBuild rozšíří řetězec "\@(KeyFile -> % (verze))" na "1.0.0.3".  
  
 Všimněte si, že tato zpráva objevuje i v případě, že skupiny vlastností a položek byly vráceny zpět v pořadí.  
  
 Druhý příklad zvažte, co se může stát, když vlastnosti a položky skupiny se nacházejí v rámci cíle:  
  
```xml  
<Target Name="AfterBuild">  
    <PropertyGroup>  
        <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>  
    </PropertyGroup>  
    <ItemGroup>  
        <KeyFile Include="KeyFile.cs">  
            <Version>1.0.0.3</Version>  
        </KeyFile>  
    </ItemGroup>  
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />  
</Target>  
```  
  
 Úloha zprávy zobrazí tato zpráva:  
  
```  
KeyFileVersion:   
```  
  
 Důvodem je, že během fáze spuštění sestavení, jsou vyhodnocovány vlastnosti a položky skupiny definované v rámci cíle shora dolů ve stejnou dobu. Když `KeyFileVersion` je definován, `KeyFile` neznámý. Proto transformace položky rozšíří na prázdný řetězec.  
  
 V takovém případě obráceným pořadím porovnávaných skupiny vlastností a položek obnoví původní zprávy:  
  
```xml  
<Target Name="AfterBuild">  
    <ItemGroup>  
        <KeyFile Include="KeyFile.cs">  
            <Version>1.0.0.3</Version>  
        </KeyFile>  
    </ItemGroup>  
    <PropertyGroup>  
        <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>  
    </PropertyGroup>  
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />  
</Target>  
```  
  
 Hodnota `KeyFileVersion` je nastavena na "1.0.0.3" a nikoli k "\@(KeyFile -> % (verze))". Úloha zprávy zobrazí tato zpráva:  
  
```  
KeyFileVersion: 1.0.0.3  
```  
  
## <a name="see-also"></a>Viz také:  
 [Rozšířené koncepty](../msbuild/msbuild-advanced-concepts.md)