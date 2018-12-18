---
title: Sada nástrojů MSBuild (atribut ToolsVersion) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, multitargeting
- targeting a specific .NET framework [MSBuild]
- MSBuild, targeting a specific .NET framework
- multitargeting [MSBuild]
ms.assetid: 40040ee7-4620-4043-a6d8-ccba921421d1
caps.latest.revision: 33
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd516501acfc7690c12a253adc5da6cf163b5592
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49851826"
---
# <a name="msbuild-toolset-toolsversion"></a>Sada nástrojů MSBuild (atribut ToolsVersion)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Nástroj MSBuild používá sada nástrojů pro úkoly, cíle a nástrojů k sestavení aplikace. Sada nástrojů MSBuild obvykle zahrnuje microsoft.common.tasks souboru, soubor cílů microsoft.common.targets a kompilátory jako csc.exe a vbc.exe. Většina nástrojů je možné pro kompilaci aplikací pro více než jednu verzi rozhraní .NET Framework a více než jednu platformu systému. Sada nástrojů MSBuild 2.0 je však možné cílit na rozhraní .NET Framework 2.0.  
  
## <a name="toolsversion-attribute"></a>ToolsVersion – atribut  
 Určení sady nástrojů v `ToolsVersion` atribut na [projektu](../msbuild/project-element-msbuild.md) element v souboru projektu. Následující příklad určuje, že projekt by měly být sestaveny pomocí sady nástrojů MSBuild 12.0.  
  
```  
<Project ToolsVersion="12.0" ... </Project>  
```  
  
## <a name="how-the-toolsversion-attribute-works"></a>Jak funguje atribut ToolsVersion  
 Při vytváření projektu v sadě Visual Studio nebo upgrade existujícího projektu, atribut s názvem `ToolsVersion` automaticky zahrnut v projektu soubor a jeho hodnota odpovídá verzi nástroje MSBuild, který je součástí edici sady Visual Studio. Další informace najdete v tématu [cílení na konkrétní verzi rozhraní .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).  
  
 Když `ToolsVersion` hodnota je definována v souboru projektu, MSBuild používá tuto hodnotu k určení hodnoty vlastnosti sady nástrojů, které jsou k dispozici do projektu. Jedna sada nástrojů vlastnost `$(MSBuildToolsPath)`, který určuje cestu k nástrojům rozhraní .NET Framework. Pouze vlastnosti sady nástrojů (nebo `$(MSBuildBinPath)`), je povinný.  
  
 Spouští se v sadě Visual Studio 2013, sada nástrojů MSBuild verze je stejná jako číslo verze sady Visual Studio. Výchozí hodnota nástroje MSBuild je touto sadou nástrojů v sadě Visual Studio a na příkazovém řádku, bez ohledu na verzi sady nástrojů zadané v souboru projektu.  Toto chování lze přepsat pomocí příznaku /ToolsVersion. Další informace najdete v tématu [přepsání nastavení ToolsVersion](../msbuild/overriding-toolsversion-settings.md).  
  
 V následujícím příkladu, MSBuild vyhledá soubor Microsoft.CSharp.targets pomocí `MSBuildToolsPath` rezervované vlastnosti.  
  
```  
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />  
```  
  
 Můžete upravit hodnotu `MSBuildToolsPath` tak, že definujete vlastní sady nástrojů. Další informace najdete v tématu [standardní a vlastní konfigurace sady nástrojů](../msbuild/standard-and-custom-toolset-configurations.md)  
  
 Při sestavení řešení na příkazovém řádku a zadejte `ToolsVersion` pro msbuild.exe, všechny projekty a jejich závislosti projektu na projekt jsou vytvořeny podle, který `ToolsVersion`i v případě jednotlivých projektů v řešení určuje vlastního `ToolsVersion`. Chcete-li definovat `ToolsVersion` hodnoty na základě jednotlivých projektů, naleznete v tématu [přepsání nastavení ToolsVersion](../msbuild/overriding-toolsversion-settings.md).  
  
 `ToolsVersion` Atribut je použit také pro projekt migrace. Například pokud otevřete projekt sady Visual Studio 2008 v sadě Visual Studio 2010 soubor projektu je aktualizován zahrnout ToolsVersion = "4.0". Pokud se pak pokusíte otevřít tento projekt v sadě Visual Studio 2008, nedokáže rozpoznat upgradovaný `ToolsVersion` a proto vytvoří projekt, jako by šlo by byl atribut stále nastavený na hodnotu 3.5.  
  
 Visual Studio 2010 a Visual Studio 2012 používat k hodnotě ToolsVersion 4.0. Visual Studio 2013 se používá k hodnotě ToolsVersion 12.0. V řadě případů můžete otevřít projekt ve všech třech verzích sady Visual Studio bez úprav. Vždy používá správnou sadu nástrojů Visual Studio, ale se zobrazí upozornění, pokud je verze použitá se neshoduje s verzí v souboru projektu. V téměř všech případech se toto upozornění je neškodný, jsou kompatibilní ve většině případů sad nástrojů.  
  
 Sub – sady nástrojů, které jsou popsány dále v tomto tématu, povolit MSBuild automaticky přepnout, která sadu nástrojů pro použití podle kontextu, ve kterém je spuštěn sestavení. Například nástroj MSBuild používá novější sadu nástrojů při spuštění v sadě Visual Studio 2012 než při spuštění v sadě Visual Studio 2010, bez nutnosti explicitně změny souboru projektu. Další informace najdete v tématu [provádění vlastní projekty podporující verze](../misc/making-custom-projects-version-aware.md).  
  
## <a name="toolset-implementation"></a>Implementace sady nástrojů  
 Implementujte sadu nástrojů tak, že vyberete cesty různých nástrojů, cíle a úlohy, které tvoří sadu nástrojů. Nástroje v sadu nástrojů, která definuje MSBuild přicházet z těchto zdrojů:  
  
- Složku rozhraní.NET Framework.  
  
- Další spravované nástroje.  
  
  Spravované nástroje zahrnují ResGen.exe a TlbImp.exe.  
  
  Nástroj MSBuild poskytuje dva způsoby přístupu k sady nástrojů:  
  
- Pomocí vlastností sady nástrojů  
  
- S použitím <xref:Microsoft.Build.Utilities.ToolLocationHelper> metody  
  
  Vlastnosti nástrojů pro zadání cesty nástroje. Nástroj MSBuild používá hodnoty `ToolsVersion` atributu v souboru projektu vyhledejte odpovídající klíče registru a poté použije informace v klíči registru pro nastavení vlastností sady nástrojů. Například pokud `ToolsVersion` má hodnotu `12.0`, MSBuild nastaví vlastnosti sady nástrojů podle tohoto klíče registru: HKLM\Software\Microsoft\MSBuild\ToolsVersions\12.0.  
  
  Toto jsou vlastnosti sady nástrojů:  
  
- `MSBuildToolsPath` Určuje cestu k MSBuild binární soubory.  
  
- `SDK40ToolsPath` Určuje cestu k další spravované nástroje pro MSBuild 4.x (které by mohly být 4.0 nebo 4.5).  
  
- `SDK35ToolsPath` Určuje cestu k další spravované nástroje pro MSBuild 3.5.  
  
  Alternativně můžete určit sadu nástrojů prostřednictvím kódu programu pomocí volání metody <xref:Microsoft.Build.Utilities.ToolLocationHelper> třídy. Třída zahrnuje tyto metody:  
  
- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFramework%2A> vrátí cestu ke složce rozhraní .NET Framework.  
  
- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkFile%2A> vrátí cestu k souboru ve složce rozhraní .NET Framework.  
  
- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdk%2A> vrátí cestu spravovaných nástroje složky.  
  
- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdkFile%2A> vrátí cestu souboru, který je obvykle umístěn ve složce Nástroje pro spravované.  
  
- <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToBuildTools%2A> vrátí cestu nástroje sestavení.  
  
### <a name="sub-toolsets"></a>Dílčí sady nástrojů  
 Jak je popsáno výše v tomto tématu, nástroj MSBuild používá klíč registru pro zadání cesty základní nástroje. Pokud klíč podklíč, nástroj MSBuild používá pro zadání cesty dílčí, který obsahuje další nástroje. V takovém případě sada nástrojů je definována kombinací definice vlastností, které jsou definovány v obou klíčů.  
  
> [!NOTE]
>  Pokud názvy vlastností sady nástrojů kolidují, přepíše hodnotu, která je definována pro podklíče cestu hodnotu, která je definována pro kořenovou cestu klíče.  
  
 Dílčí sady nástrojů aktivní, z nichž se nachází `VisualStudioVersion` vlastnost sestavení. Tato vlastnost může mít jednu z těchto hodnot:  
  
- "10.0" Určuje dílčí rozhraní .NET Framework 4  
  
- "11.0" Určuje dílčí rozhraní .NET Framework 4.5  
  
- "12,0" Určuje dílčí rozhraní .NET Framework 4.5.1  
  
  Sub – sady nástrojů 10.0 a 11.0 je třeba použít pomocí parametru ToolsVersion 4.0. V novějších verzích by měl odpovídat dílčí verze a ToolsVersion.  
  
  Během sestavení, nástroj MSBuild automaticky zjistí a nastaví výchozí hodnoty `VisualStudioVersion` vlastnosti, pokud je ještě není definované.  
  
  Přetížení pro poskytuje nástroj MSBuild `ToolLocationHelper` metody, které aplikacím dodávají `VisualStudioVersion` výčtu hodnotu jako parametr  
  
  Dílčí sady nástrojů byla zavedena v rozhraní .NET Framework 4.5.  
  
## <a name="see-also"></a>Viz také  
 [Standardní a vlastní konfigurace sady nástrojů](../msbuild/standard-and-custom-toolset-configurations.md)   
 [Cílení na více verzí](../msbuild/msbuild-multitargeting-overview.md)



