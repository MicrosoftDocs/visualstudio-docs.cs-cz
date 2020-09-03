---
title: Úloha GenerateApplicationManifest – | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f77420c5ab269e1b0052ce6102c4e3196a3be52b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77634094"
---
# <a name="generateapplicationmanifest-task"></a>GenerateApplicationManifest – úloha

Generuje manifest aplikace ClickOnce nebo nativní manifest. Nativní manifest popisuje komponentu tak, že definuje jedinečnou identitu pro komponentu a identifikuje všechna sestavení a soubory, které tvoří komponentu. Manifest aplikace ClickOnce rozšiřuje nativní manifest tím, že označuje vstupní bod aplikace a určuje úroveň zabezpečení aplikace.

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry pro `GenerateApplicationManifest` úlohu.

| Parametr | Popis |
|---------------------------------| - |
| `AssemblyName` | Volitelný `String` parametr.<br /><br /> Určuje `Name` pole identity sestavení pro generovaný manifest. Pokud tento parametr není zadán, název je odvozen z `EntryPoint` `InputManifest` parametrů nebo. Pokud nelze vytvořit žádný název, úloha vyvolá chybu. |
| `AssemblyVersion` | Volitelný `String` parametr.<br /><br /> Určuje `Version` pole identity sestavení pro generovaný manifest. Pokud tento parametr není zadán, je použita výchozí hodnota "1.0.0.0". |
| `ClrVersion` | Volitelný `String` parametr.<br /><br /> Určuje minimální verzi modulu CLR (Common Language Runtime), kterou aplikace požaduje. Výchozí hodnota je verze CLR, kterou používá systém sestavení. Pokud úloha generuje nativní manifest, tento parametr je ignorován. |
| `ConfigFile` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje, která položka obsahuje konfigurační soubor aplikace. Pokud úloha generuje nativní manifest, tento parametr je ignorován. |
| `Dependencies` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje seznam položek, který definuje sadu závislých sestavení pro generovaný manifest. Každá položka může být dále popsána metadaty položky k označení dalšího stavu nasazení a typu závislosti. Další informace najdete v tématu [Metadata položek](#item-metadata). |
| `Description` | Volitelný `String` parametr.<br /><br /> Určuje popis aplikace nebo komponenty. |
| `EntryPoint` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje jednu položku, která označuje vstupní bod pro vygenerované sestavení manifestu.<br /><br /> Pro manifest aplikace ClickOnce tento parametr určuje sestavení, které se spustí při spuštění aplikace. |
| `ErrorReportUrl` | Volitelný <xref:System.String?displayProperty=fullName> parametr.<br /><br /> Určuje adresu URL webové stránky, která se zobrazí v dialogových oknech během hlášení chyb v instalacích ClickOnce. |
| `FileAssociations` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje seznam jednoho nebo více typů souborů, které jsou přidruženy k manifestu nasazení ClickOnce.<br /><br /> Přidružení souborů jsou platná pouze v případě, že je cílem .NET Framework 3,5 nebo novější. |
| `Files` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Soubory, které mají být zahrnuty do manifestu. Zadejte úplnou cestu pro každý soubor. |
| `HostInBrowser` | Volitelný <xref:System.Boolean> parametr.<br /><br /> Pokud `true` je aplikace hostována v prohlížeči (stejně jako aplikace WPF pro webový prohlížeč). |
| `IconFile` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje soubor ikony aplikace. Ikona aplikace je vyjádřena v manifestu generované aplikace a používá se v **nabídce Start** a v dialogovém okně **Přidat nebo odebrat programy** . Pokud tento vstup není zadán, je použita výchozí ikona. Pokud úloha generuje nativní manifest, tento parametr je ignorován. |
| `InputManifest` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Označuje vstupní dokument XML, který bude sloužit jako základ pro generátor manifestu. To umožňuje, aby se strukturovaná data, jako je například zabezpečení aplikace nebo definice vlastního manifestu, projevila ve výstupním manifestu. Kořenový element v dokumentu XML musí být uzlem sestavení v oboru názvů asmv1. |
| `IsolatedComReferences` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje komponenty modelu COM, které mají být izolovány ve vygenerovaném manifestu. Tento parametr podporuje možnost izolovat komponenty modelu COM pro nasazení "bezplatné COM" s registrací. Funguje tak, že automaticky generuje manifest se standardními definicemi registrace modelu COM. Nicméně komponenty modelu COM musí být registrovány v počítači sestavení, aby tato funkce fungovala správně. |
| `ManifestType` | Volitelný `String` parametr.<br /><br /> Určuje typ manifestu, který se má vygenerovat. Tento parametr může mít následující hodnoty:<br /><br /> -   `Native`<br />-   `ClickOnce`<br /><br /> Pokud tento parametr není zadán, je výchozí hodnota úlohy `ClickOnce` . |
| `MaxTargetPath` | Volitelný `String` parametr.<br /><br /> Určuje maximální povolenou délku cesty k souboru v nasazení aplikace ClickOnce. Pokud je tato hodnota zadaná, u této meze se kontroluje délka každé cesty souboru v aplikaci. Všechny položky, které překračují limit, se vyvolají v upozornění sestavení. Pokud tento vstup není zadán nebo je nula, žádná kontrola se neprovede. Pokud úloha generuje nativní manifest, tento parametr je ignorován. |
| `OSVersion` | Volitelný `String` parametr.<br /><br /> Určuje minimální požadovanou verzi operačního systému (OS), kterou aplikace vyžaduje. Například hodnota "5.1.2600.0" označuje operační systém Windows XP. Pokud tento parametr není zadán, je použita hodnota "4.10.0.0", která označuje systém Windows 98 Second Edition, minimální podporovaný operační systém .NET Framework. Pokud úloha generuje nativní manifest, tento vstup se ignoruje. |
| `OutputManifest` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> výstupní parametr.<br /><br /> Určuje název vygenerovaného výstupního souboru manifestu. Pokud tento parametr není zadán, název výstupního souboru je odvozen z identity generovaného manifestu. |
| `Platform` | Volitelný `String` parametr.<br /><br /> Určuje cílovou platformu aplikace. Tento parametr může mít následující hodnoty:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> Pokud tento parametr není zadán, je výchozí hodnota úlohy `AnyCPU` . |
| `Product` | Volitelný `String` parametr.<br /><br /> Určuje název aplikace. Pokud tento parametr není zadán, název je odvozen z identity generovaného manifestu. Tento název se používá pro název zástupce v nabídce **Start** a je součástí názvu, který se zobrazí v dialogovém okně **Přidat nebo odebrat programy** . |
| `Publisher` | Volitelný `String` parametr.<br /><br /> Určuje vydavatele aplikace. Pokud tento parametr není zadán, je název odvozen od registrovaného uživatele nebo z identity generovaného manifestu. Tento název se používá pro název složky v nabídce **Start** a je součástí názvu, který se zobrazí v dialogovém okně **Přidat nebo odebrat programy** . |
| `RequiresMinimumFramework35SP1` | Volitelný `Boolean` parametr.<br /><br /> V případě hodnoty true vyžaduje aplikace .NET Framework 3,5 SP1 nebo novější verzi. |
| `TargetCulture` | Volitelný `String` parametr.<br /><br /> Určuje jazykovou verzi aplikace a určuje `Language` pole identity sestavení pro generovaný manifest. Pokud není tento parametr zadán, předpokládá se, že aplikace je invariantní jazykové verze. |
| `TargetFrameworkMoniker` | Volitelný `String` parametr.<br /><br /> Určuje moniker cílového rozhraní .NET Framework. |
| `TargetFrameworkProfile` | Volitelný `String` parametr.<br /><br /> Určuje profil cílového rozhraní .NET Framework. |
| `TargetFrameworkSubset` | Volitelný `String` parametr.<br /><br /> Určuje název podmnožiny .NET Framework, na kterou se má cílit. |
| `TargetFrameworkVersion` | Volitelný `String` parametr.<br /><br /> Určuje cílovou .NET Framework projektu. |
| `TrustInfoFile` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Označuje dokument XML, který určuje zabezpečení aplikace. Kořenový element v dokumentu XML musí být uzel trustInfo v oboru názvů asmv2. Pokud úloha generuje nativní manifest, tento parametr je ignorován. |
| `UseApplicationTrust` | Volitelný `Boolean` parametr.<br /><br /> Pokud je hodnota true `Product` , `Publisher` vlastnosti, a `SupportUrl` jsou zapsány do manifestu aplikace. |

## <a name="remarks"></a>Poznámky

Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.GenerateManifestBase> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam parametrů třídy Task naleznete v tématu [základní třída Task](../msbuild/task-base-class.md).

Informace o tom, jak používat `GenerateDeploymentManifest` úlohu, najdete v tématu [GenerateApplicationManifest – Task](../msbuild/generateapplicationmanifest-task.md).

Vstupy pro závislosti a soubory mohou být dále upraveny pomocí metadat položek k určení dalšího stavu nasazení pro každou položku.

## <a name="item-metadata"></a>Metadata položky

|Název metadat|Popis|
|-------------------|-----------------|
|`DependencyType`|Určuje, zda je závislost publikována a instalována s aplikací nebo součástí. Tato metadata jsou platná pro všechny závislosti, ale nepoužívají se pro soubory. Dostupné hodnoty pro tato metadata jsou:<br /><br /> -   `Install`<br />-   `Prerequisite`<br /><br /> Instalace je výchozí hodnota.|
|`AssemblyType`|Označuje, zda je závislost spravovaná, nebo nativním sestavením. Tato metadata jsou platná pro všechny závislosti, ale nepoužívají se pro soubory. Dostupné hodnoty pro tato metadata jsou:<br /><br /> -   `Managed`<br />-   `Native`<br />-   `Unspecified`<br /><br /> `Unspecified` je výchozí hodnota, která označuje, že generátor manifestu určí typ sestavení automaticky.|
|`Group`|Označuje skupinu pro stahování dalších souborů na vyžádání. Název skupiny je definovaný aplikací a může to být libovolný řetězec. Prázdný řetězec označuje, že soubor není součástí skupiny stahování, což je výchozí nastavení. Soubory, které nejsou ve skupině, jsou součástí prvotního stažení aplikace. Soubory ve skupině se stáhnou pouze v případě, že aplikace je explicitně požaduje <xref:System.Deployment.Application> .<br /><br /> Tato metadata jsou platná pro všechny soubory, kde `IsDataFile` je `false` a všechny závislosti, kde `DependencyType` je `Install` .|
|`TargetPath`|Určuje, jak má být cesta definována ve vygenerovaném manifestu. Tento atribut je platný pro všechny soubory. Pokud tento atribut není zadán, je použita specifikace položky. Tento atribut je platný pro všechny soubory a závislosti s `DependencyType` hodnotou `Install` .|
|`IsDataFile`|`Boolean`Hodnota metadat, která označuje, zda je soubor datovým souborem. Datový soubor je speciální v tom, že je migrován mezi aktualizacemi aplikace. Tato metadata jsou platná pouze pro soubory. `False` je výchozí hodnota.|

## <a name="example"></a>Příklad

Tento příklad používá `GenerateApplicationManifest` úlohu k vygenerování manifestu aplikace ClickOnce a `GenerateDeploymentManifest` úlohu pro generování manifestu nasazení pro aplikaci s jedním sestavením. Potom používá `SignFile` úlohu k podepsání manifestů.

To ukazuje nejjednodušší možný scénář generování manifestu, kde jsou pro jeden program generovány manifesty ClickOnce. Výchozí název a identita jsou odvozeny ze sestavení pro manifest.

> [!NOTE]
> V následujícím příkladu jsou všechny binární soubory aplikace předem připravené, aby se daly zaměřit na aspekty vytváření manifestu. Tento příklad vytvoří plně funkční nasazení ClickOnce.
>
> [!NOTE]
> Další informace o `Thumbprint` vlastnosti použité v `SignFile` úloze v tomto příkladu naleznete v tématu [SignFile – Task](../msbuild/signfile-task.md).

```xml
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

Tento příklad používá `GenerateApplicationManifest` úlohy a `GenerateDeploymentManifest` k vygenerování manifestů aplikace ClickOnce a nasazení pro aplikaci s jedním sestavením a určením názvu a identity manifestů.

Tento příklad je podobný předchozímu příkladu s tím rozdílem, že název a identita manifestů jsou explicitně určeny. Tento příklad je také nakonfigurován jako online aplikace namísto nainstalované aplikace.

> [!NOTE]
> V následujícím příkladu jsou všechny binární soubory aplikace předem připravené, aby se daly zaměřit na aspekty vytváření manifestu. Tento příklad vytvoří plně funkční nasazení ClickOnce.
>
> [!NOTE]
> Další informace o `Thumbprint` vlastnosti použité v `SignFile` úloze v tomto příkladu naleznete v tématu [SignFile – Task](../msbuild/signfile-task.md).

```xml
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

Tento příklad používá `GenerateApplicationManifest` úkoly a `GenerateDeploymentManifest` k vygenerování manifestů aplikace ClickOnce a nasazení pro aplikaci s více soubory a sestaveními.

> [!NOTE]
> V následujícím příkladu jsou všechny binární soubory aplikace předem připravené, aby se daly zaměřit na aspekty vytváření manifestu. Tento příklad vytvoří plně funkční nasazení ClickOnce.
>
> [!NOTE]
> Další informace o `Thumbprint` vlastnosti použité v `SignFile` úloze v tomto příkladu naleznete v tématu [SignFile – Task](../msbuild/signfile-task.md).

```xml
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

Tento příklad používá `GenerateApplicationManifest` úlohu k vygenerování nativního manifestu pro aplikaci *Test.exe*, odkazování na nativní komponentu *Alpha.dll* a izolované součásti modelu COM *Bravo.dll*.

V tomto příkladu se vytvoří *Test.exe. manifest*, což provede nasazení xcopy pro aplikaci a využití bezplatné registrace modelu COM.

> [!NOTE]
> V následujícím příkladu jsou všechny binární soubory aplikace předem připravené, aby se daly zaměřit na aspekty vytváření manifestu. Tento příklad vytvoří plně funkční nasazení ClickOnce.

```xml
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

- [Úlohy](../msbuild/msbuild-tasks.md)
- [GenerateDeploymentManifest – úloha](../msbuild/generatedeploymentmanifest-task.md)
- [SignFile – úloha](../msbuild/signfile-task.md)
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
