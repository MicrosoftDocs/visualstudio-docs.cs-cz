---
title: Přidávání adresářů do dialogového okna Nový projekt | Dokumentace Microsoftu
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
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6a03e61cf3699cd45a7b4b8e6a7e5b7d192ca6de
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51769733"
---
# <a name="adding-directories-to-the-new-project-dialog-box"></a>Přidávání adresářů do dialogového okna Nový projekt
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Při vytváření nových typů projektů také můžete zaregistrovat nový adresář v **nový projekt** dialogové okno se zobrazí pro použití jako šablony. Následující příklad vysvětluje, jak zaregistrovat nový adresář, označované také jako uzel. V tomto příkladu jsou registrovány šablony vystavené VSPackage CLSID_Package. V důsledku toho na levé straně **nový projekt** dialogové okno nabízí přidání uzel s názvem určené Folder_Label_ResID prostředků. Tento prostředek je načtena z balíčku VSPackage satelitní knihovny DLL.  
  
 **Složky** hodnota představuje identifikátor GUID do složky, ve kterém se zobrazí uzel Folder_Label_ResID. V tomto příkladu představuje identifikátor GUID **ostatní projekty** složky **typy projektů** podokně **nový projekt** dialogové okno. Pokud **ostatní projekty** chybí hodnota, popisek je umístěn na nejvyšší úrovni.  
  
 Hodnota TemplatesDir Určuje úplnou cestu adresáře, který obsahuje šablony projektů. Tyto soubory mohou být .vsz soubory nebo soubory šablon typické ke klonování.  
  
 Pokud chcete zadat TemplatesLocalizedSubDir, musí být ID prostředku řetězce, který pojmenovává podadresáři TemplatesDir obsahující lokalizované šablony. Protože [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] načte prostředek řetězce ze satelitní knihovny DLL, máte-li každý satelitní knihovny DLL může obsahovat název jiné podadresáře. Hodnota SortPriority určuje prioritu třídění.  
  
```  
NoRemove NewProjectTemplates  
{  
    NoRemove TemplateDirs  
  {  
    ForceRemove %CLSID_Package%  
    {  
      ForceRemove /1 = s '#%Folder_Label_ResID%'  
      {  
        val Folder = s '{DCF2A94A-45B0-11D1-ADBF-00C04FB6BE4C}'  
        val TemplatesDir = s '%Template_Path%'  
        val TemplatesLocalizedSubDir = s '#100'  
        val SortPriority = d 1000  
      }  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Registrace šablon projektů a položek](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Přidávání položek do přidání nové položky v dialogových oknech](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Přidávání adresářů do dialogového okna Přidat novou položku](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)

