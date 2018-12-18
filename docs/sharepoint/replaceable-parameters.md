---
title: Nahraditelné parametry | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, tokens
- tokens [SharePoint development in Visual Studio]
- replaceable parameters [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, replaceable parameters
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload: office
ms.openlocfilehash: e79442ea42583f326f9cb59360777269c399b7a0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49879295"
---
# <a name="replaceable-parameters"></a>Nahraditelné parametry
  Nahraditelné parametry, nebo *tokeny*, je možné zadat hodnoty pro položky řešení služby SharePoint, skutečné hodnoty nejsou známá v době návrhu v souborech projektu. Jsou to funkce podobná standardní [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tokeny šablony. Další informace najdete v tématu [parametry šablony](/visualstudio/ide/template-parameters).  
  
## <a name="token-format"></a>Formát tokenu
 Tokeny začínají i končí znakem dolaru ($). Při nasazení, použití tokenů jsou nahradit skutečnými hodnotami při projektu je zabalená do balíčku řešení služby SharePoint (*.wsp* souboru). Například token **$SharePoint.Package.Name$** vyřešit na řetězec "Balíček SharePoint".  
  
## <a name="token-rules"></a>Token pravidla
 Následující pravidla platí pro tokeny:  
  
- Tokeny se dá nastavit kdekoli v řádku.  
  
- Tokeny nemůžou zahrnovat více řádků.  
  
- Stejný token může být zadán více než jednou na stejném řádku a ve stejném souboru.  
  
- Různé tokeny je možné zadat na stejném řádku.  
  
  Tokeny, které se neřídí tato pravidla jsou ignorovány a za následek upozornění nebo chyby.  
  
  Nahrazení tokeny pomocí řetězcové hodnoty se provádí ihned po manifestu transformace. Toto nahrazení umožňuje uživateli upravit manifestu šablony s tokeny.  
  
### <a name="token-name-resolution"></a>Název tokenu řešení
 Ve většině případů token přeloží na určitou hodnotu bez ohledu na to, kde se nachází. Ale pokud token má vztah k balíčku nebo funkce, hodnota tokenu závisí na ve kterém je obsažená. Například pokud je funkce v balíček pak se token `$SharePoint.Package.Name$` překládá na hodnotu "Balíček A." Pokud tatáž funkce je v balíček B, pak `$SharePoint.Package.Name$` přeloží na "Balíček B."  
  
## <a name="tokens-list"></a>Seznam tokenů
 V následující tabulce jsou uvedeny dostupné tokeny.  
  
|Název|Popis|  
|----------|-----------------|  
|$SharePoint.Project.FileName$|Název nadřazeného souboru, jako jsou například projektu *NewProj.csproj*.|  
|$SharePoint.Project.FileNameWithoutExtension$|Název obsahující soubor projektu bez přípony názvu souboru. Například "NewProj".|  
|$SharePoint.Project.AssemblyFullName$|Zobrazovaný název (silný název) obsahující projekt výstupního sestavení.|  
|$SharePoint.Project.AssemblyFileName$|Název nadřazeného projektu výstupního sestavení.|  
|$SharePoint.Project.AssemblyFileNameWithoutExtension$|Název projektu, která obsahuje výstupní sestavení bez přípony názvu souboru.|  
|$SharePoint.Project.AssemblyPublicKeyToken$|Token veřejného klíče z nadřazeného projektu výstupní sestavení, převedeno na řetězec. (16 znaků v "x2" šestnáctkovém formátu.)|  
|$SharePoint.Package.Name$|Název obsahující balíček.|  
|$SharePoint.Package.FileName$|Název souboru definice obsahující balíček.|  
|$SharePoint.Package.FileNameWithoutExtension$|Název souboru definice balíčku obsahující (bez přípony).|  
|$SharePoint.Package.Id$|Sharepointové ID nadřazeného balíčku. Pokud funkce se používá ve více než jeden balíček, tato hodnota se změní.|  
|$SharePoint.Feature.FileName$|Název souboru definice nadřazeného funkcí, jako například *Feature1.feature*.|  
|$SharePoint.Feature.FileNameWithoutExtension$|Název souboru definice funkce bez přípony názvu souboru.|  
|$SharePoint.Feature.DeploymentPath$|Název složky, která obsahuje funkci v balíčku. Tento token odpovídá vlastnosti "Cesta nasazení" v Návrháři funkce. Příkladem hodnoty je "Project1_Feature1".|  
|$SharePoint.Feature.Id$|Sharepointové ID funkce obsahující. Tento token, protože všechny tokeny úroveň funkcí, mohou být používány pouze soubory obsažené v balíčku prostřednictvím funkce, ne přímo do balíčku přidat mimo funkci.|  
|$SharePoint.ProjectItem.Name$|Název položky projektu (nikoli jeho název souboru), jako získané z **ISharePointProjectItem.Name**.|  
|$SharePoint.Type. \<GUID >. AssemblyQualifiedName$|Kvalifikovaný název sestavení odpovídající typ [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] tokenu. Formát [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] je malá písmena a odpovídá Guid.ToString("D") formátu (to znamená, že tomuto: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|  
|$SharePoint.Type. \<GUID >. Jméno a příjmení$|Úplný název typu odpovídající identifikátor GUID v tokenu. Formát čísla GUID je malá písmena a odpovídá Guid.ToString("D") formátu (to znamená, že tomuto: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|  
  
## <a name="add-extensions-to-the-token-replacement-file-extensions-list"></a>Přidejte rozšíření do seznamu přípon souborů náhradních tokenů
 Tokeny lze teoreticky podle všech souborů, které patří do projektu služby SharePoint položky obsažené v balíčku, ve výchozím nastavení, ale [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vyhledá tokeny pouze v balíčku soubory, soubory manifestu a soubory, které mají následující přípony:  
  
- [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]  
  
- ASCX  
  
- ASPX  
  
- Webová část  
  
- DWP  
  
  Tato rozšíření jsou definovány `<TokenReplacementFileExtensions>` element v souboru Microsoft.VisualStudio.SharePoint.targets umístěné v... \\< programové soubory\>\MSBuild\Microsoft\VisualStudio\v11.0\SharePointTools složky.  
  
  Dodatečné přípony souborů můžou, ale přidat do seznamu. Přidat `<TokenReplacementFileExtensions>` element na jakékoli PropertyGroup v souboru projektu služby SharePoint, který je definován před \<Import > souboru cíle služby SharePoint.  
  
> [!NOTE]  
>  Protože náhradních tokenů dochází po kompilaci projektu, neměli byste přidávat přípony souborů pro typy souborů, které jsou kompilovány jako *.cs*, *.vb* nebo *RESX*. Tokeny jsou nahrazena jenom v souborech, které nejsou zkompilovány.  
  
 Například, chcete-li přidat přípony názvů souborů (*.myextension* a *.yourextension*) do seznamu přípon názvů souborů náhradních tokenů, přidejte následující příkaz pro projekt (*.csproj* ) souboru:  
  
```xml  
<Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
    <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
.  
.  
.  
    <!-- Define the following property to add your extension to the list of token replacement file extensions.  -->  
<TokenReplacementFileExtensions>myextension;yourextension</TokenReplacementFileExtensions>  
</PropertyGroup>  
```  
  
 Rozšíření můžete přidat přímo do cíle (*.targets*) soubor. Ale přidání rozšíření mění seznamu rozšíření pro všechny projekty SharePoint zabalené v místním systému, ne jenom vlastní. Toto rozšíření může být vhodné, jsou výhradní pro vývojáře v systému nebo pokud to vyžaduje většina vašich projektů. Ale protože je specifické pro systém, tento přístup není přenosný a proto je vhodné přidat žádná rozšíření do souboru projektu místo.  
  
## <a name="see-also"></a>Viz také:
 [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
