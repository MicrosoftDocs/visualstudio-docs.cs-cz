---
title: Úloha GenerateBootstrapper – | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 488caf02a20b4f0855df1ba2ef64c85e70e1a6a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149631"
---
# <a name="generatebootstrapper-task"></a>GenerateBootstrapper – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Poskytuje automatizovaný způsob detekce, stažení a instalace aplikace a jejích požadavků. Slouží jako jediný instalační program, který integruje samostatné instalační programy pro všechny komponenty, které tvoří aplikaci.  
  
## <a name="task-parameters"></a>Parametry úlohy  
 Následující tabulka popisuje parametry `GenerateBootstrapper` úkolu.  
  
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
  
  ```  
  <BootstrapperItem  
      Include="ProductCode">  
      <ProductName>  
          ProductName  
      </ProductName>  
  </BootstrapperItem>  
  ```  
  
   `Include`Atribut slouží k reprezentaci názvu předpokladu, který by měl být nainstalován. `ProductName`Metadata položky jsou volitelná a budou se používat modul buildu jako uživatelsky přívětivý název pro případ, že balíček nejde najít. Tyto položky nejsou vyžadovány [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] vstupními parametry `ApplicationFile` , pokud není zadán parametr No. Měli byste zahrnout jednu položku pro všechny požadavky, které musí být nainstalované pro vaši aplikaci.  
  
   Pokud `BootstrapperItems` není zadán ani parametr, bude výsledkem chyba sestavení `ApplicationFile` .  
  
- `BootstrapperKeyFile`  
  
   Volitelný `String` výstupní parametr.  
  
   Určuje sestavené umístění setup.exe  
  
- `ComponentsLocation`  
  
   Volitelný `String` parametr.  
  
   Určuje umístění pro zaváděcí nástroj, který bude hledat požadavky instalace pro instalaci. Tento parametr může mít následující hodnoty::  
  
  - `HomeSite`: Označuje, že požadovaná součást je hostována dodavatelem součásti.  
  
  - `Relative`: Označuje, že preqrequisite je ve stejném umístění aplikace.  
  
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
  
   Určuje jazykovou verzi, která se má použít pro uživatelské rozhraní zaváděcího nástroje a požadavky na instalaci. Pokud je zadaná jazyková verze není k dispozici, úloha používá hodnotu `FallbackCulture` parametru.  
  
- `FallbackCulture`  
  
   Volitelný `String` parametr.  
  
   Určuje sekundární jazykovou verzi, která se má použít pro uživatelské rozhraní Bootstrap a požadavky na instalaci.  
  
- `OutputPath`  
  
   Volitelný `String` parametr.  
  
   Určuje umístění pro kopírování setup.exe a všechny soubory balíčku.  
  
- `Path`  
  
   Volitelný `String` parametr.  
  
   Určuje umístění všech dostupných balíčků požadovaných součástí.  
  
- `SupportUrl`  
  
   Volitelný `String` parametr.  
  
   Určuje adresu URL, která má být k dispozici, pokud instalace zaváděcího nástroje selže.  
  
- `Validate`  
  
   Volitelný `Boolean` parametr.  
  
   Pokud `true` nástroj provede ověření XSD na zadaných položkách zaváděcího nástroje pro vstup. Výchozí hodnota tohoto parametru je `false` .  
  
## <a name="remarks"></a>Poznámky  
 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `GenerateBootstrapper` úlohu k instalaci aplikace, která musí mít [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] nainstalovaný jako požadavek.  
  
```  
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
 [Provádění](../msbuild/msbuild-tasks.md)   
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
