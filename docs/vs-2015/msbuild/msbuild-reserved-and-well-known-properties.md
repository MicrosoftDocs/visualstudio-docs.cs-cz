---
title: Vyhrazené a dobře známé vlastnosti nástroje MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, reserved properties
ms.assetid: 99333e61-83c9-4804-84e3-eda297c2478d
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 19fa9c35011e42905c1f26ed34da405be61d0aba
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68181077"
---
# <a name="msbuild-reserved-and-well-known-properties"></a>Vyhrazené a známé vlastnosti nástroje MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] poskytuje sadu předdefinovaných vlastností, které ukládají informace o souboru projektu a [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] binárních souborech. Tyto vlastnosti jsou vyhodnocovány stejným způsobem jako ostatní [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Vlastnosti. Chcete-li například použít `MSBuildProjectFile` vlastnost, zadáte `$(MSBuildProjectFile)` .  
  
 Nástroj MSBuild používá hodnoty v následující tabulce k předdefinování rezervovaných a dobře známých vlastností. Vyhrazené vlastnosti nelze přepsat, ale známé vlastnosti lze přepsat pomocí identicky pojmenovaných vlastností prostředí, globálních vlastností nebo vlastností, které jsou deklarovány v souboru projektu.  
  
## <a name="reserved-and-well-known-properties"></a>Vyhrazené a známé vlastnosti  
 V následující tabulce jsou popsány [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] předdefinované vlastnosti.  
  
|Vlastnost|Popis|Rezervované nebo dobře známé|  
|--------------|-----------------|-----------------------------|  
|`MSBuildBinPath`|Absolutní cesta ke složce [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , kde jsou umístěny binární soubory, které jsou právě používány (například C:\Windows\Microsoft.NET\Framework \\ *číslo_verze*). Tato vlastnost je užitečná, pokud se musíte odkazovat na soubory v [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] adresáři.<br /><br /> Do této vlastnosti nezahrnujte konečné zpětné lomítko.|Vyhrazené|  
|`MSBuildExtensionsPath`|Zavedeno v .NET Framework 4: neexistuje žádný rozdíl mezi výchozími hodnotami `MSBuildExtensionsPath` a `MSBuildExtensionsPath32` . Proměnnou prostředí lze nastavit `MSBUILDLEGACYEXTENSIONSPATH` na hodnotu, která není null, chcete-li povolit chování výchozí hodnoty `MSBuildExtensionsPath` v předchozích verzích.<br /><br /> V .NET Framework 3,5 a starších verzích výchozí hodnota `MSBuildExtensionsPath` odkazuje na cestu podsložky MSBuild ve složce \Program Files \ nebo \Program Files (x86) v závislosti na bitová verze aktuálního procesu. Například pro 32 proces na 64 počítači tato vlastnost odkazuje na složku \Program Files (x86). Pro 64 proces na 64 počítači tato vlastnost odkazuje na složku \Program Files.<br /><br /> Do této vlastnosti nezahrnujte konečné zpětné lomítko.<br /><br /> Toto umístění je užitečné místo pro vložení vlastních cílových souborů. Například vaše cílové soubory mohou být nainstalovány do složky \Program Files\MSBuild\MyFiles\Northwind.targets a následně importovány do souborů projektu pomocí tohoto kódu XML:<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>`|Dobře známé|  
|`MSBuildExtensionsPath32`|Cesta [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] podsložky ve složce \Program Files nebo \Program Files (x86). Tato cesta vždy odkazuje na 32 složku \Program Files na 32 počítači a \Program Files (x86) v počítači s 64. Viz také `MSBuildExtensionsPath` a `MSBuildExtensionsPath64` .<br /><br /> Do této vlastnosti nezahrnujte konečné zpětné lomítko.|Dobře známé|  
`MSBuildExtensionsPath64`|Cesta [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] podsložky ve složce \Program Files. Pro 64 počítač tato cesta vždy odkazuje na složku \Program Files. Pro 32 počítač je tato cesta prázdná. Viz také `MSBuildExtensionsPath` a `MSBuildExtensionsPath32` .<br /><br /> Do této vlastnosti nezahrnujte konečné zpětné lomítko.|Dobře známé|  
|`MSBuildLastTaskResult`|`true` v případě, že předchozí úloha byla dokončena bez chyb (i v případě výskytu upozornění) nebo `false` v případě, že předchozí úloha obsahovala chyby. Při výskytu chyby v úloze obvykle dojde k chybě poslední věcí, ke které dojde v projektu. Hodnota této vlastnosti proto nikdy není `false` , s výjimkou těchto scénářů:<br /><br /> – Pokud `ContinueOnError` je atribut [elementu Task (MSBuild)](../msbuild/task-element-msbuild.md) nastaven na `WarnAndContinue` (nebo `true` ) nebo `ErrorAndContinue` .<br /><br /> – Pokud `Target` má [element Error (MSBuild)](../msbuild/onerror-element-msbuild.md) jako podřízený element.|Vyhrazené|  
|`MSBuildNodeCount`|Maximální počet souběžných procesů, které jsou používány při sestavování. Jedná se o hodnotu, kterou jste zadali pro **/maxcpucount** na příkazovém řádku. Pokud jste zadali **/maxcpucount** bez zadání hodnoty, pak `MSBuildNodeCount` určí počet procesorů v počítači. Další informace naleznete v tématu [Reference k příkazovému řádku](../msbuild/msbuild-command-line-reference.md) a [Souběžné sestavování více projektů](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).|Vyhrazené|  
|`MSBuildProgramFiles32`|Umístění 32 složky programu; například `C:\Program Files (x86)` .<br /><br /> Do této vlastnosti nezahrnujte konečné zpětné lomítko.|Vyhrazené|  
|`MSBuildProjectDefaultTargets`|Úplný seznam cílů, které jsou zadány v `DefaultTargets` atributu `Project` elementu. Například následující `Project` element by měl `MSBuildDefaultTargets` hodnotu vlastnosti `A;B;C` :<br /><br /> `<Project DefaultTargets="A;B;C" >`|Vyhrazené|  
|`MSBuildProjectDirectory`|Absolutní cesta k adresáři, ve kterém je umístěn soubor projektu, například `C:\MyCompany\MyProduct` .<br /><br /> Do této vlastnosti nezahrnujte konečné zpětné lomítko.|Vyhrazené|  
|`MSBuildProjectDirectoryNoRoot`|Hodnota `MSBuildProjectDirectory` vlastnosti s výjimkou kořenové jednotky.<br /><br /> Do této vlastnosti nezahrnujte konečné zpětné lomítko.|Vyhrazené|  
|`MSBuildProjectExtension`|Přípona názvu souboru projektu, včetně období; například. proj.|Vyhrazené|  
|`MSBuildProjectFile`|Úplný název souboru projektu, včetně přípony názvu souboru; například MyApp. proj.|Vyhrazené|  
|`MSBuildProjectFullPath`|Absolutní cesta a úplný název souboru projektu, včetně přípony názvu souboru; například C:\MyCompany\MyProduct\MyApp.proj.|Vyhrazené|  
|`MSBuildProjectName`|Název souboru projektu bez přípony názvu souboru; například MyApp.|Vyhrazené|  
|`MSBuildStartupDirectory`|Absolutní cesta ke složce, ve které [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] je volána. Pomocí této vlastnosti můžete sestavit vše pod konkrétním bodem ve stromové struktuře projektu bez vytváření souborů adresářů. proj v každém adresáři. Místo toho máte pouze jeden projekt – například c:\traversal.proj, jak je znázorněno zde:<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> Chcete-li vytvořit libovolný bod stromu, zadejte:<br /><br /> `msbuild c:\traversal.proj`<br /><br /> Do této vlastnosti nezahrnujte konečné zpětné lomítko.|Vyhrazené|  
|`MSBuildThisFile`|Část názvu souboru a přípony souboru `MSBuildThisFileFullPath` .|Vyhrazené|  
|`MSBuildThisFileDirectory`|Část adresáře `MSBuildThisFileFullPath` .<br /><br /> V cestě zahrňte konečné zpětné lomítko.|Vyhrazené|  
|`MSBuildThisFileDirectoryNoRoot`|Část adresáře s `MSBuildThisFileFullPath` výjimkou kořenové jednotky.<br /><br /> V cestě zahrňte konečné zpětné lomítko.|Vyhrazené|  
|`MSBuildThisFileExtension`|Část s příponou názvu souboru `MSBuildThisFileFullPath` .|Vyhrazené|  
|`MSBuildThisFileFullPath`|Absolutní cesta k souboru projektu nebo cíle, který obsahuje cíl, na kterém je spuštěný.<br /><br /> Tip: v souboru cílů můžete zadat relativní cestu, která je relativní vzhledem k souboru cílů, a není relativní vzhledem k původnímu souboru projektu.|Vyhrazené|  
|`MSBuildThisFileName`|Část názvu souboru `MSBuildThisFileFullPath` bez přípony názvu souboru.|Vyhrazené|  
|`MSBuildToolsPath`|Instalační cesta [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] verze, která je přidružena k hodnotě `MSBuildToolsVersion` .<br /><br /> Do cesty nezahrnujte koncové zpětné lomítko.<br /><br /> Tuto vlastnost nelze přepsat.|Vyhrazené|  
|`MSBuildToolsVersion`|Verze sady [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] nástrojů, která se používá k sestavení projektu.<br /><br /> Poznámka: [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Sada nástrojů se skládá z úloh, cílů a nástrojů, které se používají k sestavení aplikace. Mezi tyto nástroje patří kompilátory, jako jsou csc.exe a vbc.exe. Další informace najdete v tématech [Sada nástrojů (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)a [standardní a vlastní konfigurace sady nástrojů](../msbuild/standard-and-custom-toolset-configurations.md).|Vyhrazené|  
  
## <a name="see-also"></a>Viz také  
 Vlastnosti nástroje MSBuild [reference](../msbuild/msbuild-reference.md) [MSBuild](msbuild-properties1.md)
