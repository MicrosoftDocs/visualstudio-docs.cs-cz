---
title: Odkaz na schéma šablon sady Visual Studio | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSTEMPLATE files
- Visual Studio templates, schema
- .vstemplate files
ms.assetid: 6f74a2d5-3811-43d6-8b10-eb5823ad8995
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3b49b15047d11e8d09690c90dd3011700481fcef
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817422"
---
# <a name="visual-studio-template-schema-reference"></a>Odkaz na schéma šablon sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento oddíl obsahuje informace o elementech XML v souborech .vstemplate, což jsou soubory, do nichž se ukládají metadata pro šablony projektů, šablony položek a úvodní sady.  
  
 Vlastní soubory .vstemplate můžete ověřit pomocí souboru vstemplate.xsd. Tento soubor je k dispozici na... \\ *Instalační složky sady visual Studio*\Xml\Schemas\1033\vstemplate.xsd.  
  
|Prvek|Podřízené elementy|Atributy|  
|-------------|--------------------|----------------|  
|[AppliesTo –](../extensibility/appliesto-element-visual-studio-templates.md)|Žádné|Žádné|  
|[Assembly (šablona)](../extensibility/assembly-element-visual-studio-templates.md)|--|--|  
|[Sestavení (rozšíření průvodce)](../extensibility/assembly-element-visual-studio-template-wizard-extension.md)|--|--|  
|[Buildprojectonload –](../extensibility/buildprojectonload-element-visual-studio-templates.md)|--|--|  
|[CreateInPlace](../extensibility/createinplace-visual-studio-templates.md)|--|--|  
|[Createnewfolder –](../extensibility/createnewfolder-element-visual-studio-templates.md)|--|--|  
|[CustomDataSignature –](../extensibility/customdatasignature-element-visual-studio-templates.md)|--|--|  
|[CustomParameter –](../extensibility/customparameter-element-visual-studio-templates.md)|--|Název<br /><br /> Hodnota|  
|[CustomParameters –](../extensibility/customparameters-element-visual-studio-templates.md)|CustomParameter|--|  
|[Defaultname –](../extensibility/defaultname-element-visual-studio-templates.md)|--|--|  
|[Popis](../extensibility/description-element-visual-studio-templates.md)|--|Balíček<br /><br /> ID|  
|[Enableeditoflocationfield –](../extensibility/enableeditoflocationfield-element-visual-studio-templates.md)|--|--|  
|[Enablelocationbrowsebutton –](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md)|--|--|  
|[Složka](../extensibility/folder-element-visual-studio-project-templates.md)|ProjectItem<br /><br /> Folder|Název|  
||[zastaralé]|--|  
|[FullClassName](../extensibility/fullclassname-element-visual-studio-template-wizard-extension.md)|--|--|  
|[Skryté](../extensibility/hidden-element-visual-studio-templates.md)|--|--|  
|[Ikona](../extensibility/icon-element-visual-studio-templates.md)|--|Balíček<br /><br /> ID|  
|[Locationfield –](../extensibility/locationfield-element-visual-studio-project-templates.md)|--|--|  
|[Locationfieldmruprefix –](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md)|--|--|  
|[Maxframeworkversion –](../extensibility/maxframeworkversion-element-visual-studio-templates.md)|--|--|  
|[Jméno](../extensibility/name-element-visual-studio-templates.md)|--|Balíček<br /><br /> ID|  
|[NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)|--|--|  
|[Previewimage –](../extensibility/previewimage-element-visual-studio-templates.md)|--|--|  
|[Projekt](../extensibility/project-element-visual-studio-templates.md)|Folder<br /><br /> ProjectItem|Soubor<br /><br /> TargetFileName<br /><br /> ReplaceParameters|  
|[Projectcollection –](../extensibility/projectcollection-element-visual-studio-templates.md)|ProjectTemplateLink<br /><br /> SolutionFolder|--|  
|[ProjectItem (šablony položek)](../extensibility/projectitem-element-visual-studio-item-templates.md)|--|SubType<br /><br /> CustomTool<br /><br /> ItemType<br /><br /> ReplaceParameters<br /><br /> TargetFileName|  
|[ProjectItem (šablony projektů)](../extensibility/projectitem-element-visual-studio-project-templates.md)|--|TargetFileName<br /><br /> ReplaceParameters<br /><br /> OpenInEditor<br /><br /> OpenOrder<br /><br /> OpenInWebBrowser<br /><br /> OpenInHelpBrowser|  
|[ProjectSubType –](../extensibility/projectsubtype-element-visual-studio-templates.md)|--|--|  
|[ProjectTemplateLink –](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|--|ProjectName|  
|[ProjectType](../extensibility/projecttype-element-visual-studio-templates.md)|--|--|  
|[PromptForSaveOnCreation –](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md)|--|--|  
|[Providedefaultname –](../extensibility/providedefaultname-element-visual-studio-templates.md)|--|--|  
|[Referenční informace](../extensibility/reference-element-visual-studio-templates.md)|Assembly|--|  
|[Odkazy](../extensibility/references-element-visual-studio-templates.md)|Odkaz|--|  
|[Requiredframeworkversion –](../extensibility/requiredframeworkversion-element-visual-studio-templates.md)|--|--|  
|[Requiredplatformversion –](../extensibility/requiredplatformversion-element-visual-studio-templates.md)|--|Version|  
|[Sdkreference –](../extensibility/sdkreference-element-visual-studio-templates.md)|--|Balíček|  
|[ShowByDefault](../extensibility/showbydefault-visual-studio-templates.md)|--|--|  
|[SolutionFolder –](../extensibility/solutionfolder-element-visual-studio-templates.md)|ProjectTemplateLink<br /><br /> SolutionFolder|Název|  
|[Pořadí řazení](../extensibility/sortorder-element-visual-studio-templates.md)|--|--|  
|[Supportscodeseparation –](../extensibility/supportscodeseparation-element-visual-studio-templates.md)|--|--|  
|[Supportslanguagedropdown –](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md)|--|--|  
|[Supportsmasterpage –](../extensibility/supportsmasterpage-element-visual-studio-templates.md)|--|--|  
|[Targetplatformname –](../extensibility/targetplatformname-element-visual-studio-templates.md)|RequiredPlatformVersion|--|  
|[TemplateContent –](../extensibility/templatecontent-element-visual-studio-templates.md)|ProjectCollection<br /><br /> Projekt<br /><br /> Odkazy<br /><br /> ProjectItem<br /><br /> CustomParameters|[Buildonload –](../extensibility/buildprojectonload-visual-studio-templates.md)|  
|[TemplateData –](../extensibility/templatedata-element-visual-studio-templates.md)|Název<br /><br /> Popis<br /><br /> Ikona<br /><br /> PreviewImage<br /><br /> ProjectType<br /><br /> ProjectSubType<br /><br /> TemplateID<br /><br /> TemplateGroupID<br /><br /> SortOrder<br /><br /> CreateNewFolder<br /><br /> DefaultName<br /><br /> ProvideDefaultName<br /><br /> PromptForSaveOnCreation<br /><br /> EnableLocationBrowseButton<br /><br /> EnableEditOfLocationField<br /><br /> Hidden<br /><br /> DisplayInParentCategories<br /><br /> LocationFieldMRUPrefix<br /><br /> NumberOfParentCategoriesToRollUp<br /><br /> CreateInPlace<br /><br /> BuildOnLoad<br /><br /> BuildProjectOnload<br /><br /> ShowByDefault<br /><br /> LocationField<br /><br /> SupportsMasterPage<br /><br /> SupportsCodeSeparation<br /><br /> SupportsLanguageDropDown<br /><br /> RequiredFrameworkVersion<br /><br /> FrameworkVersion<br /><br /> MaxFrameworkVersion<br /><br /> CustomDataSignature<br /><br /> TargetPlatformName|--|  
|[Templategroupid –](../extensibility/templategroupid-element-visual-studio-templates.md)|--|--|  
|[TemplateId –](../extensibility/templateid-element-visual-studio-templates.md)|--|--|  
|[Vstemplate –](../extensibility/vstemplate-element-visual-studio-templates.md)|TemplateData<br /><br /> TemplateContent<br /><br /> WizardExtension<br /><br /> WizardData|Typ<br /><br /> Version|  
|[WizardData –](../extensibility/wizarddata-element-visual-studio-templates.md)|--|Název|  
|[WizardExtension –](../extensibility/wizardextension-element-visual-studio-templates.md)|Assembly<br /><br /> FullClassName|--|  
  
## <a name="see-also"></a>Viz také  
 [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)   
 [Postupy: Vytváření startovních sad](../ide/how-to-create-starter-kits.md)