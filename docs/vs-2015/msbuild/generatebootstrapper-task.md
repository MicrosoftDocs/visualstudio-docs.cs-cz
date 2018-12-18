---
title: GenerateBootstrapper – úloha | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: c5c96c91a48e854c1619aa112bae5e1d84737765
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49811905"
---
# <a name="generatebootstrapper-task"></a>GenerateBootstrapper – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Poskytuje automatizovaný způsob, jak zjistit, stáhnout a nainstalovat aplikace a její požadované součásti. Slouží jako jeden instalační program, který integruje dva různé instalační programy pro všechny součásti tvořící aplikaci.  
  
## <a name="task-parameters"></a>Parametry úlohy  
 Následující tabulka popisuje parametry `GenerateBootstrapper` úloh.  
  
- `ApplicationFile`  
  
   Volitelné `String` parametru.  
  
   Určuje soubor, který bude používat zaváděcí nástroj a spusťte tak instalaci aplikace poté, co jsou nainstalované veškeré požadované součásti. Způsobí chybu sestavení, pokud `BootstrapperItems` ani `ApplicationFile` je zadán parametr.  
  
- `ApplicationName`  
  
   Volitelné `String` parametru.  
  
   Určuje název aplikace, který bude instalovat zaváděcí nástroj. Tento název se zobrazí v uživatelském rozhraní používá zaváděcí nástroj během instalace.  
  
- `ApplicationRequiresElevation`  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, komponenty běží se zvýšenými oprávněními po instalaci na cílovém počítači.  
  
- `ApplicationUrl`  
  
   Volitelné `String` parametru.  
  
   Určuje umístění na webu, který je hostitelem aplikace Instalační služby.  
  
- `BootstrapperComponentFiles`  
  
   Volitelné `String[]` výstupní parametr.  
  
   Určuje umístění sestavené soubory balíčku zaváděcího nástroje.  
  
- `BootstrapperItems`  
  
   Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.  
  
   Určuje produkty, které chcete sestavit zaváděcí nástroj. Položky předaných tomuto parametru by měl mít následující syntaxi:  
  
  ```  
  <BootstrapperItem  
      Include="ProductCode">  
      <ProductName>  
          ProductName  
      </ProductName>  
  </BootstrapperItem>  
  ```  
  
   `Include` Atribut se používá k reprezentování název požadovaných součástí, která se má nainstalovat. `ProductName` Metadata položky je volitelné a použije stroj sestavení jako popisný název v případě, že balíček se nenašel. Tyto položky nejsou vyžadovány [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] vstupní parametry, pokud žádné `ApplicationFile` je zadán. Měli byste zahrnout jednu položku pro každý požadavek, který musí být nainstalovaný pro vaši aplikaci.  
  
   Způsobí chybu sestavení, pokud `BootstrapperItems` ani `ApplicationFile` je zadán parametr.  
  
- `BootstrapperKeyFile`  
  
   Volitelné `String` výstupní parametr.  
  
   Určuje umístění sestavené setup.exe  
  
- `ComponentsLocation`  
  
   Volitelné `String` parametru.  
  
   Určuje umístění pro zaváděcí nástroj hledání instalační požadavky k instalaci. Tento parametr může mít následující hodnoty:  
  
  - `HomeSite`: Označuje, že se kontrolu požadovaných součástí hostována dodavatelem součásti.  
  
  - `Relative`: Označuje, preqrequisite je ve stejném umístění aplikace.  
  
  - `Absolute`: Označuje, že všechny komponenty se nachází na centralizované adrese URL. Tato hodnota má být použita ve spojení s `ComponentsUrl` vstupního parametru.  
  
    Pokud `ComponentsLocation` není zadán, `HomeSite` se používá ve výchozím nastavení.  
  
- `ComponentsUrl`  
  
   Volitelné `String` parametru.  
  
   Určuje adresu URL obsahující instalační požadavky.  
  
- `CopyComponents`  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, zaváděcí nástroj zkopíruje všechny výstupní soubory na cestě zadané v `OutputPath` parametru. Hodnoty `BootstrapperComponentFiles` parametr by všechny měly vycházet tuto cestu. Pokud `false`, soubory nejsou zkopírovány a `BootstrapperComponentFiles` hodnoty jsou založené na hodnotě `Path` parametru.  Výchozí hodnota tohoto parametru je `true`.  
  
- `Culture`  
  
   Volitelné `String` parametru.  
  
   Určuje jazykovou verzi k použití pro zaváděcí nástroj uživatelského rozhraní a požadavky na instalaci. Pokud je zadaná jazyková verze není k dispozici, úkol používá hodnotu `FallbackCulture` parametru.  
  
- `FallbackCulture`  
  
   Volitelné `String` parametru.  
  
   Určuje sekundární jazykovou verzi k použití pro bootstraper uživatelského rozhraní a požadavky na instalaci.  
  
- `OutputPath`  
  
   Volitelné `String` parametru.  
  
   Určuje umístění pro kopírování setup.exe a všechny soubory balíčku.  
  
- `Path`  
  
   Volitelné `String` parametru.  
  
   Určuje umístění k dispozici všechny požadované balíčky.  
  
- `SupportUrl`  
  
   Volitelné `String` parametru.  
  
   Určuje adresu URL k poskytování by selhat instalace zaváděcího nástroje  
  
- `Validate`  
  
   Volitelné `Boolean` parametru.  
  
   Pokud `true`, zaváděcí nástroj provádí ověření XSD položky zadané vstupní zaváděcího nástroje. Výchozí hodnota tohoto parametru je `false`.  
  
## <a name="remarks"></a>Poznámky  
 Kromě výše uvedených parametrů zdědí tento úkol parametry ze <xref:Microsoft.Build.Tasks.TaskExtension> třída, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popisy najdete v tématu [taskextension – základní třída](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `GenerateBootstrapper` úloh k instalaci aplikace, která musí mít [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] nainstalována jako předpoklad.  
  
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
 [Úlohy](../msbuild/msbuild-tasks.md)   
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)



