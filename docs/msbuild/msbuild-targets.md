---
title: Cíle nástroje MSBuild | Microsoft Docs
description: Zjistěte, jak nástroj MSBuild používá cíle k seskupení úloh a umožnění, aby byl proces sestavení začten do menších jednotek.
ms.custom: SEO-VS-2020
ms.date: 06/13/2019
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, targets
ms.assetid: 8060b4d2-e4a9-48cf-a437-852649ceb417
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 294877e4884ae7b89f1e9d6f015c5c9213eba52d
ms.sourcegitcommit: 4908561809ad397c99cf204f52d5e779512e502c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112254820"
---
# <a name="msbuild-targets"></a>Cíle nástroje MSBuild

Cíle seskupují úkoly v konkrétním pořadí a umožňují, aby se proces sestavení zohlednil v menších jednotkách. Jeden cíl může například odstranit všechny soubory ve výstupním adresáři, aby se připravil na sestavení, zatímco jiný zkompiluje vstupy pro projekt a umístí je do prázdného adresáře. Další informace o úlohách najdete v tématu [Úlohy](../msbuild/msbuild-tasks.md).

## <a name="declare-targets-in-the-project-file"></a>Deklarace cílů v souboru projektu

 Cíle jsou deklarovány v souboru projektu s [elementem Target.](../msbuild/target-element-msbuild.md) Například následující KÓD XML vytvoří cíl s názvem Konstruktor, který pak zavolá úlohu Csc s typem položky Compile.

```xml
<Target Name="Construct">
    <Csc Sources="@(Compile)" />
</Target>
```

 Podobně jako vlastnosti nástroje MSBuild je možné cíle znovu definovat. Třeba

```xml
<Target Name="AfterBuild" >
    <Message Text="First occurrence" />
</Target>
<Target Name="AfterBuild" >
    <Message Text="Second occurrence" />
</Target>
```

Při spuštění se zobrazí pouze "Druhý výskyt", protože druhá `AfterBuild` definice `AfterBuild` skryje první.

Nástroj MSBuild je závislý na pořadí importu a poslední definicí cíle je použitá definice. Pokud se pokusíte znovu definovat cíl, nebude se projeví, pokud je integrovaný cíl definován později. V případě projektů, které používají sadu SDK, není pořadí definice nutně zřejmé, protože importy cílů se implicitně přidávají za konec souboru projektu.

Pokud tedy chcete rozšířit chování existujícího cíle, vytvořte nový cíl a `BeforeTargets` zadejte (nebo `AfterTargets` podle potřeby) následujícím způsobem:

```xml
<Target Name="MessageBeforePublish" BeforeTargets="BeforePublish">
  <Message Text="BeforePublish" Importance="high" />
</Target>
```

Zadejte pro cíl popisný název, stejně jako funkci v kódu.

## <a name="target-build-order"></a>Pořadí sestavení cílů

 Cíle musí být seřazeny, pokud vstup do jednoho cíle závisí na výstupu jiného cíle.
 
 Existuje několik způsobů, jak určit pořadí spouštění cílů.

- Počáteční cíle

- Výchozí cíle

- První cíl

- Cílové závislosti

- `BeforeTargets` a `AfterTargets` (MSBuild 4.0)

Cíl se nikdy během jednoho sestavení spustí dvakrát, i když na tom závisí následný cíl v sestavení. Po spuštění cíle se dokončí jeho příspěvek k sestavení.

Podrobnosti a další informace o cílovém pořadí sestavení najdete v tématu [Cílové pořadí sestavení](../msbuild/target-build-order.md).

## <a name="target-batching"></a>Dávkování cílů

Cílový prvek může mít atribut `Outputs` , který určuje metadata ve tvaru %( \<Metadata> ). Pokud ano, nástroj MSBuild spustí cíl jednou pro každou jedinečnou hodnotu metadat, seskupí nebo "dávkování" položek, které mají hodnotu metadat. Třeba

```xml
<ItemGroup>
    <Reference Include="System.Core">
      <RequiredTargetFramework>3.5</RequiredTargetFramework>
    </Reference>
    <Reference Include="System.Xml.Linq">
      <RequiredTargetFramework>3.5</RequiredTargetFramework>
    </Reference>
    <Reference Include="Microsoft.CSharp">
      <RequiredTargetFramework>4.0</RequiredTargetFramework>
    </Reference>
</ItemGroup>
<Target Name="AfterBuild"
    Outputs="%(Reference.RequiredTargetFramework)">
    <Message Text="Reference:
      @(Reference->'%(RequiredTargetFramework)')" />
</Target>
```

 batchs the Reference items by their RequiredTargetFramework metadata. Výstup cíle vypadá takhle:

```
Reference: 3.5;3.5
Reference: 4.0
```

 Dávkování cílů se v reálných sestaveních používá jen zřídka. Dávkování úkolů je častější. Další informace najdete v tématu [Dávkování](../msbuild/msbuild-batching.md).

## <a name="incremental-builds"></a>Přírůstková sestavení

 Přírůstková sestavení jsou sestavení optimalizovaná tak, aby cíle s výstupními soubory, které jsou aktuální s ohledem na jejich odpovídající vstupní soubory, nebyly provedeny. Cílový prvek může mít atributy i , které indikují, jaké položky cíl očekává jako vstup a jaké položky vytvoří `Inputs` `Outputs` jako výstup.

 Pokud jsou všechny výstupní položky aktuální, nástroj MSBuild přeskočí cíl, což výrazně zvyšuje rychlost sestavení. Tomu se říká přírůstkové sestavení cíle. Pokud jsou aktuální pouze některé soubory, nástroj MSBuild spustí cíl bez aktuálních položek. To se nazývá částečné přírůstkové sestavení cíle. Další informace najdete v tématu [Přírůstková sestavení.](../msbuild/incremental-builds.md)

## <a name="default-build-targets"></a>Výchozí cíle sestavení

Následující seznam uvádí veřejné cíle v Microsoft.Common.CurrentVersion.Targets.

```
===================================================
Build
The main build entry point.
===================================================
<Target Name="Build"
        Condition=" '$(_InvalidConfigurationWarning)' != 'true' "
        DependsOnTargets="$(BuildDependsOn)"
        Returns="$(TargetPath)" />


===================================================
BeforeBuild
===================================================
<Target Name="BeforeBuild"/>


===================================================
AfterBuild
===================================================
<Target Name="AfterBuild"/>


===================================================
CoreBuild
The core build step calls each of the build targets.
===================================================
<Target Name="CoreBuild"
        DependsOnTargets="$(CoreBuildDependsOn)">


===================================================
Rebuild
Delete all intermediate and final build outputs, and then build the project from scratch.
===================================================
<Target Name="Rebuild"
        Condition=" '$(_InvalidConfigurationWarning)' != 'true' "
        DependsOnTargets="$(RebuildDependsOn)"
        Returns="$(TargetPath)"/>


===================================================
BeforeRebuild
===================================================
<Target Name="BeforeRebuild"/>


===================================================
AfterRebuild
===================================================
<Target Name="AfterRebuild"/>


===================================================
BuildGenerateSources
Set BuildPassReferences to enable P2P builds
===================================================
<Target Name="BuildGenerateSources"
        DependsOnTargets="BuildGenerateSourcesTraverse;$(BuildGenerateSourcesAction)" />


===================================================
BuildCompile
===================================================
<Target Name="BuildCompile"
        DependsOnTargets="BuildCompileTraverse;$(BuildCompileAction)" />


===================================================
BuildLink
===================================================
<Target Name="BuildLink"
        DependsOnTargets="BuildLinkTraverse;$(BuildLinkAction)" />


===================================================
CopyRunEnvironmentFiles
Copy environment files necessary to run the user's app to the final directory.
This is a public target that can be invoked by an IDE.
This may be used by an IDE to make the app.config file available for running
the target app.
===================================================
<Target
        Name="CopyRunEnvironmentFiles"
        DependsOnTargets="PrepareForBuild;SetWin32ManifestProperties;_CopyAppConfigFile;_CleanRecordFileWrites"/>


===================================================
Run
Run the final build output if it is a .EXE
===================================================
<Target
        Name="Run"
        DependsOnTargets="$(RunDependsOn)">


===================================================
BuildOnlySettings
This target is called only when doing a real build.  It is specifically not called during project load.
===================================================
<Target Name="BuildOnlySettings">


===================================================
PrepareForBuild
Prepare the prerequisites for building.
===================================================
<Target Name="PrepareForBuild"
        DependsOnTargets="$(PrepareForBuildDependsOn)">


===================================================
GetFrameworkPaths
Get the paths for the .NET Framework installation directory

These paths are not used directly by this .targets file but are available for pre and
post build steps.

This is a generally overriden target, for example it is overriden in the Microsoft.NETFramework.targets file
===================================================
<Target Name="GetFrameworkPaths"/>


===================================================
GetReferenceAssemblyPaths
Get the paths for the Reference Assemblies for the known versions of the
.NET Framework.

These paths are used by the build process in order to resolve the correct
assemblies from the various directories, and to support multi-targeting
===================================================
<Target Name="GetReferenceAssemblyPaths"
        DependsOnTargets="$(GetReferenceAssemblyPathsDependsOn)">


===================================================
AssignLinkMetadata
For items of a certain set of allowed types, make sure that
if they are defined in a file other than the project file, that 
they have "Link" metadata set to an appropriate default. 
===================================================
<Target Name="AssignLinkMetadata"
        Condition=" '$(SynthesizeLinkMetadata)' == 'true' ">


===================================================
PreBuildEvent
Run the pre-build event if there is one.
===================================================
<Target Name="PreBuildEvent"
        Condition="'$(PreBuildEvent)'!=''"
        DependsOnTargets="$(PreBuildEventDependsOn)">


===================================================
UnmanagedUnregistration
If the main assembly had previously been registered for COM interop, unregister it now.
We will re-register the new version after it has been built.
===================================================
<Target Name="UnmanagedUnregistration"
        Condition="(('$(_AssemblyTimestampBeforeCompile)' != '$(_AssemblyTimestampAfterCompile)' or '$(RegisterForComInterop)' != 'true' or '$(OutputType)' != 'library') or
                                ('$(_AssemblyTimestampBeforeCompile)' == '')) and
                                Exists('@(_UnmanagedRegistrationCache)')"
        DependsOnTargets="$(UnmanagedUnregistrationDependsOn)">


===================================================
GetTargetFrameworkVersion
This stand-alone target returns the target framework version (i.e. v3.5, v4.0, etc.)
that would be used if we built this project.
===================================================
<Target
        Name="GetTargetFrameworkVersion"
        Returns="$(TargetFrameworkVersion)" />


===================================================
ResolveReferences
===================================================
<Target Name="ResolveReferences"
        DependsOnTargets="$(ResolveReferencesDependsOn)"/>


===================================================
BeforeResolveReferences
===================================================
<Target Name="BeforeResolveReferences"/>


===================================================
AfterResolveReferences
===================================================
<Target Name="AfterResolveReferences"/>


===================================================
AssignProjectConfiguration
Assigns the appropriate configuration to each project in the list of project references passed in.
Adds to the project references passed in any project references implied by dependencies expressed in the solution file, if any.
===================================================
<Target Name="AssignProjectConfiguration"
        Condition="'$(CurrentSolutionConfigurationContents)' != '' or '@(ProjectReference)'!=''">


===================================================
ResolveProjectReferences
Build referenced projects
===================================================
<Target Name="ResolveProjectReferences"
        DependsOnTargets="AssignProjectConfiguration;_SplitProjectReferencesByFileExistence"
        Returns="@(_ResolvedNativeProjectReferencePaths);@(_ResolvedProjectReferencePaths)">


===================================================
GetTargetPath
This stand-alone target returns the name of the build product (i.e. EXE, DLL)
that would be produced if we built this project.
===================================================
<Target Name="GetTargetPath"
        DependsOnTargets="$(GetTargetPathDependsOn)"
        Returns="$(TargetPath)"/>


===================================================
GetTargetPathWithTargetPlatformMoniker
This stand-alone target returns the name and version of the target platform for this project.
===================================================
<Target Name="GetTargetPathWithTargetPlatformMoniker"
        DependsOnTargets="$(GetTargetPathWithTargetPlatformMonikerDependsOn)"
        Returns="@(TargetPathWithTargetPlatformMoniker)">


===================================================
GetNativeManifest
Compute the manifest item for this project.
===================================================
<Target
        Name="GetNativeManifest"
        Returns="@(ComputedApplicationManifest)">


===================================================
ResolveNativeReferences
Resolve native references
===================================================
<Target Name="ResolveNativeReferences"
        Condition="'@(NativeReference)'!=''"
        DependsOnTargets="ResolveProjectReferences">


===================================================
ResolveAssemblyReferences
Given the list of assemblies, find the closure of all assemblies that they depend on. These are
what we need to copy to the output directory.

[IN]
@(Reference) - List of assembly references as fusion names.
@(_ResolvedProjectReferencePaths) - List of project references produced by projects that this project depends on.

        The 'Private' attribute on the reference corresponds to the Copy Local flag in IDE.
        The 'Private' flag can have three possible values:
                - 'True' means the reference should be Copied Local
                - 'False' means the reference should not be Copied Local
                - [Missing] means this task will decide whether to treat this reference as CopyLocal or not.

[OUT]
@(ReferencePath) - Paths to resolved primary files.
@(ReferenceDependencyPaths) - Paths to resolved dependency files.
@(_ReferenceRelatedPaths) - Paths to .xmls and .pdbs.
@(ReferenceSatellitePaths) - Paths to satellites.
@(_ReferenceSerializationAssemblyPaths) - Paths to XML serialization assemblies created by sgen.
@(_ReferenceScatterPaths) - Paths to scatter files.
@(ReferenceCopyLocalPaths) - Paths to files that should be copied to the local directory.
===================================================
<Target Name="ResolveAssemblyReferences"
        Returns="@(ReferencePath)"
        DependsOnTargets="$(ResolveAssemblyReferencesDependsOn)">


===================================================
GenerateBindingRedirects
Inject the binding redirects into the app config file based on suggested redirects as output from ResolveAssemblyReferences.

[IN]
@(AppConfigWithTargetPath) - Path to the source app config file. This can be null if the project 
                                                        doesn't contain an app config file.
$(TargetFileName) -          The file name of the build target.

[OUT]
@(OutputAppConfigFile) -     Path to the output app config file in the intermediate directory.
===================================================
<Target Name="GenerateBindingRedirects"
        Inputs="$(MSBuildAllProjects);@(AppConfigFile);$(ResolveAssemblyReferencesStateFile);$(IntermediateOutputPath);@(SuggestedBindingRedirects)"
        Outputs="$(_GenerateBindingRedirectsIntermediateAppConfig)"
        Condition="'$(AutoGenerateBindingRedirects)' == 'true' and '$(GenerateBindingRedirectsOutputType)' == 'true'">


===================================================
GenerateBindingRedirectsUpdateAppConfig
Updates the project to use the generated app.config content.  This needs to run regardless of 
inputs/outputs so it is separate from GenerateBindingRedirects.
===================================================
<Target Name="GenerateBindingRedirectsUpdateAppConfig"
        AfterTargets="GenerateBindingRedirects"
        Condition="'$(AutoGenerateBindingRedirects)' == 'true' and '$(GenerateBindingRedirectsOutputType)' == 'true' and Exists('$(_GenerateBindingRedirectsIntermediateAppConfig)')">


===================================================
GetInstalledSDKs
Gets the list of SDKs installed in the SDKDirectoryRoot and SDKRegistryRoot locations
These paths are used by the ResolveSDKReference task and the ResolveAssemblyReference task.
===================================================
<Target Name="GetInstalledSDKLocations"
      DependsOnTargets="$(GetInstalledSDKLocationsDependsOn)"
      Returns="@(InstalledSDKLocations)" />


===================================================
ResolveSDKReferences
Given a list of SDKReference items and a list of resolved winmd files which may contain metadata as to which sdk they came from
we need to find the sdk root folders on disk and populate a ResolvedSDKReference item which has the full path to the SDK ROOT 
and the sdk identity as a piece of metadata.
===================================================
<Target Name="ResolveSDKReferences"
        Returns="@(ResolvedSDKReference)"
        DependsOnTargets="$(ResolveSDKReferencesDependsOn)">


===================================================
FindInvalidProjectReferences
Find project to project references with target platform version higher than the one used by the current project and 
creates a list of invalid references to be unresolved. It issues a warning for each invalid reference.
===================================================
<Target Name="FindInvalidProjectReferences"
        Condition ="'$(FindInvalidProjectReferences)' == 'true'"
        DependsOnTargets="$(FindInvalidProjectReferencesDependsOn)">


===================================================
ExpandSDKReferences
After we have resolved the sdk refrence we need to make sure that we automatically include the references which are part of the SDK (both winmd and dll)
as part of the assemblies passed to the compiler.

Project systems or project which do not want to reference all dlls or winmd files should override this target to do nothing.
===================================================
<Target Name="ExpandSDKReferences"
        Returns="@(ReferencesFromSDK)"
        DependsOnTargets="$(ExpandSDKReferencesDependsOn)" />


===================================================
ExportWindowsMDFile
When a project is generating a a winmd file through c# or vb, ect the compiler will create a WinMDModule file. This file needs to be run
through the winmdexp tool in order to generate the resulting WinMD file.
===================================================
<Target Name="ExportWindowsMDFile"
        DependsOnTargets="Compile"
        Condition="'$(ExportWinMDFile)' == 'true'"
        Inputs="@(IntermediateAssembly);@(DocFileItem);@(_DebugSymbolsIntermediatePath);@(ReferencePath);$(MSBuildAllProjects)"
        Outputs="$(_IntermediateWindowsMetadataPath);$(WinMDExpOutputPdb);$(WinMDOutputDocumentationFile)" />


===================================================
DesignTimeResolveAssemblyReferences
Given the list of assemblies, resolve their reference paths.
This target is called by Visual Studio at run time in order to filter references
according to the targeted framework.
===================================================
<Target Name="DesignTimeResolveAssemblyReferences"
        Condition="'$(DesignTimeReference)'!=''"
        DependsOnTargets="$(DesignTimeResolveAssemblyReferencesDependsOn)">


===================================================
ResolveComReferences
Resolve COM references
===================================================
<Target Name="ResolveComReferences"
        Condition="'@(COMReference)'!='' or '@(COMFileReference)'!=''"
        Returns="@(ReferencePath)"
        DependsOnTargets="PrepareForBuild;ResolveKeySource;ResolveAssemblyReferences" />


===================================================
PrepareResources
Prepare resources for the Compile step.
===================================================
<Target Name="PrepareResources"
        DependsOnTargets="$(PrepareResourcesDependsOn)"/>


===================================================
PrepareResourceNames
Prepare the names of resource files.
===================================================
<Target Name="PrepareResourceNames"
        DependsOnTargets="$(PrepareResourceNamesDependsOn)"/>


===================================================
AssignTargetPaths
This target creates <TargetPath> tags for items. <TargetPath> is a relative folder plus filename
for the destination of this item.
===================================================
<Target Name="AssignTargetPaths"
        DependsOnTargets="$(AssignTargetPathsDependsOn)">


===================================================
GetItemTargetPaths
This target returns all items that have TargetPath metadata assigned by the AssignTargetPaths target.
===================================================
<Target Name="GetItemTargetPaths"
        DependsOnTargets="AssignTargetPaths"
        Returns="
        @(EmbeddedResource);
        @(ContentWithTargetPath);
        @(_NoneWithTargetPath);
        @(_DeploymentBaseManifestWithTargetPath);
        " />


===================================================
SplitResourcesByCulture
Split EmbeddedResource items into five lists based on whether
they are resx files, licx files or other resources and whether they should be localized. Also adds Type and Culture
metadata. Type indicates whether the resource is "Resx" or "Non-Resx".
===================================================
<Target Name="SplitResourcesByCulture"
        DependsOnTargets="AssignTargetPaths">


===================================================
CreateCustomManifestResourceNames
Allows custom manifest resource name generation tasks to plug
into the build process
===================================================
<Target Name="CreateCustomManifestResourceNames"
        DependsOnTargets="$(CreateCustomManifestResourceNamesDependsOn)"/>


===================================================
ResGen
Run GenerateResource on the given resx files.
===================================================
<Target Name="ResGen"
        DependsOnTargets="$(ResGenDependsOn)"/>


===================================================
BeforeResGen
===================================================
<Target Name="BeforeResGen"/>


===================================================
AfterResGen
===================================================
<Target Name="AfterResGen"/>


===================================================
ResolveKeySource
Resolve the strong name key used to sign the assembly as well as the certificate used to
sign the ClickOnce manifests.
===================================================
<Target Name="ResolveKeySource"
        Condition="$(SignManifests) == 'true' or $(SignAssembly) == 'true'">


===================================================
Compile
===================================================
<Target Name="Compile"
        DependsOnTargets="$(CompileDependsOn)"/>


===================================================
GenerateTargetFrameworkMonikerAttribute
Emit the target framework moniker attribute as  a code fragment into a temporary source file for the compiler.
===================================================
<Target Name="GenerateTargetFrameworkMonikerAttribute"
        BeforeTargets="BeforeCompile"
        DependsOnTargets="PrepareForBuild;GetReferenceAssemblyPaths"
        Inputs="$(MSBuildToolsPath)\Microsoft.Common.targets"
        Outputs="$(TargetFrameworkMonikerAssemblyAttributesPath)"
        Condition="'$(GenerateTargetFrameworkAttribute)' == 'true'">


===================================================
GenerateAdditionalSources
Emit any specified code fragments into a temporary source file for the compiler.
===================================================
<Target Name="GenerateAdditionalSources"
        BeforeTargets="BeforeCompile"
        DependsOnTargets="PrepareForBuild;GetReferenceAssemblyPaths"
        Inputs="$(MSBuildAllProjects)"
        Outputs="$(AssemblyAttributesPath)"
        Condition="'@(AssemblyAttributes)' != '' and '$(GenerateAdditionalSources)' == 'true'">


===================================================
BeforeCompile
===================================================
<Target Name="BeforeCompile"/>


===================================================
AfterCompile
===================================================
<Target Name="AfterCompile"/>


===================================================
GenerateSerializationAssemblies
Run GenerateSerializationAssemblies on the assembly produced by this build.
===================================================
<Target Name="GenerateSerializationAssemblies"
        Condition="'$(_SGenGenerateSerializationAssembliesConfig)' == 'On' or ('@(WebReferenceUrl)'!='' and '$(_SGenGenerateSerializationAssembliesConfig)' == 'Auto')"
        DependsOnTargets="AssignTargetPaths;Compile;ResolveKeySource"
        Inputs="$(MSBuildAllProjects);@(IntermediateAssembly)"
        Outputs="$(IntermediateOutputPath)$(_SGenDllName)">


===================================================
CreateSatelliteAssemblies
Create one satellite assembly for every unique culture in the resources.
===================================================
<Target Name="CreateSatelliteAssemblies"
        DependsOnTargets="$(CreateSatelliteAssembliesDependsOn)" />


===================================================
GenerateSatelliteAssemblies
Actually run al.exe to create the satellite assemblies.
===================================================
<Target Name="GenerateSatelliteAssemblies"
        Inputs="$(MSBuildAllProjects);@(_SatelliteAssemblyResourceInputs);$(IntermediateOutputPath)$(TargetName)$(TargetExt)"
        Outputs="$(IntermediateOutputPath)%(Culture)\$(TargetName).resources.dll"
        Condition="'@(_SatelliteAssemblyResourceInputs)' != ''">


===================================================
ComputeIntermediateSatelliteAssemblies
Compute the paths to the intermediate satellite assemblies,
with culture attributes so we can copy them to the right place.
===================================================
<Target Name="ComputeIntermediateSatelliteAssemblies"
        Condition="@(EmbeddedResource->'%(WithCulture)') != ''"
        DependsOnTargets="$(ComputeIntermediateSatelliteAssembliesDependsOn)">


===================================================
SetWin32ManifestProperties
Set Win32Manifest and EmbeddedManifest properties to be used later in the build.
===================================================
<Target Name="SetWin32ManifestProperties"
        Condition="'$(Win32Manifest)'==''"
        DependsOnTargets="ResolveComReferences;ResolveNativeReferences;_SetExternalWin32ManifestProperties;_SetEmbeddedWin32ManifestProperties" />


===================================================
GenerateManifests
Generates ClickOnce application and deployment manifests or a native manifest.
===================================================
<Target Name="GenerateManifests"
        Condition="'$(GenerateClickOnceManifests)'=='true' or '@(NativeReference)'!='' or '@(ResolvedIsolatedComModules)'!='' or '$(GenerateAppxManifest)' == 'true'"
        DependsOnTargets="$(GenerateManifestsDependsOn)"/>


===================================================
GenerateApplicationManifest
Generates a ClickOnce or native application manifest.
An application manifest specifies declarative application identity, dependency and security information.
===================================================
<Target Name="GenerateApplicationManifest"
        DependsOnTargets="
                _DeploymentComputeNativeManifestInfo;
                _DeploymentComputeClickOnceManifestInfo;
                ResolveComReferences;
                ResolveNativeReferences;
                _GenerateResolvedDeploymentManifestEntryPoint"
        Inputs="
                $(MSBuildAllProjects);
                @(AppConfigWithTargetPath);
                $(_DeploymentBaseManifest);
                @(ResolvedIsolatedComModules);
                @(_DeploymentManifestDependencies);
                @(_DeploymentResolvedManifestEntryPoint);
                @(_DeploymentManifestFiles)"
        Outputs="@(ApplicationManifest)">


===================================================
GenerateDeploymentManifest
Generates a ClickOnce deployment manifest.
An deployment manifest specifies declarative application identity and application update information.
===================================================
<Target Name="GenerateDeploymentManifest"
        DependsOnTargets="GenerateApplicationManifest"
        Inputs="
                $(MSBuildAllProjects);
                @(ApplicationManifest)
                "
        Outputs="@(DeployManifest)">


===================================================
PrepareForRun
Copy the build outputs to the final directory if they have changed.
===================================================
<Target Name="PrepareForRun"
        DependsOnTargets="$(PrepareForRunDependsOn)"/>


===================================================
CopyFilesToOutputDirectory
Copy all build outputs, satellites and other necessary files to the final directory.
===================================================
<Target Name="CopyFilesToOutputDirectory"
        DependsOnTargets="
                ComputeIntermediateSatelliteAssemblies;
                _CopyFilesMarkedCopyLocal;
                _CopySourceItemsToOutputDirectory;
                _CopyAppConfigFile;
                _CopyManifestFiles;
                _CheckForCompileOutputs;
                _SGenCheckForOutputs">


===================================================
GetCopyToOutputDirectoryItems
Get all project items that may need to be transferred to the output directory.
This includes baggage items from transitively referenced projects. It would appear
that this target computes full transitive closure of content items for all referenced
projects; however that is not the case. It only collects the content items from its
immediate children and not children of children. The reason this happens is that
the ProjectReferenceWithConfiguration list that is consumed by _SplitProjectReferencesByFileExistence
is only populated in the current project and is empty in the children. The empty list
causes _MSBuildProjectReferenceExistent to be empty and terminates the recursion.
===================================================
<Target Name="GetCopyToOutputDirectoryItems"
        Returns="@(AllItemsFullPathWithTargetPath)"
        KeepDuplicateOutputs=" '$(MSBuildDisableGetCopyToOutputDirectoryItemsOptimization)' == '' "
        DependsOnTargets="$(GetCopyToOutputDirectoryItemsDependsOn)">


===================================================
UnmanagedRegistration
Registers the main assembly for COM interop.
===================================================
<Target Name="UnmanagedRegistration"
        Condition="'$(RegisterForComInterop)'=='true' and '$(OutputType)'=='library'"
        DependsOnTargets="$(UnmanagedRegistrationDependsOn)" />>


===================================================
IncrementalClean
Remove files that were produced in a prior build but weren't produced in the current build.
The reason is that if, for example, the name of the .exe has changed we want to delete the
old copy.

Leave the Clean cache file containing only the files produced in the current build.
===================================================
<Target Name="IncrementalClean"
        DependsOnTargets="_CleanGetCurrentAndPriorFileWrites">


===================================================
Clean
Delete all intermediate and final build outputs.
===================================================
<Target Name="Clean"
        Condition=" '$(_InvalidConfigurationWarning)' != 'true' "
        DependsOnTargets="$(CleanDependsOn)" />


===================================================
BeforeClean
===================================================
<Target Name="BeforeClean"/>


===================================================
AfterClean
===================================================
<Target Name="AfterClean"/>


===================================================
CleanReferencedProjects
Call Clean target on all Referenced Projects.
===================================================
<Target Name="CleanReferencedProjects"
        DependsOnTargets="AssignProjectConfiguration; _SplitProjectReferencesByFileExistence">


===================================================
CleanPublishFolder
===================================================
<Target Name="CleanPublishFolder"/>


===================================================
PostBuildEvent
Run the post-build event. This step is driven by two parameters:

(1) The $(RunPostBuildEvent) property is set by the user through the IDE and can be one of four values.

        - OnBuildSuccess: In this case, every step of the build must succeed for the post-build step to run.
        - <Blank>: This is the same as OnBuildSuccess.
        - OnOutputUpdated: In this case, the post-build step will run only if the main output assembly was
        actually updated.
        - Always: The post-build step is always run.

(2) The $(_AssemblyTimestampBeforeCompile) and $(_AssemblyTimestampAfterCompile) values are
        set by the _TimeStampBeforeCompile and _TimeStampAfterCompile targets.  If the assembly was actually
        rebuilt during this build, then the two values will be different.
===================================================
<Target Name="PostBuildEvent"
        Condition="'$(PostBuildEvent)' != '' and ('$(RunPostBuildEvent)' != 'OnOutputUpdated' or '$(_AssemblyTimestampBeforeCompile)' != '$(_AssemblyTimestampAfterCompile)')"
        DependsOnTargets="$(PostBuildEventDependsOn)">


===================================================
Publish
This target is only called when doing ClickOnce publishing outside the IDE, which implicitly builds before publishing.
===================================================
<Target Name="Publish"
        DependsOnTargets="$(PublishDependsOn)"/>


===================================================
SetGenerateManifests
This target simply assures the GenerateClickOnceManifests property is set whenever the publish target is invoked.
===================================================
<Target Name="SetGenerateManifests"/>


===================================================
PublishOnly
The "PublishOnly" target is intended for ClickOnce publishing inside the IDE, where the build has already been done
by the BuildManager.
===================================================
<Target Name="PublishOnly"
        DependsOnTargets="$(PublishOnlyDependsOn)"/>


===================================================
BeforePublish
===================================================
<Target Name="BeforePublish"/>


===================================================
AfterPublish
===================================================
<Target Name="AfterPublish"/>


===================================================
PublishBuild
Defines the set of targets that publishing is directly dependent on.
===================================================
<Target Name="PublishBuild"
        DependsOnTargets="$(PublishBuildDependsOn)"/>


===================================================
AllProjectOutputGroups
The targets below drive output groups, which provide generic information about a
project's inputs (e.g., content files, compilation sources, etc.) and built outputs
(e.g., built EXE/DLL, PDB, XML documentation files, etc.)

Each target may produce two kinds of items:  outputs and dependencies.  Outputs are
items from the current project; dependencies are items that are brought into the
current project as a result of referencing other projects or components.

For both outputs and dependencies, the Include attribute
specifies the location of the output/dependency; it must be a full path.  Any number
of additional attributes may be placed on an output/dependency item.
===================================================
<Target Name="AllProjectOutputGroups"
        DependsOnTargets="
                BuiltProjectOutputGroup;
                DebugSymbolsProjectOutputGroup;
                DocumentationProjectOutputGroup;
                SatelliteDllsProjectOutputGroup;
                SourceFilesProjectOutputGroup;
                ContentFilesProjectOutputGroup;
                SGenFilesOutputGroup"/>


===================================================
BuiltProjectOutputGroup
This target performs population of the Build project output group.
===================================================
<Target Name="BuiltProjectOutputGroup"
        Returns="@(BuiltProjectOutputGroupOutput)"
        DependsOnTargets="$(BuiltProjectOutputGroupDependsOn)">


===================================================
DebugSymbolsProjectOutputGroup
This target performs population of the Debug Symbols project output group.
===================================================
<Target Name="DebugSymbolsProjectOutputGroup"
        Returns="@(DebugSymbolsProjectOutputGroupOutput)"
        DependsOnTargets="$(DebugSymbolsProjectOutputGroupDependsOn)"/>


===================================================
DocumentationProjectOutputGroup
This target performs population of the Documentation project output group.
===================================================
<Target Name="DocumentationProjectOutputGroup"
        Returns="@(DocumentationProjectOutputGroupOutput)"
        DependsOnTargets="$(DocumentationProjectOutputGroupDependsOn)"/>


===================================================
SatelliteDllsProjectOutputGroup
This target performs population of the Satellite Files project output group.
===================================================
<Target Name="SatelliteDllsProjectOutputGroup"
        Returns="@(SatelliteDllsProjectOutputGroupOutput)"
        DependsOnTargets="$(SatelliteDllsProjectOutputGroupDependsOn)">


===================================================
SourceFilesProjectOutputGroup
This target performs population of the Source Files project output group.
Source files are items in the project whose type is "Compile" and "EmbeddedResource".
===================================================
<Target Name="SourceFilesProjectOutputGroup"
        Returns="@(SourceFilesProjectOutputGroupOutput)"
        DependsOnTargets="$(SourceFilesProjectOutputGroupDependsOn)">


===================================================
ContentFilesProjectOutputGroup
This target performs population of the Content Files project output group.
Content files are items in the project whose type is "Content".
===================================================
<Target Name="ContentFilesProjectOutputGroup"
        Returns="@(ContentFilesProjectOutputGroupOutput)"
        DependsOnTargets="$(ContentFilesProjectOutputGroupDependsOn)">


===================================================
SGenFilesOutputGroup
This target performs population of the GenerateSerializationAssemblies Files project output group.
GenerateSerializationAssemblies files are those generated by the GenerateSerializationAssemblies target and task.
===================================================
<Target Name="SGenFilesOutputGroup"
        Returns="@(SGenFilesOutputGroupOutput)"
        DependsOnTargets="$(SGenFilesOutputGroupDependsOn)"/>


===================================================
GetResolvedSDKReferences
These targets are to gather information from the SDKs.
===================================================
<Target Name="GetResolvedSDKReferences"
        DependsOnTargets="ResolveSDKReferences"
        Returns="@(ResolvedSDKReference)"/>


===================================================
PriFilesOutputGroup
This target performs population of the pri files output group
===================================================
<Target Name="PriFilesOutputGroup"
        Condition="'@(_ReferenceRelatedPaths)' != ''"
        DependsOnTargets="BuildOnlySettings;PrepareForBuild;AssignTargetPaths;ResolveReferences"
        Returns="@(PriFilesOutputGroupOutput)">


===================================================
SDKRedistOutputGroup
This target gathers the Redist folders from the SDKs which have been resolved.
===================================================
<Target Name="SDKRedistOutputGroup"
        Returns="@(SDKRedistOutputGroupOutput)"
        DependsOnTargets="$(SDKRedistOutputGroupDependsOn)"/>
```

## <a name="see-also"></a>Viz také

- [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)
- [Postupy: Použití stejného cíle ve více souborech projektu](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)
