---
title: Nástroj MSBuild vyhrazené a známé vlastnosti | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 6f121701ff5d463c852f386f012fe22a7a46d43e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49225404"
---
# <a name="msbuild-reserved-and-well-known-properties"></a>Vyhrazené a známé vlastnosti nástroje MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] poskytuje sadu předdefinovaných vlastností, které ukládají informace o souboru projektu a [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] binární soubory. Tyto vlastnosti jsou vyhodnocovány stejným způsobem jako ostatní [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] vlastnosti. Chcete-li například použít `MSBuildProjectFile` vlastnost, typ `$(MSBuildProjectFile)`.  
  
 Nástroj MSBuild používá hodnoty v následující tabulce pro předdefinování rezervovaných a dobře známých vlastností. Rezervované vlastnosti nemohou být potlačeny, ale dobře známé vlastnosti lze přepsat pomocí nazvanými vlastnostmi prostředí, globálními vlastnostmi nebo vlastnostmi, které jsou deklarovány v souboru projektu.  
  
## <a name="reserved-and-well-known-properties"></a>Vyhrazené a známé vlastnosti  
 V následující tabulce jsou popsány [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] předdefinované vlastnosti.  
  
|Vlastnost|Popis|Vyhrazené nebo známé|  
|--------------|-----------------|-----------------------------|  
|`MSBuildBinPath`|Absolutní cesta ke složce kde [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] jsou umístěny binární soubory, které jsou právě používány (například C:\Windows\Microsoft.Net\Framework\\*číslo_verze*). Tato vlastnost je užitečná, pokud máte k odkazování na soubory v [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] adresáře.<br /><br /> Nezahrnují konečné zpětné lomítko pro tuto vlastnost.|Rezervováno|  
|`MSBuildExtensionsPath`|Zavedena v rozhraní .NET Framework 4: není žádný rozdíl mezi výchozími hodnotami `MSBuildExtensionsPath` a `MSBuildExtensionsPath32`. Můžete nastavit proměnné prostředí `MSBUILDLEGACYEXTENSIONSPATH` na nenulovou hodnotu, chcete-li povolit chování výchozí hodnoty `MSBuildExtensionsPath` v dřívějších verzích.<br /><br /> V rozhraní .NET Framework 3.5 a starších, výchozí hodnota `MSBuildExtensionsPath` odkazuje na cestu podsložky MSBuild ve složce \Program Files\ nebo \Program (x86) Files, v závislosti na počtu bitů aktuálního procesu. Například pro 32bitový proces na 64bitovém počítači, tato vlastnost odkazuje na složku \Program Files (x86). Pro 64bitový proces na 64bitovém počítači tato vlastnost odkazuje na složku \Program Files.<br /><br /> Nezahrnují konečné zpětné lomítko pro tuto vlastnost.<br /><br /> Toto umístění je vhodné místo pro vlastní cílové soubory. Například cílové soubory může instalovat v \Program Files\MSBuild\MyFiles\Northwind.targets a následně importovány do projektových souborů pomocí tohoto kódu XML:<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>`|Známé|  
|`MSBuildExtensionsPath32`|Cesta [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] podsložku \Program Files nebo složku \Program Files (x86). Tato cesta vždy odkazuje na složku 32-bit \Program Files pro 32bitové počítače a \Program soubory (x86) na 64bitovém počítači. Viz také `MSBuildExtensionsPath` a `MSBuildExtensionsPath64`.<br /><br /> Nezahrnují konečné zpětné lomítko pro tuto vlastnost.|Známé|  
`MSBuildExtensionsPath64`|Cesta [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] podsložky ve složce \Program Files. Pro 64bitový počítač tato cesta vždy odkazuje na složku \Program Files. Pro 32bitový počítač tato cesta je prázdná. Viz také `MSBuildExtensionsPath` a `MSBuildExtensionsPath32`.<br /><br /> Nezahrnují konečné zpětné lomítko pro tuto vlastnost.|Známé|  
|`MSBuildLastTaskResult`|`true` Pokud byl předchozí úkol dokončen bez chyb (i kdyby to byla upozornění), nebo `false` Pokud předchozí úloha obsahovala chyby. Obvykle když dojde k chybě v úloze, chyba je poslední věcí, ke které dochází v daném projektu. Hodnota této vlastnosti tedy nikdy `false`, s výjimkou v těchto scénářích:<br /><br /> – Když `ContinueOnError` atribut [Task – Element (MSBuild)](../msbuild/task-element-msbuild.md) je nastavena na `WarnAndContinue` (nebo `true`) nebo `ErrorAndContinue`.<br /><br /> – Když `Target` má [onerror – Element (MSBuild)](../msbuild/onerror-element-msbuild.md) jako podřízený prvek.|Rezervováno|  
|`MSBuildNodeCount`|Maximální počet souběžných procesů, které se používají při sestavování. Jedná se o hodnotu, která jste zadali pro **/maxcpucount** na příkazovém řádku. Pokud jste zadali **/maxcpucount** bez zadání hodnoty, pak `MSBuildNodeCount` určuje počet procesorů v počítači. Další informace najdete v tématu [Reference k příkazovému řádku](../msbuild/msbuild-command-line-reference.md) a [sestavování více projektů současně](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).|Rezervováno|  
|`MSBuildProgramFiles32`|Umístění složky 32bitových programů; například `C:\Program Files (x86)`.<br /><br /> Nezahrnují konečné zpětné lomítko pro tuto vlastnost.|Rezervováno|  
|`MSBuildProjectDefaultTargets`|Úplný seznam cílů, které jsou určené v `DefaultTargets` atribut `Project` elementu. Například následující `Project` element bude mít `MSBuildDefaultTargets` hodnotou vlastnosti `A;B;C`:<br /><br /> `<Project DefaultTargets="A;B;C" >`|Rezervováno|  
|`MSBuildProjectDirectory`|Absolutní cesta adresáře, kde je soubor projektu umístěn, například `C:\MyCompany\MyProduct`.<br /><br /> Nezahrnují konečné zpětné lomítko pro tuto vlastnost.|Rezervováno|  
|`MSBuildProjectDirectoryNoRoot`|Hodnota `MSBuildProjectDirectory` vlastnost, s výjimkou kořenové jednotky.<br /><br /> Nezahrnují konečné zpětné lomítko pro tuto vlastnost.|Rezervováno|  
|`MSBuildProjectExtension`|Příponu názvu souboru projektu, včetně tečky; například souborů .proj.|Rezervováno|  
|`MSBuildProjectFile`|Celý název souboru projektu, včetně přípony názvu souboru; například MyApp.proj.|Rezervováno|  
|`MSBuildProjectFullPath`|Absolutní cesta a celý název souboru projektu, včetně přípony názvu souboru; například C:\MyCompany\MyProduct\MyApp.proj.|Rezervováno|  
|`MSBuildProjectName`|Název souboru bez přípony názvu souboru; v souboru projektu například MyApp.|Rezervováno|  
|`MSBuildStartupDirectory`|Absolutní cesta ke složce kde [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] je volána. Pomocí této vlastnosti můžete sestavit vše pod určitým bodem ve stromu projektu bez vytváření souborů dirs.proj v každém adresáři. Místo toho máte pouze jeden projekt, například c:\traversal.proj, jak je znázorněno zde:<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> Pokud chcete sestavit jakýkoli bod ve stromové struktuře, zadejte:<br /><br /> `msbuild c:\traversal.proj`<br /><br /> Nezahrnují konečné zpětné lomítko pro tuto vlastnost.|Rezervováno|  
|`MSBuildThisFile`|Název souboru a část přípony souboru `MSBuildThisFileFullPath`.|Rezervováno|  
|`MSBuildThisFileDirectory`|Část adresáře `MSBuildThisFileFullPath`.<br /><br /> Zahrňte v cestě konečné zpětné lomítko.|Rezervováno|  
|`MSBuildThisFileDirectoryNoRoot`|Část adresáře `MSBuildThisFileFullPath`, s výjimkou kořenové jednotky.<br /><br /> Zahrňte v cestě konečné zpětné lomítko.|Rezervováno|  
|`MSBuildThisFileExtension`|Část přípony názvu souboru z `MSBuildThisFileFullPath`.|Rezervováno|  
|`MSBuildThisFileFullPath`|Absolutní cesta souboru projektu nebo cílů, který obsahuje cíl, na kterém běží.<br /><br /> Tip: Lze zadat relativní cestu v souboru cílů, která je relativní vzhledem k souboru cílů a ne vzhledem k původnímu souboru projektu.|Rezervováno|  
|`MSBuildThisFileName`|Část názvu souboru `MSBuildThisFileFullPath`, bez přípony názvu souboru.|Rezervováno|  
|`MSBuildToolsPath`|Instalační cesta [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] verzi, která je přidružená hodnota `MSBuildToolsVersion`.<br /><br /> Nezahrnují v cestě konečné zpětné lomítko.<br /><br /> Tuto vlastnost nelze přepsat.|Rezervováno|  
|`MSBuildToolsVersion`|Verze [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] nástrojů, která se používá k sestavení projektu.<br /><br /> Poznámka: [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] sada nástrojů obsahuje úkoly, cíle a nástroje, které slouží k sestavení aplikace. Mezi tyto nástroje patří kompilátory jako csc.exe a vbc.exe. Další informace najdete v tématu [sada nástrojů (atribut ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md), a [standardní a vlastní konfigurace sady nástrojů](../msbuild/standard-and-custom-toolset-configurations.md).|Rezervováno|  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md) [vlastnosti nástroje MSBuild](msbuild-properties1.md)



