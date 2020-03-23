---
title: GenerateBootstrapper úkol | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634081"
---
# <a name="generatebootstrapper-task"></a>GenerateBootstrapper – úloha

Poskytuje automatizovaný způsob, jak zjistit, stáhnout a nainstalovat aplikaci a její požadavky. Slouží jako jediný instalátor, který integruje samostatné instalační programy pro všechny součásti tvořící aplikaci.

## <a name="task-parameters"></a>Parametry úlohy

Následující popište parametry `GenerateBootstrapper` úlohy.

- `ApplicationFile`

   Volitelný `String` parametr.

   Určuje soubor, který zaváděcí nástroj použije k zahájení instalace aplikace po instalaci všech požadavků. Chyba sestavení bude mít za `BootstrapperItems` následek, pokud není zadán ani `ApplicationFile` parametr ani parametr.

- `ApplicationName`

   Volitelný `String` parametr.

   Určuje název aplikace, kterou bude zaváděcí nástroj instalovat. Tento název se zobrazí v uživatelském uživatelském médiu, které zaváděcí nástroj používá během instalace.

- `ApplicationRequiresElevation`

   Volitelný `Boolean` parametr.

   Pokud `true`je komponenta spuštěna se zvýšenými oprávněními, když je nainstalována v cílovém počítači.

- `ApplicationUrl`

   Volitelný `String` parametr.

   Určuje webové umístění, které je hostitelem instalačního programu aplikace.

- `BootstrapperComponentFiles`

   Volitelný `String[]` výstupní parametr.

   Určuje vytvořené umístění souborů balíčků zaváděcího nástroje.

- `BootstrapperItems`

   Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.

   Určuje produkty, které mají být zaváděny do zaváděcího nástroje. Položky předané tomuto parametru by měly mít následující syntaxi:

  ```xml
  <BootstrapperItem
      Include="ProductCode">
      <ProductName>
          ProductName
      </ProductName>
  </BootstrapperItem>
  ```

   Atribut `Include` představuje název předpokladu, který by měl být nainstalován. Metadata `ProductName` položky je volitelné a budou použity modul sestavení jako uživatelsky přívětivý název, pokud balíček nelze najít. Tyto položky nejsou požadovány MSBuild `ApplicationFile` vstupní parametry, pokud není zadán žádný. Měli byste zahrnout jednu položku pro každý předpoklad, který musí být nainstalován pro vaši aplikaci.

   Chyba sestavení bude mít za `BootstrapperItems` následek, pokud není zadán ani `ApplicationFile` parametr ani parametr.

- `BootstrapperKeyFile`

   Volitelný `String` výstupní parametr.

   Určuje zabudované umístění programu *setup.exe.*

- `ComponentsLocation`

   Volitelný `String` parametr.

   Určuje umístění zaváděcího nástroje, kde má nástroj hledat požadavky na instalaci. Tento parametr může mít následující hodnoty:

  - `HomeSite`: Označuje, že předpoklad je hostován dodavatelem komponenty.

  - `Relative`: Označuje, že předpoklad je ve stejném umístění aplikace.

  - `Absolute`: Označuje, že všechny součásti se nacházejí na centralizované adrese URL. Tato hodnota by měla být `ComponentsUrl` použita ve spojení se vstupním parametrem.

    Pokud `ComponentsLocation` není zadán, `HomeSite` je používán ve výchozím nastavení.

- `ComponentsUrl`

   Volitelný `String` parametr.

   Určuje adresu URL obsahující požadavky na instalaci.

- `CopyComponents`

   Volitelný `Boolean` parametr.

   Pokud `true`nástrojač zkopíruje všechny výstupní soubory do `OutputPath` cesty určené v parametru. Všechny hodnoty `BootstrapperComponentFiles` parametru by měly být založeny na této cestě. Pokud `false`se soubory nezkopírují a `BootstrapperComponentFiles` hodnoty jsou založeny `Path` na hodnotě parametru.  Výchozí hodnota tohoto parametru je `true`.

- `Culture`

   Volitelný `String` parametr.

   Určuje jazykovou verzi, která má být používána pro zaváděcí nástroj a požadavky na instalaci. Pokud zadaná jazyková verze není k `FallbackCulture` dispozici, úloha použije hodnotu parametru.

- `FallbackCulture`

   Volitelný `String` parametr.

   Určuje sekundární jazykovou verzi, která má být používána pro zaváděcí prostředí a požadavky instalace.

- `OutputPath`

   Volitelný `String` parametr.

   Určuje umístění, ve které chcete kopírovat *soubor setup.exe* a všechny soubory balíčků.

- `Path`

   Volitelný `String` parametr.

   Určuje umístění všech dostupných nezbytných balíčků.

- `SupportUrl`

   Volitelný `String` parametr.

   Určuje adresu URL, která má být poskytnuta, pokud se instalace zaváděcího nástroje nezdaří.

- `Validate`

   Volitelný `Boolean` parametr.

   Pokud `true`nástrojač provádí ověření XSD u zadaných položek vstupního zaváděcího nástroje. Výchozí hodnota tohoto parametru je `false`.

## <a name="remarks"></a>Poznámky

Kromě výše uvedených parametrů tato úloha dědí <xref:Microsoft.Build.Tasks.TaskExtension> parametry z třídy, <xref:Microsoft.Build.Utilities.Task> která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

Následující příklad používá `GenerateBootstrapper` úlohu k instalaci aplikace, která musí mít jako podmínku nainstalována rozhraní .NET Framework 2.0.

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
