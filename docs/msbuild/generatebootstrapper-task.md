---
title: Úloha GenerateBootstrapper – | Microsoft Docs
description: Použijte úlohu GenerateBootstrapper – nástroje MSBuild pro automatizovaný způsob detekce, stažení a instalace aplikace a jejích požadavků.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 93dbe9d3bf49118328cb53dcd6602bb5fda77b13
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914873"
---
# <a name="generatebootstrapper-task"></a>GenerateBootstrapper – úloha

Poskytuje automatizovaný způsob detekce, stažení a instalace aplikace a jejích požadavků. Slouží jako jediný instalační program, který integruje samostatné instalační programy pro všechny komponenty, které tvoří aplikaci.

## <a name="task-parameters"></a>Parametry úlohy

Následující popis popisuje parametry `GenerateBootstrapper` úkolu.

- `ApplicationFile`

   Volitelný `String` parametr.

   Určuje soubor, který zaváděcí program použije k zahájení instalace aplikace po instalaci všech požadovaných součástí. Pokud `BootstrapperItems` není zadán ani parametr, bude výsledkem chyba sestavení `ApplicationFile` .

- `ApplicationName`

   Volitelný `String` parametr.

   Určuje název aplikace, kterou bude instalovat zaváděcí nástroj. Tento název se zobrazí v uživatelském rozhraní, které zaváděcí nástroj používá během instalace.

- `ApplicationRequiresElevation`

   Volitelný `Boolean` parametr.

   Pokud se `true` komponenta spouští se zvýšenými oprávněními, když je nainstalovaná na cílovém počítači.

- `ApplicationUrl`

   Volitelný `String` parametr.

   Určuje umístění webu, které hostuje instalační program aplikace.

- `BootstrapperComponentFiles`

   Volitelný `String[]` výstupní parametr.

   Určuje sestavené umístění souborů balíčku zaváděcího nástroje.

- `BootstrapperItems`

   Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.

   Určuje produkty, které se mají sestavit do zaváděcího nástroje. Položky předané do tohoto parametru by měly mít následující syntaxi:

  ```xml
  <BootstrapperItem
      Include="ProductCode">
      <ProductName>
          ProductName
      </ProductName>
  </BootstrapperItem>
  ```

   `Include`Atribut představuje název předpokladu, který by měl být nainstalován. `ProductName`Metadata položky jsou volitelná a modul sestavení ho použije jako uživatelsky přívětivý název, pokud balíček nejde najít. Tyto položky nejsou vyžadovány vstupními parametry nástroje MSBuild, pokud `ApplicationFile` není zadán parametr No. Měli byste zahrnout jednu položku pro každý požadavek, který musí být nainstalovaný pro vaši aplikaci.

   Pokud `BootstrapperItems` není zadán ani parametr, bude výsledkem chyba sestavení `ApplicationFile` .

- `BootstrapperKeyFile`

   Volitelný `String` výstupní parametr.

   Určuje sestavené umístění *setup.exe*

- `ComponentsLocation`

   Volitelný `String` parametr.

   Určuje umístění pro zaváděcí nástroj, který bude hledat požadavky instalace pro instalaci. Tento parametr může mít následující hodnoty:

  - `HomeSite`: Označuje, že požadovaná součást je hostována dodavatelem součásti.

  - `Relative`: Označuje, že požadovaná součást je ve stejném umístění aplikace.

  - `Absolute`: Označuje, že všechny součásti se mají najít na centralizované adrese URL. Tato hodnota by měla být použita ve spojení se `ComponentsUrl` vstupním parametrem.

    Pokud není `ComponentsLocation` zadaný, `HomeSite` použije se ve výchozím nastavení.

- `ComponentsUrl`

   Volitelný `String` parametr.

   Určuje adresu URL obsahující předpoklady pro instalaci.

- `CopyComponents`

   Volitelný `Boolean` parametr.

   Pokud `true` Nástroj nakopíruje všechny výstupní soubory do cesty zadané v `OutputPath` parametru. Hodnoty `BootstrapperComponentFiles` parametru by měly být založené na této cestě. Pokud nejsou `false` soubory zkopírovány a `BootstrapperComponentFiles` hodnoty jsou založeny na hodnotě `Path` parametru.  Výchozí hodnota tohoto parametru je `true` .

- `Culture`

   Volitelný `String` parametr.

   Určuje jazykovou verzi, která se má použít pro uživatelské rozhraní zaváděcího nástroje a požadavky na instalaci. Pokud zadaná jazyková verze není k dispozici, úloha použije hodnotu `FallbackCulture` parametru.

- `FallbackCulture`

   Volitelný `String` parametr.

   Určuje sekundární jazykovou verzi, která se má použít pro uživatelské rozhraní zaváděcího nástroje a požadavky na instalaci.

- `OutputPath`

   Volitelný `String` parametr.

   Určuje umístění pro kopírování *setup.exe* a všechny soubory balíčku.

- `Path`

   Volitelný `String` parametr.

   Určuje umístění všech dostupných balíčků požadovaných součástí.

- `SupportUrl`

   Volitelný `String` parametr.

   Určuje adresu URL, která má být zadaná, pokud se instalace zaváděcího nástroje nepovede.

- `Validate`

   Volitelný `Boolean` parametr.

   Pokud `true` nástroj provede ověření XSD na zadaných položkách zaváděcího nástroje pro vstup. Výchozí hodnota tohoto parametru je `false` .

## <a name="remarks"></a>Poznámky

Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

Následující příklad používá `GenerateBootstrapper` úlohu k instalaci aplikace, která musí mít nainstalovanou .NET Framework 2,0 jako předpoklad.

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
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
