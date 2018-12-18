---
title: Vlastnosti nástroje MSBuild podporované službou SharePoint | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, MSBuild properties
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1695a23ba9dddc27a37f23c714678fe6b779d328
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35675873"
---
# <a name="msbuild-properties-supported-by-sharepoint"></a>Vlastnosti nástroje MsBuild podporované službou SharePoint
  Žádné [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] vlastnosti definované v souboru Microsoft.VisualStudio.SharePoint.targets, soubor projektu nebo uživatelský soubor projektu je možné v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektů služby SharePoint. Kromě společné [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] vlastnosti zadaný v projektu služby SharePoint definuje další vlastnosti, které jsou specifické pro projekty SharePoint.  
  
 Seznam běžných [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] vlastnosti, viz [obecné vlastnosti projektu nástroje MSBuild](http://go.microsoft.com/fwlink/?LinkID=168687). Úplný seznam vlastností podporuje svůj oblíbený programovací jazyk, najdete *.targets* souboru, soubor projektu (*.csproj* nebo *.vbproj*), nebo uživatel projektu souboru () *csproj.user* nebo *. vbproj.user*).  
  
## <a name="msbuild-properties-specific-to-sharepoint"></a>Vlastnosti nástroje MsBuild specifické pro službu SharePoint
 Následující tabulka uvádí [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] vlastnosti, které platí konkrétně do projektů služby SharePoint v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Existují další vlastnosti, ale jsou pro interní použití.  
  
|Název vlastnosti|Popis|  
|-------------------|-----------------|  
|SharePointSiteUrl|Řetězec, který představuje [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] na web služby SharePoint.|  
|SandboxedSolution|Logická hodnota určující, zda je řešení řešení v izolovaném prostoru.|  
|ActiveDeploymentConfiguration|Konfigurace aktivního nasazení.|  
|IncludeAssemblyInPackage|Logická hodnota, která určuje, zda je sestavení součástí souboru balíčku.|  
|PreDeploymentCommand|Řetězcovou hodnotu, která představuje příkazu ke spuštění v kroku příkaz před nasazením.|  
|PostDeploymentCommand|Řetězcovou hodnotu, která představuje příkazu ke spuštění v kroku příkaz po nasazení.|  
|CustomBeforeSharePointTargets|Řetězec, který představuje cestu [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] soubor cílů. Pokud soubor cílů existuje a je definován, je importován před všechny cíle dat služby SharePoint. Tato vlastnost umožňuje přizpůsobit proces balíčku podle předběžné definování balení souvisejících vlastností beze změny souboru dodané cíle služby SharePoint, ale soubor cílů stále platí pro všechny projekty služby SharePoint.|  
|CustomAfterSharePointTargets|Řetězec, který představuje cestu [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] soubor cílů. Pokud soubor cílů existuje a je definován, je po všech importovaných dat cíle služby SharePoint. Tato vlastnost umožňuje přizpůsobit proces balíčku tak, že přepíšete balení souvisejících vlastností a cílů, aniž byste museli upravovat uvidíte soubor cílů SharePoint, ale soubor cílů stále platí pro všechny projekty služby SharePoint.|  
|LayoutPath|Řetězec, který představuje kořenový adresář, kde jednotlivé soubory, které chcete zabalit jsou dočasně umístěny před jejich přidání do *.wsp* souboru. Tato cesta se dá vědět, pokud přepíšete BeforeLayout a AfterLayout cíle přidat, odebrat nebo změnit soubory zabalit, protože ho můžete změnit obsah *.wsp* souboru.|  
|BasePackagePath|Řetězec, který představuje složku, ve kterém je umístí balíček. Tato hodnota používá výstupního adresáře projektu, například Bin\Debug.|  
|PackageExtension|Řetězec, který představuje příponu názvu souboru připojit k balíčku. Výchozí hodnota je soubor wsp.|  
|AssemblyDeploymentTarget|Řetězec, který představuje umístění, které se nasadí sestavení projektu na serveru SharePoint. Jeho hodnota je GlobalAssemblyCache (výchozí) nebo webovou aplikaci. Tuto vlastnost můžete nastavit také v okně Vlastnosti.|  
|Packagewithvalidation Msbuildu|Logická hodnota určující, zda ověření je provedeno před balení. Tato vlastnost umožňuje ignorovat chyby ověřování při vytváření balíčků.|  
|ValidatePackageDependsOn|Řetězec, který definuje další cílů ke spuštění před cílem ValidatePackage.|  
|TokenReplacementFileExensions|Řetězec, který definuje soubory, které mají jejich tokeny nahrazena v průběhu balení.|  
  
## <a name="use-msbuild-properties-in-the-properties-page"></a>Na stránce vlastností použijte vlastnosti nástroje MsBuild
 Zajišťuje tak flexibilitu, namísto použití pevně zakódované řetězce v **příkazový řádek před nasazením** a **příkazový řádek po nasazení** polí na stránce Vlastnosti služby SharePoint můžete použít služby SharePoint vlastnosti jako argumenty. Například místo určení konkrétní [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] řetězec pro Sharepointový web, můžete místo toho použít `$(SharePointSiteUrl)`.  
  
> [!NOTE]  
>  Můžete použít buď [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] syntaxi proměnných `$(` *propertyName* `)` nebo syntaxi proměnných prostředí `%` *propertyName* `%` můžete zadat vlastnost.  
  
## <a name="see-also"></a>Viz také:
 [Referenční dokumentace nástroje MSBuild](/visualstudio/msbuild/msbuild-reference)  
  