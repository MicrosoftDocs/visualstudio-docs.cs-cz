---
title: Úloha GenerateBootstrapper – | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateBootstrapper
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateBootstrapper task
- GenerateBootstrapper task [MSBuild]
ms.assetid: ca3ba2c6-d2ea-41f2-b7e3-0fc2b0730460
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6da773fdf6cd84819ea0e73083995f60e3c17e2d
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634081"
---
# <a name="generatebootstrapper-task"></a>GenerateBootstrapper – úloha

Poskytuje automatizovaný způsob detekce, stažení a instalace aplikace a jejích požadavků. Slouží jako jediný instalační program, který integruje samostatné instalační programy pro všechny komponenty, které tvoří aplikaci.

## <a name="task-parameters"></a>Parametry úlohy

Následující popis parametrů úlohy `GenerateBootstrapper`.

- `ApplicationFile`

   Volitelný parametr `String`.

   Určuje soubor, který zaváděcí program použije k zahájení instalace aplikace po instalaci všech požadovaných součástí. Pokud není zadán parametr `BootstrapperItems` ani `ApplicationFile`, bude chyba sestavení výsledkem.

- `ApplicationName`

   Volitelný parametr `String`.

   Určuje název aplikace, kterou bude instalovat zaváděcí nástroj. Tento název se zobrazí v uživatelském rozhraní, které zaváděcí nástroj používá během instalace.

- `ApplicationRequiresElevation`

   Volitelný parametr `Boolean`.

   Pokud `true`, bude se komponenta spouštět se zvýšenými oprávněními, když je nainstalovaná na cílovém počítači.

- `ApplicationUrl`

   Volitelný parametr `String`.

   Určuje umístění webu, které hostuje instalační program aplikace.

- `BootstrapperComponentFiles`

   Volitelný výstupní parametr `String[]`.

   Určuje sestavené umístění souborů balíčku zaváděcího nástroje.

- `BootstrapperItems`

   Volitelný <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr.

   Určuje produkty, které se mají sestavit do zaváděcího nástroje. Položky předané do tohoto parametru by měly mít následující syntaxi:

  ```xml
  <BootstrapperItem
      Include="ProductCode">
      <ProductName>
          ProductName
      </ProductName>
  </BootstrapperItem>
  ```

   Atribut `Include` představuje název předpokladu, který by měl být nainstalován. Metadata `ProductName` položky jsou volitelná a modul sestavení ho použije jako uživatelsky přívětivý název, pokud balíček nejde najít. Tyto položky nejsou vyžadovány vstupními parametry nástroje MSBuild, pokud není zadána žádná `ApplicationFile`. Měli byste zahrnout jednu položku pro každý požadavek, který musí být nainstalovaný pro vaši aplikaci.

   Pokud není zadán parametr `BootstrapperItems` ani `ApplicationFile`, bude chyba sestavení výsledkem.

- `BootstrapperKeyFile`

   Volitelný výstupní parametr `String`.

   Určuje sestavené umístění souboru *Setup. exe.*

- `ComponentsLocation`

   Volitelný parametr `String`.

   Určuje umístění pro zaváděcí nástroj, který bude hledat požadavky instalace pro instalaci. Tento parametr může mít následující hodnoty:

  - `HomeSite`: označuje, že je požadovaná součást hostována dodavatelem součásti.

  - `Relative`: označuje, že požadovaná součást je ve stejném umístění aplikace.

  - `Absolute`: označuje, že všechny součásti se mají najít na centralizované adrese URL. Tato hodnota by měla být použita ve spojení s parametrem `ComponentsUrl` Input.

    Pokud není zadaný `ComponentsLocation`, ve výchozím nastavení se použije `HomeSite`.

- `ComponentsUrl`

   Volitelný parametr `String`.

   Určuje adresu URL obsahující předpoklady pro instalaci.

- `CopyComponents`

   Volitelný parametr `Boolean`.

   Pokud `true`, zaváděcí nástroj zkopíruje všechny výstupní soubory do cesty zadané v parametru `OutputPath`. Hodnoty parametru `BootstrapperComponentFiles` by měly být založené na této cestě. Pokud `false`, soubory nejsou zkopírovány a hodnoty `BootstrapperComponentFiles` jsou založeny na hodnotě parametru `Path`.  Výchozí hodnota tohoto parametru je `true`.

- `Culture`

   Volitelný parametr `String`.

   Určuje jazykovou verzi, která se má použít pro uživatelské rozhraní zaváděcího nástroje a požadavky na instalaci. Pokud zadaná jazyková verze není k dispozici, úloha používá hodnotu parametru `FallbackCulture`.

- `FallbackCulture`

   Volitelný parametr `String`.

   Určuje sekundární jazykovou verzi, která se má použít pro uživatelské rozhraní zaváděcího nástroje a požadavky na instalaci.

- `OutputPath`

   Volitelný parametr `String`.

   Určuje umístění pro kopírování souboru *Setup. exe* a všech souborů balíčku.

- `Path`

   Volitelný parametr `String`.

   Určuje umístění všech dostupných balíčků požadovaných součástí.

- `SupportUrl`

   Volitelný parametr `String`.

   Určuje adresu URL, která má být zadaná, pokud se instalace zaváděcího nástroje nepovede.

- `Validate`

   Volitelný parametr `Boolean`.

   Pokud `true`, zaváděcí nástroj provede ověření XSD na zadaných položkách zaváděcího nástroje. Výchozí hodnota tohoto parametru je `false`.

## <a name="remarks"></a>Poznámky

Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, které sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

Následující příklad používá úlohu `GenerateBootstrapper` k instalaci aplikace, která musí mít nainstalovanou .NET Framework 2,0 jako předpoklad.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <BootstrapperFile Include="Microsoft.Net.Framework.2.0">
            <ProductName>Microsoft .NET Framework 2.0</ProductName>
        </BootstrapperFile>
    </ItemGroup>

    <Target Name="BuildBootstrapper">
        <GenerateBootstrapper
            ApplicationFile="WindowsApplication1.application"
            ApplicationName="WindowsApplication1"
            ApplicationUrl="http://mycomputer"
            BootstrapperItems="@(BootstrapperFile)"
            OutputPath="C:\output" />
    </Target>

</Project>
```

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
