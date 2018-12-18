---
title: Generateapplicationmanifest – úloha | Dokumentace Microsoftu
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
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateApplicationManifest
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateApplicationManifest task
- HostInBrowser property (MSBuild)
- GenerateApplicationManifest task [MSBuild]
ms.assetid: a494102b-0cb2-4755-8e2a-d2c0f39fac1d
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da5c9cb78ff4d3d9542c956a377f6342945d11a0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245567"
---
# <a name="generateapplicationmanifest-task"></a>GenerateApplicationManifest – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Generuje [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifest aplikace nebo nativní manifest. Nativní manifest popisuje komponentu definováním jedinečné identity pro komponentu a identifikaci všech sestavení a souborů, které tvoří součást. A [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifest aplikace rozšiřuje nativní manifest označením vstupního bodu aplikace a určením úrovně zabezpečení aplikace.  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry `GenerateApplicationManifest` úloh.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`AssemblyName`|Volitelné `String` parametru.<br /><br /> Určuje, `Name` pole identity sestavení pro generovaný manifest. Pokud tento parametr nezadáte, název je odvozen z `EntryPoint` nebo `InputManifest` parametry. Pokud nelze vytvořit žádný název, úkol vyvolá chybu.|  
|`AssemblyVersion`|Volitelné `String` parametru.<br /><br /> Určuje, `Version` pole identity sestavení pro generovaný manifest. Pokud není tento parametr zadán, je použita výchozí hodnota ikona "1.0.0.0".|  
|`ClrVersion`|Volitelné `String` parametru.<br /><br /> Určuje minimální verzi aplikace CLR Common Language Runtime () vyžadovaného aplikací. Výchozí hodnota je verze CLR používaná systémem sestavení. Pokud úloha generuje nativní manifest, tento parametr je ignorován.|  
|`ConfigFile`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Určuje, která položka obsahuje konfigurační soubor aplikace. Pokud úloha generuje nativní manifest, tento parametr je ignorován.|  
|`Dependencies`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Určuje seznam položek, který definuje sadu závislých sestavení pro generovaný manifest. Každá položka může být dále popsána metadaty položky pro označují další stav nasazení a typ závislosti. Další informace naleznete v části "Metadata položky" níže.|  
|`Description`|Volitelné `String` parametru.<br /><br /> Určuje popis aplikace nebo komponenty.|  
|`EntryPoint`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Určuje jednu položku, která označuje vstupní bod pro generované sestavení manifestu.<br /><br /> Pro [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestu aplikace tento parametr určuje sestavení, který se spustí při spuštění aplikace.|  
|`ErrorReportUrl`|Volitelné [String] (<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->) parametru.<br /><br /> Určuje adresu URL webové stránky, který se zobrazí v dialogových oknech během chybových sestav v instalacích ClickOnce.|  
|`FileAssociations`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Určuje seznam jednoho nebo více typů souboru, které jsou propojeny s manifestem nasazení ClickOnce.<br /><br /> Přidružení souborů platné, pouze v případě, že je cílem rozhraní .NET Framework 3.5 nebo novější.|  
|`Files`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Soubory k zahrnutí do manifestu. Zadejte úplnou cestu pro každý soubor.|  
|`HostInBrowser`|Volitelná [logická hodnota] (<!-- TODO: review code entity reference <xref:assetId:///Boolean?qualifyHint=False&amp;autoUpgrade=True>  -->) parametru.<br /><br /> Pokud `true`, je aplikace hostovaná v prohlížeči (jako jsou aplikace WPF webového prohlížeče).|  
|`IconFile`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Určuje soubor ikony aplikace. Ikona aplikace je vyjádřena v manifestu generované aplikace a používá se pro dialogové okno nabídky Start a přidat nebo odebrat programy. Pokud tento vstup není zadán, je použita výchozí ikona. Pokud úloha generuje nativní manifest, tento parametr je ignorován.|  
|`InputManifest`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Označuje vstupní dokument XML, který bude sloužit jako základ pro generátor manifestu. To umožňuje strukturovaným datům, například zabezpečení aplikace nebo definicím vlastního manifestu, se projevovat ve výstupním manifestu. Kořenový element v dokumentu XML musí být uzel sestavení v oboru názvů asmv1.|  
|`IsolatedComReferences`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Určuje model COM izolovat v generovaném manifestu. Tento parametr podporuje schopnost izolovat komponenty modelu COM pro nasazení "Model COM bez registrace". Funguje díky automaticky vygeneruje manifest se standardními definicemi registrace COM. Nicméně komponenty modelu COM musí být zaregistrovaný v počítači sestavení, aby toto fungovalo správně.|  
|`ManifestType`|Volitelné `String` parametru.<br /><br /> Určuje, který typ manifestu se má vygenerovat. Tento parametr může mít následující hodnoty:<br /><br /> -   `Native`<br />-   `ClickOnce`<br /><br /> Je-li tento parametr není zadán, výchozí úlohy `ClickOnce`.|  
|`MaxTargetPath`|Volitelné `String` parametru.<br /><br /> Určuje maximální povolenou délku cesty souboru v [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení aplikace. Pokud je tato hodnota zadána, délka každé cesty souboru v aplikaci je porovnávána s toto omezení. Všechny položky, které překračují limit, vyvolají upozornění sestavení. Pokud tento vstup není zadán nebo je nula, pak žádná kontrola se neprovádí. Pokud úloha generuje nativní manifest, tento parametr je ignorován.|  
|`OSVersion`|Volitelné `String` parametru.<br /><br /> Určuje verzi minimální požadovaný operační systém (OS) vyžadovaného aplikací. Například hodnota "5.1.2600.0" znamená, že operační systém je Windows XP. Pokud není tento parametr zadán, je použita hodnota "4.10.0.0", což znamená Windows 98 Druhé vydání, minimální podporovaný OS rozhraní .NET Framework. Pokud úloha generuje nativní manifest, tento vstup je ignorován.|  
|`OutputManifest`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> výstupní parametr.<br /><br /> Určuje název generovaného výstupního souboru manifestu. Pokud tento parametr nezadáte, název výstupního souboru je odvozen z identity generovaného manifestu.|  
|`Platform`|Volitelné `String` parametru.<br /><br /> Určuje cílovou platformu aplikace. Tento parametr může mít následující hodnoty:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> Je-li tento parametr není zadán, výchozí úlohy `AnyCPU`.|  
|`Product`|Volitelné `String` parametru.<br /><br /> Určuje název aplikace. Pokud tento parametr nezadáte, název je odvozen z identity generovaného manifestu. Tento název se používá pro název zástupce v nabídce Start a je součástí názvu, který se zobrazí v dialogovém okně Přidat nebo odebrat programy.|  
|`Publisher`|Volitelné `String` parametru.<br /><br /> Určuje název vydavatele aplikace. Pokud tento parametr nezadáte, název je odvozen z registrovaného uživatele, nebo z identity generovaného manifestu. Tento název se používá pro název složky v nabídce Start a je součástí názvu, který se zobrazí v dialogovém okně Přidat nebo odebrat programy.|  
|`RequiresMinimumFramework35SP1`|Volitelné `Boolean` parametru.<br /><br /> Pokud je hodnota true, aplikace požaduje instalaci rozhraní .NET Framework 3.5 SP1 nebo novější verze.|  
|`TargetCulture`|Volitelné `String` parametru.<br /><br /> Určuje jazykovou verzi aplikace a určuje, `Language` pole identity sestavení pro generovaný manifest. Pokud není tento parametr zadán, předpokládá se, že aplikace je invariantní jazyková verze.|  
|`TargetFrameworkMoniker`|Volitelné <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> parametru.<br /><br /> Určuje moniker cílového rozhraní.|  
|`TargetFrameworkProfile`|Volitelné <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> parametru.<br /><br /> Určuje profil cílového rozhraní framework.|  
|`TargetFrameworkSubset`|Volitelné <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> parametru.<br /><br /> Určuje název podsady rozhraní .NET Framework na cíl.|  
|`TargetFrameworkVersion`|Volitelné <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> parametru.<br /><br /> Určuje cílovou platformu .NET Framework projektu.|  
|`TrustInfoFile`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Označuje dokument XML, který určuje zabezpečení aplikace. Kořenový element v dokumentu XML musí být uzel trustInfo v oboru názvů asmv2. Pokud úloha generuje nativní manifest, tento parametr je ignorován.|  
|`UseApplicationTrust`|Volitelné <!-- TODO: review code entity reference <xref:assetId:///Boolean?qualifyHint=False&amp;autoUpgrade=True>  --> parametru.<br /><br /> Hodnota TRUE znamená, `Product`, `Publisher`, a `SupportUrl` vlastnosti jsou zapisovány do manifestu aplikace.|  
  
## <a name="remarks"></a>Poznámky  
 Kromě výše uvedených parametrů zdědí tento úkol parametry ze <xref:Microsoft.Build.Tasks.GenerateManifestBase> třída, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam parametrů třídy úkoly naleznete v tématu [Třída Base úlohy](../msbuild/task-base-class.md).  
  
 Informace o tom, jak používat `GenerateDeploymentManifest` úloh naleznete v tématu [generateapplicationmanifest – úloha](../msbuild/generateapplicationmanifest-task.md).  
  
 Vstupy pro závislosti a soubory mohou dále obohaceny metadaty položky pro určení dalšího stavu nasazení pro každou položku.  
  
## <a name="item-metadata"></a>Metadata položky  
  
|Název metadat|Popis|  
|-------------------|-----------------|  
|`DependencyType`|Určuje, zda závislost je publikována a nainstalovaná pomocí aplikace nebo jako předpoklad. Tato metadata je platná pro všechny závislosti, ale nejsou použita pro soubory. Dostupné hodnoty pro tato metadata jsou:<br /><br /> -   `Install`<br />-   `Prerequisite`<br /><br /> Výchozí hodnota je Install.|  
|`AssemblyType`|Určuje, zda je závislost spravované nebo nativní sestavení. Tato metadata je platná pro všechny závislosti, ale nejsou použita pro soubory. Dostupné hodnoty pro tato metadata jsou:<br /><br /> -   `Managed`<br />-   `Native`<br />-   `Unspecified`<br /><br /> `Unspecified` je výchozí hodnota, která označuje, že generátor manifestu automaticky určí typ sestavení.|  
|`Group`|Označuje skupinu pro stahování dalších souborů na vyžádání. Název skupiny je definován aplikací a může být libovolný řetězec. Prázdný řetězec znamená, že soubor není součástí skupiny stažení, což je výchozí hodnota. Souborů mimo skupiny jsou součástí původní žádosti o stažení. Soubory ve skupině jsou staženy pouze při explicitním požadavku aplikace pomocí <xref:System.Deployment.Application>.<br /><br /> Tato metadata jsou platná pro všechny soubory kde `IsDataFile` je `false` a všechny závislosti kde `DependencyType` je `Install`.|  
|`TargetPath`|Určuje, jak cesta musí být definován v vygenerovaný manifest. Tento atribut je platný pro všechny soubory. Pokud tento atribut není zadán, použije se specifikace položky. Tento atribut je platný pro všechny soubory a závislosti s `DependencyType` hodnotu `Install`.|  
|`IsDataFile`|A `Boolean` hodnota metadat, která určuje, zda je soubor datového souboru. Datový soubor je zvláštní v tom, že je migrován mezi aktualizacemi aplikace. Tato metadata jsou platná pouze pro soubory. `False` je výchozí hodnota.|  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `GenerateApplicationManifest` úkolů ke generování [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifest aplikace a `GenerateDeploymentManifest` úkolů ke generování manifestu nasazení pro aplikaci s jedním sestavením. Poté použije `SignFile` úloh k podepsání manifestů.  
  
 To ukazuje nejjednodušší možný scénář generování manifestu kde [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestů jsou generovány pro jeden program. Výchozí název a identita jsou odvozeny z manifestu sestavení.  
  
> [!NOTE]
>  V následujícím příkladu jsou všechny binární soubory aplikace předem připravené, abychom se mohli zaměřit na aspekty generování manifestu. Tento příklad vytvoří plně funkční [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení.  
  
> [!NOTE]
>  Další informace o `Thumbprint` vlastnosti používané `SignFile` úlohy v tomto příkladu najdete v tématu [signfile – úloha](../msbuild/signfile-task.md).  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
    </PropertyGroup>  
  
    <Target Name="Build">  
  
        <GenerateApplicationManifest  
            EntryPoint="@(EntryPoint)">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
        <GenerateDeploymentManifest  
            EntryPoint="@(ApplicationManifest)">  
            <Output  
                ItemName="DeployManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  
  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `GenerateApplicationManifest` a `GenerateDeploymentManifest` úkoly ke generování [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace a manifestů nasazení pro aplikaci s jedním sestavením, přičemž název a identitu manifestů.  
  
 Tento příklad je podobný jako předchozí příklad s výjimkou název a identita manifestů jsou explicitně zadány. Navíc tento příklad je nakonfigurován jako online aplikace namísto aplikace nainstalované.  
  
> [!NOTE]
>  V následujícím příkladu jsou všechny binární soubory aplikace předem připravené, abychom se mohli zaměřit na aspekty generování manifestu. Tento příklad vytvoří plně funkční [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení.  
  
> [!NOTE]
>  Další informace o `Thumbprint` vlastnosti používané `SignFile` úlohy v tomto příkladu najdete v tématu [signfile – úloha](../msbuild/signfile-task.md).  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
    </PropertyGroup>  
  
    <Target Name="Build">  
  
        <GenerateApplicationManifest  
            AssemblyName="SimpleWinApp.exe"  
            AssemblyVersion="1.0.0.0"  
            EntryPoint="@(EntryPoint)"  
            OutputManifest="SimpleWinApp.exe.manifest">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
        <GenerateDeploymentManifest  
                AssemblyName="SimpleWinApp.application"  
                AssemblyVersion="1.0.0.0"  
                EntryPoint="@(ApplicationManifest)"  
                Install="false"  
                OutputManifest="SimpleWinApp.application">  
                <Output  
                    ItemName="DeployManifest"  
                    TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  
  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `GenerateApplicationManifest` a `GenerateDeploymentManifest` úkoly ke generování [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace a manifestů nasazení pro aplikaci s více soubory a sestaveními.  
  
> [!NOTE]
>  V následujícím příkladu jsou všechny binární soubory aplikace předem připravené, abychom se mohli zaměřit na aspekty generování manifestu. Tento příklad vytvoří plně funkční [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení.  
  
> [!NOTE]
>  Další informace o `Thumbprint` vlastnosti používané `SignFile` úlohy v tomto příkladu najdete v tématu [signfile – úloha](../msbuild/signfile-task.md).  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
        <DeployUrl>  
            <!-- Insert the deployment URL here -->  
        </DeployUrl>  
        <SupportUrl>  
            <!-- Insert the support URL here -->  
        </SupportUrl>  
    </PropertyGroup>  
  
    <Target Name="Build">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe"/>  
        <Dependency Include="ClassLibrary1.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
        </Dependency>  
        <Dependency Include="ClassLibrary2.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
            <Group>Secondary</Group>  
        </Dependency>  
        <Dependency Include="MyAddIn1.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
            <TargetPath>Addins\MyAddIn1.dll</TargetPath>  
        </Dependency>  
        <Dependency Include="ClassLibrary3.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Prerequisite</DependencyType>  
        </Dependency>  
  
        <File Include="Text1.txt">  
            <TargetPath>Text\Text1.txt</TargetPath>  
            <Group>Text</Group>  
        </File>  
        <File Include="DataFile1.xml ">  
            <TargetPath>Data\DataFile1.xml</TargetPath>  
            <IsDataFile>true</IsDataFile>  
        </File>  
  
        <IconFile Include="Heart.ico"/>  
        <ConfigFile Include="app.config">  
            <TargetPath>SimpleWinApp.exe.config</TargetPath>  
        </ConfigFile>  
        <BaseManifest Include="app.manifest"/>  
    </ItemGroup>  
  
    <Target Name="Build">  
  
        <GenerateApplicationManifest  
            AssemblyName="SimpleWinApp.exe"  
            AssemblyVersion="1.0.0.0"  
            ConfigFile="@(ConfigFile)"  
            Dependencies="@(Dependency)"  
            Description="TestApp"  
            EntryPoint="@(EntryPoint)"  
            Files="@(File)"  
            IconFile="@(IconFile)"  
            InputManifest="@(BaseManifest)"  
            OutputManifest="SimpleWinApp.exe.manifest">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
        <GenerateDeploymentManifest  
            AssemblyName="SimpleWinApp.application"  
            AssemblyVersion="1.0.0.0"  
            DeploymentUrl="$(DeployToUrl)"  
            Description="TestDeploy"  
            EntryPoint="@(ApplicationManifest)"  
            Install="true"  
            OutputManifest="SimpleWinApp.application"  
            Product="SimpleWinApp"  
            Publisher="Microsoft"  
            SupportUrl="$(SupportUrl)"  
            UpdateEnabled="true"  
            UpdateInterval="3"  
            UpdateMode="Background"  
            UpdateUnit="weeks">  
            <Output  
                ItemName="DeployManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  
  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `GenerateApplicationManifest` úkolů ke generování nativního manifestu pro aplikaci Test.exe, odkazující na nativní součást Alpha.dll a součást izolovaného modelu COM Bravo.dll.  
  
 Tento příklad vytvoří Test.exe.manifest, což využívat aplikace XCOPY nasaditelnou díky modelu Registration Free COM.  
  
> [!NOTE]
>  V následujícím příkladu jsou všechny binární soubory aplikace předem připravené, abychom se mohli zaměřit na aspekty generování manifestu. Tento příklad vytvoří plně funkční [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení.  
  
```  
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <File Include="Test.exe" />  
        <Dependency Include="Alpha.dll">  
            <AssemblyType>Native</AssemblyType>  
            <DependencyType>Install</DependencyType>  
        </Dependency>  
        <ComComponent Include="Bravo.dll" />  
    </ItemGroup>  
  
    <Target Name="Build">  
        <GenerateApplicationManifest  
            AssemblyName="Test.exe"  
            AssemblyVersion="1.0.0.0"  
            Dependencies="@(Dependency)"  
            Files="@(File)"  
            IsolatedComReferences="@(ComComponent)"  
            ManifestType="Native">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Viz také  
 [Úlohy](../msbuild/msbuild-tasks.md)   
 [Generatedeploymentmanifest – úloha](../msbuild/generatedeploymentmanifest-task.md)   
 [Signfile – úloha](../msbuild/signfile-task.md)   
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)



