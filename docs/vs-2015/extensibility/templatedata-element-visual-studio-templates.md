---
title: TemplateData – Element (šablony sady Visual Studio) | Dokumentace Microsoftu
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
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateData
helpviewer_keywords:
- TemplateData element [Visual Studio project templates]
ms.assetid: db17ec9b-bfdf-46b1-bbe7-5ccc140056e2
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 29b481c8560e47dff4c4fadca9dab869e4f5b361
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51743768"
---
# <a name="templatedata-element-visual-studio-templates"></a>TemplateData – element (šablony sady Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rozděluje šablonu a definuje, jak se zobrazuje **nový projekt** nebo **přidat novou položku** dialogové okno.  
  
 \<Vstemplate – >  
 \<TemplateData >  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<TemplateData>  
    <Name> ... </Name>  
    <Description> ... </Description>  
    <Icon> ... </Icon>  
    <ProjectType> ... </ProjectType>  
    ...  
</TemplateData>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[Jméno](../extensibility/name-element-visual-studio-templates.md)|Požadovaný element.<br /><br /> Určuje název šablony, protože se zobrazí buď **nový projekt** nebo **přidat novou položku** dialogové okno.|  
|[Popis](../extensibility/description-element-visual-studio-templates.md)|Požadovaný element.<br /><br /> Určuje popis šablony, protože se zobrazí buď **nový projekt** nebo **přidat novou položku** dialogové okno.|  
|[Ikona](../extensibility/icon-element-visual-studio-templates.md)|Požadovaný element.<br /><br /> Určuje cestu a název souboru, který slouží jako ikona, která se zobrazí v jednom souboru obrázku **nový projekt** nebo **přidat novou položku** dialogovém okně pro šablonu.|  
|[ProjectType](../extensibility/projecttype-element-visual-studio-templates.md)|Požadovaný element.<br /><br /> Rozděluje šablonu projektu tak, aby se objevila pod zadané skupiny v rámci **nový projekt** dialogové okno.|  
|[ProjectSubType –](../extensibility/projectsubtype-element-visual-studio-templates.md)|Volitelný element.<br /><br /> Klasifikuje šablona projektu tak, aby se objevila pod zadanou podkategorie v **nový projekt** dialogové okno.|  
|[TemplateId –](../extensibility/templateid-element-visual-studio-templates.md)|Volitelný element.<br /><br /> Určuje ID šablony.|  
|[Templategroupid –](../extensibility/templategroupid-element-visual-studio-templates.md)|Volitelný element.<br /><br /> Určuje ID šablony skupiny.|  
|[Pořadí řazení](../extensibility/sortorder-element-visual-studio-templates.md)|Volitelný element.<br /><br /> Určuje hodnotu, která slouží k uspořádání šablony, mezi další šablony ve stejné kategorii, jak se zobrazí v buď **nový projekt** nebo **přidat novou položku** dialogové okno.|  
|[Createnewfolder –](../extensibility/createnewfolder-element-visual-studio-templates.md)|Volitelný element.<br /><br /> Určuje, zda nadřazené složky se vytvoří při vytváření instance projektu.|  
|[Defaultname –](../extensibility/defaultname-element-visual-studio-templates.md)|Volitelný element.<br /><br /> Určuje název, který vygeneruje systém projektu sady Visual Studio pro projekt nebo položku při jeho vytvoření.|  
|[Providedefaultname –](../extensibility/providedefaultname-element-visual-studio-templates.md)|Volitelný element.<br /><br /> Určuje, zda systém projektu sady Visual Studio vygeneruje výchozí název pro projekt nebo položku při jeho vytvoření.|  
|[PromptForSaveOnCreation –](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md)|Volitelný element.<br /><br /> Určuje, zda je možné vytvořit projekt jako dočasný projekt.|  
|[Enablelocationbrowsebutton –](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md)|Volitelný element.<br /><br /> Určuje, zda **Procházet** tlačítko je k dispozici v **nový projekt** dialogovém okně tak, aby uživatelé mohli snadno upravovat výchozí adresář, ve kterém je uložený nový projekt.|  
|[Skryté](../extensibility/hidden-element-visual-studio-templates.md)|Volitelný element.<br /><br /> Určuje, jestli se šablona zobrazuje v buď **nový projekt** nebo **přidat novou položku** dialogové okno.|  
|[NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)|Volitelný element.<br /><br /> Určuje počet nadřazených kategoriích, které se zobrazí v šabloně **nový projekt** dialogové okno.|  
|[Locationfieldmruprefix –](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md)|Volitelný element.|  
|[Locationfield –](../extensibility/locationfield-element-visual-studio-project-templates.md)|Volitelný element.<br /><br /> Určuje, zda je či není **umístění** textové pole **nový projekt** dialogové okno je povoleno, zakázané nebo skrytý pro šablonu projektu.|  
|[Requiredframeworkversion –](../extensibility/requiredframeworkversion-element-visual-studio-templates.md)|Volitelný element.<br /><br /> Pomocí tohoto prvku, pokud šablony podporuje pouze konkrétní minimální verzi a novější verze, pokud je libovolná z rozhraní .NET Framework.|  
|[Supportsmasterpage –](../extensibility/supportsmasterpage-element-visual-studio-templates.md)|Volitelný element.<br /><br /> Určuje, zda šablona podporuje stránku předlohy pro webové projekty.|  
|[Supportscodeseparation –](../extensibility/supportscodeseparation-element-visual-studio-templates.md)|Volitelný element.<br /><br /> Určuje, jestli podporuje šablony oddělení kódu nebo použití modelu code-behind model stránky, pro webové projekty.|  
|[Supportslanguagedropdown –](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md)|Volitelný element.<br /><br /> Určuje, jestli je stejný jako pro řadu jazyků šablony a zda **jazyk** možnost je k dispozici **nový projekt** dialogové okno.|  
|[Targetplatformname –](../extensibility/targetplatformname-element-visual-studio-templates.md)|Volitelný element.<br /><br /> Určuje platformu, která šablona cíle projektu. Tento prvek určuje, že šablona projektu slouží k vytvoření [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikace.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[Vstemplate –](../extensibility/vstemplate-element-visual-studio-templates.md)|Požadovaný element.<br /><br /> Obsahuje všechna metadata pro šablony projektu, šablonu položky nebo starter kit.|  
  
## <a name="remarks"></a>Poznámky  
 `TemplateData` je požadovaný element.  
  
 Pokud Volitelný element není zadána, je použita výchozí hodnota pro daný element.  
  
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
            <ProjectItem>Form1.cs<ProjectItem>  
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

