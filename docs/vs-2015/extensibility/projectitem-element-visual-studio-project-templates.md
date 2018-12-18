---
title: ProjectItem – Element (šablony projektů Visual Studio) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- ProjectItem element [Visual Studio project templates]
- <ProjectItem> element [Visual Studio project templates]
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bca26cba66169758aa882535c07846cfa451d172
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737070"
---
# <a name="projectitem-element-visual-studio-project-templates"></a>ProjectItem – element (šablony projektů Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Určuje soubor, který je součástí šablony projektu.  
  
> [!NOTE]
>  `ProjectItem` Element přijímá různé atributy v závislosti na tom, jestli je šablona pro projekt nebo položku. Toto téma vysvětluje, `ProjectItem` – element pro šablony projektů. Pro vysvětlení, `ProjectItem` – element pro šablony položek, naleznete v tématu [ProjectItem – Element (šablony položek aplikace Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md).  
  
 \<Vstemplate – >  
 \<TemplateContent – >  
 \<Project>  
 \<ProjectItem – >  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<ProjectItem  
    TargetFileName="TargetFileName.ext"  
    ReplaceParameters="true/false"  
    OpenInEditor="true/false"  
    OpenInWebBrowser="true/false"  
    OpenInHelpBrowser="true/false"  
    OpenOrder="Value">  
        FileName.ext  
</ProjectItem>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující oddíly popisují atributy a podřízené a nadřazené elementy.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`TargetFileName`|Nepovinný atribut.<br /><br /> Určuje název a cesta k položce projektu, když je projekt vytvořen z šablony. Tento atribut je užitečné pro vytvoření adresářové struktury liší od struktury adresářů v souboru ZIP šablony, nebo k vytvoření názvu položky pomocí nahrazení parametru.|  
|`ReplaceParameters`|Nepovinný atribut.<br /><br /> Logická hodnota určující, zda položka má hodnoty parametrů, které musí být nahrazen, když je projekt vytvořen z šablony. Výchozí hodnota je `false`.|  
|`OpenInEditor`|Nepovinný atribut.<br /><br /> Logická hodnota, která určuje, zda položka by měl být otevřen v jeho příslušných editoru v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] při vytvoření projektu ze šablony.<br /><br /> `OpenInWebBrowser` a `OpenInHelpBrowser` atributy se ignorují u položky s `OpenInEditor` hodnotu `true`.<br /><br /> Výchozí hodnota je `false`.|  
|`OpenInWebBrowser`|Nepovinný atribut.<br /><br /> Logická hodnota, která určuje, zda položky by měla otevřít webový prohlížeč při vytvoření projektu ze šablony.<br /><br /> Pouze soubory HTML a textové soubory, které jsou místní pro projekt lze otevřít ve webovém prohlížeči. Externí adresy URL nelze otevřít pomocí tohoto atributu.<br /><br /> Výchozí hodnota je `false`.|  
|`OpenInHelpBrowser`|Nepovinný atribut.<br /><br /> Logická hodnota, která určuje, zda položka by měl být otevřen v aplikaci Help viewer, když je projekt vytvořen z šablony.<br /><br /> Pouze soubory HTML a textové soubory, které jsou místní pro projekt lze otevřít v prohlížeči. Externí adresy URL nelze otevřít pomocí tohoto atributu.<br /><br /> Výchozí hodnota je `false`.|  
|`OpenOrder`|Nepovinný atribut.<br /><br /> Určuje číselnou hodnotu, která představuje pořadí, položky se otevřou v jejich příslušných editorech. Všechny hodnoty musí být násobky 10. Položky s vyšší `OpenOrder` hodnoty jsou otevřen jako první.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[Projekt](../extensibility/project-element-visual-studio-templates.md)|Určuje soubory nebo adresáře přidat do projektu.|  
  
## <a name="text-value"></a>Textová hodnota  
 Je vyžadována textová hodnota.  
  
 A `string` , která představuje název nebo cesta k souboru v souboru ZIP šablony.  
  
## <a name="remarks"></a>Poznámky  
 `ProjectItem` je volitelný podřízený `Project`.  
  
 `TargetFileName` Atribut lze použít k vytvoření adresářové struktury liší od struktury adresářů v souboru ZIP šablony. Například pokud soubor `MyFile.vb` existuje v kořenovém adresáři soubor ZIP šablony, ale chcete soubor, který má být umístěn v adresáři s názvem `CustomFiles` ve všech projektech ze šablony, můžete využít následující kód XML:  
  
```  
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>  
```  
  
 `TargetFileName` Atribut lze také přejmenovat soubory, které obsahují mezinárodní znaky v jejich názvy souborů. Například soubor ZIP šablony nemůže obsahovat názvy souborů se znaky Unicode, takže ho musí přejmenovat, předtím, než může být zkomprimovány do souboru .zip. `TargetFileName` Atribut je možné nastavit název souboru zpět na původní název souboru ve formátu Unicode.  
  
 `TargetFileName` Atribut lze použít také k přejmenování souborů s parametry. Následující postup vysvětluje, jak přejmenovat soubor `MyFile.vb`, která existuje v kořenovém adresáři souboru ZIP šablony s názvem souboru na základě názvu projektu.  
  
### <a name="to-rename-files-with-parameters"></a>Přejmenujte soubory s parametry  
  
1.  Použijte následující kód XML v souboru .vstemplate:  
  
    ```  
    <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>  
    ```  
  
2.  Otevřete soubor projektu (.vbproj pro [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projektu) v textovém editoru nebo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
3.  Vyhledejte řádek v souboru projektu, který vypadá podobně jako následující kód XML:  
  
    ```  
    <Compile Include="MyFile.vb">  
    ```  
  
4.  Řádek kódu nahraďte následující kód XML:  
  
    ```  
    <Compile Include="$safeprojectname$.vb">  
    ```  
  
     Pokud je projekt je vytvořen z této šablony, názvu souboru bude vycházet zadaný název uživatele v **nový projekt** dialogovém okně se všemi problematické znaky a byly odebrány mezery. Další informace najdete v tématu [parametry šablony](../ide/template-parameters.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje metadata pro šablona projektu pro [!INCLUDE[csprcs](../includes/csprcs-md.md)] aplikace.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
            <ProjectItem ReplaceParameters="true">Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na schéma šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)   
 [Parametry šablony](../ide/template-parameters.md)   
 [ProjectItem – element (šablony sady Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)

