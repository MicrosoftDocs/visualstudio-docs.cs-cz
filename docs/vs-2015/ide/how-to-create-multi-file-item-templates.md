---
title: 'Postupy: vytváření šablon položek s více soubory | Dokumentace Microsoftu'
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
- Visual Studio templates, creating multi-file item templates
- multi-file item templates
- item templates, creating multi-file item templates
ms.assetid: fe3c4257-e383-4c80-b8af-c5c521959c33
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 00d7fbaa97172c98db61f93706f7e596bb22ddee
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49862174"
---
# <a name="how-to-create-multi-file-item-templates"></a>Postupy: Tvorba šablon položek s více soubory
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Šablony položek může zadat jenom jednu položku, ale někdy položky skládá z více souborů. Například šablonu položky formulářů Windows v jazyce Visual Basic vyžaduje následující tři soubory:  
  
- Soubor .vb, který obsahuje kód pro formulář.  
  
- A. Designer.vb, který obsahuje informace o návrháři formuláře.  
  
- Soubor .resx, který obsahuje vložené prostředky pro formulář.  
  
  Šablony položek s více soubory vyžadují parametry zajistit správné přípony názvů se používají při vytvoření položky v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Pokud vytvoříte pomocí šablony položky **exportovat šablonu** průvodce, tyto parametry jsou automaticky generovány a žádné další úpravy je povinný. Následující postup vysvětluje, jak používat parametry a ověřte, že jsou správné přípony názvů vytvořen.  
  
### <a name="to-manually-create-a-multi-file-item-template"></a>Ruční vytvoření šablony položek s více soubory  
  
1.  Vytvoření šablony položky by při vytváření šablony položky jedním souborem. Další informace najdete v tématu [postupy: vytváření šablon položek](../ide/how-to-create-item-templates.md).  
  
2.  Přidat `TargetFileName` atributy ke každému `ProjectItem` elementu. Nastavte hodnoty `TargetFileName` atributy $fileinputname$. *FileExtension*, kde *FileExtension* je příponu názvu souboru, který bude zahrnut v šabloně. Příklad:  
  
    ```  
    <ProjectItem TargetFileName="$fileinputname$.vb">  
        Form1.vb  
    </ProjectItem>  
    <ProjectItem TargetFileName="$fileinputname$.Designer.vb">  
        Form1.Designer.vb  
    </ProjectItem>  
    <ProjectItem TargetFileName="$fileinputname$.resx">  
        Form1.resx  
    </ProjectItem>  
    ```  
  
     Když je položka odvozená z této šablony se přidá do projektu, názvy souborů se podle název zadaný uživatelem **přidat novou položku** dialogové okno.  
  
3.  Vyberte soubory, které chcete zahrnout do vaší šablony, klikněte pravým tlačítkem na výběr, klikněte na tlačítko **odeslat**a potom klikněte na tlačítko **komprimovaná složka (metoda ZIP)**. Do souboru .zip jsou komprimované soubory, které jste vybrali.  
  
4.  Uložte soubor .zip v umístění šablon položek uživatele. Ve výchozím adresáři je Documents\Visual Studio *verze*\Templates\ItemTemplates\\. Další informace najdete v tématu [postupy: vyhledání a uspořádat šablony](../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] šablony formulářů Windows. Když je vytvořena položka na základě této šablony, názvy tři soubory vytvořené bude shodovat s názvem zadaného v **přidat novou položku** dialogové okno.  
  
```  
<VSTemplate Version="2.0.0" Type="Item"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-file Item Template</Name>  
        <Icon>Icon.ico</Icon>  
        <Description>An example of a multi-file item template</Description>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem TargetFileName="$fileinputname$.vb" SubType="Form">  
            Form1.vb  
        </ProjectItem>  
        <ProjectItem TargetFileName="$fileinputname$.Designer.vb">  
            Form1.Designer.vb  
        </ProjectItem>  
        <ProjectItem TargetFileName="$fileinputname$.resx">  
            Form1.resx  
        </ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Viz také  
 [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)   
 [Postupy: vytváření šablon položek](../ide/how-to-create-item-templates.md)   
 [Parametry šablony](../ide/template-parameters.md)   
 [Postupy: Nahrazení parametrů v šabloně](../ide/how-to-substitute-parameters-in-a-template.md)



