---
title: GenerateApplicationManifest Úloha | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634094"
---
# <a name="generateapplicationmanifest-task"></a>GenerateApplicationManifest – úloha

Generuje manifest aplikace ClickOnce nebo nativní manifest. Nativní manifest popisuje komponentu definováním jedinečné identity pro komponentu a identifikací všech sestavení a souborů, které komponentu tvoří. Manifest aplikace ClickOnce rozšiřuje nativní manifest označením vstupního bodu aplikace a určením úrovně zabezpečení aplikace.

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry `GenerateApplicationManifest` úkolu.

| Parametr | Popis |
|---------------------------------| - |
| `AssemblyName` | Volitelný `String` parametr.<br /><br /> Určuje `Name` pole identity sestavení pro generovaný manifest. Pokud tento parametr není zadán, název je `EntryPoint` odvozen `InputManifest` z parametry nebo. Pokud nelze vytvořit žádný název, úloha vyvolá chybu. |
| `AssemblyVersion` | Volitelný `String` parametr.<br /><br /> Určuje `Version` pole identity sestavení pro generovaný manifest. Pokud tento parametr není zadán, je použita výchozí hodnota "1.0.0.0". |
| `ClrVersion` | Volitelný `String` parametr.<br /><br /> Určuje minimální verzi clr (Common Language Runtime) vyžadované aplikací. Výchozí hodnota je verze CLR, kterou používá systém sestavení. Pokud úloha generuje nativní manifest, bude tento parametr ignorován. |
| `ConfigFile` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje, která položka obsahuje konfigurační soubor aplikace. Pokud úloha generuje nativní manifest, bude tento parametr ignorován. |
| `Dependencies` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje seznam položek, který definuje sadu závislých sestavení pro generovaný manifest. Každá položka může být dále popsána metadaty položky k označení dalšího stavu nasazení a typu závislosti. Další informace naleznete [v tématu Metadata položky](#item-metadata). |
| `Description` | Volitelný `String` parametr.<br /><br /> Určuje popis aplikace nebo součásti. |
| `EntryPoint` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje jednu položku, která označuje vstupní bod pro sestavení generovaného manifestu.<br /><br /> Pro manifest aplikace ClickOnce tento parametr určuje sestavení, které se spustí při spuštění aplikace. |
| `ErrorReportUrl` | Volitelný <xref:System.String?displayProperty=fullName> parametr.<br /><br /> Určuje adresu URL webové stránky, která je zobrazena v dialogových oknech během zpráv o chybách v instalacích ClickOnce. |
| `FileAssociations` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje seznam jednoho nebo více typů souborů, které jsou přidruženy k manifestu nasazení ClickOnce.<br /><br /> Přidružení souborů platná pouze v případě, že je cílená rozhraní .NET Framework 3.5 nebo novější. |
| `Files` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Soubory, které mají být zahrnuty do manifestu. Zadejte úplnou cestu pro každý soubor. |
| `HostInBrowser` | Volitelný <xref:System.Boolean> parametr.<br /><br /> Pokud `true`je aplikace hostována v prohlížeči (stejně jako WPF webové aplikace prohlížeče). |
| `IconFile` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Označuje soubor ikony aplikace. Ikona aplikace je vyjádřena v manifestu generované aplikace a používá se pro **dialogové okno Nabídka Start** a Přidat nebo **odebrat programy.** Pokud tento vstup není zadán, použije se výchozí ikona. Pokud úloha generuje nativní manifest, bude tento parametr ignorován. |
| `InputManifest` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Označuje vstupní dokument XML, který má sloužit jako základ pro generátor manifestu. To umožňuje, aby se strukturovaná data, jako je zabezpečení aplikace nebo vlastní definice manifestů, odrazila ve výstupním manifestu. Kořenový prvek v dokumentu XML musí být uzel sestavení v oboru názvů asmv1. |
| `IsolatedComReferences` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje součásti modelu COM, které mají být v generovaném manifestu izolovány. Tento parametr podporuje možnost izolovat komponenty modelu COM pro nasazení modelu COM bez registrace. Funguje tak, že automaticky generuje manifest se standardními definicemi registrace com. Aby však součásti modelu COM fungovaly správně, musí být v počítači sestavení zaregistrovány. |
| `ManifestType` | Volitelný `String` parametr.<br /><br /> Určuje, jaký typ manifestu má být generován. Tento parametr může mít následující hodnoty:<br /><br /> -   `Native`<br />-   `ClickOnce`<br /><br /> Pokud tento parametr není zadán, úkol `ClickOnce`je výchozí pro rozhraní . |
| `MaxTargetPath` | Volitelný `String` parametr.<br /><br /> Určuje maximální přípustnou délku cesty k souboru v nasazení aplikace ClickOnce. Pokud je tato hodnota zadána, délka každé cesty k souboru v aplikaci je kontrolována proti tomuto limitu. Všechny položky, které překročí limit zvýší v sestavení upozornění. Pokud tento vstup není zadán nebo je nula, je provedena žádná kontrola. Pokud úloha generuje nativní manifest, bude tento parametr ignorován. |
| `OSVersion` | Volitelný `String` parametr.<br /><br /> Určuje minimální požadovanou verzi operačního systému (OS) požadovanou aplikací. Například hodnota "5.1.2600.0" označuje, že operační systém je Windows XP. Pokud tento parametr není zadán, je použita hodnota "4.10.0.0", která označuje Windows 98 Druhé vydání, minimální podporovaný operační systém rozhraní .NET Framework. Pokud úloha generuje nativní manifest, bude tento vstup ignorován. |
| `OutputManifest` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> výstupní parametr.<br /><br /> Určuje název generovaného výstupního souboru manifestu. Pokud tento parametr není zadán, název výstupního souboru je odvozen z identity generovaného manifestu. |
| `Platform` | Volitelný `String` parametr.<br /><br /> Určuje cílovou platformu aplikace. Tento parametr může mít následující hodnoty:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> Pokud tento parametr není zadán, úkol `AnyCPU`je výchozí pro rozhraní . |
| `Product` | Volitelný `String` parametr.<br /><br /> Určuje název aplikace. Pokud tento parametr není zadán, název je odvozen z identity generovaného manifestu. Tento název se používá pro název zástupce v nabídce **Start** a je součástí názvu, který se zobrazí v dialogovém okně **Přidat nebo odebrat programy.** |
| `Publisher` | Volitelný `String` parametr.<br /><br /> Určuje vydavatele aplikace. Pokud tento parametr není zadán, název je odvozen od registrovaného uživatele nebo identity generovaného manifestu. Tento název se používá pro název složky v nabídce **Start** a je součástí názvu, který se zobrazí v dialogovém okně **Přidat nebo odebrat programy.** |
| `RequiresMinimumFramework35SP1` | Volitelný `Boolean` parametr.<br /><br /> Pokud true, aplikace vyžaduje rozhraní .NET Framework 3.5 SP1 nebo novější verzi. |
| `TargetCulture` | Volitelný `String` parametr.<br /><br /> Identifikuje jazykovou verzi aplikace a `Language` určuje pole identity sestavení pro generovaný manifest. Pokud tento parametr není zadán, předpokládá se, že aplikace je invariantní jazykové verze. |
| `TargetFrameworkMoniker` | Volitelný `String` parametr.<br /><br /> Určuje zástupný název cílového rozhraní. |
| `TargetFrameworkProfile` | Volitelný `String` parametr.<br /><br /> Určuje profil cílového rozhraní. |
| `TargetFrameworkSubset` | Volitelný `String` parametr.<br /><br /> Určuje název podmnožiny rozhraní .NET Framework, která má být cílová. |
| `TargetFrameworkVersion` | Volitelný `String` parametr.<br /><br /> Určuje cíl .NET Framework projektu. |
| `TrustInfoFile` | Volitelný <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Označuje dokument XML, který určuje zabezpečení aplikace. Kořenový prvek v dokumentu XML musí být uzel trustInfo v oboru názvů asmv2. Pokud úloha generuje nativní manifest, bude tento parametr ignorován. |
| `UseApplicationTrust` | Volitelný `Boolean` parametr.<br /><br /> Pokud true, `Product` `Publisher`, `SupportUrl` a vlastnosti jsou zapsány do manifestu aplikace. |

## <a name="remarks"></a>Poznámky

Kromě výše uvedených parametrů tato úloha dědí <xref:Microsoft.Build.Tasks.GenerateManifestBase> parametry z třídy, <xref:Microsoft.Build.Utilities.Task> která sama dědí z třídy. Seznam parametrů třídy Task naleznete v tématu [Základní třída úlohy](../msbuild/task-base-class.md).

Informace o použití úlohy naleznete v tématu `GenerateDeploymentManifest` [GenerateApplicationManifest úlohy](../msbuild/generateapplicationmanifest-task.md).

Vstupy pro závislosti a soubory mohou být dále zdobeny metadaty položky k určení dalšího stavu nasazení pro každou položku.

## <a name="item-metadata"></a>Metadata položky

|Název metadat|Popis|
|-------------------|-----------------|
|`DependencyType`|Označuje, zda je závislost publikována a nainstalována s aplikací nebo předpokladem. Tato metadata jsou platná pro všechny závislosti, ale nepoužívají se pro soubory. Dostupné hodnoty pro tato metadata jsou:<br /><br /> -   `Install`<br />-   `Prerequisite`<br /><br /> Instalace je výchozí hodnota.|
|`AssemblyType`|Označuje, zda je závislost spravované nebo nativní sestavení. Tato metadata jsou platná pro všechny závislosti, ale nepoužívají se pro soubory. Dostupné hodnoty pro tato metadata jsou:<br /><br /> -   `Managed`<br />-   `Native`<br />-   `Unspecified`<br /><br /> `Unspecified`je výchozí hodnota, která označuje, že generátor manifestu automaticky určí typ sestavení.|
|`Group`|Označuje skupinu pro stahování dalších souborů na vyžádání. Název skupiny je definován aplikací a může být libovolný řetězec. Prázdný řetězec označuje, že soubor není součástí skupiny pro stahování, což je výchozí hodnota. Soubory, které nejsou ve skupině, jsou součástí počátečního stahování aplikace. Soubory ve skupině jsou staženy pouze na <xref:System.Deployment.Application>základě výslovného požadavku aplikace pomocí aplikace .<br /><br /> Tato metadata platí pro `IsDataFile` všechny `false` soubory, kde `DependencyType` `Install`je a všechny závislosti, kde je .|
|`TargetPath`|Určuje, jak má být cesta definována v generovaném manifestu. Tento atribut je platný pro všechny soubory. Pokud tento atribut není zadán, použije se specifikace položky. Tento atribut je platný pro všechny `DependencyType` soubory `Install`a závislosti s hodnotou .|
|`IsDataFile`|Hodnota `Boolean` metadat, která označuje, zda je soubor datový soubor. Datový soubor je zvláštní v tom, že je migrován mezi aktualizacemi aplikací. Tato metadata jsou platná pouze pro soubory. `False`je výchozí hodnota.|

## <a name="example"></a>Příklad

Tento příklad `GenerateApplicationManifest` používá úkol ke generování manifestu `GenerateDeploymentManifest` aplikace ClickOnce a úkol ke generování manifestu nasazení pro aplikaci s jedním sestavením. Potom používá `SignFile` úkol k podepsání manifestů.

To ilustruje nejjednodušší možný scénář generování manifestu, kde ClickOnce manifesty jsou generovány pro jeden program. Výchozí název a identita jsou odvozeny ze sestavení manifestu.

> [!NOTE]
> V níže uvedeném příkladu jsou všechny binární soubory aplikace předem sestaveny, aby se mohly zaměřit na aspekty generování manifestu. Tento příklad vytváří plně funkční nasazení ClickOnce.
>
> [!NOTE]
> Další informace o `Thumbprint` vlastnosti `SignFile` použité v úloze v tomto příkladu naleznete v [tématu SignFile task](../msbuild/signfile-task.md).

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

Tento příklad `GenerateApplicationManifest` používá `GenerateDeploymentManifest` a úkoly ke generování ClickOnce aplikace a nasazení manifestů pro aplikaci s jedním sestavením, zadání názvu a identity manifestů.

Tento příklad je podobný předchozímu příkladu s tím rozdílem, že název a identita manifestů jsou explicitně zadány. Tento příklad je také nakonfigurován jako online aplikace namísto nainstalované aplikace.

> [!NOTE]
> V níže uvedeném příkladu jsou všechny binární soubory aplikace předem sestaveny, aby se mohly zaměřit na aspekty generování manifestu. Tento příklad vytváří plně funkční nasazení ClickOnce.
>
> [!NOTE]
> Další informace o `Thumbprint` vlastnosti `SignFile` použité v úloze v tomto příkladu naleznete v [tématu SignFile task](../msbuild/signfile-task.md).

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

Tento příklad `GenerateApplicationManifest` používá `GenerateDeploymentManifest` a úkoly ke generování ClickOnce aplikace a nasazení manifestů pro aplikaci s více soubory a sestavení.

> [!NOTE]
> V níže uvedeném příkladu jsou všechny binární soubory aplikace předem sestaveny, aby se mohly zaměřit na aspekty generování manifestu. Tento příklad vytváří plně funkční nasazení ClickOnce.
>
> [!NOTE]
> Další informace o `Thumbprint` vlastnosti `SignFile` použité v úloze v tomto příkladu naleznete v [tématu SignFile task](../msbuild/signfile-task.md).

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

Tento příklad `GenerateApplicationManifest` používá tuto úlohu ke generování nativního manifestu pro aplikaci *Test.exe*, odkazování na nativní komponentu *Alpha.dll* a izolované komponenty COM *Bravo.dll*.

Tento příklad vytváří *Test.exe.manifest*, takže aplikace XCOPY nasaditelné a s využitím registrace zdarma COM.

> [!NOTE]
> V níže uvedeném příkladu jsou všechny binární soubory aplikace předem sestaveny, aby se mohly zaměřit na aspekty generování manifestu. Tento příklad vytváří plně funkční nasazení ClickOnce.

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
- [Úloha GenerateDeploymentManifest](../msbuild/generatedeploymentmanifest-task.md)
- [Úloha SignFile](../msbuild/signfile-task.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
