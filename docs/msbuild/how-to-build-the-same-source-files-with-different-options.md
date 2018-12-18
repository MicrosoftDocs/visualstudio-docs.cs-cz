---
title: 'Postupy: sestavení stejných zdrojových souborů s různými možnostmi | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- source files, building with different options
- MSBuild, properties
- project properties, modifying
- Hello World example [Visual Studio]
ms.assetid: d14f1212-ddd9-434f-b138-f840011b0fb2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e80252582f93c995330f9c586a56e2f8f2c4e6a3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49897170"
---
# <a name="how-to-build-the-same-source-files-with-different-options"></a>Postupy: sestavení stejných zdrojových souborů s různými možnostmi
Při sestavování projektů často kompilaci stejné komponenty s možnostmi jiné sestavení. Můžete například vytvořit sestavení pro ladění pomocí informací o symbolu nebo sestavení pro vydání se žádné informace o symbolech, ale s povolenými optimalizacemi. Nebo můžete vytvořit projektu pro spuštění na konkrétní platformě, jako je například x86 nebo [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)]. V těchto případech se většina možností sestavení zůstat stejná; řízení konfigurace sestavení se změní jenom pár možností. S [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], použijete k vytvoření konfigurace sestavení různé vlastnosti a podmínky.  
  
## <a name="use-properties-to-modify-projects"></a>Použijte vlastnosti upravit projekty  
 `Property` Element definuje proměnnou, která je popsána v souboru projektu, jako je například umístění dočasného adresáře, nebo k nastavení hodnot pro vlastnosti, které se používají v sestavení několika konfigurací, jako je například sestavení pro ladění a vydání. Další informace o vlastnostech najdete v tématu [vlastnosti nástroje MSBuild](../msbuild/msbuild-properties.md).  
  
 Vlastnosti můžete změnit konfiguraci sestavení bez nutnosti změny souboru projektu. `Condition` Atribut `Property` elementu a `PropertyGroup` element slouží ke změně hodnoty vlastnosti. Další informace o [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] podmínky, naleznete v tématu [podmínky](../msbuild/msbuild-conditions.md).  
  
#### <a name="to-set-a-group-of-properties-based-on-another-property"></a>Chcete-li nastavit skupinu vlastností na základě jiné vlastnosti  
  
-   Použití `Condition` atribut `PropertyGroup` element podobný následujícímu:  
  
    ```xml  
    <PropertyGroup Condition="'$(Flavor)'=='DEBUG'">  
        <DebugType>full</DebugType>  
        <Optimize>no</Optimize>  
    </PropertyGroup>  
    ```  
  
#### <a name="to-define-a-property-based-on-another-property"></a>Chcete-li definovat vlastnost podle jiné vlastnosti  
  
-   Použití `Condition` atribut `Property` element podobný následujícímu:  
  
    ```xml  
    <DebugType Condition="'$(Flavor)'=='DEBUG'">full</DebugType>  
    ```  
  
## <a name="specify-properties-on-the-command-line"></a>Zadat vlastnosti na příkazovém řádku  
 Jakmile váš soubor projektu je napsané tak, aby přijímal více konfigurací, musíte mít možnost změnit tyto konfigurace pokaždé, když se sestavení projektu. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Tato možnost nabízí a umožňuje zadat na příkazovém řádku pomocí vlastnosti **– vlastnost** nebo **-p** přepnout.  
  
#### <a name="to-set-a-project-property-at-the-command-line"></a>Nastavení vlastnosti projektu na příkazovém řádku  
  
-   Použití **– vlastnost** přepnout s vlastností a hodnota vlastnosti. Příklad:  
  
    ```cmd  
    msbuild file.proj -property:Flavor=Debug  
    ```  
  
    or  
  
    ```cmd  
    Msbuild file.proj -p:Flavor=Debug  
    ```  
  
#### <a name="to-specify-more-than-one-project-property-at-the-command-line"></a>Chcete-li zadat více než jednu vlastnost projektu na příkazovém řádku  
  
- Použít **– vlastnost** nebo **-p** přepínač vícekrát s vlastností a hodnot vlastností, nebo použijte jednu **– vlastnost** nebo **-p** přepnutí a víc vlastností oddělujte středníkem (;). Příklad:  
  
  ```cmd  
  msbuild file.proj -p:Flavor=Debug;Platform=x86  
  ```  
  
  or
  
  ```cmd  
  msbuild file.proj -p:Flavor=Debug -p:Platform=x86  
  ```  
  
  Proměnné prostředí jsou také považovány za vlastnosti a jsou automaticky součástí [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Další informace o použití proměnných prostředí najdete v tématu [postupy: použití proměnných prostředí v sestavení](../msbuild/how-to-use-environment-variables-in-a-build.md).  
  
  Hodnota vlastnosti, který je zadán v příkazovém řádku má přednost před jakoukoli hodnotu, která je nastavena pro stejnou vlastnost v souboru projektu, a hodnota v souboru projektu má přednost před hodnota v proměnné prostředí.  
  
  Toto chování můžete změnit pomocí `TreatAsLocalProperty` atribut ve značce projektu. Pro názvy vlastností, které jsou uvedeny se tento atribut hodnota vlastnosti, který je zadán v příkazovém řádku nemá přednost před hodnota v souboru projektu. Příklad najdete dále v tomto tématu.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu projektu "Hello World" obsahuje dvě nové vlastnosti skupiny, které slouží k vytvoření sestavení pro ladění a sestavení pro vydání.  
  
 Chcete-li sestavení verze ladění tohoto projektu, zadejte:  
  
```cmd  
msbuild consolehwcs1.proj -p:flavor=debug  
```  
  
 Chcete-li sestavení prodejní verze tohoto projektu, zadejte:  
  
```cmd  
msbuild consolehwcs1.proj -p:flavor=retail  
```  
  
```xml  
<Project DefaultTargets = "Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <!-- Sets the default flavor of an environment variable called   
    Flavor is not set or specified on the command line -->  
    <PropertyGroup>  
        <Flavor Condition="'$(Flavor)'==''">DEBUG</Flavor>  
    </PropertyGroup>  
  
    <!-- Define the DEBUG settings -->  
    <PropertyGroup Condition="'$(Flavor)'=='DEBUG'">  
        <DebugType>full</DebugType>  
        <Optimize>no</Optimize>  
    </PropertyGroup>  
  
    <!-- Define the RETAIL settings -->  
    <PropertyGroup Condition="'$(Flavor)'=='RETAIL'">  
        <DebugType>pdbonly</DebugType>  
        <Optimize>yes</Optimize>  
    </PropertyGroup>  
  
    <!-- Set the application name as a property -->  
    <PropertyGroup>  
        <appname>HelloWorldCS</appname>  
    </PropertyGroup>  
  
    <!-- Specify the inputs by type and file name -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using input files  
        of type CSFile -->  
        <CSC  Sources = "@(CSFile)"  
            DebugType="$(DebugType)"  
            Optimize="$(Optimize)"  
            OutputAssembly="$(appname).exe" >  
  
            <!-- Set the OutputAssembly attribute of the CSC  
            task to the name of the executable file that is   
            created -->  
            <Output TaskParameter="OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití `TreatAsLocalProperty` atribut. `Color` Vlastnost má hodnotu `Blue` v souboru projektu a `Green` na příkazovém řádku. S `TreatAsLocalProperty="Color"` ve značce projektu vlastnost příkazového řádku (`Green`) nepřepíše vlastnost, která je definována v souboru projektu (`Blue`).  
  
 K sestavení projektu, zadejte následující příkaz:  
  
```cmd  
msbuild colortest.proj -t:go -property:Color=Green  
```  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"  
ToolsVersion="4.0" TreatAsLocalProperty="Color">  
  
    <PropertyGroup>  
        <Color>Blue</Color>  
    </PropertyGroup>  
  
    <Target Name="go">  
        <Message Text="Color: $(Color)" />  
    </Target>  
</Project>  
  
<!--  
  Output with TreatAsLocalProperty="Color" in project tag:  
     Color: Blue  
  
  Output without TreatAsLocalProperty="Color" in project tag:  
     Color: Green  
-->  
```  
  
## <a name="see-also"></a>Viz také:  
[MSBuild](../msbuild/msbuild.md)  
 [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)   
 [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)   
 [Project – element (MSBuild)](../msbuild/project-element-msbuild.md)